---
ms.date: 08/14/2018
keywords: PowerShell, o cmdlet
title: Executar Comandos Remotos
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 2001b5509acde6ec4259bb1442944958a67aa66f
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133858"
---
# <a name="running-remote-commands"></a>Executar Comandos Remotos

Pode executar comandos num ou centenas de computadores com um único comando do PowerShell. Windows PowerShell oferece suporte a computação remoto, utilizando várias tecnologias, incluindo WMI, RPC e WS-Management.

O PowerShell Core oferece suporte a WMI, WS-Management e a comunicação remota do SSH. RPC já não é suportada.

Para obter mais informações sobre a comunicação remota do PowerShell Core, consulte os artigos seguintes:

- [SSH comunicação remota no PowerShell Core][ssh-remoting]
- [Comunicação remota do WSMan no PowerShell Core][wsman-remoting]

## <a name="windows-powershell-remoting-without-configuration"></a>Comunicação remota do Windows PowerShell sem configuração

Muitos cmdlets do Windows PowerShell tem o parâmetro ComputerName que lhe permite recolher dados e alterar as definições num ou mais computadores remotos. Estes cmdlets utilizar diferentes protocolos de comunicação e funciona em todos os sistemas de operativos do Windows sem nenhuma configuração especial.

Estes cmdlets incluem:

- [Restart-Computer](/powershell/module/microsoft.powershell.management/restart-computer)
- [Test-Connection](/powershell/module/microsoft.powershell.management/test-connection)
- [Clear-registo de eventos](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [Get-EventLog](/powershell/module/microsoft.powershell.management/get-eventlog)
- [Get-HotFix](/powershell/module/microsoft.powershell.management/get-hotfix)
- [Get-Process](/powershell/module/microsoft.powershell.management/get-process)
- [Get-Service](/powershell/module/microsoft.powershell.management/get-service)
- [Set-Service](/powershell/module/microsoft.powershell.management/set-service)
- [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [Get-WmiObject](/powershell/module/microsoft.powershell.management/get-wmiobject)

Normalmente, os cmdlets que suportam a comunicação remota sem configuração especial tem o parâmetro ComputerName e não tem o parâmetro de sessão. Para localizar estes cmdlets na sua sessão, escreva:

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Comunicação remota do Windows PowerShell

Utilizar o protocolo WS-Management, comunicação remota do Windows PowerShell permite-lhe executar qualquer comando do Windows PowerShell num ou mais computadores remotos. Pode estabelecer ligações persistentes, iniciar sessões interativas e executar scripts em computadores remotos.

Para utilizar a comunicação remota do Windows PowerShell, o computador remoto tem de ser configurado para a gestão remota.
Para obter mais informações, incluindo instruções, consulte [sobre os requisitos remoto](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).

Assim que tiver configurado a comunicação remota do Windows PowerShell, muitas estratégias de comunicação remota estão disponíveis para.
Este artigo lista apenas alguns deles. Para obter mais informações, consulte [sobre o remoto](/powershell/module/microsoft.powershell.core/about/about_remote).

### <a name="start-an-interactive-session"></a>Iniciar uma sessão interativa

Para iniciar uma sessão interativa com um único computador remoto, utilize o [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.
Por exemplo, para iniciar uma sessão interativa com o computador remoto servidor01, escreva:

```powershell
Enter-PSSession Server01
```

As alterações de linha de comandos para exibir o nome do computador remoto. Os comandos de que escreva na linha de comandos executado no computador remoto e os resultados são exibidos no computador local.

Para terminar a sessão interativa, escreva:

```powershell
Exit-PSSession
```

Para obter mais informações sobre os cmdlets de Enter-PSSession e Exit-PSSession, consulte:

- [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession)
- [Exit-PSSession](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a>Executar um comando remoto

Para executar um comando num ou mais computadores, utilize o [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet. Por exemplo, para executar uma [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) servidor01 e Server02 computadores remotos, tipo de comando:

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

O resultado é devolvido para o seu computador.

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a>Executar um Script

Para executar um script numa ou mais computadores remotos, utilize o parâmetro de caminho do ficheiro do `Invoke-Command` cmdlet. O script deve ser igual ou acessível para o computador local. Os resultados são devolvidos para o computador local.

Por exemplo, o seguinte comando executa o script de DiskCollect.ps1 nos computadores remotos, servidor01 e Server02.

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a>Estabelecer uma ligação persistente

Utilize o `New-PSSession` cmdlet para criar uma sessão persistente num computador remoto. O exemplo seguinte cria sessões remotas em servidor01 e Server02. Os objetos de sessão são armazenados no `$s` variável.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

Agora que as sessões são estabelecidas, pode executar qualquer comando nos mesmos. E como as sessões são persistentes, pode recolher dados de um comando e utilizá-lo em outro comando.

Por exemplo, o seguinte comando executa um comando de Get-HotFix em sessões na variável $s e este guarda os resultados na variável $h. A variável $h é criada em cada uma das sessões no $s, mas não existir na sessão local.

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

Agora, pode utilizar os dados no `$h` variável com outros comandos na mesma sessão. Os resultados são exibidos no computador local. Por exemplo:

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Comunicação remota avançada

Gestão remota do Windows PowerShell apenas começa aqui. Ao utilizar os cmdlets instalados com o Windows PowerShell, pode estabelecer e configurar sessões remotas, as duas das extremidades locais e remotas, a criar sessões restritos e personalizadas, permitir que os utilizadores para importar os comandos de uma sessão remota, que, na verdade, executam implicitamente na sessão remota, configure a segurança de uma sessão remota e muito mais.

Windows PowerShell inclui um provedor de WSMan. O fornecedor de cria um `WSMAN:` unidade que lhe permite navegar através de uma hierarquia de definições de configuração no computador local e computadores remotos.

Para obter mais informações sobre o fornecedor de WSMan, consulte [fornecedor de WSMan](https://technet.microsoft.com/library/dd819476.aspx) e [sobre Cmdlets de WS-Management](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), ou na consola do Windows PowerShell, escreva `Get-Help wsman`.

Para mais informações, consulte:

- [Acerca das FAQ remotas](https://technet.microsoft.com/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

Para obter ajuda com erros de comunicação remota, consulte [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).

## <a name="see-also"></a>Consulte Também

- [about_Remote](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS-Management_Cmdlets](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [New-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Fornecedor de WSMan](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md