---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Encontrar o Script
ms.openlocfilehash: 15bf23b803250c7893fe970c2580592ea7c0a4b6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="find-script"></a>Encontrar o Script

Localiza os ficheiros de script do PowerShell a partir de uma galeria online que correspondem aos critérios especificados.

## <a name="description"></a>Descrição

Encontrar o Script identifica os ficheiros de script de repositórios registados que corresponde aos critérios especificados.
Para cada script encontrado, encontrar o Script devolve um objeto de PSRepositoryItemInfo que, opcionalmente, pode ser direcionado para o Script de instalação para instalar os scripts.
Script de encontrar o cmdlet permite-lhe detetar os ficheiros de script com os critérios de pesquisa diferentes, como o nome, etiqueta, filtro, nome do comando, intervalo de versão, versão exata, todas as versões, incluindo as respetivas dependências e repositórios de todos os registado ou específicos.

- Pode encontrar o Script filtro com base num script conteúdo com o - comando e - inclui os parâmetros.
- Encontrar o Script pode filtrar com parâmetros de versão: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.
  - Estes parâmetros são mutuamente exclusivos, exceto MinmimumVersion e MaximumVersion.
  - Estes parâmetros de versão são permitidos apenas com o nome do script único sem quaisquer carateres universais.
  - Se o parâmetro RequiredVersion não for especificado, o Script de localizar devolve a versão mais recente do script que seja igual ou maior do que a versão mínima especificado ou a versão mais recente do script, não se for especificada nenhuma versão mínima. 
  - Se o parâmetro RequiredVersion for especificado, o Script de localizar devolve apenas a versão do script que corresponde exatamente a versão especificada.
- Podem filtrar scripts localizar nos metadados do script com o parâmetro-Tag.
- Encontrar o Script pode filtrar por idioma específicas do repositório de pesquisa com o parâmetro-filtro.
- Encontrar o Script pode filtrar scripts a partir de todos os ou poucos dos repositórios do registado.

**Nota:** registada PSRepository deve ter um ScriptSourceLocation válido. Pode utilizar o PSRepository de conjunto para definir o valor de ScriptSourceLocation.

## <a name="cmdlet-syntax"></a>Sintaxe de cmdlet

```powershell
Get-Command -Name Find-Script -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Referência de ajuda online do cmdlet

[Encontrar o Script](http://go.microsoft.com/fwlink/?LinkId=619785)

## <a name="example-commands"></a>Comandos de exemplo

```powershell
# Find a script from the registered repository with ScriptSourceLocation
Find-Script Connect-AzureVM

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...

# Find multiple scripts
Find-Script -Name Connect-AzureVM, Show-Tree, Connect-O365

# Find scripts with wildcards in -Name
Find-Script -Name *Azure*

# Find all versions of a script
Find-Script -Name Connect-O365 -AllVersions

# Find a script with -MinimumVersion. 
# With MinimumVersion we can find a script whose version is greate than or equal to the specified MinimumVersion value.
Find-Script Connect-O365 -MinimumVersion 1.4

# Find a script with MaximumVersion
Find-Script -Name Connect-O365 -MaximumVersion 1.6.2

# Find a script with both MinimumVersion and MaximumVersion range.
Find-Script -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.2

# Find a script with exact version
Find-Script -Name Connect-O365 -RequiredVersion 1.5.7

# Find a script from the specified repository
Find-Script -Name Fabrikam-ServerScript -Repository MyLocalRepo

# Find available scripts from all registered repositories
Find-Script

# Find available scripts from few registered repositories
Find-Script -Repository PSGallery, PrivatePSGallery

# Find a script along with its dependent modules and scripts
Find-Script -Name Connect-AzureVM -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...
1.4.0      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management
1.1.2      Azure.Storage                       PSGallery            Microsoft Azure PowerShell - Storage service cmd...
1.0.8      AzureRM.profile                     PSGallery            Microsoft Azure PowerShell - Profile credential ...

# Find all scripts with workflows
Find-Script -Includes Workflow

# Find all scripts with functions
Find-Script -Includes Function

# Find scripts with specific commands
Find-Script -Command Log-Message
Find-Script -Command Log-Message, Show-Tree -Includes Function
Find-Script -Command Connect-AzureVM -Includes Workflow

# Find scripts with -Filter based search. -Filter searches in description and names
Find-Script -Filter Windows
Find-Script -Filter Azure

# Find all scripts with tags O365 or Nano
Find-Script -Tag O365, Nano

# Properties of Find-Script returned object
Find-Script Show-Tree | Format-List * -Force
Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              :
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
AdditionalMetadata         : {versionDownloadCount, ItemType, copyright, PackageManagementProvider...}


# Includes property on PSRepositoryItemInfo object
$t = Find-Script -Includes Workflow -Repository INT -Name Fabrikam-ClientScript
$t.Includes

Name                           Value
----                           -----
Function                       {Test-FunctionFromScript_Fabrikam-ClientScript}
RoleCapability                 {}
Command                        {Test-FunctionFromScript_Fabrikam-ClientScript, Test-WorkflowFromScript_Fabrikam-Clie...
DscResource                    {}
Workflow                       {Test-WorkflowFromScript_Fabrikam-ClientScript}
Cmdlet                         {}


```

