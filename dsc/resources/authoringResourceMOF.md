---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Escrever um recurso personalizado do DSC com o MOF
ms.openlocfilehash: f243c3e3297711e6f6346a0f813a9c017fe227c3
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059733"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a>Escrever um recurso personalizado do DSC com o MOF

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Neste tópico, iremos definir o esquema para um recurso personalizado do Windows PowerShell Desired State Configuration (DSC) num ficheiro MOF e, implementar o recurso num arquivo de script do Windows PowerShell. Este recurso personalizado destina-se a criação e manutenção de um web site.

## <a name="creating-the-mof-schema"></a>Criar o esquema MOF

O esquema define as propriedades do seu recurso que podem ser configuradas por um script de configuração de DSC.

### <a name="folder-structure-for-a-mof-resource"></a>Estrutura de pastas para um recurso MOF

Para implementar um recurso personalizado do DSC com um esquema MOF, crie a seguinte estrutura de pasta. O esquema da MOF é definido no ficheiro Demo_IISWebsite.schema.mof, e o script de recurso é definido no Demo_IISWebsite.psm1. Opcionalmente, pode criar um ficheiro de manifesto (. psd1) do módulo.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

Tenha em atenção que é necessário criar uma pasta denominada DSCResources sob a pasta de nível superior e que a pasta para cada recurso tem de ter o mesmo nome que o recurso.

### <a name="the-contents-of-the-mof-file"></a>O conteúdo do ficheiro MOF

Segue-se um ficheiro MOF de exemplo que pode ser utilizado para um recurso de Web site personalizado. Para seguir este exemplo, salvar esse esquema num arquivo e chame o arquivo *Demo_IISWebsite.schema.mof*.

```
[ClassVersion("1.0.0"), FriendlyName("Website")]
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

Tenha em atenção o seguinte sobre o código anterior:

* `FriendlyName` Define o nome que pode usar para fazer referência a este recurso personalizado em scripts de configuração de DSC. Neste exemplo, `Website` é equivalente ao nome amigável `Archive` para o recurso de arquivo interno.
* A classe definir para o recurso personalizado deve ser derivados dos `OMI_BaseResource`.
* O qualificador de tipo, `[Key]`, numa propriedade indica que esta propriedade irá identificar exclusivamente a instância de recurso. Pelo menos um `[Key]` propriedade é necessária.
* O `[Required]` qualificador indica que a propriedade é necessária (tem de ser especificado um valor em qualquer script de configuração que utiliza este recurso).
* O `[write]` qualificador indica que esta propriedade é opcional ao usar o recurso personalizado num script de configuração. O `[read]` qualificador indica que uma propriedade não pode ser definida por uma configuração e destina-se apenas a fins de relatórios.
* `Values` restringe os valores que podem ser atribuídos à propriedade à lista de valores definidos no `ValueMap`. Para obter mais informações, consulte [ValueMap e qualificadores de valor](/windows/desktop/WmiSdk/value-map).
* Incluindo uma propriedade chamada `Ensure` com os valores `Present` e `Absent` no seu recurso, é recomendado como uma forma de manter um estilo consistente com os recursos de DSC incorporados.
* Nomeie o arquivo de esquema para o seu recurso personalizado da seguinte forma: `classname.schema.mof`, onde `classname` é o identificador após o `class` palavra-chave em sua definição de esquema.

### <a name="writing-the-resource-script"></a>Escrever o script de recursos

O script de recurso implementa a lógica do recurso. Neste módulo, tem de incluir três funções chamadas **Get-TargetResource**, **conjunto TargetResource**, e **teste TargetResource**. Todas as três funções tem de executar um conjunto de parâmetros é idêntico ao conjunto de propriedades definidas no esquema do MOF que criou para o seu recurso. Neste documento, este conjunto de propriedades é referido como "Propriedades de recurso." Store essas três funções num arquivo chamadas <ResourceName>. psm1. No exemplo seguinte, as funções são armazenadas num arquivo chamado Demo_IISWebsite.psm1.

> [!NOTE]
> Ao executar o mesmo script de configuração no recurso mais de uma vez, deverá receber sem erros e o recurso deve permanecer no mesmo Estado de execução do script de uma vez. Para tal, certifique-se de que sua **Get-TargetResource** e **teste TargetResource** deixe de funções, o recurso inalterado e esse invocando o **conjunto-TargetResource**funcionar mais do que uma vez numa sequência com o mesmo parâmetro de valores equivale sempre ao invocá-lo uma vez.

Na **Get-TargetResource** implementação de função, utilize os valores de propriedade de recursos principais que são fornecidos como parâmetros para verificar o estado da instância do recurso especificado. Esta função tem de devolver uma tabela de hash que lista todas as propriedades de recurso como chaves e valores reais dessas propriedades como os valores correspondentes. O código a seguir fornece um exemplo.

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
function Get-TargetResource
{
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name;
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }

        $getTargetResourceResult;
}
```

