---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Filtrar os resultados da pesquisa
ms.openlocfilehash: 13270a310613a974e1588a9f56d443a936cfebb8
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004214"
---
# <a name="filtering-search-results"></a><span data-ttu-id="3ce07-103">Filtrar os resultados da pesquisa</span><span class="sxs-lookup"><span data-stu-id="3ce07-103">Filtering search results</span></span>

<span data-ttu-id="3ce07-104">O [guia de pacotes](https://www.powershellgallery.com/packages) apresenta todos os pacotes disponíveis na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3ce07-104">The [Packages tab](https://www.powershellgallery.com/packages) displays all available packages in the PowerShell Gallery.</span></span>

<span data-ttu-id="3ce07-105">Existem várias formas de filtrar, ordenar e pesquisar os pacotes.</span><span class="sxs-lookup"><span data-stu-id="3ce07-105">There are several ways to filter, sort, and search the packages.</span></span>
<span data-ttu-id="3ce07-106">Para ver mais detalhes sobre um determinado pacote, clique no pacote.</span><span class="sxs-lookup"><span data-stu-id="3ce07-106">To see more details about a particular package, click the package.</span></span>

## <a name="filter-by"></a><span data-ttu-id="3ce07-107">Filtrar por</span><span class="sxs-lookup"><span data-stu-id="3ce07-107">Filter By</span></span>

<span data-ttu-id="3ce07-108">Na lista pendente em "Filtrar por" permite aos utilizadores filtrar os resultados por:</span><span class="sxs-lookup"><span data-stu-id="3ce07-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
- <span data-ttu-id="3ce07-109">Incluir pré-lançamento</span><span class="sxs-lookup"><span data-stu-id="3ce07-109">Include Prerelease</span></span>
- <span data-ttu-id="3ce07-110">Apenas estável</span><span class="sxs-lookup"><span data-stu-id="3ce07-110">Stable Only</span></span>

<span data-ttu-id="3ce07-111">Para obter informações sobre "Prerelease" e "Estável", consulte [versão de pré-lançamento do controle de versão adicionada à PowerShellGet e galeria do PowerShell](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) no Blog da Equipe do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3ce07-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="3ce07-112">As caixas de seleção na lista pendente permitem aos utilizadores filtrar os resultados por:</span><span class="sxs-lookup"><span data-stu-id="3ce07-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
- <span data-ttu-id="3ce07-113">Tipos de pacotes</span><span class="sxs-lookup"><span data-stu-id="3ce07-113">Package Types</span></span>
  - <span data-ttu-id="3ce07-114">Módulo</span><span class="sxs-lookup"><span data-stu-id="3ce07-114">Module</span></span>
  - <span data-ttu-id="3ce07-115">Script</span><span class="sxs-lookup"><span data-stu-id="3ce07-115">Script</span></span>
- <span data-ttu-id="3ce07-116">Categorias</span><span class="sxs-lookup"><span data-stu-id="3ce07-116">Categories</span></span>
  - <span data-ttu-id="3ce07-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3ce07-117">Cmdlet</span></span>
  - <span data-ttu-id="3ce07-118">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="3ce07-118">DSC Resource</span></span>
  - <span data-ttu-id="3ce07-119">Função</span><span class="sxs-lookup"><span data-stu-id="3ce07-119">Function</span></span>
  - <span data-ttu-id="3ce07-120">Capacidade de função</span><span class="sxs-lookup"><span data-stu-id="3ce07-120">Role Capability</span></span>
  - <span data-ttu-id="3ce07-121">Fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="3ce07-121">Workflow</span></span>

<span data-ttu-id="3ce07-122">Para ver apenas os módulos na galeria do PowerShell, verifique o módulo os tipos de pacote.</span><span class="sxs-lookup"><span data-stu-id="3ce07-122">To see only modules in the PowerShell Gallery, check Module in the Package Types.</span></span>
<span data-ttu-id="3ce07-123">Da mesma forma, para ver apenas os scripts na galeria do PowerShell, verifique o Script os tipos de pacote.</span><span class="sxs-lookup"><span data-stu-id="3ce07-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Package Types.</span></span>

> [!NOTE]
> <span data-ttu-id="3ce07-124">Os filtros são, inclusivos.</span><span class="sxs-lookup"><span data-stu-id="3ce07-124">Filters are inclusive.</span></span>
> <span data-ttu-id="3ce07-125">Exemplo: Um pacote que contém cmdlets e funções será apresentada se o Cmdlet ou função (ou ambos) são verificadas.</span><span class="sxs-lookup"><span data-stu-id="3ce07-125">Example: A package containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="3ce07-126">Se não forem selecionados, o pacote não serão apresentados.</span><span class="sxs-lookup"><span data-stu-id="3ce07-126">If neither are selected, the package will not appear.</span></span>
> <span data-ttu-id="3ce07-127">Da mesma forma, se forem selecionadas todas as categorias, serão apresentada apenas os pacotes que contêm uma dessas categorias.</span><span class="sxs-lookup"><span data-stu-id="3ce07-127">Similarly, if all categories are selected, only packages containing one of those categories will appear.</span></span>
> <span data-ttu-id="3ce07-128">**Pacotes que não pertencem a qualquer uma dessas categorias não serão apresentados.**</span><span class="sxs-lookup"><span data-stu-id="3ce07-128">**Packages that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="3ce07-129">Ordenar por</span><span class="sxs-lookup"><span data-stu-id="3ce07-129">Sort By</span></span>

<span data-ttu-id="3ce07-130">Ordenar por pendente permite aos utilizadores ordenar os resultados por:</span><span class="sxs-lookup"><span data-stu-id="3ce07-130">The Sort By drop-down allows users to sort the results by:</span></span>
- <span data-ttu-id="3ce07-131">Popularidade - popularidade é determinada pela contagem de Download</span><span class="sxs-lookup"><span data-stu-id="3ce07-131">Popularity - Popularity is determined by Download Count</span></span>
- <span data-ttu-id="3ce07-132">A-Z - por ordem alfabética pelo nome do pacote</span><span class="sxs-lookup"><span data-stu-id="3ce07-132">A-Z - Alphabetically by package name</span></span>
- <span data-ttu-id="3ce07-133">Recentes - pacotes são apresentados por ordem da data de publicação</span><span class="sxs-lookup"><span data-stu-id="3ce07-133">Recent - Packages appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="3ce07-134">Caixa de pesquisa</span><span class="sxs-lookup"><span data-stu-id="3ce07-134">Search Box</span></span>

<span data-ttu-id="3ce07-135">Caixa de pesquisa permite que os usuários pesquisem os pacotes em palavras-chave.</span><span class="sxs-lookup"><span data-stu-id="3ce07-135">The Search Box allows users to search the packages on keywords.</span></span>
<span data-ttu-id="3ce07-136">Para obter mais informações, consulte [sintaxe de pesquisa da galeria](search-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="3ce07-136">For more information, see [Gallery Search Syntax](search-syntax.md).</span></span>
