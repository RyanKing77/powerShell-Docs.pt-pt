---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Gerir Processos com os Cmdlets Process
ms.openlocfilehash: 0962290327a02141f582acdf168143dee14ac60a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030188"
---
# <a name="managing-processes-with-process-cmdlets"></a><span data-ttu-id="9b5e0-103">Gerir Processos com os Cmdlets Process</span><span class="sxs-lookup"><span data-stu-id="9b5e0-103">Managing Processes with Process Cmdlets</span></span>

<span data-ttu-id="9b5e0-104">Pode utilizar os cmdlets de processo no Windows PowerShell para gerenciar processos locais e remotos no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-104">You can use the Process cmdlets in Windows PowerShell to manage local and remote processes in Windows PowerShell.</span></span>

## <a name="getting-processes-get-process"></a><span data-ttu-id="9b5e0-105">Získávají se Procesy (Get-Process)</span><span class="sxs-lookup"><span data-stu-id="9b5e0-105">Getting Processes (Get-Process)</span></span>

<span data-ttu-id="9b5e0-106">Para obter os processos em execução no computador local, execute uma **Get-Process** sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-106">To get the processes running on the local computer, run a **Get-Process** with no parameters.</span></span>

<span data-ttu-id="9b5e0-107">Pode obter processos específicos ao especificar seus nomes de processo ou o ID de processo.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-107">You can get particular processes by specifying their process names or process IDs.</span></span> <span data-ttu-id="9b5e0-108">O comando seguinte obtém o processo inativo:</span><span class="sxs-lookup"><span data-stu-id="9b5e0-108">The following command gets the Idle process:</span></span>

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

<span data-ttu-id="9b5e0-109">Embora seja normal de cmdlets para não devolvem dados em algumas situações, quando especifica um processo pelo seu ID do processo, **Get-Process** gera um erro se ele encontrar nenhuma correspondência, uma vez que o objetivo habitual é obter um processo em execução conhecido.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-109">Although it is normal for cmdlets to return no data in some situations, when you specify a process by its ProcessId, **Get-Process** generates an error if it finds no matches, because the usual intent is to retrieve a known running process.</span></span> <span data-ttu-id="9b5e0-110">Se não houver nenhum processo com esse Id, é provável que o Id é incorreto ou que já terminou o processo de interesse:</span><span class="sxs-lookup"><span data-stu-id="9b5e0-110">If there is no process with that Id, it is likely that the Id is incorrect or that the process of interest has already exited:</span></span>

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

<span data-ttu-id="9b5e0-111">Pode utilizar o parâmetro Name do cmdlet Get-Process para especificar um subconjunto de processos com base no nome do processo.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-111">You can use the Name parameter of the Get-Process cmdlet to specify a subset of processes based on the process name.</span></span> <span data-ttu-id="9b5e0-112">O parâmetro de nome pode demorar vários nomes numa lista separada por vírgulas e ele suporta a utilização de carateres universais, pode digitar padrões de nome.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-112">The Name parameter can take multiple names in a comma-separated list and it supports the use of wildcards, so you can type name patterns.</span></span>

<span data-ttu-id="9b5e0-113">Por exemplo, o comando seguinte obtém o processo cujos nomes comecem com "ex."</span><span class="sxs-lookup"><span data-stu-id="9b5e0-113">For example, the following command gets process whose names begin with "ex."</span></span>

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

<span data-ttu-id="9b5e0-114">Como a classe do .NET Diagnostics é a base para processos do Windows PowerShell, que segue algumas das convenções usadas por Diagnostics.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-114">Because the .NET System.Diagnostics.Process class is the foundation for Windows PowerShell processes, it follows some of the conventions used by System.Diagnostics.Process.</span></span> <span data-ttu-id="9b5e0-115">Uma dessas convenções é que o nome do processo para um executável inclui nunca ".exe" no final do nome do executável.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-115">One of those conventions is that the process name for an executable never includes the ".exe" at the end of the executable name.</span></span>

