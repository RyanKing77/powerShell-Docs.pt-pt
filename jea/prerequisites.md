---
ms.date: 07/10/2019
keywords: jea, powershell, segurança
title: Pré-requisitos JEA
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734287"
---
# <a name="prerequisites"></a><span data-ttu-id="92109-103">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="92109-103">Prerequisites</span></span>

<span data-ttu-id="92109-104">Administração just Enough é uma funcionalidade incluída no PowerShell 5.0 e superior.</span><span class="sxs-lookup"><span data-stu-id="92109-104">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="92109-105">Este artigo descreve os pré-requisitos que devem ser satisfeitos para começar a utilizar a JEA.</span><span class="sxs-lookup"><span data-stu-id="92109-105">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>


## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="92109-106">Verifique qual é a versão do PowerShell está instalada</span><span class="sxs-lookup"><span data-stu-id="92109-106">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="92109-107">Para verificar a versão do PowerShell está instalada no seu sistema, verifique o `$PSVersionTable` variável numa linha de comandos do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="92109-107">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="92109-108">JEA está disponível com o PowerShell 5.0 e superior.</span><span class="sxs-lookup"><span data-stu-id="92109-108">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="92109-109">Para todas as funcionalidades, recomenda-se que instale a versão mais recente do PowerShell disponível para o seu sistema.</span><span class="sxs-lookup"><span data-stu-id="92109-109">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="92109-110">A tabela seguinte descreve a disponibilidade da JEA no Windows Server:</span><span class="sxs-lookup"><span data-stu-id="92109-110">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="92109-111">Sistema operativo do servidor</span><span class="sxs-lookup"><span data-stu-id="92109-111">Server Operating System</span></span> |                <span data-ttu-id="92109-112">Disponibilidade JEA</span><span class="sxs-lookup"><span data-stu-id="92109-112">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="92109-113">Windows Server 2016+</span><span class="sxs-lookup"><span data-stu-id="92109-113">Windows Server 2016+</span></span>    | <span data-ttu-id="92109-114">Pré-instalados</span><span class="sxs-lookup"><span data-stu-id="92109-114">Preinstalled</span></span>                                   |
| <span data-ttu-id="92109-115">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="92109-115">Windows Server 2012 R2</span></span>  | <span data-ttu-id="92109-116">Todas as funcionalidades com o WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="92109-116">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="92109-117">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="92109-117">Windows Server 2012</span></span>     | <span data-ttu-id="92109-118">Todas as funcionalidades com o WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="92109-118">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="92109-119">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="92109-119">Windows Server 2008 R2</span></span>  | <span data-ttu-id="92109-120">Funcionalidades reduzidas<sup>1</sup> com o WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="92109-120">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="92109-121">Também pode utilizar a JEA no seu computador doméstica ou de trabalho:</span><span class="sxs-lookup"><span data-stu-id="92109-121">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="92109-122">Sistema operativo do cliente</span><span class="sxs-lookup"><span data-stu-id="92109-122">Client Operating System</span></span> |                   <span data-ttu-id="92109-123">Disponibilidade JEA</span><span class="sxs-lookup"><span data-stu-id="92109-123">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="92109-124">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="92109-124">Windows 10 1607+</span></span>        | <span data-ttu-id="92109-125">Pré-instalados</span><span class="sxs-lookup"><span data-stu-id="92109-125">Preinstalled</span></span>                                         |
| <span data-ttu-id="92109-126">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="92109-126">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="92109-127">Pré-instalado, com funcionalidades reduzidas<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="92109-127">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="92109-128">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="92109-128">Windows 10 1507</span></span>         | <span data-ttu-id="92109-129">Não disponível</span><span class="sxs-lookup"><span data-stu-id="92109-129">Not available</span></span>                                        |
| <span data-ttu-id="92109-130">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="92109-130">Windows 8, 8.1</span></span>          | <span data-ttu-id="92109-131">Todas as funcionalidades com o WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="92109-131">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="92109-132">Windows 7</span><span class="sxs-lookup"><span data-stu-id="92109-132">Windows 7</span></span>               | <span data-ttu-id="92109-133">Funcionalidades reduzidas<sup>1</sup> com o WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="92109-133">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="92109-134"><sup>1</sup> JEA não pode ser configurado para utilizar contas de serviço gerida de grupo no Windows Server 2008 R2 ou Windows 7.</span><span class="sxs-lookup"><span data-stu-id="92109-134"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="92109-135">Contas virtuais e outros recursos JEA *são* suportado.</span><span class="sxs-lookup"><span data-stu-id="92109-135">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="92109-136"><sup>2</sup> as seguintes funcionalidades JEA não são suportadas em versões do Windows 10 1511 e 1603:</span><span class="sxs-lookup"><span data-stu-id="92109-136"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="92109-137">Em execução como uma conta de serviço gerida de grupo</span><span class="sxs-lookup"><span data-stu-id="92109-137">Running as a group-managed service account</span></span>
  - <span data-ttu-id="92109-138">Regras de acesso condicional em configurações de sessão</span><span class="sxs-lookup"><span data-stu-id="92109-138">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="92109-139">A unidade de utilizador</span><span class="sxs-lookup"><span data-stu-id="92109-139">The user drive</span></span>
  - <span data-ttu-id="92109-140">Conceder acesso a contas de utilizador local</span><span class="sxs-lookup"><span data-stu-id="92109-140">Granting access to local user accounts</span></span>

  <span data-ttu-id="92109-141">Para obter suporte para estas funcionalidades, atualizar o Windows para a versão 1607 (atualização de aniversário) ou superior.</span><span class="sxs-lookup"><span data-stu-id="92109-141">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="92109-142">Instalar o Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="92109-142">Install Windows Management Framework</span></span>

