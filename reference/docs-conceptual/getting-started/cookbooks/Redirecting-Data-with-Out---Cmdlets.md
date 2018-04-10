---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Redirecionar Dados com Cmdlets Out
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: 3ca7984e831a995e80cbd8a4d83ae9225c2a4f4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="redirecting-data-with-out--cmdlets"></a>Redirecionar dados com Out-* Cmdlets

O Windows PowerShell oferece vários cmdlets que lhe permitem que controlar diretamente a saída de dados. Estes cmdlets partilham características importantes dois.

Em primeiro lugar, geralmente, estes transformar dados em alguma forma de texto. Tal porque estes dados para os componentes de sistema que necessitam de entrada de texto de saída. Isto significa que precisam para representar objetos como texto. Por conseguinte, o texto é formatado como vê-lo na janela da consola do Windows PowerShell.

Segundo, estes cmdlets utilizam o Windows PowerShell verbo **saída** porque enviam informações a partir do Windows PowerShell para qualquer outro local. O **out-anfitrião** cmdlet não é exceção: a apresentação da janela de anfitrião está fora do Windows PowerShell. Isto é importante porque, quando são enviados dados fora do Windows PowerShell, na realidade é removido. Pode ver esta se tentar criar um pipeline que páginas os dados para a janela de anfitrião e, em seguida, tentar formate-o como uma lista, conforme mostrado aqui:

```powershell
Get-Process | Out-Host -Paging | Format-List
```

Que seria de esperar o comando para apresentar as páginas de informações de processo no formato de lista. Em vez disso, apresenta a lista de tabela:

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

O **out-anfitrião** cmdlet envia os dados diretamente para a consola, por isso, o **formato-lista** comando nunca recebe nada para formatar.

A forma correta de estrutura este comando é colocar o **out-anfitrião** cmdlet no fim do pipeline conforme mostrado abaixo. Isto faz com que os dados de processo a formatados numa lista antes de ser do bloco paginado e apresentada.

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

Isto aplica-se a todos os o **saída** cmdlets. Um **saída** cmdlet sempre deve aparecer no fim do pipeline.

> [!NOTE]
> Todos os o **saída** cmdlets compor o resultado como texto, utilizando a formatação em vigor para a janela de consola, incluindo limites de comprimento de linha.

#### <a name="paging-console-output-out-host"></a>Resultado da consola de paginação (Out-anfitrião)

Por predefinição, o Windows PowerShell envia dados para a janela de anfitrião, o que é exatamente o que o Out-anfitrião cmdlet does. A utilização principal para o Out-anfitrião cmdlet é os dados de paginação que discutimos anteriormente. Por exemplo, as seguintes utilizações de comando out-anfitrião para a página a saída do cmdlet Get-Command:

```powershell
Get-Command | Out-Host -Paging
```

Também pode utilizar o **mais** função para dados de página. No Windows PowerShell, **mais** é uma função que chama **out-alojar-paginação**. O comando seguinte demonstra a utilizar o **mais** função para a página a saída de Get-Command:

```powershell
Get-Command | more
```

Se incluir um ou mais nomes de ficheiros como argumentos para a função mais, a função irá ler os ficheiros especificados e os respetivos conteúdos para o anfitrião de página:

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a>Rejeitar saída (Out-nulo)

O **out-nulo** cmdlet foi concebido para eliminar imediatamente qualquer entrada que receber. Isto é útil para eliminar dados desnecessários que obtém como um efeito de um comando em execução. Quando escrever o seguinte comando, não voltar nada do comando:

```powreshell
Get-Command | Out-Null
```

O **out-nulo** cmdlet não rejeição a saída de erro. Por exemplo, se introduzir o seguinte comando, será apresentada uma mensagem informando-o de que o Windows PowerShell não reconhece 'NotACommand é':

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a>Dados de impressão (Out-impressoras)

Pode imprimir dados utilizando o **Out-impressora** cmdlet. O **Out-impressora** cmdlet utilizará a impressora predefinida se não fornecer um nome de impressora. Pode utilizar qualquer impressora baseado no Windows, especificando o nome a apresentar. Não é necessário para qualquer tipo de mapeamento de portas de impressora ou mesmo uma impressora física real. Por exemplo, se tiver as Microsoft Office documento processamento de imagens as ferramentas instaladas, pode enviar os dados para um ficheiro de imagem, escrevendo:

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a>Os dados (out-File)

Pode enviar o resultado para um ficheiro em vez da janela de consola utilizando o **out-File** cmdlet. A seguinte linha de comandos envia uma lista de processos para o ficheiro **c:\\temp\\processlist.txt**:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

Os resultados de utilizar o **out-File** cmdlet não pode ser o que esperar se forem utilizados para redirecionamento de saída tradicional. Para compreender o respetivo comportamento, tem de ser informados da contexto no qual o **out-File** cmdlet funciona.

Por predefinição, o **out-File** cmdlet cria um ficheiro Unicode. Esta é a predefinição melhor longa run, mas significa que as ferramentas que esperam ficheiros ASCII não funcionarão corretamente com o formato de saída predefinido. Pode alterar o formato de saída predefinido para ASCII utilizando o **codificação** parâmetro:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

**Out-file** formatos de ficheiro de conteúdo para o aspeto do resultado da consola. Isto faz com que o resultado a ser truncado tal como faz parte de uma janela da consola na maior parte das circunstâncias. Por exemplo, se executar o seguinte comando:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

O resultado será ter este aspeto:

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

Para obter o resultado não forçar a linha encapsula num wrapper para corresponder a largura do ecrã, pode utilizar o **largura** parâmetro para especificar a largura da linha. Porque **largura** é um parâmetro de número inteiro de 32 bits, o valor máximo pode ter é 2147483647. Escreva o seguinte para definir a largura da linha para este valor máximo:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

O **out-File** cmdlet é mais útil quando pretende guardar a saída tal como faria ter apresentado na consola. Para melhorar o controlo sobre o formato de saída, terá de ferramentas mais avançadas. Iremos abordar os o capítulo seguinte, juntamente com alguns detalhes sobre a manipulação de objeto.