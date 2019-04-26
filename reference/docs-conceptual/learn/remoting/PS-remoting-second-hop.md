---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Efetuar o segundo salto na Comunicação Remota do PowerShell
ms.openlocfilehash: 1b6e5ad53346324adc7be2d013e154c8600afa4f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086345"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>Efetuar o segundo salto na Comunicação Remota do PowerShell

O "segundo salto problema" refere-se a uma situação semelhante ao seguinte:

1. Tem sessão iniciada para _ServerA_.
2. Partir _ServerA_, iniciar uma sessão do PowerShell remota para ligar ao _ServerB_.
3. Um comando a executar num _ServerB_ por meio de sua comunicação remota do PowerShell tenta acessar um recurso da sessão _ServerC_.
4. Aceder ao recurso no _ServerC_ é negado porque as credenciais que utilizou para criar a sessão de comunicação remota do PowerShell não são passadas da _ServerB_ para _ServerC_.

Existem várias formas de resolver esse problema. Neste tópico, vamos examinar várias das soluções mais populares para o segundo problema de salto.

## <a name="credssp"></a>CredSSP

Pode utilizar o [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) para autenticação. CredSSP coloca em cache as credenciais no servidor remoto (_ServerB_), por isso deixa utilizá-lo até ataques de roubo de credenciais. Se o computador remoto for comprometido, o atacante tem acesso às credenciais do utilizador. CredSSP está desativada por predefinição nos computadores cliente e servidor. Deve ativar o CredSSP apenas nos ambientes de maior confiança. Por exemplo, um administrador de domínio ligar a um controlador de domínio, uma vez que o controlador de domínio é altamente fidedigno.

Para obter mais informações sobre as questões de segurança ao utilizar CredSSP para comunicação remota do PowerShell, consulte [Sabotage acidental: Tome cuidado com CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).