Dependendo dos valores que são especificados para as propriedades de recurso no script de configuração, o **Set-TargetResource** tem de efetuar um dos seguintes:

* Criar um novo Web site
* Atualizar um site existente
* Eliminar um site existente

O exemplo a seguir ilustra isso.

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine.
function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

Por fim, o **teste TargetResource** função tem de ter o mesmo parâmetro definido como **Get-TargetResource** e **conjunto TargetResource**. Na sua implementação do **teste TargetResource**, verificar o estado da instância do recurso que está especificado nos parâmetros de chave. Se o estado real da instância do recurso não coincide com os valores especificados no conjunto de parâmetros, devolver **$false**. Caso contrário, devolver **$true**.

O seguinte código implementa a **teste TargetResource** função.

```powershell
function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[parameter(Mandatory = $true)]
[System.String]
$Name,

[parameter(Mandatory = $true)]
[System.String]
$PhysicalPath,

[ValidateSet("Started","Stopped")]
[System.String]
$State,

[System.String[]]
$Protocol,

[System.String[]]
$BindingData,

[System.String]
$ApplicationPool
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result
}
```

**Tenha em atenção**: Para depuração mais fácil, utilize o **Write-Verbose** cmdlet em sua implementação das três funções anteriores.
>Este cmdlet escreve texto no fluxo de mensagens verbosas.
>Por predefinição, o fluxo de mensagens verbosas não for apresentado, mas pode exibi-lo ao alterar o valor do **$VerbosePreference** variável ou utilizando o **verboso** parâmetro nos cmdlets de DSC = novo.

### <a name="creating-the-module-manifest"></a>Criando o manifesto de módulo

Por último, utilize o **New-ModuleManifest** cmdlet para definir um <ResourceName>ficheiro. psd1 para seu módulo de recurso personalizado. Quando invoca este cmdlet, referencia o ficheiro do módulo (. psm1) de script descrito na secção anterior. Incluem **Get-TargetResource**, **conjunto TargetResource**, e **teste TargetResource** na lista de funções para exportar. Segue-se um ficheiro de manifesto de exemplo.

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

## <a name="supporting-psdscrunascredential"></a>Suporte PsDscRunAsCredential

>**Nota:** **PsDscRunAsCredential** é suportada no PowerShell 5.0 e posterior.

O **PsDscRunAsCredential** propriedade pode ser utilizada em [configurações de DSC](../configurations/configurations.md) bloco de recurso para especificar que o recurso deve ser executado num conjunto especificado de credenciais.
Para obter mais informações, consulte [a executar o DSC com as credenciais de utilizador](../configurations/runAsUser.md).

Para acessar o contexto de utilizador a partir de um recurso personalizado, pode utilizar a variável automática `$PsDscContext`.

Por exemplo, o código a seguir escreveria o contexto do usuário sob a qual o recurso está em execução no fluxo de saída detalhada:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a>Reiniciar o nó

Se as ações executadas em seu `Set-TargetResource` função requerem um reinício, pode usar um sinalizador global para informar o LCM para reiniciar o nó. Este reinício ocorre imediatamente após o `Set-TargetResource` função for concluída.

Dentro de seu `Set-TargetResource` de função, adicione a seguinte linha de código.

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

Para que o MMC para reiniciar o nó, o **RebootNodeIfNeeded** sinalizador precisa ser definida `$true`. O **ActionAfterReboot** definição também deve ser definida como **ContinueConfiguration**, que é a predefinição. Para obter mais informações sobre como configurar o LCM, consulte [configurar o Gestor de configuração Local](../managing-nodes/metaConfig.md), ou [configurar o Gestor de configuração Local (v4)](../managing-nodes/metaConfig4.md).
