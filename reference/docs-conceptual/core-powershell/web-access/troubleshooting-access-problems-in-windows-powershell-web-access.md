---
ms.date: 08/23/2017
keywords: PowerShell, o cmdlet
title: resolução de problemas de acesso no windows powershell web access
ms.openlocfilehash: ef476d8e386e5380cb2c9dda69180dfce8748bf4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953451"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="a7d8d-103">Resolução de Problemas de Acesso no Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="a7d8d-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="a7d8d-104">Foram atualizadas: 24 de Junho de 2013 (revisto 23 de Agosto de 2017)</span><span class="sxs-lookup"><span data-stu-id="a7d8d-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="a7d8d-105">Aplica-se a: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a7d8d-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="a7d8d-106">As secções seguintes identificam alguns problemas comuns ao tentar ligar a um computador remoto utilizando o acesso Web Windows PowerShell e inclui sugestões para resolver os problemas.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="a7d8d-107">Falha de início de sessão</span><span class="sxs-lookup"><span data-stu-id="a7d8d-107">Sign-in failure</span></span>

<span data-ttu-id="a7d8d-108">Falha pode ocorrer devido a qualquer um dos seguintes procedimentos.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="a7d8d-109">Uma regra de autorização que permita o acesso do utilizador ao computador, ou uma configuração específica de sessão no computador remoto não existe.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="a7d8d-110">Segurança de acesso Web Windows PowerShell é restrita; os utilizadores devem receber acesso explícito a computadores remotos utilizando regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="a7d8d-111">Para obter mais informações sobre como criar regras de autorização, consulte [regras de autorização e segurança funcionalidades de acesso Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="a7d8d-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="a7d8d-112">O utilizador não tem acesso autorizado ao computador de destino.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="a7d8d-113">É determinado por listas de controlo de acesso (ACL).</span><span class="sxs-lookup"><span data-stu-id="a7d8d-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="a7d8d-114">Para obter mais informações, consulte [iniciar sessão no Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), ou o blogue de equipa do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="a7d8d-115">Gestão remota do Windows PowerShell não pode ser ativada no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="a7d8d-116">Certifique-se a gestão remota está ativada no computador ao qual o utilizador está a tentar ligar.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="a7d8d-117">Para obter mais informações, consulte [como configurar o seu computador para a gestão remota](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span><span class="sxs-lookup"><span data-stu-id="a7d8d-117">For more information, see [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="a7d8d-118">Erro interno do servidor</span><span class="sxs-lookup"><span data-stu-id="a7d8d-118">Internal Server Error</span></span>

<span data-ttu-id="a7d8d-119">Quando os utilizadores tentam iniciar sessão no Windows PowerShell Web Access numa janela do Internet Explorer, é apresentada uma **erro interno do servidor** página, ou *Internet Explorer* deixa de responder.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="a7d8d-120">Este problema é específico ao Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="a7d8d-121">Causa possível</span><span class="sxs-lookup"><span data-stu-id="a7d8d-121">Possible cause</span></span>

<span data-ttu-id="a7d8d-122">Esta situação pode ocorrer a utilizadores que tenham sessão iniciada com um nome de domínio que contém carateres chineses, ou se um ou mais carateres chineses fizerem parte do nome de servidor do gateway.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="a7d8d-123">Solução</span><span class="sxs-lookup"><span data-stu-id="a7d8d-123">Workaround</span></span>

1. [<span data-ttu-id="a7d8d-124">Instalar e executar o Internet Explorer 10</span><span class="sxs-lookup"><span data-stu-id="a7d8d-124">Install and run Internet Explorer 10</span></span>](http://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. <span data-ttu-id="a7d8d-125">Alterar o Internet Explorer **modo do documento** definição *IE10* normas.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="a7d8d-126">Prima **F12** para abrir a consola de ferramentas de programador</span><span class="sxs-lookup"><span data-stu-id="a7d8d-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="a7d8d-127">No Internet Explorer 10, clique em **modo do Browser**e, em seguida, selecione *Internet Explorer 10*.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="a7d8d-128">Clique em **modo do documento**e, em seguida, clique em *IE10* normas.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="a7d8d-129">Prima **F12** novamente para fechar a consola ferramentas de programador.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="a7d8d-130">Desative a configuração automática do proxy no Internet Explorer 10.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="a7d8d-131">Clique em **ferramentas**e, em seguida, clique em **opções da Internet**.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="a7d8d-132">No **opções da Internet** caixa de diálogo a **ligações** separador, clique em **definições de LAN**.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="a7d8d-133">Limpar o **detetar automaticamente as definições** caixa de verificação.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="a7d8d-134">Clique em **OK**e, em seguida, clique em **OK** novamente para fechar o *opções da Internet* caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="a7d8d-135">Não é possível ligar a um computador de grupo de trabalho remoto</span><span class="sxs-lookup"><span data-stu-id="a7d8d-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="a7d8d-136">Se o computador de destino for um membro do grupo de trabalho, utilize a seguinte sintaxe para fornecer o nome de utilizador e inicie sessão computador: `<workgroup_name>\<user_name>`</span><span class="sxs-lookup"><span data-stu-id="a7d8d-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="a7d8d-137">Não é possível localizar ferramentas de gestão do Servidor Web (IIS), apesar da função ter sido instalada</span><span class="sxs-lookup"><span data-stu-id="a7d8d-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="a7d8d-138">Se tiver instalado o acesso Web Windows PowerShell utilizando o `Install-WindowsFeature` cmdlet, gestão tools não estão instaladas, a menos que o `-IncludeManagementTools` parâmetro é adicionado ao cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the `-IncludeManagementTools` parameter is added to the cmdlet.</span></span>

<span data-ttu-id="a7d8d-139">Por exemplo, consulte [para instalar o acesso Web Windows PowerShell utilizando cmdlets do Windows PowerShell](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="a7d8d-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="a7d8d-140">Pode adicionar a consola do Gestor de IIS e outro gestão do IIS ferramentas que necessita, ao selecionar as ferramentas num **Assistente Adicionar funções e funcionalidades** sessão que é direcionada para o servidor de gateway.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span>
<span data-ttu-id="a7d8d-141">Adicionar funções e funcionalidades assistente aberto a partir do Gestor de servidores.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="a7d8d-142">Web site do acesso Web Windows PowerShell não está acessível</span><span class="sxs-lookup"><span data-stu-id="a7d8d-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="a7d8d-143">Se a configuração de segurança avançada estiver ativada no Internet Explorer (IE ESC), pode adicionar o Web site do acesso Web Windows PowerShell à lista de sites fidedignos.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="a7d8d-144">Uma abordagem recomendada inferior, devido a riscos de segurança, é desativar IE ESC.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span>
<span data-ttu-id="a7d8d-145">Pode desativar IE ESC no mosaico propriedades na página servidor Local no Gestor de servidores.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="a7d8d-146">Ocorreu uma falha de autorização.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-146">An authorization failure occurred.</span></span> <span data-ttu-id="a7d8d-147">Certifique-se de que está autorizado para se ligar ao computador de destino.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="a7d8d-148">Ao tentar ligar ao servidor de gateway é o computador de destino e também está num grupo de trabalho, é apresentada a mensagem de erro acima.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="a7d8d-149">Quando o servidor de gateway também é o servidor de destino e faz parte de um grupo de trabalho, especifique o nome de utilizador, o nome do computador e o nome de grupo do utilizador.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span>
<span data-ttu-id="a7d8d-150">Não utilize um ponto (.) autonomamente para representar o nome do computador.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="a7d8d-151">Cenários e valores adequados</span><span class="sxs-lookup"><span data-stu-id="a7d8d-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="a7d8d-152">Todos os casos</span><span class="sxs-lookup"><span data-stu-id="a7d8d-152">All cases</span></span>

<span data-ttu-id="a7d8d-153">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a7d8d-153">Parameter</span></span> | <span data-ttu-id="a7d8d-154">Valor</span><span class="sxs-lookup"><span data-stu-id="a7d8d-154">Value</span></span>
-- | --
<span data-ttu-id="a7d8d-155">UserName</span><span class="sxs-lookup"><span data-stu-id="a7d8d-155">UserName</span></span> | <span data-ttu-id="a7d8d-156">Server\_name\\user\_name</span><span class="sxs-lookup"><span data-stu-id="a7d8d-156">Server\_name\\user\_name</span></span><br/><span data-ttu-id="a7d8d-157">Localhost\\user\_name</span><span class="sxs-lookup"><span data-stu-id="a7d8d-157">Localhost\\user\_name</span></span><br/><span data-ttu-id="a7d8d-158">. \\utilizador\_nome</span><span class="sxs-lookup"><span data-stu-id="a7d8d-158">.\\user\_name</span></span>
<span data-ttu-id="a7d8d-159">Grupo de utilizador</span><span class="sxs-lookup"><span data-stu-id="a7d8d-159">UserGroup</span></span> | <span data-ttu-id="a7d8d-160">Server\_name\\user\_group</span><span class="sxs-lookup"><span data-stu-id="a7d8d-160">Server\_name\\user\_group</span></span><br/><span data-ttu-id="a7d8d-161">Localhost\\user\_group</span><span class="sxs-lookup"><span data-stu-id="a7d8d-161">Localhost\\user\_group</span></span><br/><span data-ttu-id="a7d8d-162">. \\utilizador\_grupo</span><span class="sxs-lookup"><span data-stu-id="a7d8d-162">.\\user\_group</span></span>
<span data-ttu-id="a7d8d-163">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="a7d8d-163">ComputerGroup</span></span> | <span data-ttu-id="a7d8d-164">Server\_name\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="a7d8d-164">Server\_name\\computer\_group</span></span><br/><span data-ttu-id="a7d8d-165">Localhost\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="a7d8d-165">Localhost\\computer\_group</span></span><br/><span data-ttu-id="a7d8d-166">. \\computador\_grupo</span><span class="sxs-lookup"><span data-stu-id="a7d8d-166">.\\computer\_group</span></span>

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="a7d8d-167">Servidor de gateway está num domínio</span><span class="sxs-lookup"><span data-stu-id="a7d8d-167">Gateway server is in a domain</span></span>

<span data-ttu-id="a7d8d-168">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a7d8d-168">Parameter</span></span> | <span data-ttu-id="a7d8d-169">Valor</span><span class="sxs-lookup"><span data-stu-id="a7d8d-169">Value</span></span>
-- | --
<span data-ttu-id="a7d8d-170">ComputerName</span><span class="sxs-lookup"><span data-stu-id="a7d8d-170">ComputerName</span></span> | <span data-ttu-id="a7d8d-171">Nome completamente qualificado do servidor de gateway ou Localhost</span><span class="sxs-lookup"><span data-stu-id="a7d8d-171">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="a7d8d-172">O servidor de gateway está num grupo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a7d8d-172">Gateway server is in a workgroup</span></span>

<span data-ttu-id="a7d8d-173">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a7d8d-173">Parameter</span></span> | <span data-ttu-id="a7d8d-174">Valor</span><span class="sxs-lookup"><span data-stu-id="a7d8d-174">Value</span></span>
-- | --
<span data-ttu-id="a7d8d-175">ComputerName</span><span class="sxs-lookup"><span data-stu-id="a7d8d-175">ComputerName</span></span> | <span data-ttu-id="a7d8d-176">Nome do servidor</span><span class="sxs-lookup"><span data-stu-id="a7d8d-176">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="a7d8d-177">Credenciais de gateway</span><span class="sxs-lookup"><span data-stu-id="a7d8d-177">Gateway credentials</span></span>

<span data-ttu-id="a7d8d-178">Inicie sessão num servidor de gateway como computador de destino utilizando as credenciais formatadas através de um dos seguintes procedimentos.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-178">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- <span data-ttu-id="a7d8d-179">Server\_name\\user\_name</span><span class="sxs-lookup"><span data-stu-id="a7d8d-179">Server\_name\\user\_name</span></span>
- <span data-ttu-id="a7d8d-180">Localhost\\user\_name</span><span class="sxs-lookup"><span data-stu-id="a7d8d-180">Localhost\\user\_name</span></span>
- <span data-ttu-id="a7d8d-181">. \\utilizador\_nome</span><span class="sxs-lookup"><span data-stu-id="a7d8d-181">.\\user\_name</span></span>

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="a7d8d-182">Um identificador de segurança (SID) é apresentado numa regra de autorização</span><span class="sxs-lookup"><span data-stu-id="a7d8d-182">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="a7d8d-183">Um identificador de segurança (SID) é apresentado numa regra de autorização em vez do utilizador de sintaxe\_nome/computador\_nome.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-183">A security identifier (SID) is displayed in an authorization rule instead of the syntax user\_name/computer\_name.</span></span>

<span data-ttu-id="a7d8d-184">A regra já não é válida ou a consulta dos Serviços de Domínio do Active Directory falhou.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-184">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span>
<span data-ttu-id="a7d8d-185">Uma regra de autorização normalmente, não é válida em cenários que o servidor de gateway pertenceu num dado momento num grupo de trabalho, mas foi posteriormente associado a um domínio</span><span class="sxs-lookup"><span data-stu-id="a7d8d-185">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="a7d8d-186">Não é possível iniciar sessão com regra como um endereço IPv6 com um domínio</span><span class="sxs-lookup"><span data-stu-id="a7d8d-186">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="a7d8d-187">Não é possível iniciar sessão num computador de destino que foi especificado nas regras de autorização como um endereço IPv6 com um domínio.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-187">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="a7d8d-188">As regras de autorização não suportam um endereço IPv6 no formato de um nome de domínio.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-188">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="a7d8d-189">Para especificar um computador de destino utilizando um endereço IPv6, utilize o endereço IPv6 original (que contém dois pontos) na regra de autorização.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-189">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span>
<span data-ttu-id="a7d8d-190">O domínio e os endereços IPv6 numéricos (com dois pontos) são suportados como o nome do computador de destino na página de início de sessão de acesso Web Windows PowerShell, mas não em regras de autorização.</span><span class="sxs-lookup"><span data-stu-id="a7d8d-190">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span>

<span data-ttu-id="a7d8d-191">Para obter mais informações sobre os endereços IPv6, consulte [como IPv6 funciona](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="a7d8d-191">For more information about IPv6 addresses, see [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="a7d8d-192">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="a7d8d-192">See Also</span></span>

- <span data-ttu-id="a7d8d-193">[Regras de autorização e funcionalidades de segurança de acesso Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="a7d8d-193">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span></span>
- <span data-ttu-id="a7d8d-194">[Utilize a consola do PowerShell Windows baseada na Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="a7d8d-194">[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span></span>
- [<span data-ttu-id="a7d8d-195">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="a7d8d-195">about_Remote_Requirements</span></span>](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements)