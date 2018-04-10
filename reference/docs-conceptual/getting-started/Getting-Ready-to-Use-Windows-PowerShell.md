---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Preparar-se para Utilizar o Windows PowerShell
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
ms.openlocfilehash: 5e095984286ff89958dc0a4e3d27e40eae5b2c5e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="getting-ready-to-use-windows-powershell"></a>Preparar-se para Utilizar o Windows PowerShell
Quando o Windows PowerShell está instalado e iniciado, considere as seguintes opções de configuração. Pode efetuar estas tarefas em qualquer altura.

- **Instale ficheiros de ajuda.** Os cmdlets que estão incluídos no Windows PowerShell 3.0 não são fornecidos com ficheiros de ajuda. No entanto, pode utilizar o [Update-Help](/powershell/module/microsoft.powershell.core/update-help) cmdlet para transferir e instalar os ficheiros de ajuda mais recentes no seu computador. Quando os ficheiros são instalados, pode utilizar o [Get-Help](/powershell/module/microsoft.powershell.core/get-help) cmdlet para as mostrar à direita na linha de comandos. Para obter mais informações, consulte [about_Updatable_Help](/powershell/module/microsoft.powershell.core/about/about_updatable_help).

    Se optar por não instalar os ficheiros de ajuda, pode ainda ler os tópicos de ajuda online. Para encontrar a versão online de qualquer tópico de ajuda do cmdlet, escreva: `Get-Help <CmdletName> -Online`. Para procurar o consulte Tópicos de ajuda do Windows PowerShell a [PowerShell documentação](/powershell/scripting).

- **Execute scripts.** Para manter o Windows PowerShell segura, a política de execução predefinida no Windows PowerShell é **restrito**. Esta política permite-lhe executar cmdlets, mas não os scripts. Para executar scripts, utilize o [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) cmdlet para alterar a política de execução para **AllSigned** ou **RemoteSigned**. Apenas os membros do grupo Administradores no computador podem executar este cmdlet. Para obter mais informações, consulte [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

- **Ative a comunicação remota.** O sistema já está configurado por si executar comandos remotos noutros computadores. No Windows Server 2012 R2 e Windows Server 2012, o sistema também está configurado para receber comandos remotos, ou seja, para permitir que os outros computadores executar comandos remotos no computador local. Para ativar computadores com outras versões do Windows para receber comandos remotos, execute o [Enable-PSRemoting](/powershell/module/microsoft.powershell.core/enable-psremoting) cmdlet no computador que pretende gerir remotamente. Apenas os membros do grupo Administradores no computador podem executar este cmdlet. Para obter mais informações, consulte [about_Remote](/powershell/module/microsoft.powershell.core/about/about_remote).

    Nota: Se a comunicação remota está ativada num computador que está a executar o Windows PowerShell 2.0, sistema de interação remota ainda está ativado depois de instalar o Windows Management Framework 3.0. No entanto, no Windows Server 2008 (não Windows Server 2008 R2), deve reativar a comunicação remota depois de instalar o Windows Management Framework 3.0.

## <a name="see-also"></a>Consulte Também
- [Instalar o Windows PowerShell](../setup/Installing-Windows-PowerShell.md)
- [A partir do Windows PowerShell](/powershell/scripting/setup/starting-windows-powershell)