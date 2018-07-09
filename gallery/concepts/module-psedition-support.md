---
ms.date: 06/12/2017
contributor: manikb
keywords: cmdlet do powershell do galeria, psget
title: Módulos com edições do PowerShell compatíveis
ms.openlocfilehash: 653cfa82be9d0150da8d8765c96e35be99497262
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892326"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="fe57c-103">Módulos com edições do PowerShell compatíveis</span><span class="sxs-lookup"><span data-stu-id="fe57c-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="fe57c-104">Começando na versão 5.1, o PowerShell está disponível nas diferentes edições que denotam conjuntos de funcionalidade e compatibilidade de plataforma variados.</span><span class="sxs-lookup"><span data-stu-id="fe57c-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="fe57c-105">**Edição Desktop:** incorporada no .NET Framework e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço total do Windows, tais como Server Core e o Ambiente de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="fe57c-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="fe57c-106">**Edição Core:** incorporada no .NET Core e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço reduzido do Windows, tais como Servidor Nano e o IoT do Windows.</span><span class="sxs-lookup"><span data-stu-id="fe57c-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="the-running-edition-of-powershell-is-shown-in-the-psedition-property-of-psversiontable"></a><span data-ttu-id="fe57c-107">A edição em execução do PowerShell é apresentada na propriedade PSEdition da $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="fe57c-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

```powershell
$PSVersionTable
```

```output
Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

## <a name="module-authors-can-declare-their-modules-to-be-compatible-with-one-or-more-powershell-editions-using-the-compatiblepseditions-module-manifest-key-this-key-is-only-supported-on-powershell-51-or-later"></a><span data-ttu-id="fe57c-108">Os autores de módulo podem declarar os módulos para torná-los compatíveis com uma ou mais edições do PowerShell com a chave de manifesto de módulo CompatiblePSEditions.</span><span class="sxs-lookup"><span data-stu-id="fe57c-108">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="fe57c-109">Esta chave apenas é suportada no PowerShell 5.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="fe57c-109">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="fe57c-110">Depois de um manifesto de módulo é especificado com a chave de CompatiblePSEditions, não pode ser importado em versões mais baixas do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe57c-110">Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on lower versions of PowerShell.</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

<span data-ttu-id="fe57c-111">Ao obter uma lista de módulos disponíveis, pode filtrar a lista por edição do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe57c-111">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```output
    Directory: C:\Program Files\WindowsPowerShell\Modules


ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```output
Desktop
Core
```

## <a name="module-authors-can-publish-a-single-module-targeting-to-either-or-both-powershell-editions-desktop-and-core"></a><span data-ttu-id="fe57c-112">Os autores de módulo podem publicar um direcionamento de módulo único para cada um, ou ambas as edições do PowerShell (ambiente de trabalho e núcleos)</span><span class="sxs-lookup"><span data-stu-id="fe57c-112">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core)</span></span>

<span data-ttu-id="fe57c-113">Um mesmo módulo pode trabalhar em edições de ambiente de trabalho e Core, nesse módulo tem de adicionar a lógica necessária em qualquer um dos RootModule ou no manifesto do módulo usando a variável de $PSEdition autor.</span><span class="sxs-lookup"><span data-stu-id="fe57c-113">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span>
<span data-ttu-id="fe57c-114">Módulos podem ter dois conjuntos de DLLs compiladas destinados a CoreCLR e FullCLR.</span><span class="sxs-lookup"><span data-stu-id="fe57c-114">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span>
<span data-ttu-id="fe57c-115">Aqui estão as duas opções para empacotar seu módulo com a lógica para carregar dlls adequada.</span><span class="sxs-lookup"><span data-stu-id="fe57c-115">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="fe57c-116">Opção 1: Empacotando um módulo para destinados a várias versões e várias edições do PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe57c-116">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

#### <a name="module-folder-contents"></a><span data-ttu-id="fe57c-117">Conteúdo da pasta de módulo</span><span class="sxs-lookup"><span data-stu-id="fe57c-117">Module folder contents</span></span>

- <span data-ttu-id="fe57c-118">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="fe57c-118">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="fe57c-119">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="fe57c-119">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="fe57c-120">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="fe57c-120">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="fe57c-121">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="fe57c-121">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="fe57c-122">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="fe57c-122">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="fe57c-123">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="fe57c-123">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="fe57c-124">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="fe57c-124">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="fe57c-125">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="fe57c-125">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="fe57c-126">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="fe57c-126">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="fe57c-127">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="fe57c-127">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="fe57c-128">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="fe57c-128">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="fe57c-129">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="fe57c-129">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="fe57c-130">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="fe57c-130">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="fe57c-131">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="fe57c-131">Settings\DSC.psd1</span></span>
- <span data-ttu-id="fe57c-132">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="fe57c-132">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="fe57c-133">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="fe57c-133">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="fe57c-134">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="fe57c-134">Settings\ScriptSecurity.psd1</span></span>

#### <a name="contents-of-psscriptanalyzerpsd1-file"></a><span data-ttu-id="fe57c-135">Conteúdo do arquivo de PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="fe57c-135">Contents of PSScriptAnalyzer.psd1 file</span></span>

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

#### <a name="contents-of-psscriptanalyzerpsm1-file"></a><span data-ttu-id="fe57c-136">Conteúdo do arquivo de PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="fe57c-136">Contents of PSScriptAnalyzer.psm1 file</span></span>

<span data-ttu-id="fe57c-137">Abaixo lógica carrega os assemblies necessários, consoante a edição atual ou a versão.</span><span class="sxs-lookup"><span data-stu-id="fe57c-137">Below logic loads the required assemblies depending on the current edition or version.</span></span>

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0') {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}

```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="fe57c-138">Opção 2: Utilizar $PSEdition variável no ficheiro PSD1 para carregar as DLLs adequados e os módulos/necessária para aninhados</span><span class="sxs-lookup"><span data-stu-id="fe57c-138">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="fe57c-139">No PS 5.1 ou mais recente, $PSEdition de variável global é permitida no arquivo de manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="fe57c-139">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span>
<span data-ttu-id="fe57c-140">Usando esta variável, autor de módulos pode especificar os valores condicionais no arquivo de manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="fe57c-140">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="fe57c-141">É possível referenciar a variável $PSEdition no modo de idioma restrito ou uma secção de dados.</span><span class="sxs-lookup"><span data-stu-id="fe57c-141">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

> [!NOTE]
> <span data-ttu-id="fe57c-142">Depois de um manifesto de módulo é especificado com a chave de CompatiblePSEditions ou utiliza a variável de $PSEdition, não pode ser importado em versões mais baixas do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe57c-142">Once a module manifest is specified with the CompatiblePSEditions key or uses $PSEdition variable, it can not be imported on lower versions of PowerShell.</span></span>

#### <a name="sample-module-manifest-file-with-compatiblepseditions-key"></a><span data-ttu-id="fe57c-143">Ficheiro de manifesto de módulo de exemplo com a chave de CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="fe57c-143">Sample module manifest file with CompatiblePSEditions key</span></span>

```powershell
@{
# - - -

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

# -- - -
}
```

#### <a name="module-contents"></a><span data-ttu-id="fe57c-144">Conteúdo do módulo</span><span class="sxs-lookup"><span data-stu-id="fe57c-144">Module contents</span></span>

```powershell
dir -Recurse
```

```output
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/5/2016   1:37 PM                clr
d-----         7/5/2016   1:36 PM                coreclr
-a----         7/5/2016   1:34 PM           4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         7/5/2016   1:35 PM              0 MyFullClrNM1.dll
-a----         7/5/2016   1:35 PM              0 MyFullClrNM2.dll
-a----         7/5/2016   1:35 PM              0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM1.dll
-a----         7/5/2016   1:35 PM              0 MyCoreClrNM2.dll
-a----         7/5/2016   1:35 PM              0 MyCoreClrRM.dl
```

## <a name="powershell-gallery-users-can-find-the-list-of-modules-supported-on-a-specific-powershell-edition-using-tags-pseditiondesktop-and-pseditioncore"></a><span data-ttu-id="fe57c-145">Os utilizadores da galeria do PowerShell podem encontrar a lista de módulos suportado numa edição específica do PowerShell, utilizando etiquetas PSEdition_Desktop e PSEdition_Core.</span><span class="sxs-lookup"><span data-stu-id="fe57c-145">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="fe57c-146">Módulos sem etiquetas PSEdition_Desktop e PSEdition_Core são considerados como funcionam bem em edições de ambiente de trabalho do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe57c-146">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell

# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core

```

## <a name="more-details"></a><span data-ttu-id="fe57c-147">Obter mais detalhes</span><span class="sxs-lookup"><span data-stu-id="fe57c-147">More details</span></span>

[<span data-ttu-id="fe57c-148">Scripts com Edições do PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe57c-148">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="fe57c-149">Suporte de edições do PowerShell no PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="fe57c-149">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-items/searching-by-psedition.md)

[<span data-ttu-id="fe57c-150">Atualizar o manifesto do módulo</span><span class="sxs-lookup"><span data-stu-id="fe57c-150">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)