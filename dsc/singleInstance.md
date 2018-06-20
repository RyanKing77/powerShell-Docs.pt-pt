---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Escrever um recurso de DSC de instância única (melhor prática)
ms.openlocfilehash: 9494964b1b13eaa082ad5cbc279b4586bb7211cc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218370"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="221ba-103">Escrever um recurso de DSC de instância única (melhor prática)</span><span class="sxs-lookup"><span data-stu-id="221ba-103">Writing a single-instance DSC resource (best practice)</span></span>

><span data-ttu-id="221ba-104">**Nota:** este tópico descreve uma melhor prática para definir um recurso de DSC que permite apenas uma única instância numa configuração.</span><span class="sxs-lookup"><span data-stu-id="221ba-104">**Note:** This topic describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="221ba-105">Atualmente, não há nenhuma funcionalidade DSC incorporada para efetuar este procedimento.</span><span class="sxs-lookup"><span data-stu-id="221ba-105">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="221ba-106">Que poderá alterar no futuro.</span><span class="sxs-lookup"><span data-stu-id="221ba-106">That might change in the future.</span></span>

<span data-ttu-id="221ba-107">Existem situações em que não pretende permitir que um recurso a ser utilizada várias vezes numa configuração.</span><span class="sxs-lookup"><span data-stu-id="221ba-107">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="221ba-108">Por exemplo, numa implementação anterior do [xTimeZone](https://github.com/PowerShell/xTimeZone) , uma configuração foi chamada de recursos do recurso várias vezes, definir o fuso horário para uma definição diferente em cada bloco de recursos:</span><span class="sxs-lookup"><span data-stu-id="221ba-108">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

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

<span data-ttu-id="221ba-109">Isto é devido a forma como as chaves de recursos de DSC funcionar.</span><span class="sxs-lookup"><span data-stu-id="221ba-109">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="221ba-110">Um recurso tem de ter, pelo menos, uma propriedade chave.</span><span class="sxs-lookup"><span data-stu-id="221ba-110">A resource must have at least one key property.</span></span> <span data-ttu-id="221ba-111">Uma instância de recurso é considerada exclusiva se a combinação de valores de todas as respetivas propriedades chaves é exclusiva.</span><span class="sxs-lookup"><span data-stu-id="221ba-111">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="221ba-112">Na sua implementação anterior, o [xTimeZone](https://github.com/PowerShell/xTimeZone) recurso tinha apenas uma propriedade –**fuso horário**, que é exigido para ser uma chave.</span><span class="sxs-lookup"><span data-stu-id="221ba-112">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property--**TimeZone**, which was required to be a key.</span></span> <span data-ttu-id="221ba-113">Por este motivo, uma configuração, tal como o acima seria compilar e executar sem aviso.</span><span class="sxs-lookup"><span data-stu-id="221ba-113">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="221ba-114">Cada um do **xTimeZone** blocos de recurso é considerado exclusivo.</span><span class="sxs-lookup"><span data-stu-id="221ba-114">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="221ba-115">Isto fará com que a configuração ser aplicada repetidamente para o nó, ciclos o fuso horário anterior e descritos.</span><span class="sxs-lookup"><span data-stu-id="221ba-115">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="221ba-116">Para se certificar de que uma configuração foi possível definir o fuso horário para um nó de destino apenas uma vez, o recurso foi atualizado para adicionar uma segunda propriedade, **IsSingleInstance**, que está a propriedade de chave.</span><span class="sxs-lookup"><span data-stu-id="221ba-116">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance**, that became the key property.</span></span>
<span data-ttu-id="221ba-117">O **IsSingleInstance** estava limitado a um valor único, "Sim", utilizando um **ValueMap**.</span><span class="sxs-lookup"><span data-stu-id="221ba-117">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="221ba-118">O esquema MOF antigo para o recurso era:</span><span class="sxs-lookup"><span data-stu-id="221ba-118">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="221ba-119">O esquema MOF atualizado para o recurso é:</span><span class="sxs-lookup"><span data-stu-id="221ba-119">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="221ba-120">O script de recursos também foi atualizado para utilizar o novo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="221ba-120">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="221ba-121">Eis o script de recurso antigo:</span><span class="sxs-lookup"><span data-stu-id="221ba-121">Here is the old resource script:</span></span>

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
    [CmdletBinding(SupportsShouldProcess=$true)]
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

    if($PSCmdlet.ShouldProcess("'$TimeZone'","Replace the System Time Zone"))
    {
        try
        {
            if($CurrentTimeZone -ne $TimeZone)
            {
                Write-Verbose -Verbose "Setting the TimeZone"
                Set-TimeZone -TimeZone $TimeZone}
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

<span data-ttu-id="221ba-122">Tenha em atenção que o **fuso horário** propriedade já não é uma chave.</span><span class="sxs-lookup"><span data-stu-id="221ba-122">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="221ba-123">Agora, se uma configuração de tentar definir o fuso horário duas vezes (ao utilizar dois diferentes **xTimeZone** blocos com diferentes **fuso horário** valores), a tentar a configuração de compilação fará com que um erro:</span><span class="sxs-lookup"><span data-stu-id="221ba-123">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

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