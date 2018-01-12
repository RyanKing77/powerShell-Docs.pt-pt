---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Executar Comandos Remotos
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 43f07abd642e7de235647fa151537c46ebe86cae
ms.sourcegitcommit: 6aed37d7f0c9652ae09bb8c11928da7e4783ed7f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/10/2018
---
# <a name="running-remote-commands"></a>Executar Comandos Remotos

Pode executar comandos num ou centenas de computadores com um único comando do Windows PowerShell. O Windows PowerShell suporta informática remoto utilizando várias tecnologias, incluindo WMI, RPC e WS-Management.

## <a name="remoting-in-powershell-core"></a>Comunicação remota do PowerShell Core

PowerShell Core, a edição mais recente do PowerShell no Windows, macOS e Linux, suporta WMI, WS-Management e a comunicação remota SSH.
(RPC já não é suportada.)

Para obter mais informações sobre esta configuração, consulte:

* [SSH comunicação remota do PowerShell Core] [ssh-gestão remota]
* [WinRM sistema de interação remota no PowerShell Core] [winrm-sistema de interação remota]

## <a name="remoting-without-configuration"></a>Comunicação remota sem configuração
Vários cmdlets do Windows PowerShell têm o parâmetro ComputerName que lhe permite recolher dados e alterar as definições num ou mais computadores remotos. Utilizam uma variedade de tecnologias de comunicação e de trabalho muitos em todos os sistemas operativos do Windows que suporta o Windows PowerShell sem qualquer configuração especial.

Estes cmdlets incluem:

* [Reiniciar o computador](https://go.microsoft.com/fwlink/?LinkId=821625)
* [Ligação de teste](https://go.microsoft.com/fwlink/?LinkId=821646)
* [Desmarque-registo de eventos](https://go.microsoft.com/fwlink/?LinkId=821568)
* [Get-registo de eventos](https://go.microsoft.com/fwlink/?LinkId=821585)
* [Get-correção](https://go.microsoft.com/fwlink/?LinkId=821586)
* [Get-Process](https://go.microsoft.com/fwlink/?linkid=821590)
* [Get-Service](https://go.microsoft.com/fwlink/?LinkId=821593)
* [Serviço de conjunto](https://go.microsoft.com/fwlink/?LinkId=821633)
* [Get-WinEvent](https://go.microsoft.com/fwlink/?linkid=821529)
* [Get-WmiObject](https://go.microsoft.com/fwlink/?LinkId=821595)

Normalmente, os cmdlets que suportam a gestão remota sem configuração especial ter o parâmetro ComputerName e é necessário o parâmetro de sessão. Para encontrar estes cmdlets na sua sessão, escreva:

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Comunicação remota do Windows PowerShell
Comunicação remota do Windows PowerShell, que utiliza o protocolo WS-Management, permite-lhe executar qualquer comando do Windows PowerShell num ou vários computadores remotos. Permite-lhe estabelecer ligações persistentes, iniciar sessões interativas 1:1 e executar scripts em vários computadores.

Para utilizar a comunicação remota do Windows PowerShell, o computador remoto tem de ser configurado para a gestão remota. Para obter mais informações, incluindo instruções, consulte [sobre requisitos remoto](https://technet.microsoft.com/en-us/library/dd315349.aspx).

Depois de ter configurado a comunicação remota do Windows PowerShell, muitos estratégias de gestão remota estão disponíveis para si. O resto deste documento apresenta alguns dos mesmos. Para obter mais informações, consulte [sobre remoto](https://technet.microsoft.com/en-us/library/dd347744.aspx) e [sobre remoto FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).

### <a name="start-an-interactive-session"></a>Iniciar uma sessão interativa
Para iniciar uma sessão interativa com um único computador remoto, utilize o [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.
Por exemplo, para iniciar uma sessão interativa com o computador remoto servidor01, escreva:

```
Enter-PSSession Server01
```

As alterações de linha de comandos para apresentar o nome do computador ao qual estão ligados. De ora em diante, execute os comandos que escreva na linha de no computador remoto e os resultados são apresentados no computador local.

Para terminar a sessão interativa, escreva:

```
Exit-PSSession
```

Para obter mais informações sobre os cmdlets Enter-PSSession e de saída-PSSession, consulte [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) e [sair-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).

### <a name="run-a-remote-command"></a>Executar um comando remoto
Para executar qualquer comando num ou vários computadores remotos, utilize o [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.
Por exemplo, para executar um [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) comando nos servidor01 e Server02 computadores remotos, tipo:

```
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

O resultado é devolvido para o seu computador.

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```
Para obter mais informações sobre o cmdlet Invoke-Command, consulte [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="run-a-script"></a>Executar um Script
Para executar um script num ou vários computadores remotos, utilize o parâmetro de FilePath do cmdlet Invoke-Command. O script deve ser igual ou acessível para o seu computador local. Os resultados são devolvidos para o seu computador local.

Por exemplo, o seguinte comando executa o script de DiskCollect.ps1 nos computadores remotos servidor01 e Server02.

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

Para obter mais informações sobre o cmdlet Invoke-Command, consulte [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="establish-a-persistent-connection"></a>Estabelecer uma ligação persistente
Para executar uma série de comandos relacionados que partilham dados, criar uma sessão no computador remoto e, em seguida, utilize o cmdlet Invoke-Command para executar comandos na sessão que criar. Para criar uma sessão remota, utilize o cmdlet New-PSSession.

Por exemplo, o comando seguinte cria uma sessão remota no computador servidor01 e outra sessão remota no computador Server02. -Guarda os objetos de sessão na variável $s.

```
$s = New-PSSession -ComputerName Server01, Server02
```

Agora que as sessões são estabelecidas, pode executar qualquer comando nos mesmos. E visto que as sessões são persistentes, pode recolher dados de um comando utilizá-lo num comando subsequente.

Por exemplo, o comando seguinte executa um comando Get-correção em sessões na variável $s e este guarda os resultados na variável $h. A variável de $h é criada em cada uma das sessões na $s, mas não existe na sessão local.

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

Agora pode utilizar os dados na variável $h nos comandos subsequentes, tal como o seguinte. Os resultados são apresentados no computador local.

```
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Comunicação remota avançada
Gestão remota do Windows PowerShell começa imediatamente aqui. Ao utilizar os cmdlets instalados com o Windows PowerShell, pode estabelecer e configurar remotas sessões de extremidades locais e remotas, criar sessões personalizadas e restritas, permitir que os utilizadores para importar os comandos de uma sessão remota que efetivamente executam implicitamente na sessão remota, configure a segurança de uma sessão remota e muito mais.

Para facilitar a configuração remota, o Windows PowerShell inclui um fornecedor de WSMan. WSMAN: a unidade que o fornecedor cria permite-lhe navegar através de uma hierarquia de definições de configuração no computador local e computadores remotos.
Para obter mais informações sobre o fornecedor de WSMan, consulte [WSMan fornecedor](https://technet.microsoft.com/en-us/library/dd819476.aspx) e [sobre Cmdlets de WS-Management](https://technet.microsoft.com/en-us/library/dd819481.aspx), ou na consola do Windows PowerShell, escreva "Get-Help wsman".

Para mais informações, consulte:
- [Sobre FAQ remoto](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Importar-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

Para obter ajuda com erros de sistema de interação remota, consulte [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).

## <a name="see-also"></a>Consulte Também
- [about_Remote](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS Management_Cmdlets](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invocação de comando](https://go.microsoft.com/fwlink/?LinkId=821493)
- [Importar-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [Novo-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Fornecedor de WSMan](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-resmoting]: SSH-Remoting-in-PowerShell-Core.md
