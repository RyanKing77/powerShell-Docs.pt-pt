---
ms.date: 11/13/2018
keywords: PowerShell, o cmdlet
title: Decode a PowerShell command from a running process (Descodificar um comando do PowerShell a partir de um processo em execução)
author: randomnote1
ms.openlocfilehash: a6c01d8edf67aba6c47350a97cc0ceec4801ad29
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470961"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a><span data-ttu-id="f7132-103">Decode a PowerShell command from a running process (Descodificar um comando do PowerShell a partir de um processo em execução)</span><span class="sxs-lookup"><span data-stu-id="f7132-103">Decode a PowerShell command from a running process</span></span>

<span data-ttu-id="f7132-104">Às vezes, pode ter um processo em execução que está ocupando uma grande quantidade de recursos de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7132-104">At times, you may have a PowerShell process running that is taking up a large amount of resources.</span></span>
<span data-ttu-id="f7132-105">Este processo pode estar em execução no contexto de um [agendador de tarefas][] tarefa ou uma [SQL Server Agent][] tarefa.</span><span class="sxs-lookup"><span data-stu-id="f7132-105">This process could be running in the context of a [Task Scheduler][] job or a [SQL Server Agent][] job.</span></span> <span data-ttu-id="f7132-106">Em que há vários processos de PowerShell em execução, pode ser difícil saber o processo que representa o problema.</span><span class="sxs-lookup"><span data-stu-id="f7132-106">Where there are multiple PowerShell processes running, it can be difficult to know which process represents the problem.</span></span> <span data-ttu-id="f7132-107">Este artigo mostra como a descodificar um bloco de script que um processo de PowerShell está atualmente em execução.</span><span class="sxs-lookup"><span data-stu-id="f7132-107">This article shows how to decode a script block that a PowerShell process is currently running.</span></span>

## <a name="create-a-long-running-process"></a><span data-ttu-id="f7132-108">Criar um processo de execução longa</span><span class="sxs-lookup"><span data-stu-id="f7132-108">Create a long running process</span></span>

<span data-ttu-id="f7132-109">Para demonstrar este cenário, abra uma nova janela do PowerShell e execute o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="f7132-109">To demonstrate this scenario, open a new PowerShell window and run the following code.</span></span> <span data-ttu-id="f7132-110">Executa um comando do PowerShell que produz um número a cada minuto durante 10 minutos.</span><span class="sxs-lookup"><span data-stu-id="f7132-110">It executes a PowerShell command that outputs a number every minute for 10 minutes.</span></span>

```powershell
powershell.exe -Command {
    $i = 1
    while ( $i -le 10 )
    {
        Write-Output -InputObject $i
        Start-Sleep -Seconds 60
        $i++
    }
}
```

## <a name="view-the-process"></a><span data-ttu-id="f7132-111">Ver o processo</span><span class="sxs-lookup"><span data-stu-id="f7132-111">View the process</span></span>

<span data-ttu-id="f7132-112">O corpo do comando que está a executar o PowerShell é armazenado na **CommandLine** propriedade da [Win32_Process][] classe.</span><span class="sxs-lookup"><span data-stu-id="f7132-112">The body of the command which PowerShell is executing is stored in the **CommandLine** property of the [Win32_Process][] class.</span></span> <span data-ttu-id="f7132-113">Se o comando é um comando codificado, o **CommandLine** propriedade contém a cadeia de caracteres "EncodedCommand".</span><span class="sxs-lookup"><span data-stu-id="f7132-113">If the command is an encoded command, the **CommandLine** property contains the string "EncodedCommand".</span></span> <span data-ttu-id="f7132-114">Usando essas informações, o comando codificado pode ser anulado oculto por meio do seguinte processo.</span><span class="sxs-lookup"><span data-stu-id="f7132-114">Using this information, the encoded command can be de-obfuscated via the following process.</span></span>

