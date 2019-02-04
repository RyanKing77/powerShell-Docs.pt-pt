---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a0b1573611c5d4232082c19ca19b4cca79d0699e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685257"
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="a9229-102">Deteção de módulo do PowerShell, instalar e inventário com o PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a9229-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>

<span data-ttu-id="a9229-103">O PowerShellGet está incluído nesta versão do WMF:</span><span class="sxs-lookup"><span data-stu-id="a9229-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="a9229-104">Find-Module pode filtrar os metadados do módulo com o - parâmetro de etiqueta</span><span class="sxs-lookup"><span data-stu-id="a9229-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="a9229-105">Find-Module poderá filtrar na linguagem de pesquisa de repositório específico com o parâmetro - Filter</span><span class="sxs-lookup"><span data-stu-id="a9229-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="a9229-106">Find-Module pode filtrar com base num módulo de conteúdo com o - comando, - DscResource e - inclui parâmetros</span><span class="sxs-lookup"><span data-stu-id="a9229-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="a9229-107">Find-DscResource permite a deteção de recursos de DSC individuais nos repositórios</span><span class="sxs-lookup"><span data-stu-id="a9229-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="a9229-108">Suporte para a instalação do e publicação de partilhas de ficheiros com o NuGet</span><span class="sxs-lookup"><span data-stu-id="a9229-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="a9229-109">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="a9229-109">Example commands</span></span>
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

## <a name="new-features-in-powershellget"></a><span data-ttu-id="a9229-110">Novos recursos do PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a9229-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="a9229-111">Suporte para a versão de lado a lado no Windows PowerShell 5.0 ou mais recente</span><span class="sxs-lookup"><span data-stu-id="a9229-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="a9229-112">Suporte de instalação de dependência do módulo</span><span class="sxs-lookup"><span data-stu-id="a9229-112">Module dependency installation support</span></span>
-   <span data-ttu-id="a9229-113">Três novos cmdlets</span><span class="sxs-lookup"><span data-stu-id="a9229-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="a9229-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="a9229-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="a9229-115">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="a9229-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="a9229-116">Save-Module</span><span class="sxs-lookup"><span data-stu-id="a9229-116">Save-Module</span></span>
