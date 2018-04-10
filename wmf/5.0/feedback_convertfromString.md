---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: cedda61241df4965fe5db723f03e3497f046fa44
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="cb9dd-102">Extrair e Analisar Objetos Estruturados Fora de Cadeia</span><span class="sxs-lookup"><span data-stu-id="cb9dd-102">Extract and Parse Structured Objects out of String</span></span>
<span data-ttu-id="cb9dd-103">Isto também apresenta algumas funcionalidades adicionais para o cmdlet ConvertFrom cadeia:</span><span class="sxs-lookup"><span data-stu-id="cb9dd-103">This also introduces some additional functionality for the ConvertFrom-String cmdlet:</span></span>

-   <span data-ttu-id="cb9dd-104">Remove a propriedade de texto de extensão por predefinição.</span><span class="sxs-lookup"><span data-stu-id="cb9dd-104">Removes the extent text property by default.</span></span> <span data-ttu-id="cb9dd-105">Pode incluí-la com o parâmetro - IncludeExtent.</span><span class="sxs-lookup"><span data-stu-id="cb9dd-105">You can include it with the -IncludeExtent parameter.</span></span>

-   <span data-ttu-id="cb9dd-106">Muitos learning correções de erros de algoritmo de comentários MVP e da Comunidade.</span><span class="sxs-lookup"><span data-stu-id="cb9dd-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

-   <span data-ttu-id="cb9dd-107">Um parâmetro - UpdateTemplate novo para guardar os resultados do algoritmo de aprendizagem para um comentário no ficheiro de modelo.</span><span class="sxs-lookup"><span data-stu-id="cb9dd-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="cb9dd-108">Isto torna o learning processar (a fase mais lenta) um custo único.</span><span class="sxs-lookup"><span data-stu-id="cb9dd-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="cb9dd-109">Converter a cadeia a ser executado com um modelo que contém o algoritmo do learning codificado está quase instantânea.</span><span class="sxs-lookup"><span data-stu-id="cb9dd-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>


<a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="cb9dd-110">Extrair e analisar os objetos estruturados fora do conteúdo de cadeia</span><span class="sxs-lookup"><span data-stu-id="cb9dd-110">Extract and parse structured objects out of string content</span></span>
----------------------------------------------------------

<span data-ttu-id="cb9dd-111">Em colaboração com [Microsoft Research](http://research.microsoft.com/), um novo **ConvertFrom cadeia** cmdlet foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="cb9dd-111">In collaboration with [Microsoft Research](http://research.microsoft.com/), a new **ConvertFrom-String** cmdlet has been added.</span></span>

<span data-ttu-id="cb9dd-112">Este cmdlet suporta dois modos: basic delimitada por analisar e orientada por exemplo análise automática gerada.</span><span class="sxs-lookup"><span data-stu-id="cb9dd-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="cb9dd-113">Análise delimitada como, por predefinição, divide a entrada em espaço em branco e atribui os nomes de propriedade para os grupos de resultantes.</span><span class="sxs-lookup"><span data-stu-id="cb9dd-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="cb9dd-114">Pode personalizar o delimitador de:</span><span class="sxs-lookup"><span data-stu-id="cb9dd-114">You can customize the delimiter:</span></span>

> <span data-ttu-id="cb9dd-115">1 \[c:\\temp\] &gt; &gt; "Olá mundo" | Cadeia de ConvertFrom | Formato de tabela-automática</span><span class="sxs-lookup"><span data-stu-id="cb9dd-115">1 \[C:\\temp\] &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto</span></span>

<span data-ttu-id="cb9dd-116">P1    P2</span><span class="sxs-lookup"><span data-stu-id="cb9dd-116">P1    P2</span></span>
--    --

<span data-ttu-id="cb9dd-117">O cmdlet também suporta a geração automática condicionada por exemplo analisar com base no [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) pesquisar trabalho no [Microsoft Research](http://research.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="cb9dd-117">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) research work in [Microsoft Research](http://research.microsoft.com).</span></span>

<span data-ttu-id="cb9dd-118">Para começar a utilizar, considere um livro de endereços baseado em texto:</span><span class="sxs-lookup"><span data-stu-id="cb9dd-118">To get started, consider a text-based address book:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA

<span data-ttu-id="cb9dd-119">Copie alguns exemplos para um ficheiro, o que irá utilizar como o modelo:</span><span class="sxs-lookup"><span data-stu-id="cb9dd-119">Copy a few examples into a file, which you will use as your template:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA



<span data-ttu-id="cb9dd-120">Colocar chavetas à volta de dados que pretende extrair, atribua um nome como fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="cb9dd-120">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="cb9dd-121">Porque o **nome** propriedade (e a respetiva associadas a outras propriedades) pode aparecer várias vezes, utilize um asterisco (\*) para indicar que isto resulta em vários registos de (em vez de extrair um bunch das propriedades numa só registo):</span><span class="sxs-lookup"><span data-stu-id="cb9dd-121">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

<span data-ttu-id="cb9dd-122">Este conjunto de exemplos, **ConvertFrom cadeia** pode agora extrair automaticamente com base no objeto de resultado de ficheiros de entrada com uma estrutura semelhante.</span><span class="sxs-lookup"><span data-stu-id="cb9dd-122">From this set of examples, **ConvertFrom-String** can now automatically extract object-based output from input files with similar structure.</span></span>

> <span data-ttu-id="cb9dd-123">2 \[c:\\temp\]</span><span class="sxs-lookup"><span data-stu-id="cb9dd-123">2 \[C:\\temp\]</span></span>
>
> <span data-ttu-id="cb9dd-124">&gt;&gt; Get-conteúdo. \\addresses.output.txt | Cadeia ConvertFrom - TemplateFile. \\addresses.template.txt | &gt; &gt; &gt; Format-Table-automática</span><span class="sxs-lookup"><span data-stu-id="cb9dd-124">&gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto</span></span>
>
> <span data-ttu-id="cb9dd-125">Estado da cidade ExtentText nome</span><span class="sxs-lookup"><span data-stu-id="cb9dd-125">ExtentText                     Name               City     State</span></span>
> ----------                     ----               ----     -----
> <span data-ttu-id="cb9dd-126">Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno Renton WA blogue Hardy...                Blogue Hardy Seattle WA Christina Berglund...          Christina Berglund Redmond WA Hanna Moos...                  Hanna Moos         Puyallup WA</span><span class="sxs-lookup"><span data-stu-id="cb9dd-126">Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno     Renton   WA Thomas Hardy...                Thomas Hardy       Seattle  WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA</span></span>

<span data-ttu-id="cb9dd-127">Para fazer a manipulação de dados adicionais no texto extraído, o **ExtentText** propriedade captura o texto não processado a partir da qual o registo foi extraído.</span><span class="sxs-lookup"><span data-stu-id="cb9dd-127">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="cb9dd-128">Fornecer comentários sobre esta funcionalidade, ou para partilhar conteúdo para o qual estão a ter dificuldade em escrever exemplos, envie um e-mail <psdmfb@microsoft.com>.</span><span class="sxs-lookup"><span data-stu-id="cb9dd-128">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>