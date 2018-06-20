---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Escrever um recurso personalizado de DSC com MOF
ms.openlocfilehash: 50b5f2eddbac4571f5351b32648d45c54ded167e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189640"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a>Escrever um recurso personalizado de DSC com MOF

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

Neste tópico, iremos definir o esquema para um recurso personalizado de configuração de estado pretendido do Windows PowerShell (DSC) num ficheiro MOF e implementar o recurso de um ficheiro de script do Windows PowerShell. Este recurso personalizado destina-se a criação e manutenção de um web site.

## <a name="creating-the-mof-schema"></a>Criar o esquema MOF

O esquema define as propriedades dos seus recursos que podem ser configuradas por um script de configuração de DSC.

### <a name="folder-structure-for-a-mof-resource"></a>Estrutura de pastas para um recurso MOF

Para implementar um recurso personalizado de DSC com um esquema MOF, crie a seguinte estrutura de pasta. O esquema MOF está definido no ficheiro Demo_IISWebsite.schema.mof e o script de recursos está definido no Demo_IISWebsite.psm1. Opcionalmente, pode criar um ficheiro de manifesto (. psd1) do módulo.

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

Tenha em atenção que é necessário criar uma pasta denominada DSCResources sob a pasta de nível superior e que a pasta para cada recurso têm de ter o mesmo nome que o recurso.

### <a name="the-contents-of-the-mof-file"></a>O conteúdo do ficheiro MOF

Segue-se um ficheiro MOF de exemplo que pode ser utilizado para um recurso de Web site personalizado. Para seguir este exemplo, guarde este esquema de um ficheiro e chamar o ficheiro *Demo_IISWebsite.schema.mof*.

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

* `FriendlyName` Define o nome que pode utilizar para fazer referência a este recurso personalizado em scripts de configuração de DSC. Neste exemplo, `Website` é equivalente ao nome amigável `Archive` para o recurso de arquivo incorporado.
* A classe definir para o recurso personalizado tem de derivar de `OMI_BaseResource`.
* O qualificador do tipo, `[Key]`, uma propriedade indica que esta propriedade identifiquem exclusivamente a instância de recurso. Pelo menos um `[Key]` propriedade é necessária.
* O `[Required]` qualificador indica que a propriedade é necessária (um valor tem de ser especificado qualquer script de configuração que utiliza este recurso).
* O `[write]` qualificador indica que esta propriedade é opcional quando o recurso personalizado num script de configuração. O `[read]` qualificador indica que uma propriedade não pode ser definida por uma configuração e, para fins de relatórios.
* `Values` restringe os valores que podem ser atribuídos a propriedade à lista de valores definidos no `ValueMap`. Para obter mais informações, consulte [ValueMap e qualificadores de valor](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).
* Incluindo uma propriedade denominada `Ensure` com valores `Present` e `Absent` no seu recurso é recomendado como uma forma para manter um estilo consistente com os recursos de DSC incorporados.
* Nome do ficheiro de esquema para o seu recurso personalizado da seguinte forma: `classname.schema.mof`, onde `classname` é o identificador que se segue o `class` palavra-chave na definição de esquema.

### <a name="writing-the-resource-script"></a>Escrever o script de recursos

O script de recurso implementa a lógica do recurso. Este módulo, tem de incluir três funções chamadas **Get-TargetResource**, **conjunto TargetResource**, e **teste TargetResource**. Todos os três funções tem de colocar um conjunto de parâmetros é idêntico ao conjunto de propriedades definida no esquema MOF que criou para o seu recurso. Neste documento, este conjunto de propriedades é referido como "Propriedades de recurso." Arquivo estas três funções num ficheiro denominadas <ResourceName>. psm1. No exemplo seguinte, as funções são armazenadas num ficheiro denominado Demo_IISWebsite.psm1.

> **Tenha em atenção**: quando executar o mesmo script de configuração no seu recurso mais do que uma vez, deverá receber sem erros e de recursos devem permanecer no mesmo estado como executar o script de uma vez. Para tal, certifique-se de que o **Get-TargetResource** e **teste TargetResource** deixe de funções inalterado do recurso e que invocar o **Set-TargetResource**funcionar mais do que uma vez numa sequência com o mesmo parâmetro de valores é sempre equivalente ao invocar, uma vez.

No **Get-TargetResource** implementação de função, utilize os valores de propriedade de chave de recurso que são fornecidos como parâmetros para verificar o estado da instância do recurso especificado. Esta função tem de devolver uma tabela hash que apresenta uma lista de todas as propriedades de recurso como chaves e os valores reais destas propriedades como os valores correspondentes. O código seguinte fornece um exemplo.

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

Consoante os valores que são especificados para as propriedades de recurso no script de configuração, o **conjunto TargetResource** tem de efetuar um dos seguintes:

* Criar um novo Web site
* Atualizar um site existente
* Eliminar um Web site existente

O exemplo a seguir ilustra este.

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

Por fim, o **teste TargetResource** função tem de ter o mesmo parâmetro definido como **Get-TargetResource** e **conjunto TargetResource**. Na sua implementação do **teste TargetResource**, verifique o estado da instância de recurso que foi especificado nos parâmetros de chaves. Se o estado real da instância do recurso não correspondem aos valores especificados no conjunto de parâmetros, devolver **$false**. Caso contrário, devolve **$true**.

O seguinte código implementa o **teste TargetResource** função.

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

**Tenha em atenção**: para depuração mais fácil, utilize o **Write-Verbose** cmdlet na sua implementação das três funções anteriores.
>Este cmdlet escreve o texto no fluxo de mensagens verbosas.
>Por predefinição, o fluxo de mensagens verbosas não for apresentado, mas pode apresentá-lo alterando o valor da **$VerbosePreference** variável ou utilizando o **verboso** parâmetro os cmdlets do DSC = novos.

### <a name="creating-the-module-manifest"></a>Criar o manifesto de módulo

Por último, utilize o **New-ModuleManifest** cmdlet para definir um <ResourceName>. psd1 ficheiro para o módulo de recurso personalizado. Quando invocar este cmdlet, referencia o ficheiro de script do módulo (. psm1) descrito na secção anterior. Incluir **Get-TargetResource**, **conjunto TargetResource**, e **teste TargetResource** na lista de funções para exportar. Segue-se um ficheiro de manifesto de exemplo.

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

O **PsDscRunAsCredential** propriedade pode ser utilizada em [configurações de DSC](configurations.md) blocos de recurso para especificar que o recurso deve ser executado sob um conjunto especificado de credenciais.
Para obter mais informações, consulte [DSC em execução com as credenciais de utilizador](runAsUser.md).

Para aceder ao contexto de utilizador a partir de um recurso personalizado, pode utilizar a variável automática `$PsDscContext`.

Por exemplo o seguinte código teria de escrever o contexto de utilizador na qual o recurso está em execução no fluxo de saída verbosa:

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```