<span data-ttu-id="9b5e0-116">**Get-Process** também aceita vários valores para o parâmetro de nome.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-116">**Get-Process** also accepts multiple values for the Name parameter.</span></span>

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="9b5e0-117">Pode utilizar o parâmetro ComputerName do Get-Process para obter os processos em computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-117">You can use the ComputerName parameter of Get-Process to get processes on remote computers.</span></span> <span data-ttu-id="9b5e0-118">Por exemplo, o comando seguinte obtém os processos do PowerShell no computador local (representado por "localhost") e em dois computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-118">For example, the following command gets the PowerShell processes on the local computer (represented by "localhost") and on two remote computers.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="9b5e0-119">Os nomes dos computadores não são evidentes nesta tela, mas eles são armazenados na propriedade MachineName os objetos de processo que Get-Process devolve.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-119">The computer names are not evident in this display, but they are stored in the MachineName property of the process objects that Get-Process returns.</span></span> <span data-ttu-id="9b5e0-120">O comando seguinte utiliza o cmdlet Format-Table para apresentar o ID de processo, ProcessName e MachineName (ComputerName) propriedades dos objetos de processo.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-120">The following command uses the Format-Table cmdlet to display the process ID, ProcessName and MachineName (ComputerName) properties of the process objects.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

<span data-ttu-id="9b5e0-121">Este comando mais complexo adiciona a propriedade MachineName à apresentação de Get-Process padrão.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-121">This more complex command adds the MachineName property to the standard Get-Process display.</span></span>

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

## <a name="stopping-processes-stop-process"></a><span data-ttu-id="9b5e0-122">A parar a processos (Stop-Process)</span><span class="sxs-lookup"><span data-stu-id="9b5e0-122">Stopping Processes (Stop-Process)</span></span>

<span data-ttu-id="9b5e0-123">Windows PowerShell dá-lhe flexibilidade para listar processos, mas e quanto a parar um processo?</span><span class="sxs-lookup"><span data-stu-id="9b5e0-123">Windows PowerShell gives you flexibility for listing processes, but what about stopping a process?</span></span>

<span data-ttu-id="9b5e0-124">O **Stop-Process** cmdlet utiliza um nome ou Id para especificar um processo que pretende parar.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-124">The **Stop-Process** cmdlet takes a Name or Id to specify a process you want to stop.</span></span> <span data-ttu-id="9b5e0-125">Sua capacidade de parar processos depende de suas permissões.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-125">Your ability to stop processes depends on your permissions.</span></span> <span data-ttu-id="9b5e0-126">Não não possível parar alguns processos.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-126">Some processes cannot be stopped.</span></span> <span data-ttu-id="9b5e0-127">Por exemplo, se tentar parar o processo de inatividade, receberá um erro:</span><span class="sxs-lookup"><span data-stu-id="9b5e0-127">For example, if you try to stop the idle process, you get an error:</span></span>

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

<span data-ttu-id="9b5e0-128">Pode também forçar a pedir com o **confirmar** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-128">You can also force prompting with the **Confirm** parameter.</span></span> <span data-ttu-id="9b5e0-129">Este parâmetro é particularmente útil se utilizar um caráter universal ao especificar o nome do processo, porque pode acidentalmente corresponder ao alguns processos que não pretende parar:</span><span class="sxs-lookup"><span data-stu-id="9b5e0-129">This parameter is particularly useful if you use a wildcard when specifying the process name, because you may accidentally match some processes you do not want to stop:</span></span>

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

<span data-ttu-id="9b5e0-130">Manipulação de processo complexo é possível usando algumas do objeto de filtragem de cmdlets.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-130">Complex process manipulation is possible by using some of the object filtering cmdlets.</span></span> <span data-ttu-id="9b5e0-131">Como um objeto de processo possui uma propriedade a responder, que será verdadeira quando já não está a responder, pode parar todos os aplicativos sem resposta com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="9b5e0-131">Because a Process object has a Responding property that is true when it is no longer responding, you can stop all nonresponsive applications with the following command:</span></span>

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

<span data-ttu-id="9b5e0-132">Pode utilizar a mesma abordagem em outras situações.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-132">You can use the same approach in other situations.</span></span> <span data-ttu-id="9b5e0-133">Por exemplo, suponha que um aplicativo de área de notificação secundária é executada automaticamente quando os utilizadores começam a outra aplicação.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-133">For example, suppose a secondary notification area application automatically runs when users start another application.</span></span> <span data-ttu-id="9b5e0-134">Pode achar que isso não funciona corretamente em sessões de serviços de Terminal, mas pretender continuar a mantê-lo em sessões que são executadas no console do computador físico.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-134">You may find that this does not work correctly in Terminal Services sessions, but you still want to keep it in sessions that run on the physical computer console.</span></span> <span data-ttu-id="9b5e0-135">Sessões ligados na área de trabalho do computador físico sempre tem um ID de sessão 0, para que pode parar todas as instâncias do processo que estão em outras sessões utilizando **Where-Object** e o processo **SessionId** :</span><span class="sxs-lookup"><span data-stu-id="9b5e0-135">Sessions connected to the physical computer desktop always have a session ID of 0, so you can stop all instances of the process that are in other sessions by using **Where-Object** and the process, **SessionId**:</span></span>

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

<span data-ttu-id="9b5e0-136">O cmdlet Stop-Process não tem um parâmetro ComputerName.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-136">The Stop-Process cmdlet does not have a ComputerName parameter.</span></span> <span data-ttu-id="9b5e0-137">Por conseguinte, para executar um comando de processo parar num computador remoto, terá de utilizar o cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-137">Therefore, to run a stop process command on a remote computer, you need to use the Invoke-Command cmdlet.</span></span> <span data-ttu-id="9b5e0-138">Por exemplo, para parar o processo do PowerShell no computador remoto servidor01, escreva:</span><span class="sxs-lookup"><span data-stu-id="9b5e0-138">For example, to stop the PowerShell process on the Server01 remote computer, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a><span data-ttu-id="9b5e0-139">A parar todas as outras sessões do PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="9b5e0-139">Stopping All Other Windows PowerShell Sessions</span></span>

<span data-ttu-id="9b5e0-140">Ocasionalmente, poderá ser útil ser capaz de parar a execução de todas as sessões do PowerShell de Windows que não seja a sessão atual.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-140">It may occasionally be useful to be able to stop all running Windows PowerShell sessions other than the current session.</span></span> <span data-ttu-id="9b5e0-141">Se uma sessão está a utilizar demasiados recursos ou não está acessível (ele poderá estar em execução outra sessão de área de trabalho ou remotamente), poderá não conseguir diretamente pará-la.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-141">If a session is using too many resources or is inaccessible (it may be running remotely or in another desktop session), you may not be able to directly stop it.</span></span> <span data-ttu-id="9b5e0-142">Se tentar parar sessões tudo em execução, no entanto, a sessão atual pode ser terminada em vez disso.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-142">If you try to stop all running sessions, however, the current session may be terminated instead.</span></span>

<span data-ttu-id="9b5e0-143">Cada sessão do Windows PowerShell tem uma variável de ambiente PID que contém o Id do processo do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-143">Each Windows PowerShell session has an environment variable PID that contains the Id of the Windows PowerShell process.</span></span> <span data-ttu-id="9b5e0-144">Pode verificar o $PID relativamente ao Id de cada sessão e terminar apenas sessões do Windows PowerShell que possuem um ID diferente. O seguinte comando de pipeline faz isso e devolve a lista de sessões terminados (devido à utilização do **PassThru** parâmetro):</span><span class="sxs-lookup"><span data-stu-id="9b5e0-144">You can check the $PID against the Id of each session and terminate only Windows PowerShell sessions that have a different Id. The following pipeline command does this and returns the list of terminated sessions (because of the use of the **PassThru** parameter):</span></span>

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

## <a name="starting-debugging-and-waiting-for-processes"></a><span data-ttu-id="9b5e0-145">A partir de, a depuração e a aguardar processos</span><span class="sxs-lookup"><span data-stu-id="9b5e0-145">Starting, Debugging, and Waiting for Processes</span></span>

<span data-ttu-id="9b5e0-146">Windows PowerShell também inclui cmdlets para começar (ou reiniciar), um processo de depuração e aguarde pela conclusão antes de executar um comando de um processo.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-146">Windows PowerShell also comes with cmdlets to start (or restart), debug a process, and wait for a process to complete before running a command.</span></span> <span data-ttu-id="9b5e0-147">Para obter informações sobre estes cmdlets, consulte o tópico de ajuda do cmdlet para cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9b5e0-147">For information about these cmdlets, see the cmdlet help topic for each cmdlet.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b5e0-148">Veja Também</span><span class="sxs-lookup"><span data-stu-id="9b5e0-148">See Also</span></span>

- <span data-ttu-id="9b5e0-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span><span class="sxs-lookup"><span data-stu-id="9b5e0-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span></span>
- <span data-ttu-id="9b5e0-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span><span class="sxs-lookup"><span data-stu-id="9b5e0-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span></span>
- [<span data-ttu-id="9b5e0-151">Start-Process</span><span class="sxs-lookup"><span data-stu-id="9b5e0-151">Start-Process</span></span>](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [<span data-ttu-id="9b5e0-152">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="9b5e0-152">Wait-Process</span></span>](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [<span data-ttu-id="9b5e0-153">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="9b5e0-153">Debug-Process</span></span>](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [<span data-ttu-id="9b5e0-154">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="9b5e0-154">Invoke-Command</span></span>](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
