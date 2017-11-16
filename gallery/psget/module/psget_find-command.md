---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Encontrar o comando
ms.openlocfilehash: f867f12b1c6efad30a04581c6f36c5a77a2fb2ae
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="find-command"></a><span data-ttu-id="d79fd-103">Encontrar o comando</span><span class="sxs-lookup"><span data-stu-id="d79fd-103">Find-Command</span></span>

<span data-ttu-id="d79fd-104">Localiza os comandos do PowerShell nos módulos.</span><span class="sxs-lookup"><span data-stu-id="d79fd-104">Finds PowerShell commands in modules.</span></span>

## <a name="description"></a><span data-ttu-id="d79fd-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="d79fd-105">Description</span></span>
<span data-ttu-id="d79fd-106">O cmdlet do comando de localizar localiza os comandos do PowerShell como os cmdlets, aliases, funções e fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d79fd-106">The Find-Command cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="d79fd-107">Localizar comando procura módulos no repositórios registados.</span><span class="sxs-lookup"><span data-stu-id="d79fd-107">Find-Command searches modules in registered repositories.</span></span>
<span data-ttu-id="d79fd-108">Para cada comando que se encontra este cmdlet, devolve um objeto de PSGetCommandInfo.</span><span class="sxs-lookup"><span data-stu-id="d79fd-108">For each command that this cmdlet finds, it returns a PSGetCommandInfo object.</span></span> <span data-ttu-id="d79fd-109">Pode transmitir um objeto de PSGetCommandInfo para o cmdlet do módulo de instalação para instalar o módulo que contém o comando.</span><span class="sxs-lookup"><span data-stu-id="d79fd-109">You can pass a PSGetCommandInfo object to the Install-Module cmdlet to install the module that contains the command.</span></span>

- <span data-ttu-id="d79fd-110">Pode filtrar localizar comando com parâmetros de versão: MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="d79fd-110">Find-Command can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="d79fd-111">Estes parâmetros são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="d79fd-111">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="d79fd-112">Estes parâmetros de versão são permitidos apenas com o nome do módulo único sem quaisquer carateres universais.</span><span class="sxs-lookup"><span data-stu-id="d79fd-112">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="d79fd-113">Se não for especificado o parâmetro RequiredVersion, localizar comando devolve a versão mais recente do módulo que seja igual ou maior do que a versão mínima especificado ou a versão mais recente do módulo, não se for especificada nenhuma versão mínima.</span><span class="sxs-lookup"><span data-stu-id="d79fd-113">If the RequiredVersion parameter is not specified, Find-Command returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="d79fd-114">Se o parâmetro RequiredVersion for especificado, o comando de localizar devolve apenas a versão do módulo que corresponde exatamente a versão especificada.</span><span class="sxs-lookup"><span data-stu-id="d79fd-114">If the RequiredVersion parameter is specified, Find-Command only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="d79fd-115">Pode filtrar comando Localizar nos metadados do módulo com o parâmetro-etiqueta</span><span class="sxs-lookup"><span data-stu-id="d79fd-115">Find-Command can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="d79fd-116">Encontrar o comando pode filtrar por idioma específicas do repositório de pesquisa com o parâmetro-filtro.</span><span class="sxs-lookup"><span data-stu-id="d79fd-116">Find-Command can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="d79fd-117">Encontrar o comando pode filtrar por módulos de todas as ou poucos dos repositórios do registado.</span><span class="sxs-lookup"><span data-stu-id="d79fd-117">Find-Command can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="d79fd-118">Sintaxe de cmdlet</span><span class="sxs-lookup"><span data-stu-id="d79fd-118">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="d79fd-119">Referência de ajuda online do cmdlet</span><span class="sxs-lookup"><span data-stu-id="d79fd-119">Cmdlet online help reference</span></span>

[<span data-ttu-id="d79fd-120">Encontrar o comando</span><span class="sxs-lookup"><span data-stu-id="d79fd-120">Find-Command</span></span>](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a><span data-ttu-id="d79fd-121">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="d79fd-121">Example commands</span></span>
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```

