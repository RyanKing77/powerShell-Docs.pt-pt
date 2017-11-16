---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Get-InstalledScript
ms.openlocfilehash: f35e57cdadd1448bd9032ab007d692003c4cf4a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="get-installedscript"></a><span data-ttu-id="990a3-103">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="990a3-103">Get-InstalledScript</span></span>

<span data-ttu-id="990a3-104">Obtém instalado scripts num computador.</span><span class="sxs-lookup"><span data-stu-id="990a3-104">Gets installed scripts on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="990a3-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="990a3-105">Description</span></span>

<span data-ttu-id="990a3-106">O cmdlet Get-InstalledScript obtém scripts do PowerShell instaladas num computador.</span><span class="sxs-lookup"><span data-stu-id="990a3-106">The Get-InstalledScript cmdlet gets installed PowerShell scripts on a computer.</span></span>

<span data-ttu-id="990a3-107">Para cada script instalado, o Get-InstalledScript devolve um objeto de PSRepositoryItemInfo que, opcionalmente, pode ser direcionado para o Script de desinstalação para desinstalar os scripts instalados.</span><span class="sxs-lookup"><span data-stu-id="990a3-107">For each installed script, Get-InstalledScript returns a PSRepositoryItemInfo object which can optionally be piped to Uninstall-Script for uninstalling the installed scripts.</span></span>

- <span data-ttu-id="990a3-108">Get-InstalledScript pode filtrar scripts instalados com base no nome, parâmetros de versão.</span><span class="sxs-lookup"><span data-stu-id="990a3-108">Get-InstalledScript can filter installed scripts based on name, version parameters.</span></span>
- <span data-ttu-id="990a3-109">Get-InstalledScript pode filtrar com parâmetros de versão: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="990a3-109">Get-InstalledScript can filter with version parameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="990a3-110">Estes parâmetros são mutuamente exclusivos, exceto MinmimumVersion e MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="990a3-110">These parameters are mutually exclusive, except MinmimumVersion and MaximumVersion.</span></span>
  - <span data-ttu-id="990a3-111">Estes parâmetros de versão são permitidos apenas com o nome do script único sem quaisquer carateres universais.</span><span class="sxs-lookup"><span data-stu-id="990a3-111">These version parameters are allowed only with the single script name without any wildcards.</span></span>
  - <span data-ttu-id="990a3-112">Se o parâmetro RequiredVersion não for especificado, o Get-InstalledScript devolve a versão mais recente do script instalado que é igual ou maior do que a versão mínima especificado ou a versão mais recente do script, não se for especificada nenhuma versão mínima.</span><span class="sxs-lookup"><span data-stu-id="990a3-112">If the RequiredVersion parameter is not specified, Get-InstalledScript returns the latest version of the installed script that is equal to or greater than the minimum version specified or the latest version of the script if no minimum version is specified.</span></span> 
  - <span data-ttu-id="990a3-113">Se o parâmetro RequiredVersion for especificado, o Get-InstalledScript devolve apenas a versão do script instalado que corresponde exatamente a versão especificada.</span><span class="sxs-lookup"><span data-stu-id="990a3-113">If the RequiredVersion parameter is specified, Get-InstalledScript only returns the version of installed script that exactly matches the specified version.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="990a3-114">Sintaxe de cmdlet</span><span class="sxs-lookup"><span data-stu-id="990a3-114">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="990a3-115">Referência de ajuda online do cmdlet</span><span class="sxs-lookup"><span data-stu-id="990a3-115">Cmdlet online help reference</span></span>

[<span data-ttu-id="990a3-116">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="990a3-116">Get-InstalledScript</span></span>](http://go.microsoft.com/fwlink/?LinkId=619790)

## <a name="example-commands"></a><span data-ttu-id="990a3-117">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="990a3-117">Example commands</span></span>

```powershell

# Get all scripts installed using PowerShellGet cmdlets
Get-InstalledScript

# Get a specific installed script
Get-InstalledScript Show-Tree

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      Show-Tree                           PSGallery            Script to show the layout of PowerShell namespaces (Tr...

# Get installed script with wildcards
Get-InstalledScript -Name *Azure*

# Get all versions of an installed script
Get-InstalledScript -Name Connect-O365 -AllVersions

# Get installed script with MinimumVersion
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1

# Get installed script with MaximumVersion
Get-InstalledScript -Name Connect-O365 -MaximumVersion 1.6.3

# Get installed script with version range
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.3

# Get installed script with RequiredVersion
Get-InstalledScript -Name Connect-O365 -RequiredVersion 1.4

# Properties of Get-InstalledScript returned object
Get-InstalledScript Show-Tree | Format-List * -Force

Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              : 5/4/2016 11:44:13 PM
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


```

