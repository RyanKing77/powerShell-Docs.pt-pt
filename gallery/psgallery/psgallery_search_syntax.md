---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: psgallery_search_syntax
ms.openlocfilehash: 337b4b1e702994fcbc456eb31a2d8632f5220d09
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="94af0-103">Sintaxe de pesquisa de galeria</span><span class="sxs-lookup"><span data-stu-id="94af0-103">Gallery Search Syntax</span></span>

<span data-ttu-id="94af0-104">Galeria do PowerShell oferece um searchbox de texto em que pode utilizar palavras, expressões e expressões de palavra-chave para restringir os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="94af0-104">PowerShell Gallery offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="94af0-105">Procura por palavras-chave</span><span class="sxs-lookup"><span data-stu-id="94af0-105">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="94af0-106">Pesquisa fazer o seu melhor esforço para localizar documentos relevantes que contém as 3 todas as palavras-chave e devolver documentos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="94af0-106">Search will do its best effort to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="94af0-107">A procura utilizando expressões e palavras-chave</span><span class="sxs-lookup"><span data-stu-id="94af0-107">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="94af0-108">Introduzir uma frase de acesso entre aspas ("") altere a procura para procurar o frase específica em vez de palavras-chave separadas.</span><span class="sxs-lookup"><span data-stu-id="94af0-108">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="94af0-109">Correspondência de documentos, normalmente, deve conter o frase exato "sql do azure", incluindo variações no maiúsculas/minúsculas por exemplo "SQL do azure" e também normalmente contém a palavra 'implementação'.</span><span class="sxs-lookup"><span data-stu-id="94af0-109">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="94af0-110">Nos campos de filtragem</span><span class="sxs-lookup"><span data-stu-id="94af0-110">Filtering on fields</span></span>

<span data-ttu-id="94af0-111">Pode procurar um ID de item específico (ou 'Id' ou 'id') ou alguns outros campos por lhe o prefixo procurar termos com o nome do campo.</span><span class="sxs-lookup"><span data-stu-id="94af0-111">You can search for a specific item ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="94af0-112">Atualmente os campos pesquisáveis são 'Id', 'Version', 'Etiquetas', 'Autor', 'Proprietário', 'Funções', 'Cmdlets', 'DscResources' e 'PowerShellVersion'.</span><span class="sxs-lookup"><span data-stu-id="94af0-112">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="94af0-113">[O que é a diferença entre ID e título?</span><span class="sxs-lookup"><span data-stu-id="94af0-113">[What's the difference between ID and Title?</span></span> <span data-ttu-id="94af0-114">O ID é o nome que utiliza na consola do.</span><span class="sxs-lookup"><span data-stu-id="94af0-114">ID is the name you use in the console.</span></span> <span data-ttu-id="94af0-115">Título é o que é apresentado na parte superior da página item nos resultados da pesquisa.]</span><span class="sxs-lookup"><span data-stu-id="94af0-115">Title is what is shown at the top of the item page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="94af0-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="94af0-116">Examples</span></span>

    ID:"PSReadline"
    id:"AzureRM.Profile"

<span data-ttu-id="94af0-117">Localiza itens com "PSReadline" ou "AzureRM.Profile" no respetivo campo de ID, respetivamente.</span><span class="sxs-lookup"><span data-stu-id="94af0-117">finds items with "PSReadline" or "AzureRM.Profile" in their ID field respectively.</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="94af0-118">é outra forma para localizar itens com "AzureRM.Profile" no respetivo campo de ID.</span><span class="sxs-lookup"><span data-stu-id="94af0-118">is another way to find items with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="94af0-119">O filtro 'Id' é uma subcadeia corresponderem, por isso se procurar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="94af0-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="94af0-120">Irá obter resultados como 'AzureRM.Profile' e 'Azure.Storage'.</span><span class="sxs-lookup"><span data-stu-id="94af0-120">You'll get results like 'AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="94af0-121">Poderá também pesquisar por várias palavras-chave num campo único.</span><span class="sxs-lookup"><span data-stu-id="94af0-121">You can also search for multiple keywords in a single field.</span></span> <span data-ttu-id="94af0-122">Ou combinar e misturar campos.</span><span class="sxs-lookup"><span data-stu-id="94af0-122">Or mix and match fields.</span></span>

    id:azure tags:intellisense
    id:azure id:storage

<span data-ttu-id="94af0-123">E pode efetuar pesquisas de expressão:</span><span class="sxs-lookup"><span data-stu-id="94af0-123">And you can perform phrase searches:</span></span>

    id:"azure.storage"


<span data-ttu-id="94af0-124">Para procurar todos os itens com a etiqueta de DSC.</span><span class="sxs-lookup"><span data-stu-id="94af0-124">To search all items with DSC tag.</span></span>

    Tags:"DSC"

<span data-ttu-id="94af0-125">Para procurar todos os itens com a função especificada.</span><span class="sxs-lookup"><span data-stu-id="94af0-125">To search all items with the specified function.</span></span>

    Functions:"Update-AzureRM"

<span data-ttu-id="94af0-126">Para procurar todos os itens com o cmdlet especificado.</span><span class="sxs-lookup"><span data-stu-id="94af0-126">To search all items with the specified cmdlet.</span></span>

    Cmdlets:"Get-AzureRmEnvironment"

<span data-ttu-id="94af0-127">Para procurar todos os itens com o nome de recursos de DSC especificado.</span><span class="sxs-lookup"><span data-stu-id="94af0-127">To search all items with the specified DSC Resource name.</span></span>

    DscResources:"xArchive"

<span data-ttu-id="94af0-128">Para procurar todos os itens com o PowerShellVersion especificado</span><span class="sxs-lookup"><span data-stu-id="94af0-128">To search all items with the specified PowerShellVersion</span></span>

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


<span data-ttu-id="94af0-129">Por fim, se utilizar um campo que não é suportada, como 'comandos', vamos apenas ignorá-lo e todos os campos de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="94af0-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="94af0-130">Por isso, a seguinte consulta</span><span class="sxs-lookup"><span data-stu-id="94af0-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="94af0-131">É interpretado exatamente o mesmo que esta consulta:</span><span class="sxs-lookup"><span data-stu-id="94af0-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage