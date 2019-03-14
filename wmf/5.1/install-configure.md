---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: keithb
title: Instalar e configurar o WMF 5.1
ms.openlocfilehash: e5590d48d467506270ccef4089513e1afade07be
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795577"
---
# <a name="install-and-configure-wmf-51"></a><span data-ttu-id="4111f-103">Instalar e configurar o WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="4111f-103">Install and Configure WMF 5.1</span></span>

## <a name="download-and-install-the-wmf-51-package"></a><span data-ttu-id="4111f-104">Transfira e instale o pacote do WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="4111f-104">Download and install the WMF 5.1 package</span></span>

<span data-ttu-id="4111f-105">Transferir o pacote de WMF 5.1 para o sistema operativo e a arquitetura que deseja instalá-lo em:</span><span class="sxs-lookup"><span data-stu-id="4111f-105">Download the WMF 5.1 package for the operating system and architecture you wish to install it on:</span></span>

| <span data-ttu-id="4111f-106">Sistema Operativo</span><span class="sxs-lookup"><span data-stu-id="4111f-106">Operating System</span></span>       | <span data-ttu-id="4111f-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4111f-107">Prerequisites</span></span>           | <span data-ttu-id="4111f-108">Ligações de pacote</span><span class="sxs-lookup"><span data-stu-id="4111f-108">Package Links</span></span>                          |
|------------------------|-------------------------|----------------------------------------|
| <span data-ttu-id="4111f-109">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="4111f-109">Windows Server 2012 R2</span></span> |                         | <span data-ttu-id="4111f-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="4111f-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span> |
| <span data-ttu-id="4111f-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="4111f-111">Windows Server 2012</span></span>    |                         | <span data-ttu-id="4111f-112">[W2K12-KB3191565-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="4111f-112">[W2K12-KB3191565-x64.msu][]</span></span>            |
| <span data-ttu-id="4111f-113">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="4111f-113">Windows Server 2008 R2</span></span> | <span data-ttu-id="4111f-114">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="4111f-114">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="4111f-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="4111f-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span>    |
| <span data-ttu-id="4111f-116">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="4111f-116">Windows 8.1</span></span>            |                         | <span data-ttu-id="4111f-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="4111f-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span></br><span data-ttu-id="4111f-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span><span class="sxs-lookup"><span data-stu-id="4111f-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span></span> |
| <span data-ttu-id="4111f-119">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="4111f-119">Windows 7 SP1</span></span>          | <span data-ttu-id="4111f-120">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="4111f-120">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="4111f-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="4111f-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span></br><span data-ttu-id="4111f-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="4111f-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span></span> |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="4111f-129">Instale o WMF 5.1 para o Windows Server 2008 R2 e Windows 7</span><span class="sxs-lookup"><span data-stu-id="4111f-129">Install WMF 5.1 for Windows Server 2008 R2 and Windows 7</span></span>

> <span data-ttu-id="4111f-130">**Nota:** Instruções de instalação para Windows Server 2008 R2 e Windows 7 foram alterados e diferem das instruções para os outros pacotes.</span><span class="sxs-lookup"><span data-stu-id="4111f-130">**Note:** Installation instructions for Windows Server 2008 R2 and Windows 7 have changed, and differ from the instructions for the other packages.</span></span> <span data-ttu-id="4111f-131">Instruções de instalação para Windows Server 2012 R2, Windows Server 2012 e Windows 8.1 estão abaixo.</span><span class="sxs-lookup"><span data-stu-id="4111f-131">Installation instructions for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1 are below.</span></span>

<span data-ttu-id="4111f-132">**Instalar o WMF 5.1 no Windows Server 2008 R2 e Windows 7**</span><span class="sxs-lookup"><span data-stu-id="4111f-132">**Installing WMF 5.1 on Windows Server 2008 R2 and Windows 7**</span></span>

1. <span data-ttu-id="4111f-133">Navegue para a pasta na qual transferiu o ficheiro ZIP.</span><span class="sxs-lookup"><span data-stu-id="4111f-133">Navigate to the folder into which you downloaded the ZIP file.</span></span>

2. <span data-ttu-id="4111f-134">Com o botão direito no ficheiro ZIP e selecione "Extrair todos os...".</span><span class="sxs-lookup"><span data-stu-id="4111f-134">Right-click on the ZIP file, and select "Extract All...".</span></span> <span data-ttu-id="4111f-135">O Zip contém 2 ficheiros: um MSU e o ficheiro de script de instalação WMF5.1.PS1.</span><span class="sxs-lookup"><span data-stu-id="4111f-135">The Zip contains 2 files: an MSU and the Install-WMF5.1.PS1 script file.</span></span>
<span data-ttu-id="4111f-136">Depois de descompactação o ficheiro ZIP, pode copiar o conteúdo a qualquer máquina com o Windows 7 ou Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="4111f-136">Once you have unpacked the ZIP file, you can copy the contents to any machine running Windows 7 or Windows Server 2008 R2.</span></span>

3. <span data-ttu-id="4111f-137">Depois de extrair o conteúdo do ficheiro ZIP, abra o PowerShell como administrador, em seguida, navegue para a pasta que contenha o conteúdo do ficheiro ZIP.</span><span class="sxs-lookup"><span data-stu-id="4111f-137">After extracting the ZIP file contents, open PowerShell as administrator, then navigate to the folder containing the contents of the ZIP file.</span></span>

4. <span data-ttu-id="4111f-138">Execute o script de instalação Wmf5.1.ps1 nessa pasta e siga as instruções.</span><span class="sxs-lookup"><span data-stu-id="4111f-138">Run the Install-Wmf5.1.ps1 script in that folder, and follow the instructions.</span></span> <span data-ttu-id="4111f-139">Este script irá verificar os pré-requisitos no computador local e instale o WMF 5.1 se os pré-requisitos tiverem sido cumpridos.</span><span class="sxs-lookup"><span data-stu-id="4111f-139">This script will check the prerequisites on the local machine, and install WMF 5.1 if the prerequisites have been met.</span></span> <span data-ttu-id="4111f-140">Os pré-requisitos estão listados abaixo.</span><span class="sxs-lookup"><span data-stu-id="4111f-140">The prerequisites are listed below.</span></span>

<span data-ttu-id="4111f-141">Instalação WMF5.1.ps1 precisa dos seguintes parâmetros para facilitar a automatizar a instalação no Windows Server 2008 R2 e Windows 7:</span><span class="sxs-lookup"><span data-stu-id="4111f-141">Install-WMF5.1.ps1 takes the following parameters to ease automating the installation on Windows Server 2008 R2 and Windows 7:</span></span>

- <span data-ttu-id="4111f-142">AcceptEula: Quando este parâmetro está incluído, o EULA automaticamente é aceite e não será apresentado.</span><span class="sxs-lookup"><span data-stu-id="4111f-142">AcceptEula: When this parameter is included, the EULA is automatically accepted and will not be displayed.</span></span>
- <span data-ttu-id="4111f-143">AllowRestart: Este parâmetro só pode ser utilizado se não for especificado AcceptEula.</span><span class="sxs-lookup"><span data-stu-id="4111f-143">AllowRestart: This parameter can only be used if AcceptEula is specified.</span></span> <span data-ttu-id="4111f-144">Se este parâmetro está incluído e é necessário um reinício após a instalação do WMF 5.1, irá ocorrer o reinício sem pedir confirmação imediatamente após a instalação estiver concluída.</span><span class="sxs-lookup"><span data-stu-id="4111f-144">If this parameter is included, and a restart is required after installing WMF 5.1, the restart will happen without prompting immediately after the installation is completed.</span></span>

<span data-ttu-id="4111f-145">**WMF 5.1 pré-requisitos para o Windows Server 2008 R2 SP1 e Windows 7 SP1**</span><span class="sxs-lookup"><span data-stu-id="4111f-145">**WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1**</span></span>

<span data-ttu-id="4111f-146">Instalação do WMF 5.1 no Windows Server 2008 R2 SP1 ou Windows 7 SP1, necessita do seguinte:</span><span class="sxs-lookup"><span data-stu-id="4111f-146">Installation of WMF 5.1 on either Windows Server 2008 R2 SP1 or Windows 7 SP1, requires the following:</span></span>
- <span data-ttu-id="4111f-147">Deve ser instalado o service pack mais recente.</span><span class="sxs-lookup"><span data-stu-id="4111f-147">Latest service pack must be installed.</span></span>
- <span data-ttu-id="4111f-148">WMF 3.0 **não podem** ser instalado.</span><span class="sxs-lookup"><span data-stu-id="4111f-148">WMF 3.0 **must not** be installed.</span></span> <span data-ttu-id="4111f-149">Instalação do WMF 5.1 ao longo do WMF 3.0 resultará na perda de PSModulePath, que pode fazer com que outros aplicativos efetuar a ativação.</span><span class="sxs-lookup"><span data-stu-id="4111f-149">Installing WMF 5.1 over WMF 3.0 will result in the loss of the PSModulePath, which can cause other applications to fail.</span></span> <span data-ttu-id="4111f-150">Antes de instalar o WMF 5.1, tem do desinstalar WMF 3.0, ou guardar o PSModulePath e, em seguida, restaurá-lo manualmente após a conclusão da instalação do WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="4111f-150">Before installing WMF 5.1, you must either un-install WMF 3.0, or save the PSModulePath and then restore it manually after WMF 5.1 installation is complete.</span></span>
- <span data-ttu-id="4111f-151">WMF 5.1 requer pelo menos [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span><span class="sxs-lookup"><span data-stu-id="4111f-151">WMF 5.1 requires at least [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span></span>
<span data-ttu-id="4111f-152">Pode instalar o Microsoft .NET Framework 4.5.2 ao seguir as instruções na localização de transferência.</span><span class="sxs-lookup"><span data-stu-id="4111f-152">You can install Microsoft .NET Framework 4.5.2 by following the instructions at the download location.</span></span>

<span data-ttu-id="4111f-153">**Dependência de WinRM**</span><span class="sxs-lookup"><span data-stu-id="4111f-153">**WinRM Dependency**</span></span>

<span data-ttu-id="4111f-154">Windows PowerShell Desired State Configuration (DSC) depende de WinRM.</span><span class="sxs-lookup"><span data-stu-id="4111f-154">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span>
<span data-ttu-id="4111f-155">WinRM não está ativado por padrão no Windows Server 2008 R2 e Windows 7.</span><span class="sxs-lookup"><span data-stu-id="4111f-155">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span>
<span data-ttu-id="4111f-156">Executar `Set-WSManQuickConfig`, no Windows PowerShell elevados sessão, para ativar o WinRM.</span><span class="sxs-lookup"><span data-stu-id="4111f-156">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a><span data-ttu-id="4111f-157">Instale o WMF 5.1 para o Windows Server 2012 R2, Windows Server 2012 e Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="4111f-157">Install WMF 5.1 for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1</span></span>

<span data-ttu-id="4111f-158">**Instalar a partir do Explorador do Windows (ou o Explorador de ficheiros no Windows Server 2012 R2 ou Windows 8.1)**</span><span class="sxs-lookup"><span data-stu-id="4111f-158">**Install from Windows Explorer (or File Explorer in Windows Server 2012 R2 or Windows 8.1)**</span></span>

1. <span data-ttu-id="4111f-159">Navegue para a pasta na qual transferiu o ficheiro MSU.</span><span class="sxs-lookup"><span data-stu-id="4111f-159">Navigate to the folder into which you downloaded the MSU file.</span></span>
2. <span data-ttu-id="4111f-160">Faça duplo clique MSU executá-lo.</span><span class="sxs-lookup"><span data-stu-id="4111f-160">Double-click the MSU to run it.</span></span>

<span data-ttu-id="4111f-161">**Instalar a partir da linha de comandos**</span><span class="sxs-lookup"><span data-stu-id="4111f-161">**Installing from the Command Prompt**</span></span>

1. <span data-ttu-id="4111f-162">Depois de transferir o pacote correto para a arquitetura do seu computador, abra uma janela de linha de comandos com direitos de utilizador elevados (executar como administrador).</span><span class="sxs-lookup"><span data-stu-id="4111f-162">After downloading the correct package for your computer's architecture, open a Command Prompt window with elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="4111f-163">Sobre as opções de instalação Server Core do Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1, linha de comandos é aberta com direitos de utilizador elevados por predefinição.</span><span class="sxs-lookup"><span data-stu-id="4111f-163">On the Server Core installation options of Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1, Command Prompt opens with elevated user rights by default.</span></span>
2. <span data-ttu-id="4111f-164">Altere os diretórios para a pasta em que tiver transferido ou copiado o pacote de instalação do WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="4111f-164">Change directories to the folder into which you have downloaded or copied the WMF 5.1 installation package.</span></span>
3. <span data-ttu-id="4111f-165">Execute um dos seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="4111f-165">Run one of the following commands:</span></span>
   - <span data-ttu-id="4111f-166">Nos computadores que executem Windows Server 2012 R2 ou Windows 8.1 x64, execute `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="4111f-166">On computers that are running Windows Server 2012 R2 or Windows 8.1 x64, run `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="4111f-167">Nos computadores que executem Windows Server 2012, execute `W2K12-KB3191565-x64.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="4111f-167">On computers that are running Windows Server 2012, run `W2K12-KB3191565-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="4111f-168">Nos computadores que estejam a executar o Windows 8.1 x86, execute `Win8.1-KB3191564-x86.msu /quiet`.</span><span class="sxs-lookup"><span data-stu-id="4111f-168">On computers that are running Windows 8.1 x86, run `Win8.1-KB3191564-x86.msu /quiet`.</span></span>

> [!NOTE]
> <span data-ttu-id="4111f-169">A instalação de WMF 5.1 requer um reinício.</span><span class="sxs-lookup"><span data-stu-id="4111f-169">Installing WMF 5.1 requires a reboot.</span></span> <span data-ttu-id="4111f-170">Usando o `/quiet` opção irá reiniciar o sistema sem aviso.</span><span class="sxs-lookup"><span data-stu-id="4111f-170">Using the `/quiet` option will reboot the system without warning.</span></span>
> <span data-ttu-id="4111f-171">Utilize o `/norestart` opção para evitar o reinício.</span><span class="sxs-lookup"><span data-stu-id="4111f-171">Use the `/norestart` option to avoid rebooting.</span></span> <span data-ttu-id="4111f-172">No entanto, WMF 5.1 não será instalado até que foram reiniciados.</span><span class="sxs-lookup"><span data-stu-id="4111f-172">However, WMF 5.1 will not be installed until you have rebooted.</span></span>
