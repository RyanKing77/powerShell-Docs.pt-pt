# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="b238b-101">Instalar o núcleo do PowerShell no Windows</span><span class="sxs-lookup"><span data-stu-id="b238b-101">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="b238b-102">MSI</span><span class="sxs-lookup"><span data-stu-id="b238b-102">MSI</span></span>

<span data-ttu-id="b238b-103">Para instalar o PowerShell num cliente Windows ou Windows Server (funciona no Windows 7 SP1, Server 2008 R2 e posterior), transfira o pacote MSI</span><span class="sxs-lookup"><span data-stu-id="b238b-103">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from</span></span>
<!-- TODO: either the Download Center or -->
<span data-ttu-id="b238b-104">a nossa GitHub [versões][] página.</span><span class="sxs-lookup"><span data-stu-id="b238b-104">our GitHub [releases][] page.</span></span>
<span data-ttu-id="b238b-105">O ficheiro MSI aspeto-`PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="b238b-105">The MSI file looks like this - `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span></span>

<span data-ttu-id="b238b-106">Depois de transferido, faça duplo clique o instalador e siga as instruções.</span><span class="sxs-lookup"><span data-stu-id="b238b-106">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="b238b-107">Não há um atalho colocado no Menu Iniciar após a instalação.</span><span class="sxs-lookup"><span data-stu-id="b238b-107">There is a shortcut placed in the Start Menu upon installation.</span></span>

* <span data-ttu-id="b238b-108">Por predefinição, o pacote está instalado para`$env:ProgramFiles\PowerShell\`</span><span class="sxs-lookup"><span data-stu-id="b238b-108">By default the package is installed to `$env:ProgramFiles\PowerShell\`</span></span>
* <span data-ttu-id="b238b-109">Pode iniciar PowerShell através do Menu Iniciar ou`$env:ProgramFiles\PowerShell\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="b238b-109">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="b238b-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b238b-110">Prerequisites</span></span>

<span data-ttu-id="b238b-111">Para ativar a comunicação remota do PowerShell através de WSMan, os seguintes pré-requisitos tem de ser cumpridos:</span><span class="sxs-lookup"><span data-stu-id="b238b-111">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

* <span data-ttu-id="b238b-112">Instalar o [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) nas versões do Windows antes do Windows 10.</span><span class="sxs-lookup"><span data-stu-id="b238b-112">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="b238b-113">Está disponível através de transferência direta ou o Windows Update.</span><span class="sxs-lookup"><span data-stu-id="b238b-113">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="b238b-114">Totalmente aplicado (incluindo pacotes opcionais), sistemas suportados já terão isto instalado.</span><span class="sxs-lookup"><span data-stu-id="b238b-114">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
* <span data-ttu-id="b238b-115">Instalar o Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) ou mais recente ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) no Windows 7 e Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="b238b-115">Install the Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) or newer ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="b238b-116">ZIP</span><span class="sxs-lookup"><span data-stu-id="b238b-116">ZIP</span></span>

<span data-ttu-id="b238b-117">PowerShell binários ZIP arquivos são fornecidos para ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="b238b-117">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="b238b-118">É de salientar que, ao utilizar o arquivo ZIP, não irá obter a verificação de pré-requisitos, como o pacote MSI.</span><span class="sxs-lookup"><span data-stu-id="b238b-118">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="b238b-119">Por isso ordem para a gestão remota através de WSMan funcione corretamente no Windows versões anteriores ao Windows 10, terá de certificar-se do [pré-requisitos](#prerequisites) são cumpridos.</span><span class="sxs-lookup"><span data-stu-id="b238b-119">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="b238b-120">Implementar no servidor de Nano</span><span class="sxs-lookup"><span data-stu-id="b238b-120">Deploying on Nano Server</span></span>

<span data-ttu-id="b238b-121">Estas instruções partem do princípio de que uma versão do PowerShell já está em execução a imagem de servidor Nano e que foi gerado pelo [construtor de imagens do servidor Nano](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="b238b-121">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="b238b-122">Servidor de nano for um SO "sem interface" e implementação dos binários do PowerShell Core pode acontecer de duas formas diferentes:</span><span class="sxs-lookup"><span data-stu-id="b238b-122">Nano Server is a "headless" OS and deployment of PowerShell Core binaries can happen in two different ways:</span></span>

1. <span data-ttu-id="b238b-123">Offline - montar o VHD de servidor Nano e deszipe o conteúdo do ficheiro zip à sua localização escolhida dentro da imagem montada.</span><span class="sxs-lookup"><span data-stu-id="b238b-123">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
1. <span data-ttu-id="b238b-124">Online - transferir o ficheiro zip através de uma sessão do PowerShell e deszipe-lo na sua localização escolhida.</span><span class="sxs-lookup"><span data-stu-id="b238b-124">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="b238b-125">Em ambos os casos, terá da versão do Windows 10 x64 Zip do pacote e terá de executar os comandos dentro de uma instância do PowerShell do "Administrador".</span><span class="sxs-lookup"><span data-stu-id="b238b-125">In both cases, you will need the Windows 10 x64 Zip release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="b238b-126">Implementação offline do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="b238b-126">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="b238b-127">Utilize o utilitário de favorito zip para descomprimir o pacote para um diretório na imagem de servidor Nano montada.</span><span class="sxs-lookup"><span data-stu-id="b238b-127">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
1. <span data-ttu-id="b238b-128">Desmontar a imagem e efetuar o arranque-lo.</span><span class="sxs-lookup"><span data-stu-id="b238b-128">Unmount the image and boot it.</span></span>
1. <span data-ttu-id="b238b-129">Ligar à instância da pasta a receber do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b238b-129">Connect to the inbox instance of Windows PowerShell.</span></span>
1. <span data-ttu-id="b238b-130">Siga as instruções para criar um ponto final de gestão remota utilizando o [outra técnica de instância](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="b238b-130">Follow the instructions to create a remoting endpoint using the [another instance technique](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="b238b-131">Implementação online do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="b238b-131">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="b238b-132">Os passos seguintes irão ajudá-lo através da implementação do PowerShell Core para uma instância em execução de servidor Nano e a configuração do seu ponto final remoto.</span><span class="sxs-lookup"><span data-stu-id="b238b-132">The following steps will guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

* <span data-ttu-id="b238b-133">Ligar à instância da pasta a receber do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b238b-133">Connect to the inbox instance of Windows PowerShell</span></span>

```powershell
$session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
```

* <span data-ttu-id="b238b-134">Copie o ficheiro para a instância de servidor Nano</span><span class="sxs-lookup"><span data-stu-id="b238b-134">Copy the file to the Nano Server instance</span></span>

```powershell
Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
```

* <span data-ttu-id="b238b-135">Introduza a sessão</span><span class="sxs-lookup"><span data-stu-id="b238b-135">Enter the session</span></span>

```powershell
Enter-PSSession $session
```

* <span data-ttu-id="b238b-136">Extrair o ficheiro Zip</span><span class="sxs-lookup"><span data-stu-id="b238b-136">Extract the Zip file</span></span>

```powershell
# Insert the appropriate version.
Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
```

* <span data-ttu-id="b238b-137">Se pretender que o sistema de interação remota com base em WSMan, siga as instruções para criar um ponto final de gestão remota utilizando o [outra técnica de instância](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="b238b-137">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the [another instance technique](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="b238b-138">Instruções para criar um ponto final de gestão remota</span><span class="sxs-lookup"><span data-stu-id="b238b-138">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="b238b-139">PowerShell Core suporta o protocolo de comunicação remota do PowerShell (PSRP) através de SSH e WSMan.</span><span class="sxs-lookup"><span data-stu-id="b238b-139">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="b238b-140">Para mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="b238b-140">For more information, see:</span></span>

* <span data-ttu-id="b238b-141">[SSH comunicação remota do PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="b238b-141">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="b238b-142">[Comunicação remota do WSMan no PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="b238b-142">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="b238b-143">Instruções de instalação de artefactos</span><span class="sxs-lookup"><span data-stu-id="b238b-143">Artifact Installation Instructions</span></span>

<span data-ttu-id="b238b-144">Está a publicar um arquivo com CoreCLR bits em cada compilação CI com [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="b238b-144">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

## <a name="coreclr-artifacts"></a><span data-ttu-id="b238b-145">CoreCLR artefactos</span><span class="sxs-lookup"><span data-stu-id="b238b-145">CoreCLR Artifacts</span></span>

* <span data-ttu-id="b238b-146">Transferir o pacote zip da **artefactos** separador de compilação do específica.</span><span class="sxs-lookup"><span data-stu-id="b238b-146">Download zip package from **artifacts** tab of the particular build.</span></span>
* <span data-ttu-id="b238b-147">Ficheiro zip de desbloqueio: rato no Explorador de ficheiros -> propriedades -> Aplicar 'Desbloquear' -> a caixa de verificação</span><span class="sxs-lookup"><span data-stu-id="b238b-147">Unblock zip file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
* <span data-ttu-id="b238b-148">Extrair o ficheiro zip para `bin` diretório</span><span class="sxs-lookup"><span data-stu-id="b238b-148">Extract zip file to `bin` directory</span></span>
* `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[versões]: https://github.com/PowerShell/PowerShell/releases
[signing]: ../../tools/Sign-Package.ps1
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
