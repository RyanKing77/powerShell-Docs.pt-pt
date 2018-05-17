---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Escrever um recurso de DSC de instância única (melhor prática)
ms.openlocfilehash: 9494964b1b13eaa082ad5cbc279b4586bb7211cc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a>Escrever um recurso de DSC de instância única (melhor prática)

>**Nota:** este tópico descreve uma melhor prática para definir um recurso de DSC que permite apenas uma única instância numa configuração. Atualmente, não há nenhuma funcionalidade DSC incorporada para efetuar este procedimento. Que poderá alterar no futuro.

Existem situações em que não pretende permitir que um recurso a ser utilizada várias vezes numa configuração. Por exemplo, numa implementação anterior do [xTimeZone](https://github.com/PowerShell/xTimeZone) , uma configuração foi chamada de recursos do recurso várias vezes, definir o fuso horário para uma definição diferente em cada bloco de recursos:

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

Isto é devido a forma como as chaves de recursos de DSC funcionar. Um recurso tem de ter, pelo menos, uma propriedade chave. Uma instância de recurso é considerada exclusiva se a combinação de valores de todas as respetivas propriedades chaves é exclusiva. Na sua implementação anterior, o [xTimeZone](https://github.com/PowerShell/xTimeZone) recurso tinha apenas uma propriedade –**fuso horário**, que é exigido para ser uma chave. Por este motivo, uma configuração, tal como o acima seria compilar e executar sem aviso. Cada um do **xTimeZone** blocos de recurso é considerado exclusivo. Isto fará com que a configuração ser aplicada repetidamente para o nó, ciclos o fuso horário anterior e descritos.

Para se certificar de que uma configuração foi possível definir o fuso horário para um nó de destino apenas uma vez, o recurso foi atualizado para adicionar uma segunda propriedade, **IsSingleInstance**, que está a propriedade de chave.
O **IsSingleInstance** estava limitado a um valor único, "Sim", utilizando um **ValueMap**. O esquema MOF antigo para o recurso era:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

O esquema MOF atualizado para o recurso é:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

O script de recursos também foi atualizado para utilizar o novo parâmetro. Eis o script de recurso antigo:

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

Tenha em atenção que o **fuso horário** propriedade já não é uma chave. Agora, se uma configuração de tentar definir o fuso horário duas vezes (ao utilizar dois diferentes **xTimeZone** blocos com diferentes **fuso horário** valores), a tentar a configuração de compilação fará com que um erro:

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