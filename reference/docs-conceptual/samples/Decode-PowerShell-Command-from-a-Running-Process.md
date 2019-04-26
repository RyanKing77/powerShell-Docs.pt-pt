---
ms.date: 11/13/2018
keywords: PowerShell, o cmdlet
title: Decode a PowerShell command from a running process (Descodificar um comando do PowerShell a partir de um processo em execução)
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086243"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a>Decode a PowerShell command from a running process (Descodificar um comando do PowerShell a partir de um processo em execução)

Às vezes, pode ter um processo em execução que está ocupando uma grande quantidade de recursos de PowerShell.
Este processo pode estar em execução no contexto de um [agendador de tarefas][] tarefa ou uma [SQL Server Agent][] tarefa. Em que há vários processos de PowerShell em execução, pode ser difícil saber o processo que representa o problema. Este artigo mostra como a descodificar um bloco de script que um processo de PowerShell está atualmente em execução.

## <a name="create-a-long-running-process"></a>Criar um processo de execução longa

Para demonstrar este cenário, abra uma nova janela do PowerShell e execute o seguinte código. Executa um comando do PowerShell que produz um número a cada minuto durante 10 minutos.

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

## <a name="view-the-process"></a>Ver o processo

O corpo do comando que está a executar o PowerShell é armazenado na **CommandLine** propriedade da [Win32_Process][] classe. Se o comando é um [codificado comando][], o **CommandLine** propriedade contém a cadeia de caracteres "EncodedCommand". Usando essas informações, o comando codificado pode ser anulado oculto por meio do seguinte processo.

Inicie o PowerShell como administrador. É vital que o PowerShell está em execução como administrador, caso contrário, não são devolvidos resultados ao consultar os processos em execução.

Execute o seguinte comando para obter todos os processos do PowerShell que tenham um comando codificado:

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

O comando seguinte cria um objeto personalizado do PowerShell que contém o ID de processo e o comando codificado.

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

Agora pode ser descodificado o comando codificado. O trecho a seguir itera o objeto de detalhes do comando, descodifica o comando codificado e adiciona o comando descodificado novamente para o objeto para uma investigação mais aprofundada.

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

O comando descodificado agora pode ser revisto ao selecionar a propriedade command decodificada.

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
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[codificado comando]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
