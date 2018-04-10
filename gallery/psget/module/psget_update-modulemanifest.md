---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Update-ModuleManifest
ms.openlocfilehash: 45f40f753af17e82c83dbf57dea13749ba626503
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="update-modulemanifest"></a><span data-ttu-id="f922a-103">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="f922a-103">Update-ModuleManifest</span></span>
<span data-ttu-id="f922a-104">As atualizações de um ficheiro de manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="f922a-104">Updates a module manifest file.</span></span>

## <a name="description"></a><span data-ttu-id="f922a-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="f922a-105">Description</span></span>

<span data-ttu-id="f922a-106">O cmdlet Update-ModuleManifest atualiza um ficheiro de manifesto (. psd1) do módulo.</span><span class="sxs-lookup"><span data-stu-id="f922a-106">The Update-ModuleManifest cmdlet updates a module manifest (.psd1) file.</span></span>

### <a name="notes"></a><span data-ttu-id="f922a-107">Notas</span><span class="sxs-lookup"><span data-stu-id="f922a-107">Notes</span></span>
    - <span data-ttu-id="f922a-108">DscResourcesToExport só é suportada no mais recente versão 5.0 do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f922a-108">DscResourcesToExport is only supported on the latest PowerShell version 5.0.</span></span> <span data-ttu-id="f922a-109">Iremos não será possível atualizar o campo se estiver a executar versões inferior do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f922a-109">We won’t be able to update the field if you are running on lower versions of PowerShell.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="f922a-110">Sintaxe de cmdlet</span><span class="sxs-lookup"><span data-stu-id="f922a-110">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-ModuleManifest -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="f922a-111">Referência de ajuda online do cmdlet</span><span class="sxs-lookup"><span data-stu-id="f922a-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="f922a-112">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="f922a-112">Update-ModuleManifest</span></span>](http://go.microsoft.com/fwlink/?LinkId=619311)

## <a name="example-commands"></a><span data-ttu-id="f922a-113">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="f922a-113">Example commands</span></span>

<span data-ttu-id="f922a-114">Este novo cmdlet é utilizado para ajudar a atualização de manifesto do ficheiro com valores de propriedade de entrada.</span><span class="sxs-lookup"><span data-stu-id="f922a-114">This new cmdlet is used to help update manifest file with input property values.</span></span> <span data-ttu-id="f922a-115">Demora todos os parâmetros que ModuleManifest de novo.</span><span class="sxs-lookup"><span data-stu-id="f922a-115">It takes all parameters that New-ModuleManifest does.</span></span>

<span data-ttu-id="f922a-116">Repararmos que muitos autores de módulo pretende especificar "\*" valores exportado como FunctionsToExport, CmdletsToExport, etc. Durante a publicação do módulo para a galeria do PowerShell, comandos e as funções não especificadas não são preenchidos corretamente para a galeria.</span><span class="sxs-lookup"><span data-stu-id="f922a-116">We notice that a lot of module authors would like to specify “\*” in exported values such as FunctionsToExport, CmdletsToExport, etc. During module publishing to PowerShell Gallery, unspecified functions and commands will not be populated properly onto the Gallery.</span></span> <span data-ttu-id="f922a-117">Por conseguinte, sugerimos que módulo autores atualização os manifestos com valores adequados.</span><span class="sxs-lookup"><span data-stu-id="f922a-117">Therefore, we suggest module authors update their manifests with proper values.</span></span>

<span data-ttu-id="f922a-118">Se tiver de módulos que exportou propriedades, atualização ModuleManifest preencham completamente o ficheiro de manifesto especificado com as informações de funções exportadas, os cmdlets, variáveis etc:</span><span class="sxs-lookup"><span data-stu-id="f922a-118">If you have modules that have exported properties, Update-ModuleManifest will fill the specified manifest file with information from exported functions, cmdlets, variables etc:</span></span>
```powershell
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'

#(Other properties removed here for Simplicity…)

# Functions to export from this module
FunctionsToExport = '*'
# Cmdlets to export from this module
CmdletsToExport = '*'
# Variables to export from this module
VariablesToExport = '*'
# Aliases to export from this module
AliasesToExport = '*'
}
```

<span data-ttu-id="f922a-119">Após a atualização-ModuleManifest:</span><span class="sxs-lookup"><span data-stu-id="f922a-119">After Update-ModuleManifest:</span></span>
```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
#
# Module manifest for module 'NewManifest'
#
# Generated by: author name
#
# Generated on: 11/13/2015
#
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'
# Functions to export from this module
FunctionsToExport = 'Get-FooFn Get-FooWF'
# Cmdlets to export from this module
CmdletsToExport = 'Test-PSGetTestCmdlet'
}
```

<span data-ttu-id="f922a-120">Para cada módulo, também existem campos de metadados associados à mesma.</span><span class="sxs-lookup"><span data-stu-id="f922a-120">For each module, there are also metadata fields associated with it.</span></span> <span data-ttu-id="f922a-121">Para poder apresentar os metadados corretamente na Galeria de PowrShell, pode utilizar a atualização ModuleManifest para preencher os campos em PrivateData.</span><span class="sxs-lookup"><span data-stu-id="f922a-121">In order to display metadata properly on PowrShell Gallery, you can use Update-ModuleManifest to populate those fields under PrivateData.</span></span>

```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1" -Tags "Tag1" -LicenseUri "http://license.com" -ProjectUri "http://project.com" -IconUri "http://icon.com" -ReleaseNotes "Test module"
```

<span data-ttu-id="f922a-122">Tabela hash de PrivateData do modelo de ficheiro de manifesto tem as seguintes propriedades</span><span class="sxs-lookup"><span data-stu-id="f922a-122">PrivateData hashtable from the manifest file template has the following properties</span></span>

```powershell
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # External dependent modules of this module
        # ExternalModuleDependencies = ''
    } # End of PSData hashtable
} # End of PrivateData hashtable
```