---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Script publicar
ms.openlocfilehash: 0d2fd87645d2286e87e68198844adce8909739cb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="publish-script"></a>Script publicar

O cmdlet Publish-Script publica o script especificado para a Galeria online.

## <a name="description"></a>Descrição

Script publicar cmdlet permite-lhe para publicar o ficheiro de script com metadados válido como versão, Guid, autor e a descrição, etc. Parâmetro forçar no cmdlet Publish-Script bootstraps o NuGet.exe sem pedir confirmação.

## <a name="cmdlet-syntax"></a>Sintaxe de cmdlet

```powershell
Get-Command -Name Publish-Script -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Referência de ajuda online do cmdlet

[Script publicar](http://go.microsoft.com/fwlink/?LinkId=619788)

## <a name="example-commands"></a>Comandos de exemplo

```powershell
# Publish the really basic script file with required metadata

Publish-Script -Path C:\ScriptSharingDemo\Demo-Script.ps1 -Repository GalleryINT -NuGetApiKey cad91af7-a49c-4026-9570-a4c16564e785 -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you
want PowerShellGet to install NuGet.exe now?
[Y] Yes [N] No [S] Suspend [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: GET http://go.microsoft.com/fwlink/?LinkID=690216&clcid=0x409 with 0-byte payload
VERBOSE: received 1686528-byte response of content type application/octet-stream
VERBOSE: Performing the operation "Publish-Script" on target "Version '1.0' of script 'Demo-Script'".
VERBOSE: Successfully published script 'Demo-Script' to the publish location 'https://customgallery.cloudapp.net/api/v2/package/'. Please allow few minutes for 'Demo-Script' to show up in the search results.

Find-Script -Repository GalleryINT -Name Demo-Script

Version Name Type Repository Description
------- ---- ---- ---------- -----------
1.0 Demo-Script Script GalleryINT Script file description goes here

Find-Script -Repository GalleryINT -Name Demo-Script | Format-List * -Force

Name : Demo-Script
Version : 1.0
Type : Script
Description : Script file description goes here
Author : manikb
CompanyName : manikb
Copyright :
PublishedDate : 11/16/2015 6:46:28 PM
LicenseUri :
ProjectUri :
IconUri :
Tags : {PSScript}
Includes : {Function, DscResource, Cmdlet, Workflow...}
PowerShellGetFormatVersion :
ReleaseNotes :
Dependencies : {}
RepositorySourceLocation : https://customgallery.cloudapp.net/api/v2/
Repository : GalleryINT
PackageManagementProvider : NuGet
AdditionalMetadata : {description, developmentDependency, tags, PackageManagementProvider...}

```

