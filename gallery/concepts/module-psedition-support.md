---
ms.date: 03/28/2019
contributor: manikb
keywords: cmdlet do powershell do galeria, psget
title: Módulos com edições do PowerShell compatíveis
ms.openlocfilehash: 425588c168a4f864fdc0c52aa53cfd748b80dc98
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084730"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="6090c-103">Módulos com edições do PowerShell compatíveis</span><span class="sxs-lookup"><span data-stu-id="6090c-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="6090c-104">Começando na versão 5.1, o PowerShell está disponível nas diferentes edições que denotam conjuntos de funcionalidade e compatibilidade de plataforma variados.</span><span class="sxs-lookup"><span data-stu-id="6090c-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="6090c-105">**Edição Desktop:** Criado no .NET Framework, aplica-se para o Windows PowerShell v4.0 e abaixo, bem como o Windows PowerShell 5.1 no ambiente de trabalho do Windows, Windows Server, Windows Server Core e a maioria das outras edições do Windows.</span><span class="sxs-lookup"><span data-stu-id="6090c-105">**Desktop Edition:** Built on .NET Framework, applies to Windows PowerShell v4.0 and below as well as Windows PowerShell 5.1 on Windows Desktop, Windows Server, Windows Server Core and most other Windows editions.</span></span>
- <span data-ttu-id="6090c-106">**Edição Core:** Incorporada no .NET Core, aplica-se para o PowerShell Core 6.0 e superior, bem como o Windows PowerShell 5.1 nos requisitos de espaço reduzido das edições do Windows, tais como Windows IoT e Windows Nanoserver.</span><span class="sxs-lookup"><span data-stu-id="6090c-106">**Core Edition:** Built on .NET Core, applies to PowerShell Core 6.0 and above as well as Windows PowerShell 5.1 on reduced footprint Windows Editions such as Windows IoT and Windows Nanoserver.</span></span>

<span data-ttu-id="6090c-107">Para obter mais informações sobre edições do PowerShell, consulte [about_PowerShell_Editions][].</span><span class="sxs-lookup"><span data-stu-id="6090c-107">For more information on PowerShell editions, see [about_PowerShell_Editions][].</span></span>

## <a name="declaring-compatible-editions"></a><span data-ttu-id="6090c-108">Declarando edições compatíveis</span><span class="sxs-lookup"><span data-stu-id="6090c-108">Declaring compatible editions</span></span>

<span data-ttu-id="6090c-109">Os autores de módulo podem declarar os módulos para torná-los compatíveis com uma ou mais edições do PowerShell com a chave de manifesto de módulo CompatiblePSEditions.</span><span class="sxs-lookup"><span data-stu-id="6090c-109">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="6090c-110">Esta chave apenas é suportada no PowerShell 5.1 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="6090c-110">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="6090c-111">Depois de um manifesto de módulo é especificado com a chave de CompatiblePSEditions, ele não pode ser importado no PowerShell versões 4 e abaixo.</span><span class="sxs-lookup"><span data-stu-id="6090c-111">Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on PowerShell versions 4 and below.</span></span>

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

<span data-ttu-id="6090c-112">Ao obter uma lista de módulos disponíveis, pode filtrar a lista por edição do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6090c-112">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

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

## <a name="targeting-multiple-editions"></a><span data-ttu-id="6090c-113">Direcionamento várias edições</span><span class="sxs-lookup"><span data-stu-id="6090c-113">Targeting multiple editions</span></span>

<span data-ttu-id="6090c-114">Os autores de módulo podem publicar um direcionamento de módulo único para cada um, ou ambas as edições do PowerShell (ambiente de trabalho e Core).</span><span class="sxs-lookup"><span data-stu-id="6090c-114">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core).</span></span>

<span data-ttu-id="6090c-115">Um mesmo módulo pode trabalhar em edições de ambiente de trabalho e Core, nesse módulo tem de adicionar a lógica necessária em qualquer um dos RootModule ou no manifesto do módulo usando a variável de $PSEdition autor.</span><span class="sxs-lookup"><span data-stu-id="6090c-115">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span> <span data-ttu-id="6090c-116">Módulos podem ter dois conjuntos de DLLs compiladas destinados a CoreCLR e FullCLR.</span><span class="sxs-lookup"><span data-stu-id="6090c-116">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span> <span data-ttu-id="6090c-117">Aqui estão as duas opções para empacotar seu módulo com a lógica para carregar dlls adequada.</span><span class="sxs-lookup"><span data-stu-id="6090c-117">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="6090c-118">Opção 1: Empacotando um módulo para destinados a várias versões e várias edições do PowerShell</span><span class="sxs-lookup"><span data-stu-id="6090c-118">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

