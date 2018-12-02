---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Sintaxe de pesquisa da Galeria
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742861"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="ba4fa-103">Sintaxe de pesquisa da Galeria</span><span class="sxs-lookup"><span data-stu-id="ba4fa-103">Gallery Search Syntax</span></span>

<span data-ttu-id="ba4fa-104">Pode pesquisar a galeria do PowerShell, utilizando o [site da web da galeria do PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="ba4fa-104">You can search the PowerShell Gallery using the [PowerShell Gallery's web site](https://www.powershellgallery.com/).</span></span>
<span data-ttu-id="ba4fa-105">Site de galeria do PowerShell oferece uma caixa de pesquisa de texto em que pode usar palavras, frases e expressões de palavra-chave para limitar os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-105">PowerShell Gallery web site offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="ba4fa-106">Procurar por palavras-chave</span><span class="sxs-lookup"><span data-stu-id="ba4fa-106">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="ba4fa-107">Pesquisa tenta encontrar os documentos relevantes que contém todas as palavras-chave de 3 e devolver os documentos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-107">Search attempts to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="ba4fa-108">Utilizar frases e palavras-chave de pesquisa</span><span class="sxs-lookup"><span data-stu-id="ba4fa-108">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="ba4fa-109">Introduzir uma frase entre aspas ("") altere a procura para procurar a frase específica em vez de palavras-chave separadas.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-109">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="ba4fa-110">Documentos correspondentes, normalmente, devem conter a frase exata "sql do azure", incluindo variações na capitalização p. ex. "SQL do azure" e também normalmente contêm a palavra "implementação".</span><span class="sxs-lookup"><span data-stu-id="ba4fa-110">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="ba4fa-111">Filtrar em campos</span><span class="sxs-lookup"><span data-stu-id="ba4fa-111">Filtering on fields</span></span>

<span data-ttu-id="ba4fa-112">Pode pesquisar por um ID de pacote específico (ou "Id" ou "id") ou termos com o nome do campo de pesquisa de determinados outros campos colocando um prefixo.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-112">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="ba4fa-113">Atualmente, os campos pesquisáveis são 'Id', 'Versão', "Etiquetas", "Autor", "Owner", "Funções", "Cmdlets", 'DscResources' e 'PowerShellVersion'.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-113">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="ba4fa-114">[O que é a diferença entre o ID e o título?</span><span class="sxs-lookup"><span data-stu-id="ba4fa-114">[What's the difference between ID and Title?</span></span> <span data-ttu-id="ba4fa-115">O ID é o nome que utiliza na consola do.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-115">ID is the name you use in the console.</span></span> <span data-ttu-id="ba4fa-116">O título é o que é mostrado na parte superior da página pacote nos resultados da pesquisa.]</span><span class="sxs-lookup"><span data-stu-id="ba4fa-116">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="ba4fa-117">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ba4fa-117">Examples</span></span>

    ID:PSReadline
    
<span data-ttu-id="ba4fa-118">encontra pacotes com o ID que contém "PSReadline".</span><span class="sxs-lookup"><span data-stu-id="ba4fa-118">finds packages with an ID containing "PSReadline".</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="ba4fa-119">é outra maneira de encontrar os pacotes com "Azurerm. Profile" no respetivo campo de ID.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-119">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="ba4fa-120">O filtro de "Id" é uma subcadeia de corresponder, se pesquisar para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ba4fa-120">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="ba4fa-121">Isso fornece resultados que incluem o azurerm. Profile ' e 'Azure.Storage'.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-121">This provides results that include AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="ba4fa-122">Também pode pesquisar por várias palavras-chave num único campo.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-122">You can also search for multiple keywords in a single field.</span></span> 

    id:azure tags:intellisense

<span data-ttu-id="ba4fa-123">E pode efetuar pesquisas de frase com aspas duplas:</span><span class="sxs-lookup"><span data-stu-id="ba4fa-123">And you can perform phrase searches using double quotes:</span></span>

    id:"azure.storage"

<span data-ttu-id="ba4fa-124">Para pesquisar todos os pacotes com a etiqueta de DSC.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-124">To search all packages with DSC tag.</span></span>

    Tags:DSC

<span data-ttu-id="ba4fa-125">Para pesquisar todos os pacotes com a função especificada.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-125">To search all packages with the specified function.</span></span>

    Functions:Get-TreeSize

<span data-ttu-id="ba4fa-126">Para pesquisar todos os pacotes com o cmdlet especificado.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:Get-AzureRmEnvironment

<span data-ttu-id="ba4fa-127">Para pesquisar todos os pacotes com o nome de recurso de DSC especificado.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:xArchive

<span data-ttu-id="ba4fa-128">Para pesquisar todos os pacotes com o PowerShellVersion especificado</span><span class="sxs-lookup"><span data-stu-id="ba4fa-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:2.0

<span data-ttu-id="ba4fa-129">Por fim, se usar um campo que não é suportada, por exemplo, 'commands', vou ignorá-lo e todos os campos de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="ba4fa-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="ba4fa-130">Portanto, a seguinte consulta</span><span class="sxs-lookup"><span data-stu-id="ba4fa-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="ba4fa-131">É interpretado exatamente o mesmo que esta consulta:</span><span class="sxs-lookup"><span data-stu-id="ba4fa-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
