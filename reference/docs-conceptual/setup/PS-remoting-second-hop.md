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
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="ebcba-103">Tornando-o segundo hop comunicação remota do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ebcba-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="ebcba-104">O "problema salto segundo" refere-se a uma situação como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ebcba-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="ebcba-105">Tiver sessão iniciada _ServerA_.</span><span class="sxs-lookup"><span data-stu-id="ebcba-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="ebcba-106">De _ServerA_, iniciar uma sessão de PowerShell remota para ligar ao _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="ebcba-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="ebcba-107">Um comando a executar no _ServerB_ através do seu sistema de interação remota de PowerShell tenta aceder a um recurso na sessão _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="ebcba-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="ebcba-108">Acesso ao recurso no _ServerC_ é negada, porque as credenciais utilizadas para criar a sessão de comunicação remota do PowerShell não são transmitidas do _ServerB_ para _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="ebcba-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="ebcba-109">Existem várias formas para resolver este problema.</span><span class="sxs-lookup"><span data-stu-id="ebcba-109">There are several ways to address this problem.</span></span> <span data-ttu-id="ebcba-110">Neste tópico, vamos ver várias as soluções mais populares para o problema de salto segundo.</span><span class="sxs-lookup"><span data-stu-id="ebcba-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="ebcba-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="ebcba-111">CredSSP</span></span>

