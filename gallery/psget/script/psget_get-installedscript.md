---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Get-InstalledScript
ms.openlocfilehash: 668327905b0dab40119940a3134b674c452f538d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="get-installedscript"></a>Get-InstalledScript

Obtém instalado scripts num computador.

## <a name="description"></a>Descrição

O cmdlet Get-InstalledScript obtém scripts do PowerShell instaladas num computador.

Para cada script instalado, o Get-InstalledScript devolve um objeto de PSRepositoryItemInfo que, opcionalmente, pode ser direcionado para o Script de desinstalação para desinstalar os scripts instalados.

- Get-InstalledScript pode filtrar scripts instalados com base no nome, parâmetros de versão.
- Get-InstalledScript pode filtrar com parâmetros de versão: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.
  - Estes parâmetros são mutuamente exclusivos, exceto MinmimumVersion e MaximumVersion.
  - Estes parâmetros de versão são permitidos apenas com o nome do script único sem quaisquer carateres universais.
  - Se o parâmetro RequiredVersion não for especificado, o Get-InstalledScript devolve a versão mais recente do script instalado que é igual ou maior do que a versão mínima especificado ou a versão mais recente do script, não se for especificada nenhuma versão mínima.
  - Se o parâmetro RequiredVersion for especificado, o Get-InstalledScript devolve apenas a versão do script instalado que corresponde exatamente a versão especificada.

## <a name="cmdlet-syntax"></a>Sintaxe de cmdlet

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Referência de ajuda online do cmdlet

[Get-InstalledScript](http://go.microsoft.com/fwlink/?LinkId=619790)

## <a name="example-commands"></a>Comandos de exemplo

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