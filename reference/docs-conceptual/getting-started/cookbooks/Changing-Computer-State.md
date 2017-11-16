---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "A alteração de estado do computador"
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: 636690c72b16bf19826b0a7e54ce00114ce30fb6
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="changing-computer-state"></a>A alteração de estado do computador
Para repor um computador no Windows PowerShell, utilize uma ferramenta de linha de comandos padrão ou uma classe WMI. Embora estiver a utilizar o Windows PowerShell apenas para executar a ferramenta, aprender a alterar o estado de energia de um computador no Windows PowerShell ilustra alguns dos detalhes importantes sobre como trabalhar com ferramentas externas no Windows PowerShell.

### <a name="locking-a-computer"></a>Bloqueio de um computador
É a única forma de bloquear um computador diretamente com as ferramentas disponíveis padrão para chamar o **LockWorkstation()** funcionar **user32.dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

Este comando bloqueia imediatamente a estação de trabalho. Utiliza *rundll32.exe*, que é executado DLLs do Windows (e guarda os respetivos bibliotecas para utilização repetida) para executar user32.dll, uma biblioteca de funções de gestão do Windows.

Quando bloqueia uma estação de trabalho enquanto a mudança rápida de utilizador estiver ativada, tal como no Windows XP, o computador apresenta o ecrã de início de sessão do utilizador em vez de iniciar a proteção de ecrã ser o utilizador atual.

Para encerrar sessões específicas num servidor de Terminal, utilize o **tsshutdn.exe** ferramenta da linha de comandos.

### <a name="logging-off-the-current-session"></a>Terminar a sessão atual
Pode utilizar várias técnicas diferentes para terminar uma sessão no sistema local. A forma mais simples consiste em utilizar a ferramenta de linha de comandos de serviços de Terminal/ambiente de trabalho remoto, **logoff.exe** (para obter mais detalhes, na linha de comandos do Windows PowerShell, escreva **fim de sessão /?**). Para terminar a sessão atual do Active Directory, escreva **terminar sessão** sem argumentos.

Também pode utilizar o **shutdown.exe** ferramenta com a sua opção de terminar sessão:

```
shutdown.exe -l
```

Uma terceira opção consiste em utilizar o WMI. A classe Win32_OperatingSystem tem um método de Win32Shutdown. Invocar o método com o sinalizador 0 inicia a fim de sessão:

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Para obter mais informações e para localizar outras funcionalidades do método Win32Shutdown, consulte "Win32Shutdown método da classe Win32_OperatingSystem" no MSDN.

### <a name="shutting-down-or-restarting-a-computer"></a>Encerrar ou reiniciar um computador
Encerrar e reiniciar os computadores são, geralmente, os mesmos tipos de tarefas. As ferramentas que encerrar um computador, geralmente, serão reiniciá-lo, bem como — e vice-versa. Existem duas opções simples para reiniciar um computador a partir do Windows PowerShell. Utilize Tsshutdn.exe ou Shutdown.exe com argumentos adequados. Pode obter informações de utilização detalhada do **tsshutdn.exe /?** ou **shutdown.exe /?**.

Também pode efetuar encerrar e reiniciar operações utilizando **Win32_OperatingSystem** diretamente a partir do Windows PowerShell, bem como.

Para encerrar o computador, utilize o método Win32Shutdown com o **1** sinalizador.

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(1)
```

Para reiniciar o sistema operativo, utilize o método Win32Shutdown com o **2** sinalizador.

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(2)
```

