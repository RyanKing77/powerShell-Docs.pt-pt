---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Tornando-o segundo hop comunicação remota do PowerShell
ms.openlocfilehash: 1d24473178bc50321a81ebf1115a20f17078844f
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34483020"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>Tornando-o segundo hop comunicação remota do PowerShell

O "problema salto segundo" refere-se a uma situação como o seguinte:

1. Tiver sessão iniciada _ServerA_.
2. De _ServerA_, iniciar uma sessão de PowerShell remota para ligar ao _ServerB_.
3. Um comando a executar no _ServerB_ através do seu sistema de interação remota de PowerShell tenta aceder a um recurso na sessão _ServerC_.
4. Acesso ao recurso no _ServerC_ é negada, porque as credenciais utilizadas para criar a sessão de comunicação remota do PowerShell não são transmitidas do _ServerB_ para _ServerC_.

Existem várias formas para resolver este problema. Neste tópico, vamos ver várias as soluções mais populares para o problema de salto segundo.

## <a name="credssp"></a>CredSSP

Pode utilizar o [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) para autenticação. CredSSP coloca em cache as credenciais no servidor remoto (_ServerB_), por isso, utilizá-la abre até ataques de roubo de credenciais. Se o computador remoto for comprometido, o atacante tem acesso às credenciais do utilizador. CredSSP está desativada por predefinição nos computadores cliente e servidor. Deve ativar o CredSSP apenas nos ambientes de maior confiança. Por exemplo, um administrador de domínio ligação a um controlador de domínio porque o controlador de domínio é altamente fidedigno.

Para obter mais informações sobre as questões de segurança quando utilizar o CredSSP para comunicação remota do PowerShell, consulte [sabotagem instalações acidental: cuidado com do CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).

