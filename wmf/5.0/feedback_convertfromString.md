---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 3413672e73705252225300a853c10a514500baa2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a>Extrair e analisar os objetos de estruturado fora de cadeia
Isto também apresenta algumas funcionalidades adicionais para o cmdlet ConvertFrom cadeia:

-   Remove a propriedade de texto de extensão por predefinição. Pode incluí-la com o parâmetro - IncludeExtent.

-   Muitos learning correções de erros de algoritmo de comentários MVP e da Comunidade.

-   Um parâmetro - UpdateTemplate novo para guardar os resultados do algoritmo de aprendizagem para um comentário no ficheiro de modelo. Isto torna o learning processar (a fase mais lenta) um custo único. Converter a cadeia a ser executado com um modelo que contém o algoritmo do learning codificado está quase instantânea.


<a name="extract-and-parse-structured-objects-out-of-string-content"></a>Extrair e analisar os objetos estruturados fora do conteúdo de cadeia
----------------------------------------------------------

Em colaboração com [Microsoft Research](http://research.microsoft.com/), um novo **ConvertFrom cadeia** cmdlet foi adicionado.

Este cmdlet suporta dois modos: basic delimitada por analisar e orientada por exemplo análise automática gerada.

Análise delimitada como, por predefinição, divide a entrada em espaço em branco e atribui os nomes de propriedade para os grupos de resultantes. Pode personalizar o delimitador de:

> 1 \[c:\\temp\] &gt; &gt; "Olá mundo" | Cadeia de ConvertFrom | Formato de tabela-automática

P1 P2
--    --

O cmdlet também suporta a geração automática condicionada por exemplo analisar com base no [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) pesquisar trabalho no [Microsoft Research](http://research.microsoft.com).

Para começar a utilizar, considere um livro de endereços baseado em texto:

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

Copie alguns exemplos para um ficheiro, o que irá utilizar como o modelo:

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

   

Colocar chavetas à volta de dados que pretende extrair, atribua um nome como fazê-lo. Porque o **nome** propriedade (e a respetiva associadas a outras propriedades) pode aparecer várias vezes, utilize um asterisco (\*) para indicar que isto resulta em vários registos de (em vez de extrair um bunch das propriedades numa só registo):

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

Este conjunto de exemplos, **ConvertFrom cadeia** pode agora extrair automaticamente com base no objeto de resultado de ficheiros de entrada com uma estrutura semelhante.

> 2 \[c:\\temp\]
>
> &gt;&gt;Get-conteúdo. \\addresses.output.txt | Cadeia ConvertFrom - TemplateFile. \\addresses.template.txt | &gt; &gt; &gt; Format-Table-automática
>
> Estado da cidade ExtentText nome
> ----------                     ----               ----     -----
> Ana Trujillo...                Ana Trujillo Redmond WA Antonio Moreno...              Antonio Moreno Renton WA blogue Hardy...                Blogue Hardy Seattle WA Christina Berglund...          Christina Berglund Redmond WA Hanna Moos...                  Hanna Moos Puyallup WA

Para fazer a manipulação de dados adicionais no texto extraído, o **ExtentText** propriedade captura o texto não processado a partir da qual o registo foi extraído. Fornecer comentários sobre esta funcionalidade, ou para partilhar conteúdo para o qual estão a ter dificuldade em escrever exemplos, envie um e-mail < psdmfb@microsoft.com >.

