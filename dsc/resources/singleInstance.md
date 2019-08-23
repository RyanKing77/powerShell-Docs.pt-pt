---
ms.date: 06/12/2017
keywords: DSC, PowerShell, configuração, instalação
title: Escrever um recurso de DSC de instância única (melhor prática)
ms.openlocfilehash: 4d9e07c6aaa064f808a03d4252e8d352b82183ec
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986522"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="9d4d2-103">Escrever um recurso de DSC de instância única (melhor prática)</span><span class="sxs-lookup"><span data-stu-id="9d4d2-103">Writing a single-instance DSC resource (best practice)</span></span>

><span data-ttu-id="9d4d2-104">**Nota:** Este tópico descreve uma prática recomendada para definir um recurso de DSC que permite apenas uma única instância em uma configuração.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-104">**Note:** This topic describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="9d4d2-105">Atualmente, não há nenhum recurso interno de DSC para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-105">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="9d4d2-106">Isso pode ser alterado no futuro.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-106">That might change in the future.</span></span>

<span data-ttu-id="9d4d2-107">Há situações em que você não deseja permitir que um recurso seja usado várias vezes em uma configuração.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-107">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="9d4d2-108">Por exemplo, em uma implementação anterior do recurso [xTimeZone](https://github.com/PowerShell/xTimeZone) , uma configuração poderia chamar o recurso várias vezes, definindo o fuso horário para uma configuração diferente em cada bloco de recursos:</span><span class="sxs-lookup"><span data-stu-id="9d4d2-108">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

```powershell
Configuration SetTimeZone
{
    Param
    (
        [String[]]$NodeName = $env:COMPUTERNAME

    )

    Import-DSCResource -ModuleName xTimeZone


    Node $NodeName
    {
         xTimeZone TimeZoneExample
         {

            TimeZone = 'Eastern Standard Time'
         }

         xTimeZone TimeZoneExample2
         {

            TimeZone = 'Pacific Standard Time'

         }

    }
}
```

<span data-ttu-id="9d4d2-109">Isso ocorre devido à maneira como as chaves de recurso DSC funcionam.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-109">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="9d4d2-110">Um recurso deve ter pelo menos uma propriedade de chave.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-110">A resource must have at least one key property.</span></span> <span data-ttu-id="9d4d2-111">Uma instância de recurso será considerada exclusiva se a combinação dos valores de todas as suas propriedades de chave for exclusiva.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-111">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="9d4d2-112">Em sua implementação anterior, o recurso [xTimeZone](https://github.com/PowerShell/xTimeZone) tinha apenas uma propriedade--**timezone**, que era necessária para ser uma chave.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-112">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property--**TimeZone**, which was required to be a key.</span></span> <span data-ttu-id="9d4d2-113">Por isso, uma configuração como a anterior seria compilada e executada sem aviso.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-113">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="9d4d2-114">Cada um dos blocos de recursos **xTimeZone** é considerado exclusivo.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-114">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="9d4d2-115">Isso faria com que a configuração fosse aplicada repetidamente ao nó, alternando o fuso horário para frente e para trás.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-115">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="9d4d2-116">Para garantir que uma configuração possa definir o fuso horário para um nó de destino somente uma vez, o recurso foi atualizado para adicionar uma segunda propriedade, **IsSingleInstance**, que se tornou a propriedade de chave.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-116">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance**, that became the key property.</span></span>
<span data-ttu-id="9d4d2-117">O **IsSingleInstance** estava limitado a um único valor, "Sim" usando um **ValueMap**.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-117">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="9d4d2-118">O antigo esquema MOF para o recurso era:</span><span class="sxs-lookup"><span data-stu-id="9d4d2-118">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="9d4d2-119">O esquema MOF atualizado para o recurso é:</span><span class="sxs-lookup"><span data-stu-id="9d4d2-119">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="9d4d2-120">O script de recurso também foi atualizado para usar o novo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-120">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="9d4d2-121">Aqui, como o script de recurso foi alterado:</span><span class="sxs-lookup"><span data-stu-id="9d4d2-121">Here how the resource script was changed:</span></span>

```powershell
function Get-TargetResource
{
    [CmdletBinding()]
    [OutputType([Hashtable])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Get the current TimeZone
    $CurrentTimeZone = Get-TimeZone

    $returnValue = @{
        TimeZone = $CurrentTimeZone
        IsSingleInstance = 'Yes'
    }

    #Output the target resource
    $returnValue
}

function Set-TargetResource
{
    [CmdletBinding()]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output the result of Get-TargetResource function.
    $CurrentTimeZone = Get-TimeZone

    Write-Verbose -Message "Replace the System Time Zone to $TimeZone"
    
    try
    {
        if($CurrentTimeZone -ne $TimeZone)
        {
            Write-Verbose -Verbose "Setting the TimeZone"
            Set-TimeZone -TimeZone $TimeZone
        }
        else
        {
            Write-Verbose -Verbose "TimeZone already set to $TimeZone"
        }
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose -Verbose $ErrorMsg
    }
}


function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([Boolean])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output from Get-TargetResource
    $CurrentTimeZone = Get-TimeZone

    if($TimeZone -eq $CurrentTimeZone)
    {
        return $true
    }
    else
    {
        return $false
    }
}

Function Get-TimeZone {
    [CmdletBinding()]
    param()

    & tzutil.exe /g
}

Function Set-TimeZone {
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true)]
        [System.String]
        $TimeZone
    )

    try
    {
        & tzutil.exe /s $TimeZone
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose $ErrorMsg
    }
}

Export-ModuleMember -Function *-TargetResource
```

<span data-ttu-id="9d4d2-122">Observe que a propriedade **timezone** não é mais uma chave.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-122">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="9d4d2-123">Agora, se uma configuração tentar definir o fuso horário duas vezes (usando dois blocos **xTimeZone** diferentes com valores de **fuso horário** diferentes), tentar compilar a configuração causará um erro:</span><span class="sxs-lookup"><span data-stu-id="9d4d2-123">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

```powershell
Test-ConflictingResources : A conflict was detected between resources '[xTimeZone]TimeZoneExample (::15::10::xTimeZone)' and
'[xTimeZone]TimeZoneExample2 (::22::10::xTimeZone)' in node 'CONTOSO-CLIENT'. Resources have identical key properties but there are differences in the
following non-key properties: 'TimeZone'. Values 'Eastern Standard Time' don't match values 'Pacific Standard Time'. Please update these property
values so that they are identical in both cases.
At line:271 char:9
+         Test-ConflictingResources $keywordName $canonicalizedValue $k ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : ConflictingDuplicateResource,Test-ConflictingResources
Errors occurred while processing configuration 'SetTimeZone'.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3705 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (SetTimeZone:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```
