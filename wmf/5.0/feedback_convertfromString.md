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
# <a name="extract-and-parse-structured-objects-out-of-string"></a>Extrair e Analisar Objetos Estruturados Fora de Cadeia

Isto também apresenta algumas funcionalidades adicionais para o `ConvertFrom-String` cmdlet:

- Remove a propriedade de texto extensão por predefinição. Pode incluí-lo com o parâmetro - IncludeExtent.

- Muitas correções de erros do algoritmo de comentários da Comunidade e MVP de aprendizado.

- Um novo parâmetro - UpdateTemplate para guardar os resultados do algoritmo de aprendizado num comentário no ficheiro de modelo. Isso torna o aprendizado processar (a fase mais lenta) um custo único. Executar o Convert-cadeia de caracteres com um modelo que contém o algoritmo de aprendizagem codificada agora é quase instantânea.

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a>Extrair e analisar objetos estruturados fora de conteúdo de cadeia de caracteres

Em colaboração com [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), um novo `ConvertFrom-String` cmdlet foi adicionado.

Este cmdlet suporta dois modos: basic delimitados por análise e gerado automaticamente baseadas no exemplo de análise.

Análise delimitados, por predefinição, divide a entrada em espaço em branco e atribui os nomes das propriedades aos grupos resultantes. Pode personalizar o delimitador de:

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

O cmdlet também suporta gerado automaticamente controladas por exemplo análise com base na [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) pesquisar o trabalho na [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).

Para começar a utilizar, considere um livro de endereços com base em texto:

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

Copie alguns exemplos num arquivo, que irá utilizar como o modelo:

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

Coloque entre chaves em todos os dados que pretende extrair, dando a ele um nome como fazer isso. Uma vez que o **nome** propriedade (e a respetiva associadas a outras propriedades) pode sejam exibidas várias vezes, utilizar um asterisco (\*) para indicar que isso resulta em vários registos (em vez de extrair um monte de propriedades em uma registo):

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

Este conjunto de exemplos, `ConvertFrom-String` pode agora extrair automaticamente com base no objeto de saída de ficheiros de entrada com uma estrutura semelhante.

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

Para fazer a manipulação de dados adicionais no texto extraído, o **ExtentText** propriedade captura o partir do qual foi extraído o registo de texto não processado. Para fornecer comentários sobre esta funcionalidade, ou para partilhar conteúdo para o qual tiver dificuldade para escrever exemplos, envie um e-mail <psdmfb@microsoft.com>.