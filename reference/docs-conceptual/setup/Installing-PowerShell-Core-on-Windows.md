# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="2c37f-101">Instalar o PowerShell Core no Windows</span><span class="sxs-lookup"><span data-stu-id="2c37f-101">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="2c37f-102">MSI</span><span class="sxs-lookup"><span data-stu-id="2c37f-102">MSI</span></span>

<span data-ttu-id="2c37f-103">Para instalar o PowerShell num cliente Windows ou Windows Server (funciona no Windows 7 SP1, Server 2008 R2 e posterior), transfira o pacote MSI da nossa página do GitHub [versões] [].</span><span class="sxs-lookup"><span data-stu-id="2c37f-103">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="2c37f-104">O ficheiro MSI aspeto- `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span><span class="sxs-lookup"><span data-stu-id="2c37f-104">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span></span>

<span data-ttu-id="2c37f-105">Depois de transferido, faça duplo clique o instalador e siga as instruções.</span><span class="sxs-lookup"><span data-stu-id="2c37f-105">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="2c37f-106">Não há um atalho colocado no Menu Iniciar após a instalação.</span><span class="sxs-lookup"><span data-stu-id="2c37f-106">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="2c37f-107">Por predefinição, o pacote está instalado para `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="2c37f-107">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="2c37f-108">Pode iniciar PowerShell através do Menu Iniciar ou `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="2c37f-108">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="2c37f-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2c37f-109">Prerequisites</span></span>

<span data-ttu-id="2c37f-110">Para ativar a comunicação remota do PowerShell através de WSMan, os seguintes pré-requisitos tem de ser cumpridos:</span><span class="sxs-lookup"><span data-stu-id="2c37f-110">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="2c37f-111">Instalar o [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) nas versões do Windows antes do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="2c37f-111">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="2c37f-112">Está disponível através de transferência direta ou o Windows Update.</span><span class="sxs-lookup"><span data-stu-id="2c37f-112">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="2c37f-113">Totalmente aplicado (incluindo pacotes opcionais), sistemas suportados já terão isto instalado.</span><span class="sxs-lookup"><span data-stu-id="2c37f-113">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="2c37f-114">Instale o Windows Management Framework (WMF) 4.0 ou mais recente no Windows 7 e Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="2c37f-114">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="2c37f-115">ZIP</span><span class="sxs-lookup"><span data-stu-id="2c37f-115">ZIP</span></span>

<span data-ttu-id="2c37f-116">PowerShell binários ZIP arquivos são fornecidos para ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="2c37f-116">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="2c37f-117">É de salientar que, ao utilizar o arquivo ZIP, não irá obter a verificação de pré-requisitos, como o pacote MSI.</span><span class="sxs-lookup"><span data-stu-id="2c37f-117">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="2c37f-118">Por isso ordem para a gestão remota através de WSMan funcione corretamente no Windows versões anteriores ao Windows 10, terá de certificar-se do [pré-requisitos](#prerequisites) são cumpridos.</span><span class="sxs-lookup"><span data-stu-id="2c37f-118">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="2c37f-119">A implementar em Windows IoT</span><span class="sxs-lookup"><span data-stu-id="2c37f-119">Deploying on Windows IoT</span></span>

<span data-ttu-id="2c37f-120">Windows IoT é fornecido com o Windows PowerShell que iremos utilizar para implementar PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="2c37f-120">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="2c37f-121">Criar `PSSession` para o dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="2c37f-121">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="2c37f-122">Copie o pacote ZIP para o dispositivo</span><span class="sxs-lookup"><span data-stu-id="2c37f-122">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.0.2-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="2c37f-123">Ligar ao dispositivo e expanda o arquivo</span><span class="sxs-lookup"><span data-stu-id="2c37f-123">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   cd u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.0.2-win-arm32.zip
   ```

4. <span data-ttu-id="2c37f-124">Configurar a comunicação remota do PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="2c37f-124">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   cd .\PowerShell-6.0.2-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="2c37f-125">Ligar ao ponto final de PowerShell Core 6 no dispositivo</span><span class="sxs-lookup"><span data-stu-id="2c37f-125">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.0.2
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="2c37f-126">Implementar no servidor de Nano</span><span class="sxs-lookup"><span data-stu-id="2c37f-126">Deploying on Nano Server</span></span>

