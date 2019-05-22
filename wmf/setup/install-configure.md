---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: keithb
title: Instalar e configurar o WMF 5.1
ms.openlocfilehash: cb223844c2a214846e7206bcb476fac9154fda4b
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856148"
---
# <a name="install-and-configure-wmf-51"></a><span data-ttu-id="13e11-103">Instalar e configurar o WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="13e11-103">Install and Configure WMF 5.1</span></span>

> [!IMPORTANT]
> <span data-ttu-id="13e11-104">WMF 5.0 é substituído pelo WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="13e11-104">WMF 5.0 is superseded by WMF 5.1.</span></span> <span data-ttu-id="13e11-105">Os utilizadores com o WMF 5.0 tem de atualizar para o WMF 5.1 para receber suporte.</span><span class="sxs-lookup"><span data-stu-id="13e11-105">Users with WMF 5.0 must upgrade to WMF 5.1 to receive support.</span></span>
> <span data-ttu-id="13e11-106">**WMF 5.1 requer o .NET Framework 4.5.2** (ou superior).</span><span class="sxs-lookup"><span data-stu-id="13e11-106">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="13e11-107">Instalação será concluída com êxito, mas os principais recursos irão falhar se a .NET 4.5.2 (ou superior) não está instalado.</span><span class="sxs-lookup"><span data-stu-id="13e11-107">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span>

## <a name="download-and-install-the-wmf-51-package"></a><span data-ttu-id="13e11-108">Transfira e instale o pacote do WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="13e11-108">Download and install the WMF 5.1 package</span></span>

<span data-ttu-id="13e11-109">Transferir o pacote de WMF 5.1 para o sistema operativo e a arquitetura que deseja instalá-lo em:</span><span class="sxs-lookup"><span data-stu-id="13e11-109">Download the WMF 5.1 package for the operating system and architecture you wish to install it on:</span></span>

