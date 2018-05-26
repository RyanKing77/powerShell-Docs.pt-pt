---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Iniciar o Motor do Windows PowerShell 2.0
ms.assetid: edafc2fa-7576-49c2-bbba-9336f4bcfc28
ms.openlocfilehash: 618745ff4865dd046acf46487e87c3ca0e324f95
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/25/2018
---
# <a name="starting-the-windows-powershell-20-engine"></a>Iniciar o Motor do Windows PowerShell 2.0

Esta secção explica como iniciar o motor do Windows PowerShell 2.0 no Windows 8.1, Windows Server 2012 R2, Windows 8 e Windows Server 2012, que incluem o motor do Windows PowerShell 2.0 e em outros sistemas na qual o Windows PowerShell 2.0, Windows PowerShell 3.0 e o Windows PowerShell 4.0 estão instalado.

Windows PowerShell 4.0 e o Windows PowerShell 3.0 foram concebidos para serem retrocompatíveis com o Windows PowerShell 2.0. Os cmdlets, fornecedores, snap-ins, módulos e scripts escritos para o Windows PowerShell 2.0 executam inalterados no Windows PowerShell 4.0 e o Windows PowerShell 3.0. No entanto, devido a uma alteração na política de ativação de tempo de execução no Microsoft .NET Framework 4, alojar programas do Windows PowerShell que foram escritos para o Windows PowerShell 2.0 e compilados com o Common Language Runtime (CLR) 2.0 não é possível executar sem modificação no Windows PowerShell 3.0 ou Windows PowerShell 4.0, que são compiladas com CLR 4.0. O motor do Windows PowerShell 2.0 se destina a ser utilizado apenas quando um script existente ou não é possível executar o programa de anfitrião porque é incompatível com o Windows PowerShell 4.0, o Windows PowerShell 3.0 ou o Microsoft .NET Framework 4. Nestes casos deverão estar raro.

Muitos programas que requerem o motor do Windows PowerShell 2.0 iniciam-o automaticamente. Estas instruções estão incluídas nas situações raras nos quais tem de iniciar o motor manualmente.

## <a name="installing-and-enabling-required-programs"></a>Instalar e ativar os programas necessários

Antes de iniciar o motor do Windows PowerShell 2.0, ative o motor do Windows PowerShell 2.0 e o Microsoft .NET Framework 3.5 com Service Pack 1. Para obter instruções, consulte [instalar o Windows PowerShell](Installing-Windows-PowerShell.md).

Sistemas no qual [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) ou o Windows Management Framework 3.0 estão instalados ter todos os componentes necessários. Não é necessária nenhuma configuração adicional. Para obter informações sobre a instalação [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) ou o Windows Management Framework 3.0, consulte [instalar o Windows PowerShell](Installing-Windows-PowerShell.md).

## <a name="how-to-start-the-windows-powershell-20-engine"></a>Como iniciar o motor do Windows PowerShell 2.0

Quando iniciar o Windows PowerShell a versão mais recente é iniciado por predefinição. Para iniciar o Windows PowerShell com o motor do Windows PowerShell 2.0, utilize o parâmetro de versão de PowerShell.exe. Pode executar o comando qualquer linha de comandos, incluindo o Windows PowerShell e Cmd.exe.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Como iniciar uma sessão remota com o motor do Windows PowerShell 2.0

Para executar uma sessão remota do motor do Windows PowerShell 2.0, crie uma configuração de sessão (também conhecido como um "ponto final") no computador remoto que carrega o motor do Windows PowerShell 2.0. A configuração de sessão é guardada no computador remoto e pode ser utilizada por qualquer utilizador autorizado a criar sessões que utilizam o motor do Windows PowerShell 2.0.

Esta é uma tarefa avançada que normalmente é efetuada por um administrador de sistema.

O procedimento seguinte utiliza o **PSVersion** parâmetro o [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet para criar uma configuração de sessão que utiliza o motor do Windows PowerShell 2.0. Também pode utilizar o **PowerShellVersion** parâmetro o [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet para criar um ficheiro de configuração de sessão para uma sessão que carrega o motor do Windows PowerShell 2.0 e Pode utilizar o **PSVersion** parâmetro o [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) parâmetro para alterar uma configuração de sessão para utilizar o motor do Windows PowerShell 2.0.

Para mais informações sobre os ficheiros de configuração de sessão, consulte [about_Session_Configuration_Files](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8). Para obter informações sobre configurações de sessão, incluindo a configuração e segurança, consulte [about_Session_Configurations [v4]](https://technet.microsoft.com/library/a2fbe12a-350c-4d04-be50-24102824e3ab).

#### <a name="to-start-a-remote-windows-powershell-20-session"></a>Para iniciar uma sessão remota do Windows PowerShell 2.0

1. Para criar uma configuração de sessão que requer que o motor do Windows PowerShell 2.0, utilize o **PSVersion** parâmetro o [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet com um valor de "2.0". Execute este comando no computador no "lado do servidor" ou do recetor da ligação.

   O comando de exemplo seguinte cria a configuração de sessão PS2 no computador servidor01. Para executar este comando, inicie o Windows PowerShell 4.0 ou o Windows PowerShell 3.0 com o **executar como administrador** opção.

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

2. Para criar uma sessão no computador servidor01 que utiliza a configuração de sessão PS2, utilize o **ConfigurationName** parâmetro de cmdlets que criar uma sessão remota, tais como o [New-PSSession](https://technet.microsoft.com/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f) cmdlet.

   Quando uma sessão que utiliza a configuração de sessão é iniciado, o motor do Windows PowerShell 2.0 automaticamente foi carregado para a sessão.

   O seguinte comando inicia uma sessão no computador servidor01 que utiliza a configuração de sessão PS2. O comando guarda a sessão na variável $s.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Como iniciar uma tarefa em segundo plano com o motor do Windows PowerShell 2.0

Para iniciar uma tarefa em segundo plano com o motor do Windows PowerShell 2.0, utilize o **PSVersion** parâmetro o [Start-Job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) cmdlet.

O seguinte comando inicia uma tarefa em segundo plano com o motor do Windows PowerShell 2.0

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Para mais informações sobre tarefas em segundo plano, consulte [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).