Para mais informações sobre os ataques de roubo de credenciais, consulte [ataques de secção mitigação passagem do Hash (PtH) e de outros roubos de credenciais](https://www.microsoft.com/en-us/download/details.aspx?id=36036).

Para obter um exemplo de como ativar e utilizar o CredSSP para comunicação remota do PowerShell, consulte [utilizando o CredSSP para resolver o problema de Double-hop](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).

### <a name="pros"></a>Vantagens

- Funciona para todos os servidores com o Windows Server 2008 ou posterior.

### <a name="cons"></a>Desvantagens

- Tem vulnerabilidades de segurança.
- Requer a configuração das funções do cliente e servidor.

## <a name="kerberos-delegation-unconstrained"></a>Delegação de Kerberos (restrita)

A delegação restrita de Kerberos também pode ser utilizado para tornar o segundo hop. No entanto, este método fornece sem controlo da onde são utilizadas credenciais delegadas.

>**Nota:** contas do Active Directory que tenham o **conta é sensível e não pode ser delegada** não pode ser delegada a propriedade definida. Para obter mais informações, consulte [foco de segurança: Analysing 'Conta é sensível e não pode ser delegada' para contas com privilégios](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) e [Kerberos Authentication ferramentas e definições](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Vantagens

- Não necessita de nenhum codificação especiais.

### <a name="cons"></a>Desvantagens

- Não suporta o segundo hop para WinRM.
- Não fornece nenhum controlo sobre em que as credenciais são utilizadas, criar uma vulnerabilidade de segurança.

## <a name="kerberos-constrained-delegation"></a>Delegação restringida de Kerberos

Pode utilizar a delegação restrita legada (não baseada em recursos) para tornar o segundo hop.

>**Nota:** contas do Active Directory que tenham o **conta é sensível e não pode ser delegada** não pode ser delegada a propriedade definida. Para obter mais informações, consulte [foco de segurança: Analysing 'Conta é sensível e não pode ser delegada' para contas com privilégios](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) e [Kerberos Authentication ferramentas e definições](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Vantagens

- Não necessita de nenhum codificação especiais

### <a name="cons"></a>Desvantagens

- Não suporta o segundo hop para WinRM.
- Tem de ser configurada no objeto do Active Directory do servidor remoto (_ServerB_).
- Limitado a um domínio. Não é possível de se estender domínios ou florestas.
- Necessita de direitos para atualizar objetos e nomes de principais de serviço (SPNs).

## <a name="resource-based-kerberos-constrained-delegation"></a>Delegação restrita de Kerberos baseada em recursos

Utilizar baseada em recursos restrita de Kerberos delegação (introduzida no Windows Server 2012), configurar a delegação de credenciais no objeto de servidor onde residem os recursos.
O segundo cenário de salto descrito acima, pode configurar _ServerC_ para especificar a partir do qual irá aceitar delegado credenciais.

>**Nota:** contas do Active Directory que tenham o **conta é sensível e não pode ser delegada** não pode ser delegada a propriedade definida. Para obter mais informações, consulte [foco de segurança: Analysing 'Conta é sensível e não pode ser delegada' para contas com privilégios](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) e [Kerberos Authentication ferramentas e definições](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Vantagens

- As credenciais não são armazenadas.
- Relativamente fácil de configurar utilizando cmdlets do PowerShell – sem codificação especial necessário.
- Sem acesso de domínio especial não é necessário.
- Funciona em domínios e florestas.
- Código do PowerShell.

### <a name="cons"></a>Desvantagens

- Requer o Windows Server 2012 ou posterior.
- Não suporta o segundo hop para WinRM.
- Necessita de direitos para atualizar objetos e nomes de principais de serviço (SPNs).

### <a name="example"></a>Exemplo

Vamos ver um exemplo que configura recursos baseia a delegação restrita de PowerShell _ServerC_ para permitir que as credenciais de delegado de um _ServerB_.
Este exemplo assume que todos os servidores são com o Windows Server 2012 ou posterior, e que existe pelo menos um controlador de domínio do Windows Server 2012 cada domínio para que qualquer um dos servidores pertencem.

Antes de poder configurar a delegação restrita, tem de adicionar o `RSAT-AD-PowerShell` funcionalidade para instalar o módulo PowerShell do Active Directory e, em seguida, importar esse módulo para a sua sessão:

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
Vários cmdlets disponíveis agora tem um **PrincipalsAllowedToDelegateToAccount** parâmetro:

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

O **PrincipalsAllowedToDelegateToAccount** parâmetro define o atributo de objeto do Active Directory **msDS-AllowedToActOnBehalfOfOtherIdentity**, que contém uma lista de controlo de acesso (ACL) que Especifica quais as contas que têm autorização para delegar as credenciais para a conta associada (no nosso exemplo, será a conta de computador para _servidor_).

Agora vamos configurar as variáveis que iremos utilizar para representar os servidores:

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

WinRM (e, por conseguinte, comunicação remota do PowerShell) é executado como a conta de computador por predefinição. Pode ver este observando a **StartName** propriedade o `winrm` serviço:

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

Para _ServerC_ para permitir a delegação de uma sessão de comunicação remota do PowerShell no _ServerB_, iremos irá conceder acesso ao definir o **PrincipalsAllowedToDelegateToAccount** parâmetro em _ServerC_ para o objeto de computador do _ServerB_:

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

O Kerberos [Centro de distribuição de chaves (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches negado tentativas de acesso (cache negativa), para 15 minutos. Se _ServerB_ anteriormente tentou aceder _ServerC_, terá de limpar a cache no _ServerB_ invocando o seguinte comando:

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

Também pode reiniciar o computador ou aguarde, pelo menos, 15 minutos para limpar a cache.

Após limpar a cache, pode executar com êxito o código de _ServerA_ através de _ServerB_ para _ServerC_:

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

Neste exemplo, o `$using` variável é utilizada para efetuar o `$ServerC` variável visível para _ServerB_. Para obter mais informações sobre o `$using` variável, consulte [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).

Para permitir que vários servidores delegar as credenciais para _ServerC_, defina o valor da **PrincipalsAllowedToDelegateToAccount** parâmetro no _ServerC_ numa matriz:

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

Se pretender que o segundo hop entre domínios, adicione o nome de domínio completamente qualificado (FQDN) do controlador de domínio do domínio ao qual _ServerB_ pertence:

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

Para remover a capacidade para delegar as credenciais para ServerC, defina o valor da **PrincipalsAllowedToDelegateToAccount** parâmetro no _ServerC_ para `$null`:

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>Informações sobre a delegação restringida Kerberos baseada em recursos

- [Novidades na autenticação Kerberos](https://technet.microsoft.com/library/hh831747.aspx)
- [Como o Windows Server 2012 Eases tensão de Kerberos a delegação restrita, parte 1](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [Como o Windows Server 2012 Eases tensão de Kerberos a delegação restrita, faz parte 2](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [Restrita de Kerberos de compreender a delegação para implementações de Proxy de aplicações do Azure Active Directory com a autenticação integrada do Windows](http://aka.ms/kcdpaper)
- [[MS-ADA2]: msDS-AllowedToActOnBehalfOfOtherIdentity de atributo do M2.210 de atributos de esquema do Active Directory](https://msdn.microsoft.com/library/hh554126.aspx)
- [[MS-SFU]: extensões de protocolo do Kerberos: serviço para utilizador e a delegação restrita protocolo 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)
- [Recursos com base em Kerberos a delegação restrita](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [Administração remota sem PrincipalsAllowedToDelegateToAccount a utilizar a delegação restrita](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a>PSSessionConfiguration utilizando RunAs

Pode criar uma configuração de sessão em _ServerB_ e definir o respetivo **RunAsCredential** parâmetro.

Para obter informações sobre como utilizar PSSessionConfiguration e RunAs para resolver o problema de salto segundo, consulte [outra solução para comunicação remota do PowerShell multi-HOP](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).

### <a name="pros"></a>Vantagens

- Funciona com qualquer servidor com o WMF 3.0 ou posterior.

### <a name="cons"></a>Desvantagens

- Requer a configuração de **PSSessionConfiguration** e **RunAs** em cada servidor intermédia (_ServerB_).
- Necessita de manutenção de palavra-passe quando utilizar um domínio **RunAs** conta

## <a name="just-enough-administration-jea"></a>Administração JEA (Just Enough Administration)

JEA permite-lhe restringir os comandos que um administrador pode ser executado durante uma sessão do PowerShell. Pode ser utilizado para resolver o problema de salto segundo.

Para obter informações sobre JEA, consulte [apenas suficiente administração](https://docs.microsoft.com/powershell/jea/overview).

### <a name="pros"></a>Vantagens

- Nenhuma manutenção de palavra-passe ao utilizar uma conta virtual.

### <a name="cons"></a>Desvantagens

- Requer o WMF 5.0 ou posterior.
- Requer configuração em cada servidor intermédia (_ServerB_).

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Introduzir credenciais dentro de um bloco de script de Invoke-Command

Pode passar credenciais dentro de **ScriptBlock** parâmetro de uma chamada para o [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.

### <a name="pros"></a>Vantagens

- Não necessita de configuração de servidor especial.
- Funciona em qualquer servidor que executa o WMF 2.0 ou posterior.

### <a name="cons"></a>Desvantagens

- Requer uma técnica de código awkward.
- Se executar o WMF 2.0, necessita de sintaxe diferentes para passar os argumentos para uma sessão remota.

### <a name="example"></a>Exemplo

O exemplo seguinte mostra como introduzir credenciais num **Invoke-Command** bloco de script:

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a>Consulte também

[Considerações de Segurança da Comunicação Remota do PowerShell](WinRMSecurity.md)