---
ms.date: 07/10/2019
keywords: Jea, PowerShell, segurança
title: Pré-requisitos do JEA
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017938"
---
# <a name="prerequisites"></a><span data-ttu-id="9e453-103">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9e453-103">Prerequisites</span></span>

<span data-ttu-id="9e453-104">Apenas administração suficiente é um recurso incluído no PowerShell 5,0 e superior.</span><span class="sxs-lookup"><span data-stu-id="9e453-104">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="9e453-105">Este artigo descreve os pré-requisitos que devem ser satisfeitos para começar a usar o JEA.</span><span class="sxs-lookup"><span data-stu-id="9e453-105">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>


## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="9e453-106">Verifique qual versão do PowerShell está instalada</span><span class="sxs-lookup"><span data-stu-id="9e453-106">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="9e453-107">Para verificar qual versão do PowerShell está instalada em seu sistema, verifique a `$PSVersionTable` variável em um prompt do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e453-107">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="9e453-108">O JEA está disponível com o PowerShell 5,0 e superior.</span><span class="sxs-lookup"><span data-stu-id="9e453-108">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="9e453-109">Para obter funcionalidade completa, é recomendável que você instale a versão mais recente do PowerShell disponível para seu sistema.</span><span class="sxs-lookup"><span data-stu-id="9e453-109">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="9e453-110">A tabela a seguir descreve a disponibilidade do JEA no Windows Server:</span><span class="sxs-lookup"><span data-stu-id="9e453-110">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="9e453-111">Sistema operacional do servidor</span><span class="sxs-lookup"><span data-stu-id="9e453-111">Server Operating System</span></span> |                <span data-ttu-id="9e453-112">Disponibilidade do JEA</span><span class="sxs-lookup"><span data-stu-id="9e453-112">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="9e453-113">Windows Server 2016 +</span><span class="sxs-lookup"><span data-stu-id="9e453-113">Windows Server 2016+</span></span>    | <span data-ttu-id="9e453-114">Pré-instalado</span><span class="sxs-lookup"><span data-stu-id="9e453-114">Preinstalled</span></span>                                   |
| <span data-ttu-id="9e453-115">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="9e453-115">Windows Server 2012 R2</span></span>  | <span data-ttu-id="9e453-116">Funcionalidade completa com o WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="9e453-116">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="9e453-117">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="9e453-117">Windows Server 2012</span></span>     | <span data-ttu-id="9e453-118">Funcionalidade completa com o WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="9e453-118">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="9e453-119">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="9e453-119">Windows Server 2008 R2</span></span>  | <span data-ttu-id="9e453-120">Funcionalidade reduzida<sup>1</sup> com o WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="9e453-120">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="9e453-121">Você também pode usar o JEA em seu computador doméstico ou de trabalho:</span><span class="sxs-lookup"><span data-stu-id="9e453-121">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="9e453-122">Sistema operacional do cliente</span><span class="sxs-lookup"><span data-stu-id="9e453-122">Client Operating System</span></span> |                   <span data-ttu-id="9e453-123">Disponibilidade do JEA</span><span class="sxs-lookup"><span data-stu-id="9e453-123">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="9e453-124">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="9e453-124">Windows 10 1607+</span></span>        | <span data-ttu-id="9e453-125">Pré-instalado</span><span class="sxs-lookup"><span data-stu-id="9e453-125">Preinstalled</span></span>                                         |
| <span data-ttu-id="9e453-126">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="9e453-126">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="9e453-127">Pré-instalado, com funcionalidade reduzida<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="9e453-127">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="9e453-128">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="9e453-128">Windows 10 1507</span></span>         | <span data-ttu-id="9e453-129">Não disponível</span><span class="sxs-lookup"><span data-stu-id="9e453-129">Not available</span></span>                                        |
| <span data-ttu-id="9e453-130">Windows 8, 8,1</span><span class="sxs-lookup"><span data-stu-id="9e453-130">Windows 8, 8.1</span></span>          | <span data-ttu-id="9e453-131">Funcionalidade completa com o WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="9e453-131">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="9e453-132">Windows 7</span><span class="sxs-lookup"><span data-stu-id="9e453-132">Windows 7</span></span>               | <span data-ttu-id="9e453-133">Funcionalidade reduzida<sup>1</sup> com o WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="9e453-133">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="9e453-134"><sup>1</sup> Jea não pode ser configurada para usar contas de serviço gerenciadas por grupo no windows Server 2008 R2 ou no Windows 7.</span><span class="sxs-lookup"><span data-stu-id="9e453-134"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="9e453-135">Há suporte para contas virtuais e outros recursos do Jea.</span><span class="sxs-lookup"><span data-stu-id="9e453-135">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="9e453-136"><sup>2</sup> os seguintes recursos de Jea não têm suporte no Windows 10 versões 1511 e 1603:</span><span class="sxs-lookup"><span data-stu-id="9e453-136"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="9e453-137">Executando como uma conta de serviço gerenciado por grupo</span><span class="sxs-lookup"><span data-stu-id="9e453-137">Running as a group-managed service account</span></span>
  - <span data-ttu-id="9e453-138">Regras de acesso condicional em configurações de sessão</span><span class="sxs-lookup"><span data-stu-id="9e453-138">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="9e453-139">A unidade do usuário</span><span class="sxs-lookup"><span data-stu-id="9e453-139">The user drive</span></span>
  - <span data-ttu-id="9e453-140">Concedendo acesso a contas de usuário local</span><span class="sxs-lookup"><span data-stu-id="9e453-140">Granting access to local user accounts</span></span>

  <span data-ttu-id="9e453-141">Para obter suporte para esses recursos, atualize o Windows para a versão 1607 (atualização de aniversário) ou superior.</span><span class="sxs-lookup"><span data-stu-id="9e453-141">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="9e453-142">Instalar o Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="9e453-142">Install Windows Management Framework</span></span>