<span data-ttu-id="f7132-115">Inicie o PowerShell como administrador.</span><span class="sxs-lookup"><span data-stu-id="f7132-115">Start PowerShell as Administrator.</span></span> <span data-ttu-id="f7132-116">É vital que o PowerShell está em execução como administrador, caso contrário, não são devolvidos resultados ao consultar os processos em execução.</span><span class="sxs-lookup"><span data-stu-id="f7132-116">It is vital that PowerShell is running as administrator, otherwise no results are returned when querying the running processes.</span></span>

<span data-ttu-id="f7132-117">Execute o seguinte comando para obter todos os processos do PowerShell que tenham um comando codificado:</span><span class="sxs-lookup"><span data-stu-id="f7132-117">Execute the following command to get all of the PowerShell processes that have an encoded command:</span></span>

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

<span data-ttu-id="f7132-118">O comando seguinte cria um objeto personalizado do PowerShell que contém o ID de processo e o comando codificado.</span><span class="sxs-lookup"><span data-stu-id="f7132-118">The following command creates a custom PowerShell object that contains the process ID and the encoded command.</span></span>

```powershell
$commandDetails = $powerShellProcesses | Select-Object -Property ProcessId,
@{
    name       = 'EncodedCommand'
    expression = {
        if ( $_.CommandLine -match 'encodedCommand (.*) -inputFormat' )
        {
            return $matches[1]
        }
    }
}
```

<span data-ttu-id="f7132-119">Agora pode ser descodificado o comando codificado.</span><span class="sxs-lookup"><span data-stu-id="f7132-119">Now the encoded command can be decoded.</span></span> <span data-ttu-id="f7132-120">O trecho a seguir itera o objeto de detalhes do comando, descodifica o comando codificado e adiciona o comando descodificado novamente para o objeto para uma investigação mais aprofundada.</span><span class="sxs-lookup"><span data-stu-id="f7132-120">The following snippet iterates over the command details object, decodes the encoded command, and adds the decoded command back to the object for further investigation.</span></span>

```powershell
$commandDetails | ForEach-Object -Process {
    # Get the current process
    $currentProcess = $_

    # Convert the Base 64 string to a Byte Array
    $commandBytes = [System.Convert]::FromBase64String($currentProcess.EncodedCommand)

    # Convert the Byte Array to a string
    $decodedCommand = [System.Text.Encoding]::Unicode.GetString($commandBytes)

    # Add the decoded command back to the object
    $commandDetails |
        Where-Object -FilterScript { $_.ProcessId -eq $_.ProcessId } |
        Add-Member -MemberType NoteProperty -Name DecodedCommand -Value $decodedCommand
}
$commandDetails[0]
```

<span data-ttu-id="f7132-121">O comando descodificado agora pode ser revisto ao selecionar a propriedade command decodificada.</span><span class="sxs-lookup"><span data-stu-id="f7132-121">The decoded command can now be reviewed by selecting the decoded command property.</span></span>

```output
ProcessId      : 8752
EncodedCommand : IAAKAAoACgAgAAoAIAAgACAAIAAkAGkAIAA9ACAAMQAgAAoACgAKACAACgAgACAAIAAgAHcAaABpAGwAZQAgACgAIAAkAGkAIAAtAG
                 wAZQAgADEAMAAgACkAIAAKAAoACgAgAAoAIAAgACAAIAB7ACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABXAHIAaQB0AGUALQBP
                 AHUAdABwAHUAdAAgAC0ASQBuAHAAdQB0AE8AYgBqAGUAYwB0ACAAJABpACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABTAHQAYQ
                 ByAHQALQBTAGwAZQBlAHAAIAAtAFMAZQBjAG8AbgBkAHMAIAA2ADAAIAAKAAoACgAgAAoAIAAgACAAIAAgACAAIAAgACQAaQArACsA
                 IAAKAAoACgAgAAoAIAAgACAAIAB9ACAACgAKAAoAIAAKAA==
DecodedCommand :
                     $i = 1

                     while ( $i -le 10 )

                     {

                         Write-Output -InputObject $i

                         Start-Sleep -Seconds 60

                         $i++

                     }
```

[Agendador de tarefas]: /windows/desktop/TaskSchd/task-scheduler-start-page
[Task Scheduler]: /windows/desktop/TaskSchd/task-scheduler-start-page
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
