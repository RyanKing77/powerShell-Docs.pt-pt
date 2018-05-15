---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: Filtrar os resultados de pesquisa
ms.openlocfilehash: 5a7ea8207619318efd8195ee3d1c8f8ab51209da
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: pt-PT
ms.lasthandoff: 05/10/2018
---
# <a name="filtering-search-results"></a><span data-ttu-id="b5648-103">Filtrar os resultados de pesquisa</span><span class="sxs-lookup"><span data-stu-id="b5648-103">Filtering search results</span></span>

<span data-ttu-id="b5648-104">O [separador itens](https://www.powershellgallery.com/items) apresenta todos os itens disponíveis na galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b5648-104">The [Items tab](https://www.powershellgallery.com/items) displays all available items in the PowerShell Gallery.</span></span>

<span data-ttu-id="b5648-105">Existem várias formas de filtrar, ordenar e os itens de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b5648-105">There are several ways to filter, sort, and search the items.</span></span>
<span data-ttu-id="b5648-106">Para ver mais detalhes sobre um determinado item, clique no item.</span><span class="sxs-lookup"><span data-stu-id="b5648-106">To see more details about a particular item, click the item.</span></span>

## <a name="filter-by"></a><span data-ttu-id="b5648-107">Filtrar por</span><span class="sxs-lookup"><span data-stu-id="b5648-107">Filter By</span></span>

<span data-ttu-id="b5648-108">Na lista pendente em "Filtrar por" permite que os utilizadores filtrar os resultados por:</span><span class="sxs-lookup"><span data-stu-id="b5648-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
- <span data-ttu-id="b5648-109">Incluir pré-lançamento</span><span class="sxs-lookup"><span data-stu-id="b5648-109">Include Prerelease</span></span>
- <span data-ttu-id="b5648-110">Estável apenas</span><span class="sxs-lookup"><span data-stu-id="b5648-110">Stable Only</span></span>

<span data-ttu-id="b5648-111">Para obter informações sobre "Pré-lançamento" e "Estável", consulte [adicionados de controlo de versões de pré-lançamento para PowerShellGet e galeria do PowerShell](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) no blogue de equipa do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b5648-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="b5648-112">As caixas de verificação em pendente permitem aos utilizadores filtrar os resultados por:</span><span class="sxs-lookup"><span data-stu-id="b5648-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
- <span data-ttu-id="b5648-113">Tipos de itens</span><span class="sxs-lookup"><span data-stu-id="b5648-113">Item Types</span></span>
  - <span data-ttu-id="b5648-114">Módulo</span><span class="sxs-lookup"><span data-stu-id="b5648-114">Module</span></span>
  - <span data-ttu-id="b5648-115">Script</span><span class="sxs-lookup"><span data-stu-id="b5648-115">Script</span></span>
- <span data-ttu-id="b5648-116">Categorias</span><span class="sxs-lookup"><span data-stu-id="b5648-116">Categories</span></span>
  - <span data-ttu-id="b5648-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b5648-117">Cmdlet</span></span>
  - <span data-ttu-id="b5648-118">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="b5648-118">DSC Resource</span></span>
  - <span data-ttu-id="b5648-119">Função</span><span class="sxs-lookup"><span data-stu-id="b5648-119">Function</span></span>
  - <span data-ttu-id="b5648-120">Capacidade de função</span><span class="sxs-lookup"><span data-stu-id="b5648-120">Role Capability</span></span>
  - <span data-ttu-id="b5648-121">Fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b5648-121">Workflow</span></span>

<span data-ttu-id="b5648-122">Para ver apenas os módulos na galeria do PowerShell, consulte módulo nos tipos de Item.</span><span class="sxs-lookup"><span data-stu-id="b5648-122">To see only modules in the PowerShell Gallery, check Module in the Item Types.</span></span>
<span data-ttu-id="b5648-123">Da mesma forma, para ver apenas os scripts na galeria do PowerShell, consulte os tipos de Item de Script.</span><span class="sxs-lookup"><span data-stu-id="b5648-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Item Types.</span></span>

> [!NOTE]
> <span data-ttu-id="b5648-124">Os filtros são inclusive.</span><span class="sxs-lookup"><span data-stu-id="b5648-124">Filters are inclusive.</span></span>
> <span data-ttu-id="b5648-125">Exemplo: Um item que contém os cmdlets e funções será apresentada se o Cmdlet ou função (ou ambos) são verificadas.</span><span class="sxs-lookup"><span data-stu-id="b5648-125">Example: An item containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="b5648-126">Se não forem selecionadas, o item não serão apresentados.</span><span class="sxs-lookup"><span data-stu-id="b5648-126">If neither are selected, the item will not appear.</span></span>
> <span data-ttu-id="b5648-127">Da mesma forma, se forem selecionadas todas as categorias, serão apresentado apenas os itens que contêm uma dessas categorias.</span><span class="sxs-lookup"><span data-stu-id="b5648-127">Similarly, if all categories are selected, only items containing one of those categories will appear.</span></span>
> <span data-ttu-id="b5648-128">**Não serão apresentados itens que não pertencem a nenhum nessas categorias.**</span><span class="sxs-lookup"><span data-stu-id="b5648-128">**Items that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="b5648-129">Ordenar por</span><span class="sxs-lookup"><span data-stu-id="b5648-129">Sort By</span></span>

<span data-ttu-id="b5648-130">Ordenar por pendente permite aos utilizadores ordenar os resultados por:</span><span class="sxs-lookup"><span data-stu-id="b5648-130">The Sort By drop-down allows users to sort the results by:</span></span>
- <span data-ttu-id="b5648-131">Popularidade - popularidade é determinada pelo número de transferir</span><span class="sxs-lookup"><span data-stu-id="b5648-131">Popularity - Popularity is determined by Download Count</span></span>
- <span data-ttu-id="b5648-132">A-Z - por ordem alfabética pelo nome do item</span><span class="sxs-lookup"><span data-stu-id="b5648-132">A-Z - Alphabetically by item name</span></span>
- <span data-ttu-id="b5648-133">Recente - itens são apresentados por ordem da data de publicação</span><span class="sxs-lookup"><span data-stu-id="b5648-133">Recent - Items appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="b5648-134">Caixa de pesquisa</span><span class="sxs-lookup"><span data-stu-id="b5648-134">Search Box</span></span>

<span data-ttu-id="b5648-135">Caixa de pesquisa permite aos utilizadores para os itens no palavras-chave de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b5648-135">The Search Box allows users to search the items on keywords.</span></span>
<span data-ttu-id="b5648-136">Para obter mais informações, consulte [sintaxe de pesquisa de galeria](search-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="b5648-136">For more information, see [Gallery Search Syntax](search-syntax.md).</span></span>