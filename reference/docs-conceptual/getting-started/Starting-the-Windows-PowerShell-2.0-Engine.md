---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Iniciar o Motor do Windows PowerShell 2.0
ms.openlocfilehash: 824077008d2dcfd707e977d2112f0882d07a8aca
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030438"
---
# <a name="starting-the-windows-powershell-20-engine"></a>Iniciar o Motor do Windows PowerShell 2.0

Esta secção explica como iniciar o motor do Windows PowerShell 2.0 no Windows 8.1, Windows Server 2012 R2, Windows 8 e Windows Server 2012, que incluem o motor do Windows PowerShell 2.0 e em outros sistemas na qual Windows PowerShell 2.0, Windows PowerShell 3.0 e 4.0 do Windows PowerShell são instalados.

Windows PowerShell 4.0 e Windows PowerShell 3.0 foram concebidos para compatibilidade com o Windows PowerShell 2.0. Cmdlets, fornecedores, snap-ins, módulos e scripts escritos para o Windows PowerShell 2.0 continuar em execução no Windows PowerShell 4.0 e no Windows PowerShell 3.0. No entanto, devido a uma alteração na política de ativação de tempo de execução no Microsoft .NET Framework 4, programas de anfitrião do Windows PowerShell que foram escritos para o Windows PowerShell 2.0 e compilados com o tempo de execução do CLR (Common Language) 2.0 não é possível executar sem modificações no Windows PowerShell 3.0 ou o Windows PowerShell 4.0, que são compiladas com o CLR 4.0. O motor do Windows PowerShell 2.0 se destina a ser utilizado apenas quando um script existente ou programa de anfitrião não pode ser executado porque ele não é compatível com o Windows PowerShell 4.0, Windows PowerShell 3.0 ou Microsoft .NET Framework 4. Nesses casos devem ser raros.

Muitos programas que requerem o motor do Windows PowerShell 2.0 inicialização-la automaticamente. Estas instruções estão incluídas para raras situações em que precisa para começar o mecanismo de manualmente.

## <a name="installing-and-enabling-required-programs"></a>Instalar e ativar a programas necessários

Antes de iniciar o motor do Windows PowerShell 2.0, ative o motor do Windows PowerShell 2.0 e o Microsoft .NET Framework 3.5 com Service Pack 1. Para obter instruções, consulte [instalar o Windows PowerShell](../install/Installing-Windows-PowerShell.md).

Sistemas em que Windows Management Framework 4.0 ou o Windows Management Framework 3.0 são instalados ter todos os componentes necessários. Nenhuma configuração adicional é necessária. Para obter informações sobre a instalação [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) ou o Windows Management Framework 3.0, consulte [instalar o Windows PowerShell](../install/Installing-Windows-PowerShell.md).

## <a name="how-to-start-the-windows-powershell-20-engine"></a>Como iniciar o motor do Windows PowerShell 2.0

Quando inicia o Windows PowerShell a versão mais recente é iniciado por predefinição. Para iniciar o Windows PowerShell com o mecanismo do Windows PowerShell 2.0, utilize o parâmetro de versão do PowerShell.exe. Pode executar o comando qualquer linha de comandos, incluindo o Windows PowerShell e Cmd.exe.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Como iniciar uma sessão remota com o motor do Windows PowerShell 2.0

Para executar o motor do Windows PowerShell 2.0 numa sessão remota, crie uma configuração de sessão (também conhecido como um "ponto final") no computador remoto que carrega o motor do Windows PowerShell 2.0. A configuração de sessão é guardada no computador remoto e pode ser utilizada por nenhum utilizador autorizado para criar sessões que utilizam o motor do Windows PowerShell 2.0.

Esta é uma tarefa avançada que normalmente é efetuada por um administrador de sistema.

O procedimento seguinte utiliza a **PSVersion** parâmetro do [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet para criar uma configuração de sessão que utiliza o motor do Windows PowerShell 2.0. Também pode utilizar o **PowerShellVersion** parâmetro do [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet para criar um ficheiro de configuração de sessão para uma sessão que carrega o motor do Windows PowerShell 2.0 e Pode utilizar o **PSVersion** parâmetro do [conjunto-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) parâmetro para alterar uma configuração de sessão para utilizar o motor do Windows PowerShell 2.0.

Para obter mais informações sobre os ficheiros de configuração de sessão, consulte [about_Session_Configuration_Files](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8). Para obter informações sobre configurações de sessão, incluindo a configuração e segurança, consulte [about_Session_Configurations [v4]](https://technet.microsoft.com/library/a2fbe12a-350c-4d04-be50-24102824e3ab).

#### <a name="to-start-a-remote-windows-powershell-20-session"></a>Para iniciar uma sessão remota do Windows PowerShell 2.0

1. Para criar uma configuração de sessão que requer o motor do Windows PowerShell 2.0, utilize o **PSVersion** parâmetro do [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet com um valor de "2.0". Execute este comando no computador no "no servidor" ou de extremidade de recepção da ligação.

   O comando de exemplo seguinte cria a configuração de sessão de PS2 no computador servidor01. Para executar este comando, inicie o Windows PowerShell 4.0 ou Windows PowerShell 3.0 com o **executar como administrador** opção.

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

2. Para criar uma sessão no computador servidor01 que utiliza a configuração de sessão de PS2, utilize o **ConfigurationName** parâmetro de cmdlets que criar uma sessão remota, por exemplo, o [New-PSSession](https://technet.microsoft.com/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f) cmdlet.

   Quando uma sessão que utiliza a configuração de sessão é iniciada, o motor do Windows PowerShell 2.0 é carregado automaticamente para a sessão.

   O comando seguinte inicia uma sessão no computador servidor01 que utiliza a configuração de sessão de PS2. O comando guarda a sessão na variável $s.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Como iniciar uma tarefa em segundo plano com o motor do Windows PowerShell 2.0

Para iniciar uma tarefa em segundo plano com o mecanismo do Windows PowerShell 2.0, utilize o **PSVersion** parâmetro do [tarefa de início](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) cmdlet.

O comando seguinte inicia uma tarefa em segundo plano com o mecanismo do Windows PowerShell 2.0

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Para obter mais informações sobre tarefas em segundo plano, consulte [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).
