---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Processos de gestão com os Cmdlets do processo"
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: 3786fb77167746d6a477dffdd4ea13e863c99964
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="managing-processes-with-process-cmdlets"></a>Processos de gestão com os Cmdlets do processo
Pode utilizar os cmdlets de processos do Windows PowerShell para gerir processos locais e remotos no Windows PowerShell.

## <a name="getting-processes-get-process"></a>Obter os processos (Get-Process)
Para obter os processos em execução no computador local, execute um **Get-Process** sem parâmetros.

Pode obter os processos específicos especificando os respetivos nomes de processo ou processos IDs. O seguinte comando obtém o processo de inatividade:

```
PS> Get-Process -id 0
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

Embora seja normal para os cmdlets para não devolve dados em algumas situações, quando especificar um processo com o ID do processo, **Get-Process** gera um erro se encontra não corresponde, porque é o objetivo habitual obter um processo conhecido em execução. Se não houver nenhum processo com esse Id, é provável que o Id está incorreto ou que o processo de interesse já terminou o:

```
PS> Get-Process -Id 99
Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

Pode utilizar o parâmetro de nome do cmdlet Get-Process para especificar um subconjunto dos processos com base no nome do processo. O parâmetro Name pode demorar vários nomes numa lista separada por vírgulas e suporta a utilização de carateres universais, pelo que pode escrever padrões de nome.

Por exemplo, o seguinte comando obtém o processo cujos nomes começam por "ex."

```
PS> Get-Process -Name ex*
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

Porque a classe de .NET process é o alicerce da processos do Windows PowerShell, segue alguns das convenções de utilizado pelo process. Uma desses convenções é que o nome do processo para um executável nunca inclui ".exe" no fim do nome do executável.

**Get-Process** também aceita vários valores para o parâmetro de nome.

```
PS> Get-Process -Name exp*,power* 
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

Pode utilizar o parâmetro ComputerName de Get-Process para obter os processos em computadores remotos. Por exemplo, o seguinte comando obtém os processos de PowerShell no computador local (representado por "localhost") e, em dois computadores remotos.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

Os nomes dos computadores não são evidentes apresentadas, mas que estão armazenadas na propriedade MachineName dos objetos de processo que Get-Process devolve. O seguinte comando utiliza o cmdlet Format-Table para apresentar o ID do processo, ProcessName e MachineName (ComputerName) propriedades dos objetos de processo.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName
  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

Este comando mais complexo adiciona a propriedade MachineName à apresentação de Get-Process padrão. O backtick (\`)(ASCII 96) é o carácter de continuação do Windows PowerShell.

```
get-process powershell -computername localhost, Server01, Server02 | format-table -property Handles, `
                    @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}}, `
                    @{Label="PM(K)";Expression={[int]($_.PM/1024)}}, `
                    @{Label="WS(K)";Expression={[int]($_.WS/1024)}}, `
                    @{Label="VM(M)";Expression={[int]($_.VM/1MB)}}, `
                    @{Label="CPU(s)";Expression={if ($_.CPU -ne $()` 
                    {$_.CPU.ToString("N")}}}, `                                                                         
                    Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a>Parar processos (Stop-Process)
Windows PowerShell dá-lhe a flexibilidade para listar os processos, mas e prestes a parar um processo?

O **Stop-Process** cmdlet assume um nome ou Id para especificar um processo que quer parar. A capacidade de parar processos depende as suas permissões. Não não possível parar alguns processos. Por exemplo, se tentar parar o processo de inatividade, receberá um erro:

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

Pode também forçar a pedir com o **confirmar** parâmetro. Este parâmetro é particularmente útil se utilizar um caráter universal quando especificar o nome do processo, porque acidentalmente podem corresponder alguns processos que pretende parar:

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

Manipulação de processo complexo é possível utilizar alguns do objeto de filtragem de cmdlets. Uma vez um objeto de processo tem uma propriedade de responder é verdadeira quando já não está a responder, pode parar todas as aplicações, tentadas com o seguinte comando:

```
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

Pode utilizar a mesma abordagem noutras situações. Por exemplo, suponha que uma aplicação de área de notificação secundário é executada automaticamente quando os utilizadores iniciam a outra aplicação. Pode considerar que este não funciona corretamente em sessões de serviços de Terminal, mas continua a pretender guardá-lo em sessões que são executadas na consola do computador físico. Sessões ligadas no ambiente de trabalho do computador físico sempre tem um ID de sessão de 0, pelo que pode parar todas as instâncias do processo que estão em outras sessões utilizando **Where-Object** e o processo, **SessionId** :

```
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

O cmdlet Stop-Process não tem um parâmetro ComputerName. Por conseguinte, para executar um comando de processo de paragem num computador remoto, tem de utilizar o cmdlet Invoke-Command. Por exemplo, para parar o processo de PowerShell no computador remoto servidor01, escreva:

```
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a>Parar todas as outras sessões Windows PowerShell
Ocasionalmente, poderá ser útil conseguir parar a execução de todas as sessões do Windows PowerShell que não seja a sessão atual. Se uma sessão está a utilizar demasiados recursos ou está inacessível (que poderá estar em execução outra sessão de ambiente de trabalho ou remotamente), poderá não conseguir parem diretamente. Se tentar parar a execução de todas as sessões, no entanto, a sessão atual pode ser terminada em vez disso.

Cada sessão do Windows PowerShell tem uma variável de ambiente PID que contém o Id do processo do Windows PowerShell. Pode verificar o $PID contra o Id de cada sessão e terminar apenas as sessões do Windows PowerShell tem um ID diferente. O seguinte comando do pipeline efetuar esta ação e devolve a lista de sessões terminadas (devido à utilização do **PassThru** parâmetro):

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -
PassThru
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a>A iniciar, a depuração e a aguardar processos
Windows PowerShell também vem com cmdlets para iniciar (ou reiniciar), um processo de depuração e aguarde pela conclusão antes de executar um comando de um processo. Para obter informações sobre estes cmdlets, consulte o tópico de ajuda do cmdlet para cada cmdlet.

## <a name="see-also"></a>Consulte Também
- [Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)
- [Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)
- [Processo de início](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [Processo de espera](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [Processo de depuração](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [Invocação de comando](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)

