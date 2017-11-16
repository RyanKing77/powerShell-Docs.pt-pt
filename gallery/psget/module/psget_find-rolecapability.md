---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Localizar RoleCapability
ms.openlocfilehash: 77c5b492d9681fa05315401fba410c508af1d13b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="find-rolecapability"></a><span data-ttu-id="20c83-103">Localizar RoleCapability</span><span class="sxs-lookup"><span data-stu-id="20c83-103">Find-RoleCapability</span></span>

<span data-ttu-id="20c83-104">Encontra capacidades de funções nos módulos.</span><span class="sxs-lookup"><span data-stu-id="20c83-104">Finds role capabilities in modules.</span></span>

## <a name="description"></a><span data-ttu-id="20c83-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="20c83-105">Description</span></span>
<span data-ttu-id="20c83-106">O cmdlet Find RoleCapability localiza capacidades de função do PowerShell nos módulos.</span><span class="sxs-lookup"><span data-stu-id="20c83-106">The Find-RoleCapability cmdlet finds PowerShell role capabilities in modules.</span></span> <span data-ttu-id="20c83-107">Localizar RoleCapability procura módulos no repositórios registados.</span><span class="sxs-lookup"><span data-stu-id="20c83-107">Find-RoleCapability searches modules in registered repositories.</span></span> <span data-ttu-id="20c83-108">Para cada capacidade de função que este cmdlet localiza, devolve um objeto de PSGetRoleCapabilityInfo.</span><span class="sxs-lookup"><span data-stu-id="20c83-108">For each role capability that this cmdlet finds, it returns a PSGetRoleCapabilityInfo object.</span></span> <span data-ttu-id="20c83-109">Pode transmitir um objeto de PSGetRoleCapabilityInfo para o cmdlet do módulo de instalação para instalar o módulo que contém a capacidade de função.</span><span class="sxs-lookup"><span data-stu-id="20c83-109">You can pass a PSGetRoleCapabilityInfo object to the Install-Module cmdlet to install the module that contains the role capability.</span></span>
<span data-ttu-id="20c83-110">Capacidades de função de PowerShell definem quais os comandos, aplicações e assim sucessivamente estão disponíveis para um utilizador de um ponto final apenas suficiente administração (JEA).</span><span class="sxs-lookup"><span data-stu-id="20c83-110">PowerShell role capabilities define which commands, applications, and so on are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="20c83-111">Capacidades de função são definidas pelos ficheiros com uma extensão de .psrc.</span><span class="sxs-lookup"><span data-stu-id="20c83-111">Role capabilities are defined by files with a .psrc extension.</span></span>

- <span data-ttu-id="20c83-112">Localizar RoleCapability pode filtrar com parâmetros de versão: MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="20c83-112">Find-RoleCapability can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="20c83-113">Estes parâmetros são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="20c83-113">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="20c83-114">Estes parâmetros de versão são permitidos apenas com o nome do módulo único sem quaisquer carateres universais.</span><span class="sxs-lookup"><span data-stu-id="20c83-114">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="20c83-115">Se não for especificado o parâmetro RequiredVersion, localizar RoleCapability devolve a versão mais recente do módulo que seja igual ou maior do que a versão mínima especificado ou a versão mais recente do módulo, não se for especificada nenhuma versão mínima.</span><span class="sxs-lookup"><span data-stu-id="20c83-115">If the RequiredVersion parameter is not specified, Find-RoleCapability returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="20c83-116">Se não for especificado o parâmetro RequiredVersion, localizar RoleCapability devolve apenas a versão do módulo que corresponde exatamente a versão especificada.</span><span class="sxs-lookup"><span data-stu-id="20c83-116">If the RequiredVersion parameter is specified, Find-RoleCapability only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="20c83-117">Pode filtrar RoleCapability localizar nos metadados do módulo com o parâmetro-etiqueta</span><span class="sxs-lookup"><span data-stu-id="20c83-117">Find-RoleCapability can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="20c83-118">Localizar RoleCapability pode filtrar por idioma específicas do repositório de pesquisa com o parâmetro-filtro.</span><span class="sxs-lookup"><span data-stu-id="20c83-118">Find-RoleCapability can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="20c83-119">Localizar RoleCapability pode filtrar por módulos de todas as ou poucos dos repositórios do registado.</span><span class="sxs-lookup"><span data-stu-id="20c83-119">Find-RoleCapability can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="20c83-120">Sintaxe de cmdlet</span><span class="sxs-lookup"><span data-stu-id="20c83-120">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="20c83-121">Referência de ajuda online do cmdlet</span><span class="sxs-lookup"><span data-stu-id="20c83-121">Cmdlet online help reference</span></span>

[<span data-ttu-id="20c83-122">Localizar RoleCapability</span><span class="sxs-lookup"><span data-stu-id="20c83-122">Find-RoleCapability</span></span>](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a><span data-ttu-id="20c83-123">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="20c83-123">Example commands</span></span>
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```

