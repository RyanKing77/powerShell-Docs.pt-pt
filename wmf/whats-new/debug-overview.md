---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Melhorias na Depuração de Scripts do PowerShell
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856176"
---
# <a name="improvements-in-powershell-script-debugging"></a>Melhorias na Depuração de Scripts do PowerShell

PowerShell 5.0 inclui vários melhoramentos que melhoram a experiência de depuração.

## <a name="break-all"></a>Interromper todos os

A consola do PowerShell e o ISE do PowerShell agora permitem-lhe aceder ao depurador para a execução de scripts. Isso funciona em sessões locais e remotos.

Na consola, prima <kbd>Ctrl</kbd>+<kbd>quebrar</kbd>.

No ISE, pressione <kbd>Ctrl</kbd>+<kbd>B</kbd>, ou utilizar o **depuração -> interromper todos os** comando de menu.

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a>Depuração remota e a edição de arquivos remoto no ISE do PowerShell

ISE do PowerShell agora permite-lhe abrir e editar arquivos numa sessão remota ao executar o comando PSEdit.
Por exemplo, pode abrir um arquivo para edição da linha de comando numa sessão remota da seguinte forma:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Além disso, agora pode editar e guardar as alterações num arquivo remoto que é aberto automaticamente no ISE do PowerShell quando atingir um ponto de interrupção. Agora, pode depurar um ficheiro de script que está em execução num computador remoto, edite o ficheiro para corrigir um erro e, em seguida, volte a executar o script modificado.

## <a name="advanced-script-debugging"></a>Depuração de scripts avançados

Existem novos e avançados recursos de depuração que permitem anexar a qualquer processo de computador local que carregou o PowerShell e depurar os espaços de execução arbitrários nesse processo.

### <a name="runspace-debugging"></a>Depuração do espaço de execução

Foram adicionados novos cmdlets que permitem-lhe a lista de espaços de execução atuais num processo e anexar a consola do PowerShell ou o depurador do ISE do PowerShell para esse espaço de execução para a depuração de scripts:

- Get-Runspace
- Debug-Runspace
- Enable-RunspaceDebug
- Disable-RunspaceDebug
- Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Anexar a processo que hospeda o PowerShell

Agora pode anexar a qualquer processo de computador que tenha carregado do PowerShell. Pode fazê-lo ao introduzir para uma sessão interativa com o processo de anfitrião. Para mais informações, consulte:

- [Enter-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [Exit-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