<span data-ttu-id="2c37f-127">Estas instruções partem do princípio de que uma versão do PowerShell já está em execução a imagem de servidor Nano e que foi gerado pelo [construtor de imagens do servidor Nano](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="2c37f-127">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="2c37f-128">Servidor de nano for um SO "sem interface".</span><span class="sxs-lookup"><span data-stu-id="2c37f-128">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="2c37f-129">Os binários de núcleos pode implementar utilizando dois métodos diferentes.</span><span class="sxs-lookup"><span data-stu-id="2c37f-129">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="2c37f-130">Offline - montar o VHD de servidor Nano e deszipe o conteúdo do ficheiro zip à sua localização escolhida dentro da imagem montada.</span><span class="sxs-lookup"><span data-stu-id="2c37f-130">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="2c37f-131">Online - transferir o ficheiro zip através de uma sessão do PowerShell e deszipe-lo na sua localização escolhida.</span><span class="sxs-lookup"><span data-stu-id="2c37f-131">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="2c37f-132">Em ambos os casos, terá da versão do Windows 10 x64 ZIP do pacote e terá de executar os comandos dentro de uma instância do PowerShell do "Administrador".</span><span class="sxs-lookup"><span data-stu-id="2c37f-132">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="2c37f-133">Implementação offline do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="2c37f-133">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="2c37f-134">Utilize o utilitário de favorito zip para descomprimir o pacote para um diretório na imagem de servidor Nano montada.</span><span class="sxs-lookup"><span data-stu-id="2c37f-134">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="2c37f-135">Desmontar a imagem e efetuar o arranque-lo.</span><span class="sxs-lookup"><span data-stu-id="2c37f-135">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="2c37f-136">Ligar à instância da pasta a receber do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2c37f-136">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="2c37f-137">Siga as instruções para criar um ponto final de gestão remota utilizando o ["outra técnica de instância"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="2c37f-137">Follow the instructions to create a remoting endpoint using the ["another instance technique"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="2c37f-138">Implementação online do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="2c37f-138">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="2c37f-139">Os seguintes passos guiá-lo através da implementação do PowerShell Core para uma instância em execução de servidor Nano e a configuração do seu ponto final remoto.</span><span class="sxs-lookup"><span data-stu-id="2c37f-139">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="2c37f-140">Ligar à instância da pasta a receber do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c37f-140">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="2c37f-141">Copie o ficheiro para a instância de servidor Nano</span><span class="sxs-lookup"><span data-stu-id="2c37f-141">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="2c37f-142">Introduza a sessão</span><span class="sxs-lookup"><span data-stu-id="2c37f-142">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="2c37f-143">Extrair o ficheiro ZIP</span><span class="sxs-lookup"><span data-stu-id="2c37f-143">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="2c37f-144">Se pretender que o sistema de interação remota com base em WSMan, siga as instruções para criar um ponto final de gestão remota utilizando o ["outra técnica de instância"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="2c37f-144">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="2c37f-145">Instruções para criar um ponto final de gestão remota</span><span class="sxs-lookup"><span data-stu-id="2c37f-145">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="2c37f-146">PowerShell Core suporta o protocolo de comunicação remota do PowerShell (PSRP) através de SSH e WSMan.</span><span class="sxs-lookup"><span data-stu-id="2c37f-146">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="2c37f-147">Para mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="2c37f-147">For more information, see:</span></span>

- <span data-ttu-id="2c37f-148">[SSH comunicação remota do PowerShell Core] [ssh-gestão remota]</span><span class="sxs-lookup"><span data-stu-id="2c37f-148">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="2c37f-149">[WSMan sistema de interação remota no PowerShell Core] [wsman-sistema de interação remota]</span><span class="sxs-lookup"><span data-stu-id="2c37f-149">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="2c37f-150">Instruções de instalação de artefactos</span><span class="sxs-lookup"><span data-stu-id="2c37f-150">Artifact Installation Instructions</span></span>

<span data-ttu-id="2c37f-151">Está a publicar um arquivo com CoreCLR bits em cada compilação CI com [AppVeyor] [-].</span><span class="sxs-lookup"><span data-stu-id="2c37f-151">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="2c37f-152">Para instalar o PowerShell Core de artefacto CoreCLR:</span><span class="sxs-lookup"><span data-stu-id="2c37f-152">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="2c37f-153">Transferir o pacote ZIP da **artefactos** separador de compilação do específica.</span><span class="sxs-lookup"><span data-stu-id="2c37f-153">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="2c37f-154">Ficheiro ZIP de desbloqueio: rato no Explorador de ficheiros -> propriedades -> Aplicar 'Desbloquear' -> a caixa de verificação</span><span class="sxs-lookup"><span data-stu-id="2c37f-154">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="2c37f-155">Extrair o ficheiro zip para `bin` diretório</span><span class="sxs-lookup"><span data-stu-id="2c37f-155">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<span data-ttu-id="2c37f-156"><!-- [download-center]: TODO --> [versões]: https://github.com/PowerShell/PowerShell/releases [ssh-gestão remota]:... /Core-PowerShell/SSH-Remoting-in-PowerShell-Core.MD [wsman-sistema de interação remota]:... /Core-PowerShell/wsman-Remoting-in-PowerShell-Core.MD [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell</span><span class="sxs-lookup"><span data-stu-id="2c37f-156"><!-- [download-center]: TODO --> [releases]: https://github.com/PowerShell/PowerShell/releases [ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md [wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell</span></span>