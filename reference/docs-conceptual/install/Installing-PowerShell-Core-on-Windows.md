---
title: Instalar o PowerShell Core no Windows
description: Informações sobre como instalar o PowerShell Core no Windows
ms.date: 08/06/2018
ms.openlocfilehash: 5a3c43e27f0027cfbeeefab33b045e618e0ff045
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854367"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="d9e34-103">Instalar o PowerShell Core no Windows</span><span class="sxs-lookup"><span data-stu-id="d9e34-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="d9e34-104">Existem várias formas de instalar o PowerShell Core no Windows.</span><span class="sxs-lookup"><span data-stu-id="d9e34-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d9e34-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d9e34-105">Prerequisites</span></span>

<span data-ttu-id="d9e34-106">Para ativar a comunicação remota do PowerShell em WSMan, é necessário ser cumpridos os seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="d9e34-106">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="d9e34-107">Instalar o [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) em versões do Windows antes do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="d9e34-107">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="d9e34-108">Está disponível através de transferência direta ou atualização do Windows.</span><span class="sxs-lookup"><span data-stu-id="d9e34-108">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="d9e34-109">Com todos os patches (incluindo pacotes opcionais), sistemas suportados já terá esta instalado.</span><span class="sxs-lookup"><span data-stu-id="d9e34-109">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="d9e34-110">Instale o Windows Management Framework (WMF) 4.0 ou mais recente no Windows 7 e Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="d9e34-110">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="d9e34-111">Para obter mais informações sobre o WMF, consulte [descrição geral do WMF](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="d9e34-111">For more information about WMF, see [WMF Overview](/powershell/wmf/overview).</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="d9e34-112"><a id="msi" />Instalar o pacote MSI</span><span class="sxs-lookup"><span data-stu-id="d9e34-112"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="d9e34-113">Para instalar o PowerShell num cliente Windows ou Windows Server (funciona no Windows 7 SP1, Server 2008 R2 e posterior), transfira o pacote MSI da nossa página do GitHub [versões] [].</span><span class="sxs-lookup"><span data-stu-id="d9e34-113">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span> <span data-ttu-id="d9e34-114">Desloque para baixo para o **ativos** secção da versão que pretende instalar.</span><span class="sxs-lookup"><span data-stu-id="d9e34-114">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="d9e34-115">A seção de recursos pode ser fechada, por isso terá de clicar para expandi-lo.</span><span class="sxs-lookup"><span data-stu-id="d9e34-115">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="d9e34-116">O arquivo MSI é semelhante a esta- `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="d9e34-116">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="d9e34-117">Depois de transferido, clique duas vezes o instalador e siga as instruções.</span><span class="sxs-lookup"><span data-stu-id="d9e34-117">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="d9e34-118">O instalador cria um atalho no Menu Iniciar do Windows.</span><span class="sxs-lookup"><span data-stu-id="d9e34-118">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="d9e34-119">Por predefinição, o pacote está instalado para `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="d9e34-119">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="d9e34-120">Pode iniciar o PowerShell, no menu Iniciar ou `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="d9e34-120">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="d9e34-121">Instalar administrativa a partir da linha de comandos</span><span class="sxs-lookup"><span data-stu-id="d9e34-121">Administrative install from the command line</span></span>

<span data-ttu-id="d9e34-122">Podem ser instalados pacotes MSI na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="d9e34-122">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="d9e34-123">Isso permite que os administradores implantem pacotes sem interação do utilizador.</span><span class="sxs-lookup"><span data-stu-id="d9e34-123">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="d9e34-124">O pacote do MSI para o PowerShell inclui as seguintes propriedades para controlar as opções de instalação:</span><span class="sxs-lookup"><span data-stu-id="d9e34-124">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="d9e34-125">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** -esta propriedade controla a opção para adicionar a **PowerShell aberto** item ao menu de contexto no Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="d9e34-125">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="d9e34-126">**ENABLE_PSREMOTING** -esta propriedade controla a opção para ativar a comunicação remota do PowerShell durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="d9e34-126">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="d9e34-127">**REGISTER_MANIFEST** -esta propriedade controla a opção para registar o manifesto de registo de eventos do Windows.</span><span class="sxs-lookup"><span data-stu-id="d9e34-127">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="d9e34-128">Os exemplos a seguir mostra como instalar automaticamente o PowerShell Core com todas as opções de instalação ativadas.</span><span class="sxs-lookup"><span data-stu-id="d9e34-128">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="d9e34-129">Para obter uma lista completa de opções de linha de comandos para Msiexec.exe, consulte [opções de linha de comandos](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="d9e34-129">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="d9e34-130"><a id="zip" />Instalar o pacote ZIP</span><span class="sxs-lookup"><span data-stu-id="d9e34-130"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="d9e34-131">Arquivos ZIP binários do PowerShell são fornecidos para ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="d9e34-131">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="d9e34-132">Se observar que ao usar o arquivo ZIP, não obtém a verificação de pré-requisitos, tal como o pacote MSI.</span><span class="sxs-lookup"><span data-stu-id="d9e34-132">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="d9e34-133">Para a gestão remota em WSMan funcione corretamente, certifique-se de que cumpriu os [pré-requisitos](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="d9e34-133">For remoting over WSMan to work properly,, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="d9e34-134">Implantando o Windows IoT</span><span class="sxs-lookup"><span data-stu-id="d9e34-134">Deploying on Windows IoT</span></span>

<span data-ttu-id="d9e34-135">Windows IoT já vem com o Windows PowerShell que vamos utilizar para implementar o PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="d9e34-135">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="d9e34-136">Criar `PSSession` dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="d9e34-136">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="d9e34-137">Copiar o pacote ZIP para o dispositivo</span><span class="sxs-lookup"><span data-stu-id="d9e34-137">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="d9e34-138">Ligar ao dispositivo e expanda o arquivo</span><span class="sxs-lookup"><span data-stu-id="d9e34-138">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="d9e34-139">Configurar a comunicação remota do PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="d9e34-139">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="d9e34-140">Ligar ao ponto final do PowerShell Core 6 no dispositivo</span><span class="sxs-lookup"><span data-stu-id="d9e34-140">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="d9e34-141">Implementar no servidor Nano</span><span class="sxs-lookup"><span data-stu-id="d9e34-141">Deploying on Nano Server</span></span>

<span data-ttu-id="d9e34-142">Estas instruções partem do princípio de que uma versão do PowerShell já está em execução na imagem do servidor Nano e que tenha sido gerado pela [construtor de imagens do servidor Nano](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="d9e34-142">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="d9e34-143">O servidor nano é um sistema operacional "sem interface".</span><span class="sxs-lookup"><span data-stu-id="d9e34-143">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="d9e34-144">Os binários do principal pode implementar através de dois métodos diferentes.</span><span class="sxs-lookup"><span data-stu-id="d9e34-144">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="d9e34-145">Offline - Monte o VHD do servidor Nano e Descompacte o conteúdo do ficheiro zip para a sua localização escolhida dentro da imagem montada.</span><span class="sxs-lookup"><span data-stu-id="d9e34-145">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="d9e34-146">Online - transferir o ficheiro zip através de uma sessão do PowerShell e Descompacte-o em seu local escolhido.</span><span class="sxs-lookup"><span data-stu-id="d9e34-146">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="d9e34-147">Em ambos os casos, terá da versão x64 do Windows 10 ZIP do pacote e será necessário executar os comandos dentro de uma instância do PowerShell de "Administrador".</span><span class="sxs-lookup"><span data-stu-id="d9e34-147">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="d9e34-148">Implantação offline do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="d9e34-148">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="d9e34-149">Utilize o utilitário zip Favoritos para descomprimir o pacote para um diretório dentro da imagem montada do servidor Nano.</span><span class="sxs-lookup"><span data-stu-id="d9e34-149">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="d9e34-150">Desmonte a imagem e inicializá-la.</span><span class="sxs-lookup"><span data-stu-id="d9e34-150">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="d9e34-151">Ligue à instância da caixa de entrada do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d9e34-151">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="d9e34-152">Siga as instruções para criar um ponto de extremidade de comunicação remota utilizando o ["outra técnica de instância"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="d9e34-152">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="d9e34-153">Implantação online do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="d9e34-153">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="d9e34-154">Os seguintes passos guiá-lo por meio da implantação do PowerShell Core para uma instância em execução do servidor Nano e a configuração do seu ponto final remoto.</span><span class="sxs-lookup"><span data-stu-id="d9e34-154">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="d9e34-155">Ligue à instância da caixa de entrada do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d9e34-155">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="d9e34-156">Copie o ficheiro para a instância de servidor Nano</span><span class="sxs-lookup"><span data-stu-id="d9e34-156">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="d9e34-157">Introduza a sessão</span><span class="sxs-lookup"><span data-stu-id="d9e34-157">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="d9e34-158">Extraia o ficheiro ZIP</span><span class="sxs-lookup"><span data-stu-id="d9e34-158">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="d9e34-159">Se pretender que a comunicação remota baseada em WSMan, siga as instruções para criar um ponto de extremidade de comunicação remota utilizando o ["outra técnica de instância"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="d9e34-159">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="d9e34-160">Como criar um ponto de extremidade de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="d9e34-160">How to create a remoting endpoint</span></span>

<span data-ttu-id="d9e34-161">O PowerShell Core suporta o protocolo de comunicação remota do PowerShell (PSRP) através de WSMan e SSH.</span><span class="sxs-lookup"><span data-stu-id="d9e34-161">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="d9e34-162">Para mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="d9e34-162">For more information, see:</span></span>

- <span data-ttu-id="d9e34-163">[SSH comunicação remota no PowerShell Core] [ssh-comunicação remota]</span><span class="sxs-lookup"><span data-stu-id="d9e34-163">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="d9e34-164">[WSMan comunicação remota no PowerShell Core] [wsman remoting]</span><span class="sxs-lookup"><span data-stu-id="d9e34-164">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->
[versões]: https://github.com/PowerShell/PowerShell/releases [ssh-comunicação remota]:.... /Core-PowerShell/SSH-Remoting-in-PowerShell-Core.MD [wsman remoting]:.... /Core-PowerShell/wsman-Remoting-in-PowerShell-Core.MD [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[releases]: https://github.com/PowerShell/PowerShell/releases [ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md [wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