<span data-ttu-id="9e453-143">Se você estiver executando uma versão mais antiga do PowerShell, talvez seja necessário atualizar seu sistema com a atualização mais recente do WMF (Windows Management Framework).</span><span class="sxs-lookup"><span data-stu-id="9e453-143">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="9e453-144">Para obter mais informações, consulte a [documentação do WMF](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="9e453-144">For more information, see the [WMF documentation](/powershell/wmf/overview).</span></span>

<span data-ttu-id="9e453-145">É recomendável que você teste a compatibilidade da sua carga de trabalho com o WMF antes de atualizar todos os servidores.</span><span class="sxs-lookup"><span data-stu-id="9e453-145">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="9e453-146">Os usuários do Windows 10 devem instalar as atualizações de recursos mais recentes para obter a versão atual do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e453-146">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="9e453-147">Habilitar a comunicação remota do PowerShell</span><span class="sxs-lookup"><span data-stu-id="9e453-147">Enable PowerShell Remoting</span></span>

<span data-ttu-id="9e453-148">A comunicação remota do PowerShell fornece a base na qual o JEA é criado.</span><span class="sxs-lookup"><span data-stu-id="9e453-148">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="9e453-149">É necessário garantir que a comunicação remota do PowerShell esteja habilitada e protegida corretamente antes de poder usar o JEA.</span><span class="sxs-lookup"><span data-stu-id="9e453-149">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="9e453-150">Para obter mais informações, consulte [segurança do WinRM](/powershell/scripting/learn/remoting/winrmsecurity).</span><span class="sxs-lookup"><span data-stu-id="9e453-150">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="9e453-151">A comunicação remota do PowerShell é habilitada por padrão no Windows Server 2012, 2012 R2 e 2016.</span><span class="sxs-lookup"><span data-stu-id="9e453-151">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="9e453-152">Você pode habilitar a comunicação remota do PowerShell executando o seguinte comando em uma janela do PowerShell com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="9e453-152">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="9e453-153">Habilitar o módulo do PowerShell e o log de bloco de script (opcional)</span><span class="sxs-lookup"><span data-stu-id="9e453-153">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="9e453-154">As etapas a seguir habilitam o registro em log para todas as ações do PowerShell em seu sistema.</span><span class="sxs-lookup"><span data-stu-id="9e453-154">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="9e453-155">O log de módulo do PowerShell não é necessário para JEA, no entanto, é recomendável ativar o registro em log para garantir que os comandos executados pelos usuários sejam registrados em um local central.</span><span class="sxs-lookup"><span data-stu-id="9e453-155">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="9e453-156">Você pode configurar a política de log do módulo do PowerShell usando Política de Grupo.</span><span class="sxs-lookup"><span data-stu-id="9e453-156">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="9e453-157">Abrir o Editor de Política de Grupo Local em uma estação de trabalho ou um objeto de Política de Grupo no Console de Gerenciamento de Política de Grupo em um controlador de Domínio do Active Directory</span><span class="sxs-lookup"><span data-stu-id="9e453-157">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="9e453-158">Navegue até **configuração\\do computador\\modelos administrativos componentes\\do Windows Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="9e453-158">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="9e453-159">Clique duas vezes em **Ativar registro em log de módulo**</span><span class="sxs-lookup"><span data-stu-id="9e453-159">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="9e453-160">Clique em **habilitado**</span><span class="sxs-lookup"><span data-stu-id="9e453-160">Click **Enabled**</span></span>
5. <span data-ttu-id="9e453-161">Na seção Opções, clique em **Mostrar** ao lado de nomes de módulo</span><span class="sxs-lookup"><span data-stu-id="9e453-161">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="9e453-162">Digite `*` a janela pop-up para registrar comandos de todos os módulos.</span><span class="sxs-lookup"><span data-stu-id="9e453-162">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="9e453-163">Clique em **OK** para definir a política</span><span class="sxs-lookup"><span data-stu-id="9e453-163">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="9e453-164">Clique duas vezes em **ativar o log de bloco de script do PowerShell**</span><span class="sxs-lookup"><span data-stu-id="9e453-164">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="9e453-165">Clique em **habilitado**</span><span class="sxs-lookup"><span data-stu-id="9e453-165">Click **Enabled**</span></span>
10. <span data-ttu-id="9e453-166">Clique em **OK** para definir a política</span><span class="sxs-lookup"><span data-stu-id="9e453-166">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="9e453-167">(Somente em computadores ingressados no domínio) Executar `gpupdate` ou aguardar política de grupo processar a política atualizada e aplicar as configurações</span><span class="sxs-lookup"><span data-stu-id="9e453-167">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="9e453-168">Você também pode habilitar a transcrição do PowerShell em todo o sistema por meio de Política de Grupo.</span><span class="sxs-lookup"><span data-stu-id="9e453-168">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9e453-169">Próximos passos</span><span class="sxs-lookup"><span data-stu-id="9e453-169">Next steps</span></span>

[<span data-ttu-id="9e453-170">Criar um arquivo de capacidade de função</span><span class="sxs-lookup"><span data-stu-id="9e453-170">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="9e453-171">Criar um arquivo de configuração de sessão</span><span class="sxs-lookup"><span data-stu-id="9e453-171">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="9e453-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e453-172">See also</span></span>

[<span data-ttu-id="9e453-173">Segurança do WinRM</span><span class="sxs-lookup"><span data-stu-id="9e453-173">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="9e453-174">PowerShell ♥ equipe azul</span><span class="sxs-lookup"><span data-stu-id="9e453-174">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
