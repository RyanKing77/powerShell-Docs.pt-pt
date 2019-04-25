---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 22a027ebc97e15075980bc77ce272d8ecdae0b5f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058669"
---
# <a name="improvements-in-powershell-script-debugging"></a>Melhorias na Depuração de Scripts do PowerShell

Uma série de melhorias foram feita no PowerShell 5.0 para melhorar a experiência de depuração:

## <a name="break-all"></a>Interromper todos os

A consola do PowerShell e o Windows PowerShell ISE agora o permitem-lhe aceder ao depurador para a execução de scripts. Isso funciona em sessões locais e remotos.

Na consola, prima **Ctrl + Break**.

No ISE, pressione **Ctrl + B**, ou utilize o **depuração -> interromper todos os** comando de menu.

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a>Depuração remota e a edição de arquivos remoto no ISE do Windows PowerShell

Agora o ISE do Windows PowerShell permite-lhe abrir e editar arquivos numa sessão remota ao executar o comando PSEdit.
Por exemplo, pode abrir um arquivo para edição da linha de comando numa sessão remota da seguinte forma:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Além disso, agora pode editar e guardar as alterações num arquivo remoto que é aberto automaticamente no ISE do Windows PowerShell quando atingir um ponto de interrupção.
Agora, pode depurar um ficheiro de script que está em execução num computador remoto, edite o ficheiro para corrigir um erro e, em seguida, volte a executar o script modificado.

## <a name="advanced-script-debugging"></a>Depuração de scripts avançados

Existem novos e avançados recursos de depuração que permitem anexar a qualquer processo de computador local que foi carregado o Windows PowerShell e depurar os espaços de execução arbitrários nesse processo.

### <a name="runspace-debugging"></a>Depuração do espaço de execução

Foram adicionados novos cmdlets que permitem-lhe a lista de espaços de execução atuais num processo e anexar a consola do Windows PowerShell ou o depurador ISE para esse espaço de execução para a depuração de scripts:

-   Get-Runspace
-   Debug-Runspace
-   Enable-RunspaceDebug
-   Disable-RunspaceDebug
-   Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Anexar a processo que hospeda o PowerShell

Agora pode anexar a qualquer processo de computador com o PowerShell do Windows carregados. Fazê-lo ao introduzir para uma sessão interativa com o processo, da mesma forma para como de celebrar uma sessão remota interativa ao executar o cmdlet Enter-PSSession:

-   Enter-PSHostProcess
-   Exit-PSHostProcess