<span data-ttu-id="92109-143">Se estiver a executar uma versão mais antiga do PowerShell, terá de atualizar o sistema com a atualização mais recente do Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="92109-143">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="92109-144">Para obter mais informações, consulte a [documentação de WMF](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="92109-144">For more information, see the [WMF documentation](/powershell/wmf/overview).</span></span>

<span data-ttu-id="92109-145">Recomenda-se que teste a compatibilidade de sua carga de trabalho com o WMF antes de atualizar todos os seus servidores.</span><span class="sxs-lookup"><span data-stu-id="92109-145">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="92109-146">Utilizadores do Windows 10 devem instalar as atualizações de funcionalidades mais recentes para obter a versão atual do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="92109-146">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="92109-147">Ativar a comunicação remota do PowerShell</span><span class="sxs-lookup"><span data-stu-id="92109-147">Enable PowerShell Remoting</span></span>

<span data-ttu-id="92109-148">Comunicação remota do PowerShell fornece a base no qual o JEA é criado.</span><span class="sxs-lookup"><span data-stu-id="92109-148">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="92109-149">É necessário garantir a comunicação remota do PowerShell está ativada e estão protegida corretamente antes de poder utilizar JEA.</span><span class="sxs-lookup"><span data-stu-id="92109-149">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="92109-150">Para obter mais informações, consulte [segurança de WinRM](/powershell/scripting/learn/remoting/winrmsecurity).</span><span class="sxs-lookup"><span data-stu-id="92109-150">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="92109-151">Comunicação remota do PowerShell está ativada por predefinição no Windows Server 2012, 2012 R2 e 2016.</span><span class="sxs-lookup"><span data-stu-id="92109-151">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="92109-152">Pode ativar a comunicação remota do PowerShell ao executar o seguinte comando numa janela elevada do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="92109-152">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="92109-153">Ativar o registo de bloco de script (opcional) e do módulo do PowerShell</span><span class="sxs-lookup"><span data-stu-id="92109-153">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="92109-154">Os seguintes passos ativam o registo para todas as ações do PowerShell no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="92109-154">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="92109-155">O registo de módulo do PowerShell não é necessário para JEA, no entanto recomenda-se ativar o registo para garantir que os utilizadores de comandos executarem são registados numa localização central.</span><span class="sxs-lookup"><span data-stu-id="92109-155">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="92109-156">Pode configurar a política de registo de módulo do PowerShell através da política de grupo.</span><span class="sxs-lookup"><span data-stu-id="92109-156">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="92109-157">Abra o Editor de diretiva de Grupo Local numa estação de trabalho ou um objeto de política de grupo na consola de gestão de política de grupo num controlador de domínio do Active Directory</span><span class="sxs-lookup"><span data-stu-id="92109-157">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="92109-158">Navegue para **configuração do computador\\modelos administrativos\\componentes do Windows\\Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="92109-158">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="92109-159">Faça duplo clique no **ativar o registo de módulo**</span><span class="sxs-lookup"><span data-stu-id="92109-159">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="92109-160">Clique em **ativada**</span><span class="sxs-lookup"><span data-stu-id="92109-160">Click **Enabled**</span></span>
5. <span data-ttu-id="92109-161">Na secção de opções, clique em **mostrar** junto aos nomes de módulos</span><span class="sxs-lookup"><span data-stu-id="92109-161">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="92109-162">Tipo de `*` na janela de pop-up para iniciar comandos a partir de todos os módulos.</span><span class="sxs-lookup"><span data-stu-id="92109-162">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="92109-163">Clique em **OK** para definir a política</span><span class="sxs-lookup"><span data-stu-id="92109-163">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="92109-164">Faça duplo clique no **ativar o registo de bloco de Script do PowerShell**</span><span class="sxs-lookup"><span data-stu-id="92109-164">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="92109-165">Clique em **ativada**</span><span class="sxs-lookup"><span data-stu-id="92109-165">Click **Enabled**</span></span>
10. <span data-ttu-id="92109-166">Clique em **OK** para definir a política</span><span class="sxs-lookup"><span data-stu-id="92109-166">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="92109-167">(No máquinas associadas a domínios apenas) Executar `gpupdate` ou aguarde pela diretiva de grupo para processar a política atualizada e aplicar as definições</span><span class="sxs-lookup"><span data-stu-id="92109-167">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="92109-168">Também pode ativar a transcrição do PowerShell de todo o sistema por meio da diretiva de grupo.</span><span class="sxs-lookup"><span data-stu-id="92109-168">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="92109-169">Passos Seguintes</span><span class="sxs-lookup"><span data-stu-id="92109-169">Next steps</span></span>

[<span data-ttu-id="92109-170">Crie um ficheiro de recurso de função</span><span class="sxs-lookup"><span data-stu-id="92109-170">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="92109-171">Criar um ficheiro de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="92109-171">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="92109-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92109-172">See also</span></span>

[<span data-ttu-id="92109-173">Segurança de WinRM</span><span class="sxs-lookup"><span data-stu-id="92109-173">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="92109-174">PowerShell ♥ a equipa de azul</span><span class="sxs-lookup"><span data-stu-id="92109-174">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