<span data-ttu-id="6090c-119">Conteúdo da pasta de módulo</span><span class="sxs-lookup"><span data-stu-id="6090c-119">Module folder contents</span></span>

- <span data-ttu-id="6090c-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="6090c-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="6090c-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="6090c-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="6090c-122">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="6090c-122">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="6090c-123">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="6090c-123">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="6090c-124">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="6090c-124">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="6090c-125">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="6090c-125">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="6090c-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="6090c-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="6090c-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="6090c-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="6090c-128">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="6090c-128">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="6090c-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="6090c-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="6090c-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="6090c-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="6090c-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="6090c-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="6090c-132">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="6090c-132">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="6090c-133">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="6090c-133">Settings\DSC.psd1</span></span>
- <span data-ttu-id="6090c-134">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="6090c-134">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="6090c-135">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="6090c-135">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="6090c-136">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="6090c-136">Settings\ScriptSecurity.psd1</span></span>

<span data-ttu-id="6090c-137">Conteúdo do arquivo de PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="6090c-137">Contents of PSScriptAnalyzer.psd1 file</span></span>

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

<span data-ttu-id="6090c-138">Abaixo lógica carrega os assemblies necessários, consoante a edição atual ou a versão.</span><span class="sxs-lookup"><span data-stu-id="6090c-138">Below logic loads the required assemblies depending on the current edition or version.</span></span>

<span data-ttu-id="6090c-139">Conteúdo do arquivo de PSScriptAnalyzer.psm1:</span><span class="sxs-lookup"><span data-stu-id="6090c-139">Contents of PSScriptAnalyzer.psm1 file:</span></span>

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

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="6090c-140">Opção 2: Utilizar a variável $PSEdition no ficheiro PSD1 para carregar as DLLs adequados e os módulos/necessária para aninhados</span><span class="sxs-lookup"><span data-stu-id="6090c-140">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="6090c-141">No PS 5.1 ou mais recente, $PSEdition de variável global é permitida no arquivo de manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="6090c-141">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span> <span data-ttu-id="6090c-142">Usando esta variável, autor de módulos pode especificar os valores condicionais no arquivo de manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="6090c-142">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="6090c-143">É possível referenciar a variável $PSEdition no modo de idioma restrito ou uma secção de dados.</span><span class="sxs-lookup"><span data-stu-id="6090c-143">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

> [!NOTE]
> <span data-ttu-id="6090c-144">Depois de um manifesto de módulo for especificado com a chave de CompatiblePSEditions ou utiliza `$PSEdition` variável, ele não pode ser importado em versões mais baixas do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6090c-144">Once a module manifest is specified with the CompatiblePSEditions key or uses `$PSEdition` variable, it can not be imported on lower versions of PowerShell.</span></span>

<span data-ttu-id="6090c-145">Ficheiro de manifesto de módulo de exemplo com a chave de CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="6090c-145">Sample module manifest file with CompatiblePSEditions key</span></span>

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

### <a name="module-contents"></a><span data-ttu-id="6090c-146">Conteúdo do módulo</span><span class="sxs-lookup"><span data-stu-id="6090c-146">Module contents</span></span>

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

<span data-ttu-id="6090c-147">Os utilizadores da galeria do PowerShell podem encontrar a lista de módulos suportado numa edição específica do PowerShell, utilizando etiquetas PSEdition_Desktop e PSEdition_Core.</span><span class="sxs-lookup"><span data-stu-id="6090c-147">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="6090c-148">Módulos sem etiquetas PSEdition_Desktop e PSEdition_Core são considerados como funcionam bem em edições de ambiente de trabalho do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6090c-148">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="6090c-149">Obter mais detalhes</span><span class="sxs-lookup"><span data-stu-id="6090c-149">More details</span></span>

[<span data-ttu-id="6090c-150">Scripts com Edições do PowerShell</span><span class="sxs-lookup"><span data-stu-id="6090c-150">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="6090c-151">Suporte de edições do PowerShell no PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="6090c-151">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)

[<span data-ttu-id="6090c-152">Atualizar o manifesto do módulo</span><span class="sxs-lookup"><span data-stu-id="6090c-152">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)

<span data-ttu-id="6090c-153">[about_PowerShell_Editions][]</span><span class="sxs-lookup"><span data-stu-id="6090c-153">[about_PowerShell_Editions][]</span></span>

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
