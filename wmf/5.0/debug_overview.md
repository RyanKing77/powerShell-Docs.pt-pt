---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: aaf1809277f072c82e5a1a862ea64b75586e32d1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="improvements-in-powershell-script-debugging"></a>Melhoramentos na depuração de Script do PowerShell

Um número de melhorias efetuado no PowerShell 5.0 para melhorar a experiência de depuração:

## <a name="break-all"></a>Quebrar a todos os

A consola do PowerShell e o ISE do Windows PowerShell agora permitem-lhe aceder ao depurador para executar scripts. Este procedimento funciona em sessões locais e remotas.

Na consola, prima **Ctrl + Break**.

No ISE, prima **Ctrl + B**, ou utilize o **depuração -> interromper todos os** comandos de menu.

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a>Depuração remota e edição de ficheiros remotos no ISE do Windows PowerShell

Agora o ISE do Windows PowerShell permite-lhe abrir e editar ficheiros numa sessão remota, executando o comando PSEdit.
Por exemplo, pode abrir um ficheiro para a edição na linha de comandos numa sessão remota da seguinte forma:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Além disso, agora pode editar e guardar as alterações num ficheiro remoto que é aberto automaticamente no ISE do Windows PowerShell quando atingiu um ponto de interrupção.
Agora, pode depurar um ficheiro de script está em execução num computador remoto, edite o ficheiro para corrigir um erro e, em seguida, volte a executar o script modificado.

## <a name="advanced-script-debugging"></a>A depuração de scripts avançados

Não existem funcionalidades de depuração novo, avançadas que lhe permitem ligar a nenhum processo de computador local que foi carregadas do Windows PowerShell e depurar arbitrários espaços de execução no processo.

### <a name="runspace-debugging"></a>A depuração de espaço de execução

Foram adicionados novos cmdlets que lhe permitem a lista de espaços de execução atuais num processo e anexar a consola do Windows PowerShell ou o depurador ISE para esse espaço de execução para a depuração de scripts:

-   Get-espaço de execução
-   Espaço de execução de depuração
-   Ativar RunspaceDebug
-   Desativar RunspaceDebug
-   Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Ligar ao processo de alojamento do PowerShell

Agora pode anexar à qualquer processo computador carregado com o Windows PowerShell. Fazê-lo ao introduzir para uma sessão interativa com o processo, de forma semelhante ao como introduziu para uma sessão remota interativa executando o cmdlet Enter-PSSession:

-   PSHostProcess introduza
-   Saída PSHostProcess
