---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Alterar o Estado do Computador
ms.openlocfilehash: 80692ad7c56aa13e55d4997cfec289ffb3605458
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030275"
---
# <a name="changing-computer-state"></a>Alterar o Estado do Computador

Para repor um computador no Windows PowerShell, utilize uma ferramenta de linha de comando padrão ou uma classe WMI. Embora o estiver a utilizar o Windows PowerShell apenas para executar a ferramenta, aprendendo a alterar o estado de energia de um computador no Windows PowerShell ilustra alguns dos detalhes importantes sobre como trabalhar com as ferramentas externas no Windows PowerShell.

## <a name="locking-a-computer"></a>Bloqueio de um computador

A única forma de bloquear um computador diretamente com as ferramentas disponíveis padrão é chamar o **LockWorkstation()** funcionar **user32.dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

Este comando bloqueia imediatamente a estação de trabalho. Ele usa *rundll32.exe*, que executa o Windows DLLs (e salva suas bibliotecas para uso repetido) para executar user32.dll, uma biblioteca de funções de gerenciamento do Windows.

Quando bloquear uma estação de trabalho enquanto estiver ativada a troca rápida de usuário, como no Windows XP, o computador apresenta o ecrã de início de sessão do utilizador, em vez de iniciar a proteção de tela do utilizador atual.

Para desligar sessões particulares num Terminal Server, utilize o **tsshutdn.exe** ferramenta da linha de comandos.

## <a name="logging-off-the-current-session"></a>Terminar a sessão atual

Pode usar várias técnicas diferentes para terminar sessão numa sessão no sistema local. A forma mais simples é usar a ferramenta de linha de comandos de serviços de Terminal/ambiente de trabalho remoto, **logoff.exe** (para obter detalhes, na linha de comandos da Windows PowerShell, escreva **logoff /?** ). Para terminar a sessão atual do Active Directory, escreva **logoff** sem argumentos.

Também pode utilizar o **shutdown.exe** ferramenta com a opção de terminar sessão:

```
shutdown.exe -l
```

Uma terceira opção é usar o WMI. A classe Win32_OperatingSystem tem um método de Win32Shutdown. Invocando o método com o sinalizador 0 inicia a fim de sessão:

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Para obter mais informações e para localizar outros recursos do método Win32Shutdown, consulte "Win32Shutdown método da classe Win32_OperatingSystem" no MSDN.

## <a name="shutting-down-or-restarting-a-computer"></a>Encerrar ou reiniciar um computador

Encerrar e reiniciar os computadores em geral são os mesmos tipos de tarefas. Ferramentas que encerrar um computador em geral serão reiniciá-lo também — e vice-versa. Existem duas opções simples para reiniciar um computador a partir do Windows PowerShell. Utilize Tsshutdn.exe ou Shutdown.exe com argumentos adequados. Pode obter informações de utilização detalhadas de **tsshutdn.exe /?** ou **shutdown.exe /?** .

Também pode efetuar encerrar e reiniciar operações diretamente a partir do Windows PowerShell também.

Para encerrar o computador, utilize o comando Stop-Computer

```powershell
Stop-Computer
```

Para reiniciar o sistema operativo, utilize o comando de reiniciar o computador

```powershell
Restart-Computer
```

Para forçar um reinício imediato do computador, utilize o parâmetro - Force.

```powershell
Restart-Computer -Force
```
