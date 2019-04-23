---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Redirecionar Dados com Cmdlets Out
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: 7c601b09cc53524eb55014b8ea19a5d79cb98b0e
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984413"
---
# <a name="redirecting-data-with-out--cmdlets"></a>Redirecionar dados com o Out-* Cmdlets

Windows PowerShell fornece vários cmdlets que lhe permitam que controlar dados diretamente de saída. Estes cmdlets partilhar duas características importantes.

Em primeiro lugar, eles geralmente transformam dados de alguma forma de texto. Eles fazer isso, uma vez que os dados para os componentes de sistema que exigem entrada de texto de saída. Isso significa que precisam para representar os objetos como texto. Por conseguinte, o texto esteja formatado como vê-la na janela de consola do Windows PowerShell.

Em segundo lugar, estes cmdlets usam o verbo de Windows PowerShell **horizontalmente** porque eles enviam informações do Windows PowerShell a algum outro lugar. O **out-Host** cmdlet não é exceção: a apresentação da janela de anfitrião está fora do Windows PowerShell. Isso é importante porque quando dados são enviados para fora do Windows PowerShell, na verdade, é removido. Pode ver isso se tentar criar um pipeline que páginas os dados para a janela de anfitrião e, em seguida, tentar formatá-lo como uma lista, conforme mostrado aqui:

```powershell
Get-Process | Out-Host -Paging | Format-List
```

Pode esperar o comando para exibir páginas de informações do processo num formato de lista. Em vez disso, ele exibe a lista em tabela:

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

O **out-Host** cmdlet envia os dados diretamente para a consola de, pelo que a **Format-List** comando nunca recebe nada para formatar.

A maneira correta de estruturar este comando é colocar o **out-Host** cmdlet no final do pipeline, conforme mostrado abaixo. Isso faz com que o processamento de dados sejam formatados de uma lista antes de ser paginada e apresentada.

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

Isto aplica-se a todos os **horizontalmente** cmdlets. Uma **horizontalmente** cmdlet sempre deve aparecer no final do pipeline.

> [!NOTE]
> Todos os **horizontalmente** cmdlets compõem uma saída como texto, usando a formatação em vigor para a janela de consola, incluindo limites de tamanho de linha.

## <a name="paging-console-output-out-host"></a>Resultado da consola de paginação (Out-Host)

Por predefinição, o Windows PowerShell envia dados para a janela de anfitrião, o que é exatamente o que o cmdlet out-Host faz. Usada principalmente para o Out-Host cmdlet é dados de paginação, como discutido anteriormente. Por exemplo, o seguinte comando utiliza out-Host para a página a saída do cmdlet Get-Command:

```powershell
Get-Command | Out-Host -Paging
```

Também pode utilizar o **mais** função para dados de página. No Windows PowerShell, **mais** é uma função que chama **out-Host-paginação**. O comando seguinte demonstra como utilizar o **mais** função para a página a saída de Get-Command:

```powershell
Get-Command | more
```

Se incluir um ou mais nomes de ficheiros como argumentos para a função mais, a função irá ler os ficheiros especificados e seu conteúdo para o anfitrião de página:

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

## <a name="discarding-output-out-null"></a>Descarte de saída (Out-Null)

O **out-Null** cmdlet foi desenvolvido para eliminar imediatamente qualquer entrada que recebe. Isto é útil para dados desnecessários obtidas como um efeito colateral de executar um comando de descarte. Quando escreva o seguinte comando, não recebe nada do comando:

```powershell
Get-Command | Out-Null
```

O **out-Null** cmdlet não elimine a saída de erro. Por exemplo, se introduzir o comando seguinte, é apresentada uma mensagem informando-o de que o Windows PowerShell não reconhece "NotACommand é":

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

## <a name="printing-data-out-printer"></a>Dados de impressão (Out-impressora)

Pode imprimir dados ao utilizar o **Out-impressora** cmdlet. O **Out-impressora** cmdlet irá utilizar a sua impressora padrão se não fornecer um nome da impressora. Pode usar qualquer impressora baseados em Windows, especificando seu nome de exibição. Não é necessário para qualquer tipo de mapeamento de portas de impressora ou até mesmo uma impressora física real. Por exemplo, se tiver ferramentas Microsoft Office de geração de imagens documento instaladas, pode enviar os dados para um ficheiro de imagem ao escrever:

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

## <a name="saving-data-out-file"></a>Guardar os dados (out-File)

Pode enviar a saída para um ficheiro em vez da janela de consola utilizando o **out-File** cmdlet. A seguinte linha de comando envia uma lista de processos para o ficheiro **c:\\temp\\processlist.txt**:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

Os resultados de utilizar o **out-File** cmdlet pode não ser o que esperar se forem utilizadas para redirecionamento de saída tradicional. Para compreender seu comportamento, deve estar ciente de contexto no qual o **out-File** opera de cmdlet.

Por predefinição, o **out-File** cmdlet cria um ficheiro Unicode. Esta é a predefinição de melhor a longo prazo, mas significa que as ferramentas que esperam ficheiros ASCII não funcionará corretamente com o formato de saída padrão. Pode alterar o formato de saída padrão em ASCII, utilizando o **Encoding** parâmetro:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

**Out-file** conteúdos como resultado da consola do formatos de ficheiro. Isso faz com que a saída para ser truncado, tal como numa janela de consola, na maioria das circunstâncias. Por exemplo, se executar o seguinte comando:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

A saída terá o seguinte aspeto:

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

Para obter o resultado que não o força inclui de linha de acordo com a largura da tela, pode utilizar o **largura** parâmetro para especificar a largura da linha. Uma vez **largura** é um parâmetro de número inteiro de 32 bits, o valor máximo, ele pode ter é 2147483647. Escreva o seguinte para definir a largura da linha para este valor máximo:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

O **out-File** cmdlet é mais útil quando pretende guardar a saída tal como seria ter apresentado na consola. Para obter mais controle sobre o formato de saída, precisa de ferramentas mais avançadas. Vamos ver aqueles no capítulo seguinte, juntamente com alguns detalhes sobre a manipulação de objetos.