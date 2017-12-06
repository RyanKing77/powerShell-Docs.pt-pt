---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Encontrar o Script
ms.openlocfilehash: df62a9934d8013d37bd0083c03f90fa7fa05ac0c
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2017
---
# <a name="find-script"></a><span data-ttu-id="a8495-103">Encontrar o Script</span><span class="sxs-lookup"><span data-stu-id="a8495-103">Find-Script</span></span>

<span data-ttu-id="a8495-104">Localiza os ficheiros de script do PowerShell a partir de uma galeria online que correspondem aos critérios especificados.</span><span class="sxs-lookup"><span data-stu-id="a8495-104">Finds the PowerShell script files from an online gallery that match specified criteria.</span></span>

## <a name="description"></a><span data-ttu-id="a8495-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8495-105">Description</span></span>

<span data-ttu-id="a8495-106">Encontrar o Script identifica os ficheiros de script de repositórios registados que corresponde aos critérios especificados.</span><span class="sxs-lookup"><span data-stu-id="a8495-106">Find-Script discovers the script files from registered repositories that matches the specified criteria.</span></span>
<span data-ttu-id="a8495-107">Para cada script encontrado, encontrar o Script devolve um objeto de PSRepositoryItemInfo que, opcionalmente, pode ser direcionado para o Script de instalação para instalar os scripts.</span><span class="sxs-lookup"><span data-stu-id="a8495-107">For each script found, Find-Script returns a PSRepositoryItemInfo object which can optionally be piped to Install-Script for installing the scripts.</span></span>
<span data-ttu-id="a8495-108">Script de encontrar o cmdlet permite-lhe detetar os ficheiros de script com os critérios de pesquisa diferentes, como o nome, etiqueta, filtro, nome do comando, intervalo de versão, versão exata, todas as versões, incluindo as respetivas dependências e repositórios de todos os registado ou específicos.</span><span class="sxs-lookup"><span data-stu-id="a8495-108">Find-Script cmdlet lets you to discover the script files with different search criteria like name, tag, filter, command name, version range, exact version, all versions, including its dependencies and from specific or all registered repositories.</span></span>

- <span data-ttu-id="a8495-109">Pode encontrar o Script filtro com base num script conteúdo com o - comando e - inclui os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="a8495-109">Find-Script can filter based on script contents with the -Command and -Includes parameters.</span></span>
- <span data-ttu-id="a8495-110">Encontrar o Script pode filtrar com parâmetros de versão: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="a8495-110">Find-Script can filter with version parameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="a8495-111">Estes parâmetros são mutuamente exclusivos, exceto MinmimumVersion e MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="a8495-111">These parameters are mutually exclusive, except MinmimumVersion and MaximumVersion.</span></span>
  - <span data-ttu-id="a8495-112">Estes parâmetros de versão são permitidos apenas com o nome do script único sem quaisquer carateres universais.</span><span class="sxs-lookup"><span data-stu-id="a8495-112">These version parameters are allowed only with the single script name without any wildcards.</span></span>
  - <span data-ttu-id="a8495-113">Se o parâmetro RequiredVersion não for especificado, o Script de localizar devolve a versão mais recente do script que seja igual ou maior do que a versão mínima especificado ou a versão mais recente do script, não se for especificada nenhuma versão mínima.</span><span class="sxs-lookup"><span data-stu-id="a8495-113">If the RequiredVersion parameter is not specified, Find-Script returns the latest version of the script that is equal to or greater than the minimum version specified or the latest version of the script if no minimum version is specified.</span></span> 
  - <span data-ttu-id="a8495-114">Se o parâmetro RequiredVersion for especificado, o Script de localizar devolve apenas a versão do script que corresponde exatamente a versão especificada.</span><span class="sxs-lookup"><span data-stu-id="a8495-114">If the RequiredVersion parameter is specified, Find-Script only returns the version of script that exactly matches the specified version.</span></span>
- <span data-ttu-id="a8495-115">Podem filtrar scripts localizar nos metadados do script com o parâmetro-Tag.</span><span class="sxs-lookup"><span data-stu-id="a8495-115">Find-Script can filter on script metadata with the -Tag parameter.</span></span>
- <span data-ttu-id="a8495-116">Encontrar o Script pode filtrar por idioma específicas do repositório de pesquisa com o parâmetro-filtro.</span><span class="sxs-lookup"><span data-stu-id="a8495-116">Find-Script can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="a8495-117">Encontrar o Script pode filtrar scripts a partir de todos os ou poucos dos repositórios do registado.</span><span class="sxs-lookup"><span data-stu-id="a8495-117">Find-Script can filter on scripts from all or few of the registered repositories.</span></span>

<span data-ttu-id="a8495-118">**Nota:** registada PSRepository deve ter um ScriptSourceLocation válido.</span><span class="sxs-lookup"><span data-stu-id="a8495-118">**NOTE:** Registered PSRepository should have a valid ScriptSourceLocation.</span></span> <span data-ttu-id="a8495-119">Pode utilizar o PSRepository de conjunto para definir o valor de ScriptSourceLocation.</span><span class="sxs-lookup"><span data-stu-id="a8495-119">You can use the Set-PSRepository to set ScriptSourceLocation value.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="a8495-120">Sintaxe de cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8495-120">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Find-Script -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="a8495-121">Referência de ajuda online do cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8495-121">Cmdlet online help reference</span></span>

[<span data-ttu-id="a8495-122">Encontrar o Script</span><span class="sxs-lookup"><span data-stu-id="a8495-122">Find-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619785)

## <a name="example-commands"></a><span data-ttu-id="a8495-123">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="a8495-123">Example commands</span></span>

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

# Find a script with a specific pre-release version
Find-Script -Name Connect-O365 -RequiredVersion 1.3.2-alpha -AllowPrerelease

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