<span data-ttu-id="ebcba-112">Pode utilizar o [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) para autenticação.</span><span class="sxs-lookup"><span data-stu-id="ebcba-112">You can use the [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) for authentication.</span></span> <span data-ttu-id="ebcba-113">CredSSP coloca em cache as credenciais no servidor remoto (_ServerB_), por isso, utilizá-la abre até ataques de roubo de credenciais.</span><span class="sxs-lookup"><span data-stu-id="ebcba-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="ebcba-114">Se o computador remoto for comprometido, o atacante tem acesso às credenciais do utilizador.</span><span class="sxs-lookup"><span data-stu-id="ebcba-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="ebcba-115">CredSSP está desativada por predefinição nos computadores cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="ebcba-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="ebcba-116">Deve ativar o CredSSP apenas nos ambientes de maior confiança.</span><span class="sxs-lookup"><span data-stu-id="ebcba-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="ebcba-117">Por exemplo, um administrador de domínio ligação a um controlador de domínio porque o controlador de domínio é altamente fidedigno.</span><span class="sxs-lookup"><span data-stu-id="ebcba-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="ebcba-118">Para obter mais informações sobre as questões de segurança quando utilizar o CredSSP para comunicação remota do PowerShell, consulte [sabotagem instalações acidental: cuidado com do CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span><span class="sxs-lookup"><span data-stu-id="ebcba-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="ebcba-119">Para mais informações sobre os ataques de roubo de credenciais, consulte [ataques de secção mitigação passagem do Hash (PtH) e de outros roubos de credenciais](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span><span class="sxs-lookup"><span data-stu-id="ebcba-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="ebcba-120">Para obter um exemplo de como ativar e utilizar o CredSSP para comunicação remota do PowerShell, consulte [utilizando o CredSSP para resolver o problema de Double-hop](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span><span class="sxs-lookup"><span data-stu-id="ebcba-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="ebcba-121">Vantagens</span><span class="sxs-lookup"><span data-stu-id="ebcba-121">Pros</span></span>

- <span data-ttu-id="ebcba-122">Funciona para todos os servidores com o Windows Server 2008 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="ebcba-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="ebcba-123">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="ebcba-123">Cons</span></span>

- <span data-ttu-id="ebcba-124">Tem vulnerabilidades de segurança.</span><span class="sxs-lookup"><span data-stu-id="ebcba-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="ebcba-125">Requer a configuração das funções do cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="ebcba-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="ebcba-126">Delegação de Kerberos (restrita)</span><span class="sxs-lookup"><span data-stu-id="ebcba-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="ebcba-127">A delegação restrita de Kerberos também pode ser utilizado para tornar o segundo hop.</span><span class="sxs-lookup"><span data-stu-id="ebcba-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="ebcba-128">No entanto, este método fornece sem controlo da onde são utilizadas credenciais delegadas.</span><span class="sxs-lookup"><span data-stu-id="ebcba-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="ebcba-129">**Nota:** contas do Active Directory que tenham o **conta é sensível e não pode ser delegada** não pode ser delegada a propriedade definida.</span><span class="sxs-lookup"><span data-stu-id="ebcba-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="ebcba-130">Para obter mais informações, consulte [foco de segurança: Analysing 'Conta é sensível e não pode ser delegada' para contas com privilégios](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) e [Kerberos Authentication ferramentas e definições](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="ebcba-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="ebcba-131">Vantagens</span><span class="sxs-lookup"><span data-stu-id="ebcba-131">Pros</span></span>

- <span data-ttu-id="ebcba-132">Não necessita de nenhum codificação especiais.</span><span class="sxs-lookup"><span data-stu-id="ebcba-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="ebcba-133">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="ebcba-133">Cons</span></span>

- <span data-ttu-id="ebcba-134">Não suporta o segundo hop para WinRM.</span><span class="sxs-lookup"><span data-stu-id="ebcba-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="ebcba-135">Não fornece nenhum controlo sobre em que as credenciais são utilizadas, criar uma vulnerabilidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="ebcba-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="ebcba-136">Delegação restringida de Kerberos</span><span class="sxs-lookup"><span data-stu-id="ebcba-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="ebcba-137">Pode utilizar a delegação restrita legada (não baseada em recursos) para tornar o segundo hop.</span><span class="sxs-lookup"><span data-stu-id="ebcba-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span>

><span data-ttu-id="ebcba-138">**Nota:** contas do Active Directory que tenham o **conta é sensível e não pode ser delegada** não pode ser delegada a propriedade definida.</span><span class="sxs-lookup"><span data-stu-id="ebcba-138">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="ebcba-139">Para obter mais informações, consulte [foco de segurança: Analysing 'Conta é sensível e não pode ser delegada' para contas com privilégios](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) e [Kerberos Authentication ferramentas e definições](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="ebcba-139">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="ebcba-140">Vantagens</span><span class="sxs-lookup"><span data-stu-id="ebcba-140">Pros</span></span>

- <span data-ttu-id="ebcba-141">Não necessita de nenhum codificação especiais</span><span class="sxs-lookup"><span data-stu-id="ebcba-141">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="ebcba-142">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="ebcba-142">Cons</span></span>

- <span data-ttu-id="ebcba-143">Não suporta o segundo hop para WinRM.</span><span class="sxs-lookup"><span data-stu-id="ebcba-143">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="ebcba-144">Tem de ser configurada no objeto do Active Directory do servidor remoto (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="ebcba-144">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="ebcba-145">Limitado a um domínio.</span><span class="sxs-lookup"><span data-stu-id="ebcba-145">Limited to one domain.</span></span> <span data-ttu-id="ebcba-146">Não é possível de se estender domínios ou florestas.</span><span class="sxs-lookup"><span data-stu-id="ebcba-146">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="ebcba-147">Necessita de direitos para atualizar objetos e nomes de principais de serviço (SPNs).</span><span class="sxs-lookup"><span data-stu-id="ebcba-147">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="ebcba-148">Delegação restrita de Kerberos baseada em recursos</span><span class="sxs-lookup"><span data-stu-id="ebcba-148">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="ebcba-149">Utilizar baseada em recursos restrita de Kerberos delegação (introduzida no Windows Server 2012), configurar a delegação de credenciais no objeto de servidor onde residem os recursos.</span><span class="sxs-lookup"><span data-stu-id="ebcba-149">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="ebcba-150">O segundo cenário de salto descrito acima, pode configurar _ServerC_ para especificar a partir do qual irá aceitar delegado credenciais.</span><span class="sxs-lookup"><span data-stu-id="ebcba-150">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="ebcba-151">**Nota:** contas do Active Directory que tenham o **conta é sensível e não pode ser delegada** não pode ser delegada a propriedade definida.</span><span class="sxs-lookup"><span data-stu-id="ebcba-151">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="ebcba-152">Para obter mais informações, consulte [foco de segurança: Analysing 'Conta é sensível e não pode ser delegada' para contas com privilégios](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) e [Kerberos Authentication ferramentas e definições](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="ebcba-152">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="ebcba-153">Vantagens</span><span class="sxs-lookup"><span data-stu-id="ebcba-153">Pros</span></span>

- <span data-ttu-id="ebcba-154">As credenciais não são armazenadas.</span><span class="sxs-lookup"><span data-stu-id="ebcba-154">Credentials are not stored.</span></span>
- <span data-ttu-id="ebcba-155">Relativamente fácil de configurar utilizando cmdlets do PowerShell – sem codificação especial necessário.</span><span class="sxs-lookup"><span data-stu-id="ebcba-155">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="ebcba-156">Sem acesso de domínio especial não é necessário.</span><span class="sxs-lookup"><span data-stu-id="ebcba-156">No special domain access is required.</span></span>
- <span data-ttu-id="ebcba-157">Funciona em domínios e florestas.</span><span class="sxs-lookup"><span data-stu-id="ebcba-157">Works across domains and forests.</span></span>
- <span data-ttu-id="ebcba-158">Código do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ebcba-158">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="ebcba-159">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="ebcba-159">Cons</span></span>

- <span data-ttu-id="ebcba-160">Requer o Windows Server 2012 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="ebcba-160">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="ebcba-161">Não suporta o segundo hop para WinRM.</span><span class="sxs-lookup"><span data-stu-id="ebcba-161">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="ebcba-162">Necessita de direitos para atualizar objetos e nomes de principais de serviço (SPNs).</span><span class="sxs-lookup"><span data-stu-id="ebcba-162">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="ebcba-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ebcba-163">Example</span></span>

<span data-ttu-id="ebcba-164">Vamos ver um exemplo que configura recursos baseia a delegação restrita de PowerShell _ServerC_ para permitir que as credenciais de delegado de um _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="ebcba-164">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="ebcba-165">Este exemplo assume que todos os servidores são com o Windows Server 2012 ou posterior, e que existe pelo menos um controlador de domínio do Windows Server 2012 cada domínio para que qualquer um dos servidores pertencem.</span><span class="sxs-lookup"><span data-stu-id="ebcba-165">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="ebcba-166">Antes de poder configurar a delegação restrita, tem de adicionar o `RSAT-AD-PowerShell` funcionalidade para instalar o módulo PowerShell do Active Directory e, em seguida, importar esse módulo para a sua sessão:</span><span class="sxs-lookup"><span data-stu-id="ebcba-166">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="ebcba-167">Vários cmdlets disponíveis agora tem um **PrincipalsAllowedToDelegateToAccount** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="ebcba-167">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

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

<span data-ttu-id="ebcba-168">O **PrincipalsAllowedToDelegateToAccount** parâmetro define o atributo de objeto do Active Directory **msDS-AllowedToActOnBehalfOfOtherIdentity**, que contém uma lista de controlo de acesso (ACL) que Especifica quais as contas que têm autorização para delegar as credenciais para a conta associada (no nosso exemplo, será a conta de computador para _servidor_).</span><span class="sxs-lookup"><span data-stu-id="ebcba-168">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="ebcba-169">Agora vamos configurar as variáveis que iremos utilizar para representar os servidores:</span><span class="sxs-lookup"><span data-stu-id="ebcba-169">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="ebcba-170">WinRM (e, por conseguinte, comunicação remota do PowerShell) é executado como a conta de computador por predefinição.</span><span class="sxs-lookup"><span data-stu-id="ebcba-170">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="ebcba-171">Pode ver este observando a **StartName** propriedade o `winrm` serviço:</span><span class="sxs-lookup"><span data-stu-id="ebcba-171">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="ebcba-172">Para _ServerC_ para permitir a delegação de uma sessão de comunicação remota do PowerShell no _ServerB_, iremos irá conceder acesso ao definir o **PrincipalsAllowedToDelegateToAccount** parâmetro em _ServerC_ para o objeto de computador do _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="ebcba-172">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="ebcba-173">O Kerberos [Centro de distribuição de chaves (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches negado tentativas de acesso (cache negativa), para 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="ebcba-173">The Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="ebcba-174">Se _ServerB_ anteriormente tentou aceder _ServerC_, terá de limpar a cache no _ServerB_ invocando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="ebcba-174">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="ebcba-175">Também pode reiniciar o computador ou aguarde, pelo menos, 15 minutos para limpar a cache.</span><span class="sxs-lookup"><span data-stu-id="ebcba-175">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="ebcba-176">Após limpar a cache, pode executar com êxito o código de _ServerA_ através de _ServerB_ para _ServerC_:</span><span class="sxs-lookup"><span data-stu-id="ebcba-176">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="ebcba-177">Neste exemplo, o `$using` variável é utilizada para efetuar o `$ServerC` variável visível para _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="ebcba-177">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="ebcba-178">Para obter mais informações sobre o `$using` variável, consulte [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="ebcba-178">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="ebcba-179">Para permitir que vários servidores delegar as credenciais para _ServerC_, defina o valor da **PrincipalsAllowedToDelegateToAccount** parâmetro no _ServerC_ numa matriz:</span><span class="sxs-lookup"><span data-stu-id="ebcba-179">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="ebcba-180">Se pretender que o segundo hop entre domínios, adicione o nome de domínio completamente qualificado (FQDN) do controlador de domínio do domínio ao qual _ServerB_ pertence:</span><span class="sxs-lookup"><span data-stu-id="ebcba-180">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="ebcba-181">Para remover a capacidade para delegar as credenciais para ServerC, defina o valor da **PrincipalsAllowedToDelegateToAccount** parâmetro no _ServerC_ para `$null`:</span><span class="sxs-lookup"><span data-stu-id="ebcba-181">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="ebcba-182">Informações sobre a delegação restringida Kerberos baseada em recursos</span><span class="sxs-lookup"><span data-stu-id="ebcba-182">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="ebcba-183">Novidades na autenticação Kerberos</span><span class="sxs-lookup"><span data-stu-id="ebcba-183">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- [<span data-ttu-id="ebcba-184">Como o Windows Server 2012 Eases tensão de Kerberos a delegação restrita, parte 1</span><span class="sxs-lookup"><span data-stu-id="ebcba-184">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span></span>](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [<span data-ttu-id="ebcba-185">Como o Windows Server 2012 Eases tensão de Kerberos a delegação restrita, faz parte 2</span><span class="sxs-lookup"><span data-stu-id="ebcba-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span></span>](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [<span data-ttu-id="ebcba-186">Restrita de Kerberos de compreender a delegação para implementações de Proxy de aplicações do Azure Active Directory com a autenticação integrada do Windows</span><span class="sxs-lookup"><span data-stu-id="ebcba-186">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](http://aka.ms/kcdpaper)
- <span data-ttu-id="ebcba-187">[[MS-ADA2]: msDS-AllowedToActOnBehalfOfOtherIdentity de atributo do M2.210 de atributos de esquema do Active Directory](https://msdn.microsoft.com/library/hh554126.aspx)</span><span class="sxs-lookup"><span data-stu-id="ebcba-187">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span></span>
- <span data-ttu-id="ebcba-188">[[MS-SFU]: extensões de protocolo do Kerberos: serviço para utilizador e a delegação restrita protocolo 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span><span class="sxs-lookup"><span data-stu-id="ebcba-188">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span></span>
- [<span data-ttu-id="ebcba-189">Recursos com base em Kerberos a delegação restrita</span><span class="sxs-lookup"><span data-stu-id="ebcba-189">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [<span data-ttu-id="ebcba-190">Administração remota sem PrincipalsAllowedToDelegateToAccount a utilizar a delegação restrita</span><span class="sxs-lookup"><span data-stu-id="ebcba-190">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span></span>](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="ebcba-191">PSSessionConfiguration utilizando RunAs</span><span class="sxs-lookup"><span data-stu-id="ebcba-191">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="ebcba-192">Pode criar uma configuração de sessão em _ServerB_ e definir o respetivo **RunAsCredential** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ebcba-192">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="ebcba-193">Para obter informações sobre como utilizar PSSessionConfiguration e RunAs para resolver o problema de salto segundo, consulte [outra solução para comunicação remota do PowerShell multi-HOP](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span><span class="sxs-lookup"><span data-stu-id="ebcba-193">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="ebcba-194">Vantagens</span><span class="sxs-lookup"><span data-stu-id="ebcba-194">Pros</span></span>

- <span data-ttu-id="ebcba-195">Funciona com qualquer servidor com o WMF 3.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="ebcba-195">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="ebcba-196">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="ebcba-196">Cons</span></span>

- <span data-ttu-id="ebcba-197">Requer a configuração de **PSSessionConfiguration** e **RunAs** em cada servidor intermédia (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="ebcba-197">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="ebcba-198">Necessita de manutenção de palavra-passe quando utilizar um domínio **RunAs** conta</span><span class="sxs-lookup"><span data-stu-id="ebcba-198">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="ebcba-199">Administração JEA (Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="ebcba-199">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="ebcba-200">JEA permite-lhe restringir os comandos que um administrador pode ser executado durante uma sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ebcba-200">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="ebcba-201">Pode ser utilizado para resolver o problema de salto segundo.</span><span class="sxs-lookup"><span data-stu-id="ebcba-201">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="ebcba-202">Para obter informações sobre JEA, consulte [apenas suficiente administração](https://docs.microsoft.com/powershell/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="ebcba-202">For information about JEA, see [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="ebcba-203">Vantagens</span><span class="sxs-lookup"><span data-stu-id="ebcba-203">Pros</span></span>

- <span data-ttu-id="ebcba-204">Nenhuma manutenção de palavra-passe ao utilizar uma conta virtual.</span><span class="sxs-lookup"><span data-stu-id="ebcba-204">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="ebcba-205">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="ebcba-205">Cons</span></span>

- <span data-ttu-id="ebcba-206">Requer o WMF 5.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="ebcba-206">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="ebcba-207">Requer configuração em cada servidor intermédia (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="ebcba-207">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="ebcba-208">Introduzir credenciais dentro de um bloco de script de Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="ebcba-208">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="ebcba-209">Pode passar credenciais dentro de **ScriptBlock** parâmetro de uma chamada para o [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ebcba-209">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="ebcba-210">Vantagens</span><span class="sxs-lookup"><span data-stu-id="ebcba-210">Pros</span></span>

- <span data-ttu-id="ebcba-211">Não necessita de configuração de servidor especial.</span><span class="sxs-lookup"><span data-stu-id="ebcba-211">Does not require special server configuration.</span></span>
- <span data-ttu-id="ebcba-212">Funciona em qualquer servidor que executa o WMF 2.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="ebcba-212">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="ebcba-213">Desvantagens</span><span class="sxs-lookup"><span data-stu-id="ebcba-213">Cons</span></span>

- <span data-ttu-id="ebcba-214">Requer uma técnica de código awkward.</span><span class="sxs-lookup"><span data-stu-id="ebcba-214">Requires an awkward code technique.</span></span>
- <span data-ttu-id="ebcba-215">Se executar o WMF 2.0, necessita de sintaxe diferentes para passar os argumentos para uma sessão remota.</span><span class="sxs-lookup"><span data-stu-id="ebcba-215">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="ebcba-216">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ebcba-216">Example</span></span>

<span data-ttu-id="ebcba-217">O exemplo seguinte mostra como introduzir credenciais num **Invoke-Command** bloco de script:</span><span class="sxs-lookup"><span data-stu-id="ebcba-217">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="ebcba-218">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebcba-218">See also</span></span>

[<span data-ttu-id="ebcba-219">Considerações de Segurança da Comunicação Remota do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ebcba-219">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)