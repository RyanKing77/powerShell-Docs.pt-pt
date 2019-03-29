---
ms.date: 03/28/2019
contributor: manikb
keywords: cmdlet do powershell do galeria, psget
title: Módulos com edições do PowerShell compatíveis
ms.openlocfilehash: 425588c168a4f864fdc0c52aa53cfd748b80dc98
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623845"
---
# <a name="modules-with-compatible-powershell-editions"></a>Módulos com edições do PowerShell compatíveis

Começando na versão 5.1, o PowerShell está disponível nas diferentes edições que denotam conjuntos de funcionalidade e compatibilidade de plataforma variados.

- **Edição Desktop:** Criado no .NET Framework, aplica-se para o Windows PowerShell v4.0 e abaixo, bem como o Windows PowerShell 5.1 no ambiente de trabalho do Windows, Windows Server, Windows Server Core e a maioria das outras edições do Windows.
- **Edição Core:** Incorporada no .NET Core, aplica-se para o PowerShell Core 6.0 e superior, bem como o Windows PowerShell 5.1 nos requisitos de espaço reduzido das edições do Windows, tais como Windows IoT e Windows Nanoserver.

Para obter mais informações sobre edições do PowerShell, consulte [about_PowerShell_Editions][].

## <a name="declaring-compatible-editions"></a>Declarando edições compatíveis

Os autores de módulo podem declarar os módulos para torná-los compatíveis com uma ou mais edições do PowerShell com a chave de manifesto de módulo CompatiblePSEditions. Esta chave apenas é suportada no PowerShell 5.1 ou posterior.

> [!NOTE]
> Depois de um manifesto de módulo é especificado com a chave de CompatiblePSEditions, ele não pode ser importado no PowerShell versões 4 e abaixo.

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```Output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

Ao obter uma lista de módulos disponíveis, pode filtrar a lista por edição do PowerShell.

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```Output
Desktop
Core
```

## <a name="targeting-multiple-editions"></a>Direcionamento várias edições

Os autores de módulo podem publicar um direcionamento de módulo único para cada um, ou ambas as edições do PowerShell (ambiente de trabalho e Core).

Um mesmo módulo pode trabalhar em edições de ambiente de trabalho e Core, nesse módulo tem de adicionar a lógica necessária em qualquer um dos RootModule ou no manifesto do módulo usando a variável de $PSEdition autor. Módulos podem ter dois conjuntos de DLLs compiladas destinados a CoreCLR e FullCLR. Aqui estão as duas opções para empacotar seu módulo com a lógica para carregar dlls adequada.

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a>Opção 1: Empacotando um módulo para destinados a várias versões e várias edições do PowerShell

Conteúdo da pasta de módulo

- Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- PSScriptAnalyzer.psd1
- PSScriptAnalyzer.psm1
- ScriptAnalyzer.format.ps1xml
- ScriptAnalyzer.types.ps1xml
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- en-US\about_PSScriptAnalyzer.help.txt
- en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- Settings\CmdletDesign.psd1
- Settings\DSC.psd1
- Settings\ScriptFunctions.psd1
- Settings\ScriptingStyle.psd1
- Settings\ScriptSecurity.psd1

Conteúdo do arquivo de PSScriptAnalyzer.psd1

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

Abaixo lógica carrega os assemblies necessários, consoante a edição atual ou a versão.

Conteúdo do arquivo de PSScriptAnalyzer.psm1:

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}
```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a>Opção 2: Utilizar a variável $PSEdition no ficheiro PSD1 para carregar as DLLs adequados e os módulos/necessária para aninhados

No PS 5.1 ou mais recente, $PSEdition de variável global é permitida no arquivo de manifesto do módulo. Usando esta variável, autor de módulos pode especificar os valores condicionais no arquivo de manifesto do módulo. É possível referenciar a variável $PSEdition no modo de idioma restrito ou uma secção de dados.

> [!NOTE]
> Depois de um manifesto de módulo for especificado com a chave de CompatiblePSEditions ou utiliza `$PSEdition` variável, ele não pode ser importado em versões mais baixas do PowerShell.

Ficheiro de manifesto de módulo de exemplo com a chave de CompatiblePSEditions

```powershell
@{
    # Script module or binary module file associated with this manifest.
    RootModule = if($PSEdition -eq 'Core')
    {
        'coreclr\MyCoreClrRM.dll'
    }
    else # Desktop
    {
        'clr\MyFullClrRM.dll'
    }

    # Supported PSEditions
    CompatiblePSEditions = 'Desktop', 'Core'

    # Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
    NestedModules = if($PSEdition -eq 'Core')
    {
        'coreclr\MyCoreClrNM1.dll',
        'coreclr\MyCoreClrNM2.dll'
    }
    else # Desktop
    {
        'clr\MyFullClrNM1.dll',
        'clr\MyFullClrNM2.dll'
    }
}
```

### <a name="module-contents"></a>Conteúdo do módulo

```powershell
dir -Recurse
```

```Output
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
d-----    7/5/2016   1:37 PM          clr
d-----    7/5/2016   1:36 PM          coreclr
-a----    7/5/2016   1:34 PM     4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode           LastWriteTime    Length Name
----           -------------    ------ ----
-a----    7/5/2016   1:35 PM         0 MyFullClrNM1.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrNM2.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM1.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM2.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrRM.dl
```

Os utilizadores da galeria do PowerShell podem encontrar a lista de módulos suportado numa edição específica do PowerShell, utilizando etiquetas PSEdition_Desktop e PSEdition_Core.

Módulos sem etiquetas PSEdition_Desktop e PSEdition_Core são considerados como funcionam bem em edições de ambiente de trabalho do PowerShell.

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a>Obter mais detalhes

[Scripts com Edições do PowerShell](script-psedition-support.md)

[Suporte de edições do PowerShell no PowerShellGallery](../how-to/finding-packages/searching-by-compatibility.md)

[Atualizar o manifesto do módulo](/powershell/module/powershellget/update-modulemanifest)

[about_PowerShell_Editions][]

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