Para obter mais informações sobre os ataques de roubo de credenciais, consulte [ataques Mitigating Pass-the-Hash (PtH) e outros roubos de credenciais](https://www.microsoft.com/en-us/download/details.aspx?id=36036).

Para obter um exemplo de como ativar e utilizar CredSSP para comunicação remota do PowerShell, consulte [utilizar CredSSP para resolver o problema de segundo salto](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).

### <a name="pros"></a>Profissionais de TI

- Funciona para todos os servidores com o Windows Server 2008 ou posterior.

### <a name="cons"></a>Contras

- Tem a vulnerabilidades de segurança.
- Requer a configuração das funções do cliente e servidor.

## <a name="kerberos-delegation-unconstrained"></a>Delegação de Kerberos (restrita)

A delegação restrita de Kerberos também pode ser usado para tornar o segundo salto. No entanto, este método não proporciona nenhum controle de onde são utilizadas credenciais delegadas.

>**Nota:** Contas do Active Directory que tenham o **conta é sensível e não pode ser delegada** conjunto de propriedades não pode ser delegado. Para obter mais informações, consulte [foco na segurança: Procedendo "Conta é sensível e não pode ser delegada" para contas com privilégios](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) e [definições e as ferramentas de autenticação do Kerberos](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Profissionais de TI

- Não requer especial codificação.

### <a name="cons"></a>Contras

- Não suporta o segundo salto para o WinRM.
- Não fornece nenhum controle sobre onde as credenciais são utilizadas, criação de uma vulnerabilidade de segurança.

## <a name="kerberos-constrained-delegation"></a>Delegação restringida de Kerberos

Pode utilizar a delegação restrita herdada (não baseada em recursos) para que o segundo salto. Configurar a delegação restringida de Kerberos com a opção "Utilizar qualquer protocolo de autenticação" para permitir que a transição de protocolo.

> [!NOTE]
> Contas do Active Directory que tenham o **conta é sensível e não pode ser delegada** conjunto de propriedades não pode ser delegado. Para obter mais informações, consulte [foco na segurança: Procedendo "Conta é sensível e não pode ser delegada" para contas com privilégios](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) e [definições e as ferramentas de autenticação do Kerberos](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Profissionais de TI

- Não requer especial codificação

### <a name="cons"></a>Contras

- Não suporta o segundo salto para o WinRM.
- Tem de ser configurada no objeto do Active Directory do servidor remoto (_ServerB_).
- Limitado a um domínio. Não é possível em várias florestas ou domínios.
- Necessita de direitos para atualizar objetos e nomes de principais de serviço (SPNs).

## <a name="resource-based-kerberos-constrained-delegation"></a>Delegação restrita de Kerberos baseada em recursos

Utilizar baseada em recursos restrita de Kerberos delegação (introduzida no Windows Server 2012), configurar a delegação de credenciais no objeto server onde residem os recursos.
No segundo cenário de salto descrito acima, configura _ServerC_ para especificar a partir de onde ele aceitará delegada credenciais.

>**Nota:** Contas do Active Directory que tenham o **conta é sensível e não pode ser delegada** conjunto de propriedades não pode ser delegado. Para obter mais informações, consulte [foco na segurança: Procedendo "Conta é sensível e não pode ser delegada" para contas com privilégios](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) e [definições e as ferramentas de autenticação do Kerberos](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Profissionais de TI

- Credenciais não são armazenadas.
- Relativamente fácil de configurar utilizando cmdlets do PowerShell – não especial é necessária programação.
- Sem acesso de domínio especial é necessário.
- Funciona em domínios e florestas.
- Código do PowerShell.

### <a name="cons"></a>Contras

- Requer o Windows Server 2012 ou posterior.
- Não suporta o segundo salto para o WinRM.
- Necessita de direitos para atualizar objetos e nomes de principais de serviço (SPNs).

### <a name="example"></a>Exemplo

Vamos examinar um PowerShell de exemplo que configura o recurso de delegação restrita com base na _ServerC_ para permitir que o delegado credenciais a partir de um _ServerB_.
Este exemplo assume que todos os servidores estão com o Windows Server 2012 ou posterior, e que existe pelo menos um controlador de domínio do Windows Server 2012 cada domínio para que qualquer um dos servidores pertencem.

Antes de poder configurar a delegação restrita, tem de adicionar o `RSAT-AD-PowerShell` de funcionalidade para instalar o módulo do PowerShell do Active Directory e, em seguida, importe o módulo para a sessão:

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

O **PrincipalsAllowedToDelegateToAccount** parâmetro define o atributo de objeto do Active Directory **msDS-AllowedToActOnBehalfOfOtherIdentity**, que contém uma lista de controlo de acesso (ACL) que Especifica quais as contas que têm permissão para delegar credenciais para a conta associada (no nosso exemplo, é a conta da máquina para _servidor_).

Agora vamos configurar as variáveis que usaremos para representar os servidores:

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

WinRM (e, portanto, comunicação remota do PowerShell) é executado como a conta de computador por predefinição. Pode ver isso examinando a **StartName** propriedade do `winrm` serviço:

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

Para _ServerC_ para permitir a delegação de uma sessão de comunicação remota do PowerShell na _ServerB_, irá garantir o acesso ao definir o **PrincipalsAllowedToDelegateToAccount** parâmetro em _ServerC_ para o objeto de computador dos _ServerB_:

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

O Kerberos [Centro de distribuição de chaves (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches negado tentativas de acesso (cache negativa) durante 15 minutos. Se _ServerB_ anteriormente foi realizada uma tentativa aceder aos _ServerC_, terá de limpar a cache na _ServerB_ invocando o seguinte comando:

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

Também pode reiniciar o computador ou aguarde, pelo menos, 15 minutos para limpar a cache.

Depois de limpar a cache, com êxito pode executar código a partir _ServerA_ através de _ServerB_ para _ServerC_:

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

Neste exemplo, o `$using` variável é utilizada para efetuar a `$ServerC` variável visível para _ServerB_. Para obter mais informações sobre o `$using` variável, consulte [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).

Para permitir que vários servidores para delegar credenciais para _ServerC_, defina o valor da **PrincipalsAllowedToDelegateToAccount** parâmetro no _ServerC_ para uma matriz:

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

Se pretender disponibilizar o segundo salto entre domínios, adicione o nome de domínio completamente qualificado (FQDN) do controlador de domínio do domínio ao qual _ServerB_ pertence:

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

Para remover a capacidade de delegar credenciais para o ServerC, defina o valor do **PrincipalsAllowedToDelegateToAccount** parâmetro na _ServerC_ para `$null`:

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>Informações sobre a delegação restringida Kerberos baseada em recursos

- [Quais são as novidades na autenticação Kerberos](https://technet.microsoft.com/library/hh831747.aspx)
- [Como o Windows Server 2012 Eases a dificuldade de Kerberos a delegação restrita, parte 1](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [Como o Windows Server 2012 Eases a dificuldade de Kerberos a delegação restrita, parte 2](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [Restrita de Kerberos de noções básicas sobre delegação para implementações de Proxy de aplicações do Azure Active Directory com a autenticação integrada do Windows](https://aka.ms/kcdpaper)
- [[MS-ADA2]: Active Directory esquema atributos M2.210 atributo msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)
- [[MS-SFU]: Extensões de protocolo Kerberos: Serviço para utilizador e a delegação restrita protocolo 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)
- [Recursos com base em Kerberos delegação restrita](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [Administração remota sem a delegação restrita com PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a>PSSessionConfiguration utilizando RunAs

Pode criar uma configuração de sessão no _ServerB_ e defina seu **RunAsCredential** parâmetro.

Para obter informações sobre como utilizar PSSessionConfiguration e RunAs para resolver o segundo problema de salto, consulte [outra solução para a comunicação remota do PowerShell multi-HOP](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).

### <a name="pros"></a>Profissionais de TI

- Funciona com qualquer servidor com o WMF 3.0 ou posterior.

### <a name="cons"></a>Contras

- Requer a configuração de **PSSessionConfiguration** e **RunAs** em cada servidor intermediário (_ServerB_).
- Precisa de manutenção de palavra-passe ao utilizar um domínio **RunAs** conta

## <a name="just-enough-administration-jea"></a>Administração JEA (Just Enough Administration)

JEA permite restringir quais comandos que um administrador pode executar durante uma sessão do PowerShell. Ele pode ser usado para resolver o segundo problema de salto.

Para obter informações sobre JEA, consulte [administração Just Enough](https://docs.microsoft.com/powershell/jea/overview).

### <a name="pros"></a>Profissionais de TI

- Sem manutenção de palavra-passe ao utilizar uma conta virtual.

### <a name="cons"></a>Contras

- Requer o WMF 5.0 ou posterior.
- Requer configuração em cada servidor intermediário (_ServerB_).

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Passar credenciais dentro de um bloco de script de Invoke-Command

Pode passar credenciais dentro da **ScriptBlock** parâmetro de uma chamada para o [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.

### <a name="pros"></a>Profissionais de TI

- Não necessita de configuração de servidor especiais.
- Funciona em qualquer servidor que executa o WMF 2.0 ou posterior.

### <a name="cons"></a>Contras

- Requer uma técnica de código complicado.
- Se executar o WMF 2.0, requer uma sintaxe diferente para a passagem de argumentos para uma sessão remota.

### <a name="example"></a>Exemplo

O exemplo seguinte mostra como passar credenciais numa **Invoke-Command** bloco de script:

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
