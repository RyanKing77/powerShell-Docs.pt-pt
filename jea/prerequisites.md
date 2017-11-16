---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea, powershell, segurança"
title: "Pré-requisitos JEA"
ms.openlocfilehash: 75d5db2ba446df1d461050d187dc1495a22fef18
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="prerequisites"></a><span data-ttu-id="bd7a9-103">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="bd7a9-103">Prerequisites</span></span>

> <span data-ttu-id="bd7a9-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bd7a9-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="bd7a9-105">Apenas suficiente administração é uma funcionalidade incluída com o Windows PowerShell 5.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-105">Just Enough Administration is a feature included with Windows PowerShell 5.0 and higher.</span></span>
<span data-ttu-id="bd7a9-106">Este tópico descreve os pré-requisitos que devem ser satisfeitos para poder começar a utilizar o JEA.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-106">This topic describes the prerequisites that must be satisfied in order to start using JEA.</span></span>

## <a name="install-jea"></a><span data-ttu-id="bd7a9-107">Instalar JEA</span><span class="sxs-lookup"><span data-stu-id="bd7a9-107">Install JEA</span></span>

<span data-ttu-id="bd7a9-108">O JEA é disponível com o Windows PowerShell 5.0 e posterior, mas para uma funcionalidade completa é recomendado que instale a versão mais recente do PowerShell disponível para o seu sistema.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-108">JEA is available with Windows PowerShell 5.0 and higher, but for full functionality it is recommended that you install the latest version of PowerShell available for your system.</span></span>
<span data-ttu-id="bd7a9-109">A tabela seguinte descreve a disponibilidade do JEA no Windows Server:</span><span class="sxs-lookup"><span data-stu-id="bd7a9-109">The following table describes JEA's availability on Windows Server:</span></span>

<span data-ttu-id="bd7a9-110">Sistema operativo do servidor</span><span class="sxs-lookup"><span data-stu-id="bd7a9-110">Server Operating System</span></span>   | <span data-ttu-id="bd7a9-111">Disponibilidade JEA</span><span class="sxs-lookup"><span data-stu-id="bd7a9-111">JEA Availability</span></span>
--------------------------|--------------------------------
<span data-ttu-id="bd7a9-112">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="bd7a9-112">Windows Server 2016</span></span>       | <span data-ttu-id="bd7a9-113">Pré-instalado</span><span class="sxs-lookup"><span data-stu-id="bd7a9-113">Preinstalled</span></span>
<span data-ttu-id="bd7a9-114">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="bd7a9-114">Windows Server 2012 R2</span></span>    | <span data-ttu-id="bd7a9-115">Funcionalidade completa com WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="bd7a9-115">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="bd7a9-116">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="bd7a9-116">Windows Server 2012</span></span>       | <span data-ttu-id="bd7a9-117">Funcionalidade completa com WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="bd7a9-117">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="bd7a9-118">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="bd7a9-118">Windows Server 2008 R2</span></span>    | <span data-ttu-id="bd7a9-119">Reduzido funcionalidade<sup>1</sup> com WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="bd7a9-119">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="bd7a9-120">Também pode utilizar o JEA no seu computador de casa ou de trabalho:</span><span class="sxs-lookup"><span data-stu-id="bd7a9-120">You can also use JEA on your home or work computer:</span></span>

<span data-ttu-id="bd7a9-121">Sistema operativo do cliente</span><span class="sxs-lookup"><span data-stu-id="bd7a9-121">Client Operating System</span></span>   | <span data-ttu-id="bd7a9-122">Disponibilidade JEA</span><span class="sxs-lookup"><span data-stu-id="bd7a9-122">JEA Availability</span></span>
--------------------------|-----------------------------------------------------
<span data-ttu-id="bd7a9-123">Windows 10 1607 +</span><span class="sxs-lookup"><span data-stu-id="bd7a9-123">Windows 10 1607+</span></span>          | <span data-ttu-id="bd7a9-124">Pré-instalado</span><span class="sxs-lookup"><span data-stu-id="bd7a9-124">Preinstalled</span></span>
<span data-ttu-id="bd7a9-125">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="bd7a9-125">Windows 10 1603, 1511</span></span>     | <span data-ttu-id="bd7a9-126">Pré-instalado, com um reduzido funcionalidade<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="bd7a9-126">Preinstalled, with reduced functionality<sup>2</sup></span></span>
<span data-ttu-id="bd7a9-127">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="bd7a9-127">Windows 10 1507</span></span>           | <span data-ttu-id="bd7a9-128">Não disponível</span><span class="sxs-lookup"><span data-stu-id="bd7a9-128">Not available</span></span>
<span data-ttu-id="bd7a9-129">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="bd7a9-129">Windows 8, 8.1</span></span>            | <span data-ttu-id="bd7a9-130">Funcionalidade completa com WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="bd7a9-130">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="bd7a9-131">Windows 7</span><span class="sxs-lookup"><span data-stu-id="bd7a9-131">Windows 7</span></span>                 | <span data-ttu-id="bd7a9-132">Reduzido funcionalidade<sup>1</sup> com WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="bd7a9-132">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="bd7a9-133"><sup>1</sup> JEA não pode ser configurado para utilizar contas de serviço geridas de grupo no Windows Server 2008 R2 ou Windows 7.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-133"><sup>1</sup> JEA cannot be configured to use group managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="bd7a9-134">As contas virtual e outras funcionalidades JEA *são* suportado.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-134">Virtual accounts and other JEA features *are* supported.</span></span>

