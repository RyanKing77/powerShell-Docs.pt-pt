---
title: Instalar o PowerShell Core no Windows
description: Informações sobre como instalar o PowerShell Core no Windows
ms.date: 08/06/2018
ms.openlocfilehash: 7c109c7e1848af2349092c1e70fe4a7a25be54b8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405199"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="7d01f-103">Instalar o PowerShell Core no Windows</span><span class="sxs-lookup"><span data-stu-id="7d01f-103">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="7d01f-104">MSI</span><span class="sxs-lookup"><span data-stu-id="7d01f-104">MSI</span></span>

<span data-ttu-id="7d01f-105">Para instalar o PowerShell num cliente Windows ou Windows Server (funciona no Windows 7 SP1, Server 2008 R2 e posterior), transferir o pacote MSI a partir do nosso GitHub [releases][] página.</span><span class="sxs-lookup"><span data-stu-id="7d01f-105">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="7d01f-106">O arquivo MSI é semelhante a esta- `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span><span class="sxs-lookup"><span data-stu-id="7d01f-106">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span></span>

<span data-ttu-id="7d01f-107">Depois de transferido, clique duas vezes o instalador e siga as instruções.</span><span class="sxs-lookup"><span data-stu-id="7d01f-107">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="7d01f-108">Existe um atalho colocado no Menu Iniciar, após a instalação.</span><span class="sxs-lookup"><span data-stu-id="7d01f-108">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="7d01f-109">Por predefinição, o pacote está instalado para `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="7d01f-109">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="7d01f-110">Pode iniciar o PowerShell, no menu Iniciar ou `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="7d01f-110">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="7d01f-111">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7d01f-111">Prerequisites</span></span>

<span data-ttu-id="7d01f-112">Para ativar a comunicação remota do PowerShell em WSMan, é necessário ser cumpridos os seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="7d01f-112">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="7d01f-113">Instalar o [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) em versões do Windows antes do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="7d01f-113">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="7d01f-114">Está disponível através de transferência direta ou atualização do Windows.</span><span class="sxs-lookup"><span data-stu-id="7d01f-114">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="7d01f-115">Com todos os patches (incluindo pacotes opcionais), sistemas suportados já terá esta instalado.</span><span class="sxs-lookup"><span data-stu-id="7d01f-115">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="7d01f-116">Instale o Windows Management Framework (WMF) 4.0 ou mais recente no Windows 7 e Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="7d01f-116">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="7d01f-117">ZIP</span><span class="sxs-lookup"><span data-stu-id="7d01f-117">ZIP</span></span>

<span data-ttu-id="7d01f-118">Arquivos ZIP binários do PowerShell são fornecidos para ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="7d01f-118">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="7d01f-119">Se observar que ao usar o arquivo ZIP, não obtém a verificação de pré-requisitos, tal como o pacote MSI.</span><span class="sxs-lookup"><span data-stu-id="7d01f-119">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="7d01f-120">Portanto, para a gestão remota em WSMan funcione corretamente em versões do Windows antes do Windows 10, tem de certificar-se a [pré-requisitos](#prerequisites) são cumpridos.</span><span class="sxs-lookup"><span data-stu-id="7d01f-120">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="7d01f-121">Implantando o Windows IoT</span><span class="sxs-lookup"><span data-stu-id="7d01f-121">Deploying on Windows IoT</span></span>

<span data-ttu-id="7d01f-122">Windows IoT já vem com o Windows PowerShell que vamos utilizar para implementar o PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="7d01f-122">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="7d01f-123">Criar `PSSession` dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="7d01f-123">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="7d01f-124">Copiar o pacote ZIP para o dispositivo</span><span class="sxs-lookup"><span data-stu-id="7d01f-124">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.1.0-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="7d01f-125">Ligar ao dispositivo e expanda o arquivo</span><span class="sxs-lookup"><span data-stu-id="7d01f-125">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.1.0-win-arm32.zip
   ```

4. <span data-ttu-id="7d01f-126">Configurar a comunicação remota do PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="7d01f-126">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-6.1.0-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="7d01f-127">Ligar ao ponto final do PowerShell Core 6 no dispositivo</span><span class="sxs-lookup"><span data-stu-id="7d01f-127">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.1.0
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="7d01f-128">Implementar no servidor Nano</span><span class="sxs-lookup"><span data-stu-id="7d01f-128">Deploying on Nano Server</span></span>

