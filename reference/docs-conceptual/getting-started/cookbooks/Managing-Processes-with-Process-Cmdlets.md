---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Gerir Processos com os Cmdlets Process
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: 741a3464bce6284c4933384398c4e9ddcca2572c
ms.sourcegitcommit: 417b5a40cde51029de9ed8e005732978d92c9057
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/18/2018
ms.locfileid: "46013146"
---
# <a name="managing-processes-with-process-cmdlets"></a>Gerir Processos com os Cmdlets Process

Pode utilizar os cmdlets de processo no Windows PowerShell para gerenciar processos locais e remotos no Windows PowerShell.

## <a name="getting-processes-get-process"></a>Získávají se Procesy (Get-Process)

Para obter os processos em execução no computador local, execute uma **Get-Process** sem parâmetros.

Pode obter processos específicos ao especificar seus nomes de processo ou o ID de processo. O comando seguinte obtém o processo inativo:

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

Embora seja normal de cmdlets para não devolvem dados em algumas situações, quando especifica um processo pelo seu ID do processo, **Get-Process** gera um erro se ele encontrar nenhuma correspondência, uma vez que o objetivo habitual é obter um processo em execução conhecido. Se não houver nenhum processo com esse Id, é provável que o Id é incorreto ou que já terminou o processo de interesse:

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

Pode utilizar o parâmetro Name do cmdlet Get-Process para especificar um subconjunto de processos com base no nome do processo. O parâmetro de nome pode demorar vários nomes numa lista separada por vírgulas e ele suporta a utilização de carateres universais, pode digitar padrões de nome.

Por exemplo, o comando seguinte obtém o processo cujos nomes comecem com "ex."

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

Como a classe do .NET Diagnostics é a base para processos do Windows PowerShell, que segue algumas das convenções usadas por Diagnostics. Uma dessas convenções é que o nome do processo para um executável inclui nunca ".exe" no final do nome do executável.

**Get-Process** também aceita vários valores para o parâmetro de nome.

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

Pode utilizar o parâmetro ComputerName do Get-Process para obter os processos em computadores remotos. Por exemplo, o comando seguinte obtém os processos do PowerShell no computador local (representado por "localhost") e em dois computadores remotos.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

Os nomes dos computadores não são evidentes nesta tela, mas eles são armazenados na propriedade MachineName os objetos de processo que Get-Process devolve. O comando seguinte utiliza o cmdlet Format-Table para apresentar o ID de processo, ProcessName e MachineName (ComputerName) propriedades dos objetos de processo.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

Este comando mais complexo adiciona a propriedade MachineName à apresentação de Get-Process padrão.

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $()){$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a>A parar a processos (Stop-Process)

Windows PowerShell dá-lhe flexibilidade para listar processos, mas e quanto a parar um processo?

O **Stop-Process** cmdlet utiliza um nome ou Id para especificar um processo que pretende parar. Sua capacidade de parar processos depende de suas permissões. Não não possível parar alguns processos. Por exemplo, se tentar parar o processo de inatividade, receberá um erro:

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

Pode também forçar a pedir com o **confirmar** parâmetro. Este parâmetro é particularmente útil se utilizar um caráter universal ao especificar o nome do processo, porque pode acidentalmente corresponder ao alguns processos que não pretende parar:

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

Manipulação de processo complexo é possível usando algumas do objeto de filtragem de cmdlets. Como um objeto de processo possui uma propriedade a responder, que será verdadeira quando já não está a responder, pode parar todos os aplicativos sem resposta com o seguinte comando:

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

Pode utilizar a mesma abordagem em outras situações. Por exemplo, suponha que um aplicativo de área de notificação secundária é executada automaticamente quando os utilizadores começam a outra aplicação. Pode achar que isso não funciona corretamente em sessões de serviços de Terminal, mas pretender continuar a mantê-lo em sessões que são executadas no console do computador físico. Sessões ligados na área de trabalho do computador físico sempre tem um ID de sessão 0, para que pode parar todas as instâncias do processo que estão em outras sessões utilizando **Where-Object** e o processo **SessionId** :

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

O cmdlet Stop-Process não tem um parâmetro ComputerName. Por conseguinte, para executar um comando de processo parar num computador remoto, terá de utilizar o cmdlet Invoke-Command. Por exemplo, para parar o processo do PowerShell no computador remoto servidor01, escreva:

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a>A parar todas as outras sessões do PowerShell de Windows

Ocasionalmente, poderá ser útil ser capaz de parar a execução de todas as sessões do PowerShell de Windows que não seja a sessão atual. Se uma sessão está a utilizar demasiados recursos ou não está acessível (ele poderá estar em execução outra sessão de área de trabalho ou remotamente), poderá não conseguir diretamente pará-la. Se tentar parar sessões tudo em execução, no entanto, a sessão atual pode ser terminada em vez disso.

Cada sessão do Windows PowerShell tem uma variável de ambiente PID que contém o Id do processo do Windows PowerShell. Pode verificar o $PID relativamente ao Id de cada sessão e terminar apenas sessões do Windows PowerShell que possuem um ID diferente. O seguinte comando de pipeline faz isso e devolve a lista de sessões terminados (devido à utilização do **PassThru** parâmetro):

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -PassThru

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a>A partir de, a depuração e a aguardar processos

Windows PowerShell também inclui cmdlets para começar (ou reiniciar), um processo de depuração e aguarde pela conclusão antes de executar um comando de um processo. Para obter informações sobre estes cmdlets, consulte o tópico de ajuda do cmdlet para cada cmdlet.

## <a name="see-also"></a>Consulte Também

- [Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)
- [Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)
- [Iniciar o processo](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [Processo de espera](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [Processo de depuração](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