| <span data-ttu-id="13e11-110">Sistema Operativo</span><span class="sxs-lookup"><span data-stu-id="13e11-110">Operating System</span></span>       | <span data-ttu-id="13e11-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="13e11-111">Prerequisites</span></span>           | <span data-ttu-id="13e11-112">Ligações de pacote</span><span class="sxs-lookup"><span data-stu-id="13e11-112">Package Links</span></span>                          |
|------------------------|-------------------------|----------------------------------------|
| <span data-ttu-id="13e11-113">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="13e11-113">Windows Server 2012 R2</span></span> |                         | <span data-ttu-id="13e11-114">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="13e11-114">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span> |
| <span data-ttu-id="13e11-115">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="13e11-115">Windows Server 2012</span></span>    |                         | <span data-ttu-id="13e11-116">[W2K12-KB3191565-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="13e11-116">[W2K12-KB3191565-x64.msu][]</span></span>            |
| <span data-ttu-id="13e11-117">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="13e11-117">Windows Server 2008 R2</span></span> | <span data-ttu-id="13e11-118">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="13e11-118">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="13e11-119">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="13e11-119">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span>    |
| <span data-ttu-id="13e11-120">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="13e11-120">Windows 8.1</span></span>            |                         | <span data-ttu-id="13e11-121">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="13e11-121">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span></br><span data-ttu-id="13e11-122">**x86:** [Win8.1-KB3191564-x86.msu][]</span><span class="sxs-lookup"><span data-stu-id="13e11-122">**x86:** [Win8.1-KB3191564-x86.msu][]</span></span> |
| <span data-ttu-id="13e11-123">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="13e11-123">Windows 7 SP1</span></span>          | <span data-ttu-id="13e11-124">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="13e11-124">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="13e11-125">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="13e11-125">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span></br><span data-ttu-id="13e11-126">**x86:** [Win7-KB3191566-x86.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="13e11-126">**x86:** [Win7-KB3191566-x86.ZIP][]</span></span> |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

- <span data-ttu-id="13e11-133">Pré-visualização do WMF 5.1 têm de ser desinstalada antes de instalar a versão do WMF 5.1 RTM.</span><span class="sxs-lookup"><span data-stu-id="13e11-133">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="13e11-134">WMF 5.1 pode ser instalado diretamente ao longo do WMF 5.0 ou WMF 4.0.</span><span class="sxs-lookup"><span data-stu-id="13e11-134">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="13e11-135">É **não é necessário** para instalar o WMF 4.0 antes de instalar o WMF 5.1 no Windows 7 e Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="13e11-135">It is **not required** to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="13e11-136">Instale o WMF 5.1 para o Windows Server 2008 R2 e Windows 7</span><span class="sxs-lookup"><span data-stu-id="13e11-136">Install WMF 5.1 for Windows Server 2008 R2 and Windows 7</span></span>

> [!NOTE]
> <span data-ttu-id="13e11-137">Instruções de instalação para Windows Server 2008 R2 e Windows 7 foram alterados e diferem das instruções para os outros pacotes.</span><span class="sxs-lookup"><span data-stu-id="13e11-137">Installation instructions for Windows Server 2008 R2 and Windows 7 have changed, and differ from the instructions for the other packages.</span></span> <span data-ttu-id="13e11-138">Instruções de instalação para Windows Server 2012 R2, Windows Server 2012 e Windows 8.1 estão abaixo.</span><span class="sxs-lookup"><span data-stu-id="13e11-138">Installation instructions for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1 are below.</span></span>

### <a name="installing-wmf-51-on-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="13e11-139">Instalar o WMF 5.1 no Windows Server 2008 R2 e Windows 7</span><span class="sxs-lookup"><span data-stu-id="13e11-139">Installing WMF 5.1 on Windows Server 2008 R2 and Windows 7</span></span>

1. <span data-ttu-id="13e11-140">Navegue para a pasta na qual transferiu o ficheiro ZIP.</span><span class="sxs-lookup"><span data-stu-id="13e11-140">Navigate to the folder into which you downloaded the ZIP file.</span></span>

2. <span data-ttu-id="13e11-141">Com o botão direito no ficheiro ZIP e selecione "Extrair todos os...".</span><span class="sxs-lookup"><span data-stu-id="13e11-141">Right-click on the ZIP file, and select "Extract All...".</span></span> <span data-ttu-id="13e11-142">O Zip contém 2 ficheiros: um MSU e o ficheiro de script de instalação WMF5.1.PS1.</span><span class="sxs-lookup"><span data-stu-id="13e11-142">The Zip contains 2 files: an MSU and the Install-WMF5.1.PS1 script file.</span></span> <span data-ttu-id="13e11-143">Depois de descompactação o ficheiro ZIP, pode copiar o conteúdo a qualquer máquina com o Windows 7 ou Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="13e11-143">Once you have unpacked the ZIP file, you can copy the contents to any machine running Windows 7 or Windows Server 2008 R2.</span></span>

3. <span data-ttu-id="13e11-144">Depois de extrair o conteúdo do ficheiro ZIP, abra o PowerShell como administrador, em seguida, navegue para a pasta que contenha o conteúdo do ficheiro ZIP.</span><span class="sxs-lookup"><span data-stu-id="13e11-144">After extracting the ZIP file contents, open PowerShell as administrator, then navigate to the folder containing the contents of the ZIP file.</span></span>

4. <span data-ttu-id="13e11-145">Execute o script de instalação Wmf5.1.ps1 nessa pasta e siga as instruções.</span><span class="sxs-lookup"><span data-stu-id="13e11-145">Run the Install-Wmf5.1.ps1 script in that folder, and follow the instructions.</span></span> <span data-ttu-id="13e11-146">Este script irá verificar os pré-requisitos no computador local e instale o WMF 5.1 se os pré-requisitos tiverem sido cumpridos.</span><span class="sxs-lookup"><span data-stu-id="13e11-146">This script will check the prerequisites on the local machine, and install WMF 5.1 if the prerequisites have been met.</span></span> <span data-ttu-id="13e11-147">Os pré-requisitos estão listados abaixo.</span><span class="sxs-lookup"><span data-stu-id="13e11-147">The prerequisites are listed below.</span></span>

   <span data-ttu-id="13e11-148">Instalação WMF5.1.ps1 precisa dos seguintes parâmetros para facilitar a automatizar a instalação no Windows Server 2008 R2 e Windows 7:</span><span class="sxs-lookup"><span data-stu-id="13e11-148">Install-WMF5.1.ps1 takes the following parameters to ease automating the installation on Windows Server 2008 R2 and Windows 7:</span></span>

   - <span data-ttu-id="13e11-149">AcceptEula: Quando este parâmetro está incluído, o EULA automaticamente é aceite e não será apresentado.</span><span class="sxs-lookup"><span data-stu-id="13e11-149">AcceptEula: When this parameter is included, the EULA is automatically accepted and will not be displayed.</span></span>
   - <span data-ttu-id="13e11-150">AllowRestart: Este parâmetro só pode ser utilizado se não for especificado AcceptEula.</span><span class="sxs-lookup"><span data-stu-id="13e11-150">AllowRestart: This parameter can only be used if AcceptEula is specified.</span></span> <span data-ttu-id="13e11-151">Se este parâmetro está incluído e é necessário um reinício após a instalação do WMF 5.1, irá ocorrer o reinício sem pedir confirmação imediatamente após a instalação estiver concluída.</span><span class="sxs-lookup"><span data-stu-id="13e11-151">If this parameter is included, and a restart is required after installing WMF 5.1, the restart will happen without prompting immediately after the installation is completed.</span></span>

### <a name="wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a><span data-ttu-id="13e11-152">WMF 5.1 pré-requisitos para o Windows Server 2008 R2 SP1 e Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="13e11-152">WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1</span></span>

<span data-ttu-id="13e11-153">Instalação do WMF 5.1 no Windows Server 2008 R2 SP1 ou Windows 7 SP1, necessita do seguinte:</span><span class="sxs-lookup"><span data-stu-id="13e11-153">Installation of WMF 5.1 on either Windows Server 2008 R2 SP1 or Windows 7 SP1, requires the following:</span></span>

- <span data-ttu-id="13e11-154">Deve ser instalado o service pack mais recente.</span><span class="sxs-lookup"><span data-stu-id="13e11-154">Latest service pack must be installed.</span></span>
- <span data-ttu-id="13e11-155">WMF 3.0 **não podem** ser instalado.</span><span class="sxs-lookup"><span data-stu-id="13e11-155">WMF 3.0 **must not** be installed.</span></span> <span data-ttu-id="13e11-156">Instalação do WMF 5.1 ao longo do WMF 3.0 resultará na perda de PSModulePath, que pode fazer com que outros aplicativos efetuar a ativação.</span><span class="sxs-lookup"><span data-stu-id="13e11-156">Installing WMF 5.1 over WMF 3.0 will result in the loss of the PSModulePath, which can cause other applications to fail.</span></span> <span data-ttu-id="13e11-157">Antes de instalar o WMF 5.1, tem do desinstalar WMF 3.0, ou guardar o PSModulePath e, em seguida, restaurá-lo manualmente após a conclusão da instalação do WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="13e11-157">Before installing WMF 5.1, you must either un-install WMF 3.0, or save the PSModulePath and then restore it manually after WMF 5.1 installation is complete.</span></span>
- <span data-ttu-id="13e11-158">WMF 5.1 requer pelo menos [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642).</span><span class="sxs-lookup"><span data-stu-id="13e11-158">WMF 5.1 requires at least [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642).</span></span>
  <span data-ttu-id="13e11-159">Pode instalar o Microsoft .NET Framework 4.5.2 ao seguir as instruções na localização de transferência.</span><span class="sxs-lookup"><span data-stu-id="13e11-159">You can install Microsoft .NET Framework 4.5.2 by following the instructions at the download location.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="13e11-160">Dependência de WinRM</span><span class="sxs-lookup"><span data-stu-id="13e11-160">WinRM Dependency</span></span>

<span data-ttu-id="13e11-161">Windows PowerShell Desired State Configuration (DSC) depende de WinRM.</span><span class="sxs-lookup"><span data-stu-id="13e11-161">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="13e11-162">WinRM não está ativado por padrão no Windows Server 2008 R2 e Windows 7.</span><span class="sxs-lookup"><span data-stu-id="13e11-162">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="13e11-163">Executar `Set-WSManQuickConfig`, no Windows PowerShell elevados sessão, para ativar o WinRM.</span><span class="sxs-lookup"><span data-stu-id="13e11-163">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a><span data-ttu-id="13e11-164">Instale o WMF 5.1 para o Windows Server 2012 R2, Windows Server 2012 e Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="13e11-164">Install WMF 5.1 for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1</span></span>

### <a name="install-from-windows-file-explorer"></a><span data-ttu-id="13e11-165">Instalar a partir do Explorador de ficheiros do Windows</span><span class="sxs-lookup"><span data-stu-id="13e11-165">Install from Windows File Explorer</span></span>

1. <span data-ttu-id="13e11-166">Navegue para a pasta na qual transferiu o ficheiro MSU.</span><span class="sxs-lookup"><span data-stu-id="13e11-166">Navigate to the folder into which you downloaded the MSU file.</span></span>
2. <span data-ttu-id="13e11-167">Faça duplo clique MSU executá-lo.</span><span class="sxs-lookup"><span data-stu-id="13e11-167">Double-click the MSU to run it.</span></span>

### <a name="installing-from-the-command-prompt"></a><span data-ttu-id="13e11-168">Instalar a partir da linha de comandos</span><span class="sxs-lookup"><span data-stu-id="13e11-168">Installing from the Command Prompt</span></span>

1. <span data-ttu-id="13e11-169">Depois de transferir o pacote correto para a arquitetura do seu computador, abra uma janela de linha de comandos com direitos de utilizador elevados (executar como administrador).</span><span class="sxs-lookup"><span data-stu-id="13e11-169">After downloading the correct package for your computer's architecture, open a Command Prompt window with elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="13e11-170">Sobre as opções de instalação Server Core do Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1, linha de comandos é aberta com direitos de utilizador elevados por predefinição.</span><span class="sxs-lookup"><span data-stu-id="13e11-170">On the Server Core installation options of Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1, Command Prompt opens with elevated user rights by default.</span></span>
2. <span data-ttu-id="13e11-171">Altere os diretórios para a pasta em que tiver transferido ou copiado o pacote de instalação do WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="13e11-171">Change directories to the folder into which you have downloaded or copied the WMF 5.1 installation package.</span></span>
3. <span data-ttu-id="13e11-172">Execute um dos seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="13e11-172">Run one of the following commands:</span></span>
   - <span data-ttu-id="13e11-173">Nos computadores que executem Windows Server 2012 R2 ou Windows 8.1 x64, execute `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="13e11-173">On computers that are running Windows Server 2012 R2 or Windows 8.1 x64, run `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="13e11-174">Nos computadores que executem Windows Server 2012, execute `W2K12-KB3191565-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="13e11-174">On computers that are running Windows Server 2012, run `W2K12-KB3191565-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="13e11-175">Nos computadores que estejam a executar o Windows 8.1 x86, execute `Win8.1-KB3191564-x86.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="13e11-175">On computers that are running Windows 8.1 x86, run `Win8.1-KB3191564-x86.msu /quiet`.</span></span>

> [!NOTE]
> <span data-ttu-id="13e11-176">A instalação de WMF 5.1 requer um reinício.</span><span class="sxs-lookup"><span data-stu-id="13e11-176">Installing WMF 5.1 requires a reboot.</span></span> <span data-ttu-id="13e11-177">Usando o `/quiet` opção irá reiniciar o sistema sem aviso.</span><span class="sxs-lookup"><span data-stu-id="13e11-177">Using the `/quiet` option will reboot the system without warning.</span></span> <span data-ttu-id="13e11-178">Utilize o `/norestart` opção para evitar o reinício.</span><span class="sxs-lookup"><span data-stu-id="13e11-178">Use the `/norestart` option to avoid rebooting.</span></span> <span data-ttu-id="13e11-179">No entanto, WMF 5.1 não será instalado até que foram reiniciados.</span><span class="sxs-lookup"><span data-stu-id="13e11-179">However, WMF 5.1 will not be installed until you have rebooted.</span></span>