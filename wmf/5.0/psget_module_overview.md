---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9efc640dfda7e08e59d2c56746facd9658b1f9de
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="fc205-102">Deteção de módulo do PowerShell, instalar e de inventário com PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="fc205-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>

<span data-ttu-id="fc205-103">PowerShellGet está incluído nesta versão do WMF:</span><span class="sxs-lookup"><span data-stu-id="fc205-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="fc205-104">Pode filtrar encontrar o módulo nos metadados do módulo com o parâmetro-etiqueta</span><span class="sxs-lookup"><span data-stu-id="fc205-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="fc205-105">Encontrar o módulo pode filtrar por idioma específicas do repositório de pesquisa com o filtro parâmetro -</span><span class="sxs-lookup"><span data-stu-id="fc205-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="fc205-106">Pode encontrar o módulo filtro com base num módulo conteúdo com - comando, - DscResource e - inclui os parâmetros</span><span class="sxs-lookup"><span data-stu-id="fc205-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="fc205-107">Localizar DscResource permite a deteção de recursos de DSC individuais em repositórios</span><span class="sxs-lookup"><span data-stu-id="fc205-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="fc205-108">Suporte para instalar a partir do e da publicação para partilhas de ficheiros com NuGet</span><span class="sxs-lookup"><span data-stu-id="fc205-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="fc205-109">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="fc205-109">Example commands</span></span>
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a><span data-ttu-id="fc205-110">Novas funcionalidades no PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="fc205-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="fc205-111">Suporte para a versão de lado a lado no Windows PowerShell 5.0 ou mais recente</span><span class="sxs-lookup"><span data-stu-id="fc205-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="fc205-112">Suporte de instalação de dependência do módulo</span><span class="sxs-lookup"><span data-stu-id="fc205-112">Module dependency installation support</span></span>
-   <span data-ttu-id="fc205-113">Três novos cmdlets</span><span class="sxs-lookup"><span data-stu-id="fc205-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="fc205-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="fc205-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="fc205-115">Módulo desinstalar</span><span class="sxs-lookup"><span data-stu-id="fc205-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="fc205-116">Módulo de guardar</span><span class="sxs-lookup"><span data-stu-id="fc205-116">Save-Module</span></span>
