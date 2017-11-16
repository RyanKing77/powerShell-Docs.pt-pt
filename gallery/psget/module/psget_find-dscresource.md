---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Localizar DscResource
ms.openlocfilehash: 37ba7925d6f73c453126f25e0818b3f8839d3b3b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="find-dscresource"></a><span data-ttu-id="191fa-103">Localizar DscResource</span><span class="sxs-lookup"><span data-stu-id="191fa-103">Find-DscResource</span></span>

<span data-ttu-id="191fa-104">Localiza recursos de DSC nos módulos.</span><span class="sxs-lookup"><span data-stu-id="191fa-104">Finds DSC Resources in modules.</span></span>

## <a name="description"></a><span data-ttu-id="191fa-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="191fa-105">Description</span></span>

<span data-ttu-id="191fa-106">O cmdlet Find DscResource localiza [configuração de estado pretendido (DSC)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview) recursos contidos nos módulos que correspondem aos critérios especificados da repositórios registados.</span><span class="sxs-lookup"><span data-stu-id="191fa-106">The Find-DscResource cmdlet finds [Desired State Configuration (DSC)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview) resources contained in modules that match the specified criteria from registered repositories.</span></span>
<span data-ttu-id="191fa-107">Para cada módulo que este cmdlet localiza, localizar DscResource devolve um objeto de PSGetDscResourceInfo que podem ser transmitidos para o módulo de instalação para instalar os módulos que contém os recursos que este cmdlet devolve.</span><span class="sxs-lookup"><span data-stu-id="191fa-107">For each module that this cmdlet finds, Find-DscResource returns a PSGetDscResourceInfo object that you can pipe to Install-Module to install the modules containing the resources that this cmdlet returns.</span></span>

<span data-ttu-id="191fa-108">DSC é uma nova plataforma de gestão do Windows PowerShell que lhe permite implementar e gerir dados de configuração para os serviços de software e gerir o ambiente em que estes serviços são executados.</span><span class="sxs-lookup"><span data-stu-id="191fa-108">DSC is a new management platform in Windows PowerShell that enables deploying and managing configuration data for software services and managing the environment in which these services run.</span></span>

<span data-ttu-id="191fa-109">Pretendido que recursos de configuração de estado (DSC) fornecem os blocos modulares para uma configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="191fa-109">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="191fa-110">Um recurso expõe propriedades que podem ser configurada (esquema) e contém as funções de script do PowerShell que chama o Gestor de configuração Local (MMC) para "torná-lo,".</span><span class="sxs-lookup"><span data-stu-id="191fa-110">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="191fa-111">Um recurso pode modelo algo como genérica como um ficheiro ou uma definição de servidor IIS tão específico.</span><span class="sxs-lookup"><span data-stu-id="191fa-111">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="191fa-112">Grupos de como recursos são combinados para um módulo de DSC, que organiza todos os ficheiros necessários na uma estrutura que é portátil e inclui os metadados para identificar a forma como os recursos destinam-se a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="191fa-112">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

- <span data-ttu-id="191fa-113">Localizar DscResource pode filtrar com parâmetros de versão: MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="191fa-113">Find-DscResource can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="191fa-114">Estes parâmetros são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="191fa-114">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="191fa-115">Estes parâmetros de versão são permitidos apenas com o nome do módulo único sem quaisquer carateres universais.</span><span class="sxs-lookup"><span data-stu-id="191fa-115">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="191fa-116">Se não for especificado o parâmetro RequiredVersion, localizar DscResource devolve a versão mais recente do módulo que seja igual ou maior do que a versão mínima especificado ou a versão mais recente do módulo, não se for especificada nenhuma versão mínima.</span><span class="sxs-lookup"><span data-stu-id="191fa-116">If the RequiredVersion parameter is not specified, Find-DscResource returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="191fa-117">Se não for especificado o parâmetro RequiredVersion, localizar DscResource devolve apenas a versão do módulo que corresponde exatamente a versão especificada.</span><span class="sxs-lookup"><span data-stu-id="191fa-117">If the RequiredVersion parameter is specified, Find-DscResource only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="191fa-118">Pode filtrar DscResource localizar nos metadados do módulo com o parâmetro-etiqueta</span><span class="sxs-lookup"><span data-stu-id="191fa-118">Find-DscResource can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="191fa-119">Localizar DscResource pode filtrar por idioma específicas do repositório de pesquisa com o parâmetro-filtro.</span><span class="sxs-lookup"><span data-stu-id="191fa-119">Find-DscResource can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="191fa-120">Localizar DscResource pode filtrar por módulos de todas as ou poucos dos repositórios do registado.</span><span class="sxs-lookup"><span data-stu-id="191fa-120">Find-DscResource can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="191fa-121">Sintaxe de cmdlet</span><span class="sxs-lookup"><span data-stu-id="191fa-121">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="191fa-122">Referência de ajuda online do cmdlet</span><span class="sxs-lookup"><span data-stu-id="191fa-122">Cmdlet online help reference</span></span>

[<span data-ttu-id="191fa-123">Localizar DscResource</span><span class="sxs-lookup"><span data-stu-id="191fa-123">Find-DscResource</span></span>](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a><span data-ttu-id="191fa-124">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="191fa-124">Example commands</span></span>
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```

