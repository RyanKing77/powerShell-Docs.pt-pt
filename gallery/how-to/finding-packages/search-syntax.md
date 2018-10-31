---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Sintaxe de pesquisa da Galeria
ms.openlocfilehash: 9aadb6771c85845cc3fa05cb56f0194b060d1c1b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004148"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="41611-103">Sintaxe de pesquisa da Galeria</span><span class="sxs-lookup"><span data-stu-id="41611-103">Gallery Search Syntax</span></span>

<span data-ttu-id="41611-104">Galeria do PowerShell oferece uma caixa de pesquisa de texto em que pode usar palavras, frases e expressões de palavra-chave para limitar os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="41611-104">PowerShell Gallery offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="41611-105">Procurar por palavras-chave</span><span class="sxs-lookup"><span data-stu-id="41611-105">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="41611-106">Pesquisa fará o melhor esforço para encontrar os documentos relevantes que contém todas as palavras-chave de 3 e devolver os documentos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="41611-106">Search will do its best effort to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="41611-107">Utilizar frases e palavras-chave de pesquisa</span><span class="sxs-lookup"><span data-stu-id="41611-107">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="41611-108">Introduzir uma frase entre aspas ("") altere a procura para procurar a frase específica em vez de palavras-chave separadas.</span><span class="sxs-lookup"><span data-stu-id="41611-108">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="41611-109">Documentos correspondentes, normalmente, devem conter a frase exata "sql do azure", incluindo variações na capitalização p. ex. "SQL do azure" e também normalmente contêm a palavra "implementação".</span><span class="sxs-lookup"><span data-stu-id="41611-109">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="41611-110">Filtrar em campos</span><span class="sxs-lookup"><span data-stu-id="41611-110">Filtering on fields</span></span>

<span data-ttu-id="41611-111">Pode pesquisar por um ID de pacote específico (ou "Id" ou "id") ou termos com o nome do campo de pesquisa de determinados outros campos colocando um prefixo.</span><span class="sxs-lookup"><span data-stu-id="41611-111">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="41611-112">Atualmente, os campos pesquisáveis são 'Id', 'Versão', "Etiquetas", "Autor", "Owner", "Funções", "Cmdlets", 'DscResources' e 'PowerShellVersion'.</span><span class="sxs-lookup"><span data-stu-id="41611-112">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="41611-113">[O que é a diferença entre o ID e o título?</span><span class="sxs-lookup"><span data-stu-id="41611-113">[What's the difference between ID and Title?</span></span> <span data-ttu-id="41611-114">O ID é o nome que utiliza na consola do.</span><span class="sxs-lookup"><span data-stu-id="41611-114">ID is the name you use in the console.</span></span> <span data-ttu-id="41611-115">O título é o que é mostrado na parte superior da página pacote nos resultados da pesquisa.]</span><span class="sxs-lookup"><span data-stu-id="41611-115">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="41611-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="41611-116">Examples</span></span>

    ID:"PSReadline"
    id:"AzureRM.Profile"

<span data-ttu-id="41611-117">encontra pacotes com "PSReadline" ou "Azurerm. Profile" no respetivo campo de ID, respetivamente.</span><span class="sxs-lookup"><span data-stu-id="41611-117">finds packages with "PSReadline" or "AzureRM.Profile" in their ID field respectively.</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="41611-118">é outra maneira de encontrar os pacotes com "Azurerm. Profile" no respetivo campo de ID.</span><span class="sxs-lookup"><span data-stu-id="41611-118">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="41611-119">O filtro de "Id" é uma subcadeia de corresponder, se pesquisar para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="41611-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="41611-120">Obterá resultados como 'Azurerm. Profile' e 'Azure.Storage'.</span><span class="sxs-lookup"><span data-stu-id="41611-120">You'll get results like 'AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="41611-121">Também pode pesquisar por várias palavras-chave num único campo.</span><span class="sxs-lookup"><span data-stu-id="41611-121">You can also search for multiple keywords in a single field.</span></span> <span data-ttu-id="41611-122">Ou combinar e corresponder aos campos.</span><span class="sxs-lookup"><span data-stu-id="41611-122">Or mix and match fields.</span></span>

    id:azure tags:intellisense
    id:azure id:storage

<span data-ttu-id="41611-123">E pode efetuar pesquisas de frase:</span><span class="sxs-lookup"><span data-stu-id="41611-123">And you can perform phrase searches:</span></span>

    id:"azure.storage"


<span data-ttu-id="41611-124">Para pesquisar todos os pacotes com a etiqueta de DSC.</span><span class="sxs-lookup"><span data-stu-id="41611-124">To search all packages with DSC tag.</span></span>

    Tags:"DSC"

<span data-ttu-id="41611-125">Para pesquisar todos os pacotes com a função especificada.</span><span class="sxs-lookup"><span data-stu-id="41611-125">To search all packages with the specified function.</span></span>

    Functions:"Update-AzureRM"

<span data-ttu-id="41611-126">Para pesquisar todos os pacotes com o cmdlet especificado.</span><span class="sxs-lookup"><span data-stu-id="41611-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:"Get-AzureRmEnvironment"

<span data-ttu-id="41611-127">Para pesquisar todos os pacotes com o nome de recurso de DSC especificado.</span><span class="sxs-lookup"><span data-stu-id="41611-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:"xArchive"

<span data-ttu-id="41611-128">Para pesquisar todos os pacotes com o PowerShellVersion especificado</span><span class="sxs-lookup"><span data-stu-id="41611-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


<span data-ttu-id="41611-129">Por fim, se usar um campo que não é suportada, por exemplo, 'commands', vou ignorá-lo e todos os campos de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="41611-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="41611-130">Portanto, a seguinte consulta</span><span class="sxs-lookup"><span data-stu-id="41611-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="41611-131">É interpretado exatamente o mesmo que esta consulta:</span><span class="sxs-lookup"><span data-stu-id="41611-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