<span data-ttu-id="bd7a9-135"><sup>2</sup> versões do Windows 10 1511 e 1603 não suportam as seguintes funcionalidades JEA: em execução como um grupo gerido a conta de serviço, as regras de acesso condicional em configurações de sessão, a unidade de utilizador e conceder acesso a contas de utilizador local.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-135"><sup>2</sup> Windows 10 versions 1511 and 1603 do not support the following JEA features: running as a group managed service account, conditional access rules in session configurations, the user drive, and granting access to local user accounts.</span></span>
<span data-ttu-id="bd7a9-136">Para obter suporte para estas funcionalidades, atualização do Windows para a versão 1607 (aniversário da atualização) ou superior.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-136">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="bd7a9-137">Verifique a versão do PowerShell está instalado</span><span class="sxs-lookup"><span data-stu-id="bd7a9-137">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="bd7a9-138">Para verificar qual é a versão do PowerShell está instalada no seu sistema, verifique o `$PSVersionTable` variável numa linha de comandos do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-138">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
PS C:\> $PSVersionTable.PSVersion

Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="bd7a9-139">Está pronto a utilizar o JEA se o *principais* versão for igual ou maior do que **5**.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-139">You are ready to use JEA if the *Major* version is equal to or greater than **5**.</span></span>
<span data-ttu-id="bd7a9-140">Para uma experiência otimizada e ter acesso a todas as funcionalidades mais recentes, recomenda-se que Atualize a versão do PowerShell **5.1** sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-140">For the best experience, and to have access to all the latest features, it is recommended that you upgrade to PowerShell version **5.1** when possible.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="bd7a9-141">Instalar o Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="bd7a9-141">Install Windows Management Framework</span></span>

<span data-ttu-id="bd7a9-142">Se estiver a executar uma versão mais antiga do PowerShell, terá de atualizar o sistema com a atualização mais recente do Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="bd7a9-142">If you are running an older version of PowerShell, you will need to update your system with the latest Windows Management Framework (WMF) update.</span></span>
<span data-ttu-id="bd7a9-143">Estão disponíveis em pacotes de atualização e uma ligação para as notas de versão mais recentes do WMF o [Centro de transferências](https://aka.ms/WMF5).</span><span class="sxs-lookup"><span data-stu-id="bd7a9-143">Update packages and a link to the latest WMF release notes are available in the [Download Center](https://aka.ms/WMF5).</span></span>

<span data-ttu-id="bd7a9-144">Recomenda-se vivamente que teste a compatibilidade da carga de trabalho com WMF antes da atualização de todos os servidores.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-144">It is strongly recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="bd7a9-145">Os utilizadores do Windows 10, devem instalar as atualizações de funcionalidade mais recentes para obter a versão atual do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-145">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="bd7a9-146">Ativar a comunicação remota do PowerShell</span><span class="sxs-lookup"><span data-stu-id="bd7a9-146">Enable PowerShell Remoting</span></span>

<span data-ttu-id="bd7a9-147">Comunicação remota do PowerShell fornece a base no qual o JEA é criada.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-147">PowerShell Remoting provides the foundation on which JEA is built.</span></span>
<span data-ttu-id="bd7a9-148">Consequentemente, é necessário para garantir a comunicação remota do PowerShell está ativada e [corretamente protegida](https://msdn.microsoft.com/en-us/powershell/scripting/setup/winrmsecurity) no seu sistema antes de poder utilizar JEA.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-148">It is therefore necessary to ensure PowerShell Remoting is enabled and [properly secured](https://msdn.microsoft.com/en-us/powershell/scripting/setup/winrmsecurity) on your system before you can use JEA.</span></span>

<span data-ttu-id="bd7a9-149">Comunicação remota do PowerShell está ativada por predefinição no Windows Server 2012, 2012 R2 e 2016.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-149">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span>
<span data-ttu-id="bd7a9-150">Pode ativar a comunicação remota do PowerShell, executando o seguinte comando numa janela elevada do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-150">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="bd7a9-151">Ativar o módulo do PowerShell e o registo de bloco de script (opcional)</span><span class="sxs-lookup"><span data-stu-id="bd7a9-151">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="bd7a9-152">Os seguintes passos ativam o registo de todas as ações de PowerShell no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-152">The following steps enable logging for all PowerShell actions on your system.</span></span>
<span data-ttu-id="bd7a9-153">O registo de módulo do PowerShell não é necessário para JEA, no entanto recomenda-se vivamente que ative-lo para garantir que os utilizadores de comandos executaram são registados numa localização central.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-153">PowerShell Module Logging is not required for JEA, however it is strongly recommended that you turn it on to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="bd7a9-154">Pode configurar a política de registo de módulo do PowerShell através da política de grupo.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-154">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="bd7a9-155">Abra o Editor de política de Grupo Local numa estação de trabalho ou um objeto de política de grupo na consola de gestão de política de grupo num controlador de domínio do Active Directory</span><span class="sxs-lookup"><span data-stu-id="bd7a9-155">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="bd7a9-156">Navegue para **configuração do computador\\modelos administrativos\\componentes do Windows\\do Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="bd7a9-156">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="bd7a9-157">Faça duplo clique em **ative o registo de módulo**</span><span class="sxs-lookup"><span data-stu-id="bd7a9-157">Double click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="bd7a9-158">Clique em **ativada**</span><span class="sxs-lookup"><span data-stu-id="bd7a9-158">Click **Enabled**</span></span>
5. <span data-ttu-id="bd7a9-159">Na secção Opções, clique em **mostrar** junto aos nomes de módulo</span><span class="sxs-lookup"><span data-stu-id="bd7a9-159">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="bd7a9-160">Tipo de "**\***" no pop de janela.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-160">Type "**\***" in the pop up window.</span></span> <span data-ttu-id="bd7a9-161">Isto dá instruções ao PowerShell para registar os comandos de todos os módulos.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-161">This instructs PowerShell to log commands from all modules.</span></span>
7. <span data-ttu-id="bd7a9-162">Clique em **OK** para definir a política</span><span class="sxs-lookup"><span data-stu-id="bd7a9-162">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="bd7a9-163">Faça duplo clique em **ativar o registo de bloco de Script do PowerShell**</span><span class="sxs-lookup"><span data-stu-id="bd7a9-163">Double click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="bd7a9-164">Clique em **ativada**</span><span class="sxs-lookup"><span data-stu-id="bd7a9-164">Click **Enabled**</span></span>
10. <span data-ttu-id="bd7a9-165">Clique em **OK** para definir a política</span><span class="sxs-lookup"><span data-stu-id="bd7a9-165">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="bd7a9-166">(No associados a um domínio máquinas apenas) Executar **gpupdate** ou aguarde pela política de grupo para processar a política e aplique as definições</span><span class="sxs-lookup"><span data-stu-id="bd7a9-166">(On domain-joined machines only) Run **gpupdate** or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="bd7a9-167">Também pode ativar transcription do PowerShell de todo sistema através da política de grupo.</span><span class="sxs-lookup"><span data-stu-id="bd7a9-167">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bd7a9-168">Próximos passos</span><span class="sxs-lookup"><span data-stu-id="bd7a9-168">Next steps</span></span>

- [<span data-ttu-id="bd7a9-169">Criar um ficheiro de capacidade de função</span><span class="sxs-lookup"><span data-stu-id="bd7a9-169">Create a role capability file</span></span>](role-capabilities.md)
- [<span data-ttu-id="bd7a9-170">Criar um ficheiro de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="bd7a9-170">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="bd7a9-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd7a9-171">See also</span></span>

- [<span data-ttu-id="bd7a9-172">Informações adicionais sobre a segurança de comunicação remota do PowerShell e WinRM</span><span class="sxs-lookup"><span data-stu-id="bd7a9-172">Additional information about PowerShell Remoting and WinRM security</span></span>](https://msdn.microsoft.com/en-us/powershell/scripting/setup/winrmsecurity)
- [<span data-ttu-id="bd7a9-173">*PowerShell ♥ a equipa azul* blogue de segurança</span><span class="sxs-lookup"><span data-stu-id="bd7a9-173">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