<span data-ttu-id="7d01f-129">Estas instruções partem do princípio de que uma versão do PowerShell já está em execução na imagem do servidor Nano e que tenha sido gerado pela [construtor de imagens do servidor Nano](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="7d01f-129">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="7d01f-130">O servidor nano é um sistema operacional "sem interface".</span><span class="sxs-lookup"><span data-stu-id="7d01f-130">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="7d01f-131">Os binários do principal pode implementar através de dois métodos diferentes.</span><span class="sxs-lookup"><span data-stu-id="7d01f-131">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="7d01f-132">Offline - Monte o VHD do servidor Nano e Descompacte o conteúdo do ficheiro zip para a sua localização escolhida dentro da imagem montada.</span><span class="sxs-lookup"><span data-stu-id="7d01f-132">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="7d01f-133">Online - transferir o ficheiro zip através de uma sessão do PowerShell e Descompacte-o em seu local escolhido.</span><span class="sxs-lookup"><span data-stu-id="7d01f-133">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="7d01f-134">Em ambos os casos, terá da versão x64 do Windows 10 ZIP do pacote e será necessário executar os comandos dentro de uma instância do PowerShell de "Administrador".</span><span class="sxs-lookup"><span data-stu-id="7d01f-134">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="7d01f-135">Implantação offline do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="7d01f-135">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="7d01f-136">Utilize o utilitário zip Favoritos para descomprimir o pacote para um diretório dentro da imagem montada do servidor Nano.</span><span class="sxs-lookup"><span data-stu-id="7d01f-136">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="7d01f-137">Desmonte a imagem e inicializá-la.</span><span class="sxs-lookup"><span data-stu-id="7d01f-137">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="7d01f-138">Ligue à instância da caixa de entrada do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d01f-138">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="7d01f-139">Siga as instruções para criar um ponto de extremidade de comunicação remota utilizando o ["outra técnica de instância"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="7d01f-139">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="7d01f-140">Implantação online do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="7d01f-140">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="7d01f-141">Os seguintes passos guiá-lo por meio da implantação do PowerShell Core para uma instância em execução do servidor Nano e a configuração do seu ponto final remoto.</span><span class="sxs-lookup"><span data-stu-id="7d01f-141">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="7d01f-142">Ligue à instância da caixa de entrada do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7d01f-142">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="7d01f-143">Copie o ficheiro para a instância de servidor Nano</span><span class="sxs-lookup"><span data-stu-id="7d01f-143">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="7d01f-144">Introduza a sessão</span><span class="sxs-lookup"><span data-stu-id="7d01f-144">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="7d01f-145">Extraia o ficheiro ZIP</span><span class="sxs-lookup"><span data-stu-id="7d01f-145">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="7d01f-146">Se pretender que a comunicação remota baseada em WSMan, siga as instruções para criar um ponto de extremidade de comunicação remota utilizando o ["outra técnica de instância"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="7d01f-146">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="7d01f-147">Instruções para criar um ponto de extremidade de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="7d01f-147">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="7d01f-148">O PowerShell Core suporta o protocolo de comunicação remota do PowerShell (PSRP) através de WSMan e SSH.</span><span class="sxs-lookup"><span data-stu-id="7d01f-148">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="7d01f-149">Para mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="7d01f-149">For more information, see:</span></span>

- <span data-ttu-id="7d01f-150">[SSH comunicação remota no PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="7d01f-150">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="7d01f-151">[Comunicação remota do WSMan no PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="7d01f-151">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="7d01f-152">Instruções de instalação do artefacto</span><span class="sxs-lookup"><span data-stu-id="7d01f-152">Artifact Installation Instructions</span></span>

<span data-ttu-id="7d01f-153">Publicamos um arquivo morto com bits de CoreCLR em todas as compilações CI com [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="7d01f-153">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="7d01f-154">Para instalar o PowerShell Core a partir do artefacto de CoreCLR:</span><span class="sxs-lookup"><span data-stu-id="7d01f-154">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="7d01f-155">Transferir o pacote ZIP da **artefactos** separador da compilação específica.</span><span class="sxs-lookup"><span data-stu-id="7d01f-155">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="7d01f-156">Ficheiro ZIP de desbloqueio: botão direito do rato no Explorador de ficheiros -> Properties -> aplica "Desbloquear" -> a caixa de verificação</span><span class="sxs-lookup"><span data-stu-id="7d01f-156">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="7d01f-157">Extrair o ficheiro zip para `bin` diretório</span><span class="sxs-lookup"><span data-stu-id="7d01f-157">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell