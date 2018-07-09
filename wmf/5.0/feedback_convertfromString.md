---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: fcf2adf67f36edb534df3e2a849459fb20e1c2de
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892368"
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="3399f-102">Extrair e Analisar Objetos Estruturados Fora de Cadeia</span><span class="sxs-lookup"><span data-stu-id="3399f-102">Extract and Parse Structured Objects out of String</span></span>

<span data-ttu-id="3399f-103">Isto também apresenta algumas funcionalidades adicionais para o `ConvertFrom-String` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="3399f-103">This also introduces some additional functionality for the `ConvertFrom-String` cmdlet:</span></span>

- <span data-ttu-id="3399f-104">Remove a propriedade de texto extensão por predefinição.</span><span class="sxs-lookup"><span data-stu-id="3399f-104">Removes the extent text property by default.</span></span> <span data-ttu-id="3399f-105">Pode incluí-lo com o parâmetro - IncludeExtent.</span><span class="sxs-lookup"><span data-stu-id="3399f-105">You can include it with the -IncludeExtent parameter.</span></span>

- <span data-ttu-id="3399f-106">Muitas correções de erros do algoritmo de comentários da Comunidade e MVP de aprendizado.</span><span class="sxs-lookup"><span data-stu-id="3399f-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

- <span data-ttu-id="3399f-107">Um novo parâmetro - UpdateTemplate para guardar os resultados do algoritmo de aprendizado num comentário no ficheiro de modelo.</span><span class="sxs-lookup"><span data-stu-id="3399f-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="3399f-108">Isso torna o aprendizado processar (a fase mais lenta) um custo único.</span><span class="sxs-lookup"><span data-stu-id="3399f-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="3399f-109">Executar o Convert-cadeia de caracteres com um modelo que contém o algoritmo de aprendizagem codificada agora é quase instantânea.</span><span class="sxs-lookup"><span data-stu-id="3399f-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="3399f-110">Extrair e analisar objetos estruturados fora de conteúdo de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3399f-110">Extract and parse structured objects out of string content</span></span>

<span data-ttu-id="3399f-111">Em colaboração com [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), um novo `ConvertFrom-String` cmdlet foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="3399f-111">In collaboration with [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), a new `ConvertFrom-String` cmdlet has been added.</span></span>

<span data-ttu-id="3399f-112">Este cmdlet suporta dois modos: basic delimitados por análise e gerado automaticamente baseadas no exemplo de análise.</span><span class="sxs-lookup"><span data-stu-id="3399f-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="3399f-113">Análise delimitados, por predefinição, divide a entrada em espaço em branco e atribui os nomes das propriedades aos grupos resultantes.</span><span class="sxs-lookup"><span data-stu-id="3399f-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="3399f-114">Pode personalizar o delimitador de:</span><span class="sxs-lookup"><span data-stu-id="3399f-114">You can customize the delimiter:</span></span>

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

<span data-ttu-id="3399f-115">O cmdlet também suporta gerado automaticamente controladas por exemplo análise com base na [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) pesquisar o trabalho na [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).</span><span class="sxs-lookup"><span data-stu-id="3399f-115">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) research work in [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).</span></span>

<span data-ttu-id="3399f-116">Para começar a utilizar, considere um livro de endereços com base em texto:</span><span class="sxs-lookup"><span data-stu-id="3399f-116">To get started, consider a text-based address book:</span></span>

```
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
```

<span data-ttu-id="3399f-117">Copie alguns exemplos num arquivo, que irá utilizar como o modelo:</span><span class="sxs-lookup"><span data-stu-id="3399f-117">Copy a few examples into a file, which you will use as your template:</span></span>

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

<span data-ttu-id="3399f-118">Coloque entre chaves em todos os dados que pretende extrair, dando a ele um nome como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="3399f-118">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="3399f-119">Uma vez que o **nome** propriedade (e a respetiva associadas a outras propriedades) pode sejam exibidas várias vezes, utilizar um asterisco (\*) para indicar que isso resulta em vários registos (em vez de extrair um monte de propriedades em uma registo):</span><span class="sxs-lookup"><span data-stu-id="3399f-119">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

<span data-ttu-id="3399f-120">Este conjunto de exemplos, `ConvertFrom-String` pode agora extrair automaticamente com base no objeto de saída de ficheiros de entrada com uma estrutura semelhante.</span><span class="sxs-lookup"><span data-stu-id="3399f-120">From this set of examples, `ConvertFrom-String` can now automatically extract object-based output from input files with similar structure.</span></span>

```powershell
Get-Content .\addresses.output.txt | ConvertFrom-String -TemplateFile .\addresses.template.txt | Format-Table -Auto
```

```output
ExtentText                     Name               City     State
----------                     ----               ----     -----
Ana Trujillo...                Ana Trujillo       Redmond  WA
Antonio Moreno...              Antonio Moreno     Renton   WA
Thomas Hardy...                Thomas Hardy       Seattle  WA
Christina Berglund...          Christina Berglund Redmond  WA
Hanna Moos...                  Hanna Moos         Puyallup WA
```

<span data-ttu-id="3399f-121">Para fazer a manipulação de dados adicionais no texto extraído, o **ExtentText** propriedade captura o partir do qual foi extraído o registo de texto não processado.</span><span class="sxs-lookup"><span data-stu-id="3399f-121">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="3399f-122">Para fornecer comentários sobre esta funcionalidade, ou para partilhar conteúdo para o qual tiver dificuldade para escrever exemplos, envie um e-mail <psdmfb@microsoft.com>.</span><span class="sxs-lookup"><span data-stu-id="3399f-122">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>