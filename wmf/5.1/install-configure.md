---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
contributor: keithb
title: Instalar e configurar o WMF 5.1
ms.openlocfilehash: f58676de6f7a5c51ba586a8c607097af8e60d0c9
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2018
---
# <a name="install-and-configure-wmf-51"></a><span data-ttu-id="bb7dd-103">Instalar e configurar o WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="bb7dd-103">Install and Configure WMF 5.1</span></span> #


## <a name="download-and-install-the-wmf-51-package"></a><span data-ttu-id="bb7dd-104">Transfira e instale o pacote do WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="bb7dd-104">Download and install the WMF 5.1 package</span></span>

<span data-ttu-id="bb7dd-105">Transferir o pacote do WMF 5.1 para o sistema operativo e a arquitetura que pretende instalá-lo:</span><span class="sxs-lookup"><span data-stu-id="bb7dd-105">Download the WMF 5.1 package for the operating system and architecture you wish to install it on:</span></span>

| <span data-ttu-id="bb7dd-106">Sistema Operativo</span><span class="sxs-lookup"><span data-stu-id="bb7dd-106">Operating System</span></span>       | <span data-ttu-id="bb7dd-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="bb7dd-107">Prerequisites</span></span>           | <span data-ttu-id="bb7dd-108">Ligações de pacote</span><span class="sxs-lookup"><span data-stu-id="bb7dd-108">Package Links</span></span>                          |
|------------------------|-------------------------|----------------------------------------|
| <span data-ttu-id="bb7dd-109">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="bb7dd-109">Windows Server 2012 R2</span></span> |                         | <span data-ttu-id="bb7dd-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="bb7dd-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span> |
| <span data-ttu-id="bb7dd-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="bb7dd-111">Windows Server 2012</span></span>    |                         | <span data-ttu-id="bb7dd-112">[W2K12-KB3191565-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="bb7dd-112">[W2K12-KB3191565-x64.msu][]</span></span>            |
| <span data-ttu-id="bb7dd-113">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="bb7dd-113">Windows Server 2008 R2</span></span> | <span data-ttu-id="bb7dd-114">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="bb7dd-114">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="bb7dd-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="bb7dd-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span>    |
| <span data-ttu-id="bb7dd-116">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="bb7dd-116">Windows 8.1</span></span>            |                         | <span data-ttu-id="bb7dd-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="bb7dd-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span></br><span data-ttu-id="bb7dd-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span><span class="sxs-lookup"><span data-stu-id="bb7dd-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span></span> |
| <span data-ttu-id="bb7dd-119">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="bb7dd-119">Windows 7 SP1</span></span>          | <span data-ttu-id="bb7dd-120">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="bb7dd-120">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="bb7dd-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="bb7dd-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span></br><span data-ttu-id="bb7dd-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="bb7dd-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span></span> |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="bb7dd-129">Instalar o WMF 5.1 para Windows Server 2008 R2 e Windows 7</span><span class="sxs-lookup"><span data-stu-id="bb7dd-129">Install WMF 5.1 for Windows Server 2008 R2 and Windows 7</span></span>

> <span data-ttu-id="bb7dd-130">**Nota:** instruções de instalação para o Windows Server 2008 R2 e Windows 7 foram alterados e diferem das instruções para os outros pacotes.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-130">**Note:** Installation instructions for Windows Server 2008 R2 and Windows 7 have changed, and differ from the instructions for the other packages.</span></span> <span data-ttu-id="bb7dd-131">As instruções de instalação para o Windows Server 2012 R2, Windows Server 2012 e Windows 8.1 são abaixo.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-131">Installation instructions for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1 are below.</span></span>

<span data-ttu-id="bb7dd-132">**Instalar o WMF 5.1 no Windows Server 2008 R2 e Windows 7**</span><span class="sxs-lookup"><span data-stu-id="bb7dd-132">**Installing WMF 5.1 on Windows Server 2008 R2 and Windows 7**</span></span>

1. <span data-ttu-id="bb7dd-133">Navegue para a pasta na qual transferiu o ficheiro ZIP.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-133">Navigate to the folder into which you downloaded the ZIP file.</span></span>

2. <span data-ttu-id="bb7dd-134">Clique com o botão direito no ficheiro ZIP e selecione "Extrair todos os...".</span><span class="sxs-lookup"><span data-stu-id="bb7dd-134">Right-click on the ZIP file, and select "Extract All...".</span></span> <span data-ttu-id="bb7dd-135">Zip contém 2 ficheiros: um MSU e o ficheiro de script de instalação WMF5.1.PS1.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-135">The Zip contains 2 files: an MSU and the Install-WMF5.1.PS1 script file.</span></span>
<span data-ttu-id="bb7dd-136">Após a descompactação o ficheiro ZIP, pode copiar o conteúdo a qualquer máquina com o Windows 7 ou Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-136">Once you have unpacked the ZIP file, you can copy the contents to any machine running Windows 7 or Windows Server 2008 R2.</span></span>

3. <span data-ttu-id="bb7dd-137">Após a extrair os conteúdos do ficheiro ZIP, abra o PowerShell como administrador, em seguida, navegue para a pasta que contém o conteúdo do ficheiro ZIP.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-137">After extracting the ZIP file contents, open PowerShell as administrator, then navigate to the folder containing the contents of the ZIP file.</span></span>

4. <span data-ttu-id="bb7dd-138">Execute o script de instalação Wmf5.1.ps1 nessa pasta e siga as instruções.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-138">Run the Install-Wmf5.1.ps1 script in that folder, and follow the instructions.</span></span> <span data-ttu-id="bb7dd-139">Este script irá verificar os pré-requisitos no computador local e instale o WMF 5.1 se os pré-requisitos tiverem sido cumpridos.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-139">This script will check the prerequisites on the local machine, and install WMF 5.1 if the prerequisites have been met.</span></span> <span data-ttu-id="bb7dd-140">Os pré-requisitos estão listados abaixo.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-140">The prerequisites are listed below.</span></span>

<span data-ttu-id="bb7dd-141">Instalação WMF5.1.ps1 utiliza os parâmetros seguintes para facilitar a automatizar a instalação no Windows Server 2008 R2 e Windows 7:</span><span class="sxs-lookup"><span data-stu-id="bb7dd-141">Install-WMF5.1.ps1 takes the following parameters to ease automating the installation on Windows Server 2008 R2 and Windows 7:</span></span>

- <span data-ttu-id="bb7dd-142">AcceptEula: Quando este parâmetro é incluído, o EULA é aceite automaticamente e não será apresentado.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-142">AcceptEula: When this parameter is included, the EULA is automatically accepted and will not be displayed.</span></span>
- <span data-ttu-id="bb7dd-143">AllowRestart: Este parâmetro só pode ser utilizado se AcceptEula for especificado.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-143">AllowRestart: This parameter can only be used if AcceptEula is specified.</span></span> <span data-ttu-id="bb7dd-144">Se este parâmetro é incluído e for necessário um reinício após a instalação do WMF 5.1, o reinício acontecerá sem pedir confirmação imediatamente após a instalação estiver concluída.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-144">If this parameter is included, and a restart is required after installing WMF 5.1, the restart will happen without prompting immediately after the installation is completed.</span></span>

<span data-ttu-id="bb7dd-145">**WMF 5.1 pré-requisitos para o Windows Server 2008 R2 SP1 e Windows 7 SP1**</span><span class="sxs-lookup"><span data-stu-id="bb7dd-145">**WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1**</span></span>

<span data-ttu-id="bb7dd-146">Instalação do WMF 5.1 no Windows Server 2008 R2 SP1 ou Windows 7 SP1, necessita do seguinte:</span><span class="sxs-lookup"><span data-stu-id="bb7dd-146">Installation of WMF 5.1 on either Windows Server 2008 R2 SP1 or Windows 7 SP1, requires the following:</span></span>
- <span data-ttu-id="bb7dd-147">Deve ser instalado o service pack mais recente.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-147">Latest service pack must be installed.</span></span>
- <span data-ttu-id="bb7dd-148">WMF 3.0 **tem não** ser instalado.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-148">WMF 3.0 **must not** be installed.</span></span> <span data-ttu-id="bb7dd-149">Instalar o WMF 5.1 ao longo do WMF 3.0 resultará na perda de PSModulePath, que pode fazer com que outras aplicações falhar.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-149">Installing WMF 5.1 over WMF 3.0 will result in the loss of the PSModulePath, which can cause other applications to fail.</span></span> <span data-ttu-id="bb7dd-150">Antes de instalar o WMF 5.1, tem do desinstalar WMF 3.0, ou guardar o PSModulePath e, em seguida, restaurá-lo manualmente após a conclusão da instalação do WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-150">Before installing WMF 5.1, you must either un-install WMF 3.0, or save the PSModulePath and then restore it manually after WMF 5.1 installation is complete.</span></span>
- <span data-ttu-id="bb7dd-151">WMF 5.1 requer, pelo menos, [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span><span class="sxs-lookup"><span data-stu-id="bb7dd-151">WMF 5.1 requires at least [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span></span>
<span data-ttu-id="bb7dd-152">Pode instalar o Microsoft .NET Framework 4.5.2 ao seguir as instruções na localização de transferência.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-152">You can install Microsoft .NET Framework 4.5.2 by following the instructions at the download location.</span></span>

<span data-ttu-id="bb7dd-153">**Dependência de WinRM**</span><span class="sxs-lookup"><span data-stu-id="bb7dd-153">**WinRM Dependency**</span></span>

<span data-ttu-id="bb7dd-154">Configuração de estado pretendido do Windows PowerShell (DSC) depende do WinRM.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-154">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span>
<span data-ttu-id="bb7dd-155">WinRM não está ativado por predefinição no Windows Server 2008 R2 e Windows 7.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-155">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span>
<span data-ttu-id="bb7dd-156">Executar `Set-WSManQuickConfig`, num Windows PowerShell elevada sessão, para ativar o WinRM.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-156">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>


## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a><span data-ttu-id="bb7dd-157">Instalar o WMF 5.1 para Windows Server 2012 R2, Windows Server 2012 e Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="bb7dd-157">Install WMF 5.1 for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1</span></span>
<span data-ttu-id="bb7dd-158">**Instalar a partir do Explorador do Windows (ou o Explorador de ficheiros no Windows Server 2012 R2 ou Windows 8.1)**</span><span class="sxs-lookup"><span data-stu-id="bb7dd-158">**Install from Windows Explorer (or File Explorer in Windows Server 2012 R2 or Windows 8.1)**</span></span>

1. <span data-ttu-id="bb7dd-159">Navegue para a pasta na qual transferiu o ficheiro MSU.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-159">Navigate to the folder into which you downloaded the MSU file.</span></span>
2. <span data-ttu-id="bb7dd-160">Faça duplo clique MSU executá-la.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-160">Double-click the MSU to run it.</span></span>

<span data-ttu-id="bb7dd-161">**Instalar a partir da linha de comandos**</span><span class="sxs-lookup"><span data-stu-id="bb7dd-161">**Installing from the Command Prompt**</span></span>

1. <span data-ttu-id="bb7dd-162">Depois de transferir o pacote correto para a arquitetura do seu computador, abra uma janela de linha de comandos com direitos de utilizador elevados (executar como administrador).</span><span class="sxs-lookup"><span data-stu-id="bb7dd-162">After downloading the correct package for your computer's architecture, open a Command Prompt window with elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="bb7dd-163">Nas opções de instalação Server Core do Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1, linha de comandos é aberto com direitos de utilizador elevados por predefinição.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-163">On the Server Core installation options of Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1, Command Prompt opens with elevated user rights by default.</span></span>
2. <span data-ttu-id="bb7dd-164">Altere os diretórios para a pasta na qual tem de transferir ou copiar o pacote de instalação do WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-164">Change directories to the folder into which you have downloaded or copied the WMF 5.1 installation package.</span></span>
3. <span data-ttu-id="bb7dd-165">Execute um dos seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="bb7dd-165">Run one of the following commands:</span></span>
   - <span data-ttu-id="bb7dd-166">Em computadores que estejam a executar o Windows Server 2012 R2 ou Windows 8.1 x64, execute `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-166">On computers that are running Windows Server 2012 R2 or Windows 8.1 x64, run `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="bb7dd-167">Em computadores que estejam a executar o Windows Server 2012, execute `W2K12-KB3191565-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-167">On computers that are running Windows Server 2012, run `W2K12-KB3191565-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="bb7dd-168">Em computadores que estejam a executar o Windows 8.1 x86, execute `Win8.1-KB3191564-x86.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-168">On computers that are running Windows 8.1 x86, run `Win8.1-KB3191564-x86.msu /quiet`.</span></span>

> [!NOTE]
> <span data-ttu-id="bb7dd-169">Instalar o WMF 5.1 requer um reinício.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-169">Installing WMF 5.1 requires a reboot.</span></span> <span data-ttu-id="bb7dd-170">Utilizar o `/quiet` opção irá reiniciar o sistema sem aviso.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-170">Using the `/quiet` option will reboot the system without warning.</span></span>
> <span data-ttu-id="bb7dd-171">Utilize o `/norestart` opção para evitar a ser reiniciado.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-171">Use the `/norestart` option to avoid rebooting.</span></span> <span data-ttu-id="bb7dd-172">No entanto, WMF 5.1 não será instalado até ter reiniciado.</span><span class="sxs-lookup"><span data-stu-id="bb7dd-172">However, WMF 5.1 will not be installed until you have rebooted.</span></span>