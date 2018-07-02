# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="60627-101">Comunicação Remota do PowerShell através de SSH</span><span class="sxs-lookup"><span data-stu-id="60627-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="60627-102">Descrição geral</span><span class="sxs-lookup"><span data-stu-id="60627-102">Overview</span></span>

<span data-ttu-id="60627-103">Comunicação remota do PowerShell normalmente utiliza WinRM para negociação de ligação e o transporte de dados.</span><span class="sxs-lookup"><span data-stu-id="60627-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span>
<span data-ttu-id="60627-104">SSH foi escolhido para esta implementação de sistema de interação remota porque esta está agora disponível para plataformas Linux e Windows e permite a comunicação remota do PowerShell do multiplataformas verdadeira.</span><span class="sxs-lookup"><span data-stu-id="60627-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>
<span data-ttu-id="60627-105">No entanto, WinRM também fornece um modelo de alojamento robusto para sessões remotas do PowerShell que esta implementação não ainda.</span><span class="sxs-lookup"><span data-stu-id="60627-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span>
<span data-ttu-id="60627-106">E isto significa que a configuração de ponto final remoto do PowerShell e JEA (apenas suficiente administração) ainda não é suportado nesta implementação.</span><span class="sxs-lookup"><span data-stu-id="60627-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="60627-107">Comunicação remota do PowerShell SSH permite-lhe fazer a comunicação remota do sessão PowerShell básica entre máquinas Windows e Linux.</span><span class="sxs-lookup"><span data-stu-id="60627-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span>
<span data-ttu-id="60627-108">Isto é feito através da criação de um processo no computador de destino como um subsistema SSH de alojamento de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60627-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="60627-109">Eventualmente, este será alterado para um modelo de alojamento mais geral semelhante ao funcionamento da WinRM para suportar a configuração de ponto final e JEA.</span><span class="sxs-lookup"><span data-stu-id="60627-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="60627-110">Os cmdlets New-PSSession, Enter-PSSession e Invoke-Command agora tem um novo parâmetro definido para facilitar esta nova ligação de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="60627-110">The New-PSSession, Enter-PSSession and Invoke-Command cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="60627-111">Este novo conjunto de parâmetros, provavelmente, será alterado, mas por agora permite-lhe criar SSH PSSessions que pode interagir com a linha de comandos ou invocar comandos e scripts no.</span><span class="sxs-lookup"><span data-stu-id="60627-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span>
<span data-ttu-id="60627-112">Especificar o computador de destino com o parâmetro de nome de anfitrião e forneça o nome de utilizador com o nome de utilizador.</span><span class="sxs-lookup"><span data-stu-id="60627-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span>
<span data-ttu-id="60627-113">Ao executar os cmdlets interativamente na linha de comandos do PowerShell lhe-á uma palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="60627-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span>
<span data-ttu-id="60627-114">Mas também tem a opção para utilizar a autenticação de chave SSH e forneça um caminho de ficheiro de chave privada com o parâmetro KeyFilePath.</span><span class="sxs-lookup"><span data-stu-id="60627-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="60627-115">Informações de configuração geral</span><span class="sxs-lookup"><span data-stu-id="60627-115">General setup information</span></span>

<span data-ttu-id="60627-116">SSH é necessário para ser instalado em todas as máquinas.</span><span class="sxs-lookup"><span data-stu-id="60627-116">SSH is required to be installed on all machines.</span></span>
<span data-ttu-id="60627-117">Deve instalar o cliente (ssh.exe) e o servidor (sshd.exe) para que pode experimentar a gestão remota de e para as máquinas.</span><span class="sxs-lookup"><span data-stu-id="60627-117">You should install both client (ssh.exe) and server (sshd.exe) so that you can experiment with remoting to and from the machines.</span></span>
<span data-ttu-id="60627-118">Para o Windows, terá de instalar [Win32 OpenSSH a partir do GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="60627-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="60627-119">Para Linux, terá de instalar o SSH (incluindo sshd server) adequado à sua plataforma.</span><span class="sxs-lookup"><span data-stu-id="60627-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span>
<span data-ttu-id="60627-120">Também precisa de uma compilação de PowerShell recente ou o pacote a partir do GitHub, ter a funcionalidade de comunicação remota SSH.</span><span class="sxs-lookup"><span data-stu-id="60627-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="60627-121">Subsistemas SSH é utilizado para estabelecer um processo do PowerShell no computador remoto e o servidor SSH terão de ser configurado para tal.</span><span class="sxs-lookup"><span data-stu-id="60627-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span>
<span data-ttu-id="60627-122">Além disso, terá de ativar a autenticação de palavra-passe e, opcionalmente, chave de autenticação com base em.</span><span class="sxs-lookup"><span data-stu-id="60627-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="60627-123">A configuração no computador do Windows</span><span class="sxs-lookup"><span data-stu-id="60627-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="60627-124">Instale a versão mais recente do [núcleo de PowerShell para Windows]</span><span class="sxs-lookup"><span data-stu-id="60627-124">Install the latest version of [PowerShell Core for Windows]</span></span>
    - <span data-ttu-id="60627-125">Pode saber que se tiver o suporte de comunicação remota SSH ao observar o parâmetro define para New-PSSession</span><span class="sxs-lookup"><span data-stu-id="60627-125">You can tell if it has the SSH remoting support by looking at the parameter sets for New-PSSession</span></span>

    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```

1. <span data-ttu-id="60627-126">Instalar a versão mais recente [Win32 OpenSSH] incorporar a partir do GitHub utilizando o [instalação] instruções</span><span class="sxs-lookup"><span data-stu-id="60627-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
1. <span data-ttu-id="60627-127">Edite o ficheiro de sshd_config na localização onde instalou Win32 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="60627-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>
    - <span data-ttu-id="60627-128">Certifique-se a autenticação de palavra-passe está ativada</span><span class="sxs-lookup"><span data-stu-id="60627-128">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="60627-129">Adicionar uma entrada de subsistema de PowerShell, substitua `c:/program files/powershell/6.0.0/pwsh.exe` com o caminho correto para a versão que pretende utilizar</span><span class="sxs-lookup"><span data-stu-id="60627-129">Add a PowerShell subsystem entry, replace `c:/program files/powershell/6.0.0/pwsh.exe` with the correct path to the version you want to use</span></span>

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```
    
    > [!NOTE]
    <span data-ttu-id="60627-130">Não há um erro OpenSSH para Windows que impede que os espaços de trabalhar em caminhos de executável do subsistema.</span><span class="sxs-lookup"><span data-stu-id="60627-130">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span>
    <span data-ttu-id="60627-131">Consulte [este problema no GitHub para obter mais informações](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="60627-131">See [this issue on GitHub for more information](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>
    
    <span data-ttu-id="60627-132">É uma solução criar um symlink para o diretório de instalação do Powershell não contém espaços:</span><span class="sxs-lookup"><span data-stu-id="60627-132">One solution is to create a symlink to the Powershell installation directory that does not contain spaces:</span></span>
    
    ```powershell
    mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
    ```

    <span data-ttu-id="60627-133">e, em seguida, introduza-o no subsistema:</span><span class="sxs-lookup"><span data-stu-id="60627-133">and then enter it in the subsystem:</span></span>
 
    ```
    Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="60627-134">Opcionalmente, ativar a autenticação de chave</span><span class="sxs-lookup"><span data-stu-id="60627-134">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="60627-135">Reinicie o serviço de sshd</span><span class="sxs-lookup"><span data-stu-id="60627-135">Restart the sshd service</span></span>

    ```powershell
    Restart-Service sshd
    ```

1. <span data-ttu-id="60627-136">Adicione o caminho onde OpenSSH está instalado o seu caminho Env variável</span><span class="sxs-lookup"><span data-stu-id="60627-136">Add the path where OpenSSH is installed to your Path Env Variable</span></span>
    - <span data-ttu-id="60627-137">Isto deve ser juntamente as linhas de `C:\Program Files\OpenSSH\`</span><span class="sxs-lookup"><span data-stu-id="60627-137">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
    - <span data-ttu-id="60627-138">Este procedimento permite que o ssh.exe ser encontrado</span><span class="sxs-lookup"><span data-stu-id="60627-138">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="60627-139">A configuração no computador Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="60627-139">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="60627-140">Instalar a versão mais recente [PowerShell Core para Linux] incorporar a partir do GitHub</span><span class="sxs-lookup"><span data-stu-id="60627-140">Install the latest [PowerShell Core for Linux] build from GitHub</span></span>
1. <span data-ttu-id="60627-141">Instalar [Ubuntu SSH] conforme necessário</span><span class="sxs-lookup"><span data-stu-id="60627-141">Install [Ubuntu SSH] as needed</span></span>

    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```

1. <span data-ttu-id="60627-142">Edite o ficheiro de sshd_config na localização /etc/ssh</span><span class="sxs-lookup"><span data-stu-id="60627-142">Edit the sshd_config file at location /etc/ssh</span></span>
    - <span data-ttu-id="60627-143">Certifique-se a autenticação de palavra-passe está ativada</span><span class="sxs-lookup"><span data-stu-id="60627-143">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="60627-144">Adicionar uma entrada de subsistema de PowerShell</span><span class="sxs-lookup"><span data-stu-id="60627-144">Add a PowerShell subsystem entry</span></span>

    ```
    Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="60627-145">Opcionalmente, ativar a autenticação de chave</span><span class="sxs-lookup"><span data-stu-id="60627-145">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="60627-146">Reinicie o serviço de sshd</span><span class="sxs-lookup"><span data-stu-id="60627-146">Restart the sshd service</span></span>

    ```bash
    sudo service sshd restart
    ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="60627-147">No MacOS máquina o programa de configuração</span><span class="sxs-lookup"><span data-stu-id="60627-147">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="60627-148">Instalar a versão mais recente [núcleo de PowerShell para MacOS] criar</span><span class="sxs-lookup"><span data-stu-id="60627-148">Install the latest [PowerShell Core for MacOS] build</span></span>
    - <span data-ttu-id="60627-149">Certifique-se a que comunicação remota SSH está ativada, seguindo estes passos:</span><span class="sxs-lookup"><span data-stu-id="60627-149">Make sure SSH Remoting is enabled by following these steps:</span></span>
      - <span data-ttu-id="60627-150">abrir `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="60627-150">Open `System Preferences`</span></span>
      - <span data-ttu-id="60627-151">Clique em `Sharing`</span><span class="sxs-lookup"><span data-stu-id="60627-151">Click on `Sharing`</span></span>
      - <span data-ttu-id="60627-152">Verifique `Remote Login` -deverá indicar `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="60627-152">Check `Remote Login` - Should say `Remote Login: On`</span></span>
      - <span data-ttu-id="60627-153">Permitir o acesso aos utilizadores adequados</span><span class="sxs-lookup"><span data-stu-id="60627-153">Allow access to appropriate users</span></span>
1. <span data-ttu-id="60627-154">Editar o `sshd_config` ficheiro na localização `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="60627-154">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>
    - <span data-ttu-id="60627-155">Utilizar o seu editor favorito ou</span><span class="sxs-lookup"><span data-stu-id="60627-155">Use your favorite editor or</span></span>

    ```bash
    sudo nano /private/etc/ssh/sshd_config
    ```

    - <span data-ttu-id="60627-156">Certifique-se a autenticação de palavra-passe está ativada</span><span class="sxs-lookup"><span data-stu-id="60627-156">Make sure password authentication is enabled</span></span>

    ```
    PasswordAuthentication yes
    ```

    - <span data-ttu-id="60627-157">Adicionar uma entrada de subsistema de PowerShell</span><span class="sxs-lookup"><span data-stu-id="60627-157">Add a PowerShell subsystem entry</span></span>

    ```
    Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
    ```

    - <span data-ttu-id="60627-158">Opcionalmente, ativar a autenticação de chave</span><span class="sxs-lookup"><span data-stu-id="60627-158">Optionally enable key authentication</span></span>

    ```
    PubkeyAuthentication yes
    ```

1. <span data-ttu-id="60627-159">Reinicie o serviço de sshd</span><span class="sxs-lookup"><span data-stu-id="60627-159">Restart the sshd service</span></span>

    ```bash
    sudo launchctl stop com.openssh.sshd
    sudo launchctl start com.openssh.sshd
    ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="60627-160">Exemplo de comunicação remota do PowerShell</span><span class="sxs-lookup"><span data-stu-id="60627-160">PowerShell Remoting Example</span></span>

<span data-ttu-id="60627-161">A forma mais fácil para testar a comunicação remota é experimente apenas num único computador.</span><span class="sxs-lookup"><span data-stu-id="60627-161">The easiest way to test remoting is to just try it on a single machine.</span></span>
<span data-ttu-id="60627-162">Aqui crio uma sessão remota para a mesma máquina na caixa de Linux.</span><span class="sxs-lookup"><span data-stu-id="60627-162">Here I will create a remote session back to the same machine on a Linux box.</span></span>
<span data-ttu-id="60627-163">Tenha em atenção que estiver a utilizar os cmdlets do PowerShell a partir de uma linha de comandos para vemos pede ao utilizador a partir do SSH que solicitam a certifique-se de que o computador anfitrião, bem como os pedidos de palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="60627-163">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span>
<span data-ttu-id="60627-164">Pode fazê-lo a mesma coisa num computador Windows para assegurar a gestão remota está a funcionar existe e, em seguida, remoto entre máquinas alterando simplesmente o nome de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="60627-164">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
PS /home/TestUser> $session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:

PS /home/TestUser> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available

PS /home/TestUser> Enter-PSSession $session

[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession

PS /home/TestUser> Invoke-Command $session -ScriptBlock { Get-Process powershell }

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1


#
# Linux to Windows
#
PS /home/TestUser> Enter-PSSession -HostName WinVM1 -UserName PTestName
PTestName@WinVM1s password:

[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver

Microsoft Windows [Version 10.0.10586]

[WinVM1]: PS C:\Users\PTestName\Documents>

#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.

PS C:\Users\PSUser\Documents> $session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
PS C:\Users\PSUser\Documents> $session

 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available


PS C:\Users\PSUser\Documents> Enter-PSSession -Session $session
[WinVM2]: PS C:\Users\PSRemoteUser\Documents> $PSVersionTable

Name                           Value
----                           -----
PSEdition                      Core
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
SerializationVersion           1.1.0.1
BuildVersion                   3.0.0.0
CLRVersion
PSVersion                      6.0.0-alpha
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
GitCommitId                    v6.0.0-alpha.17


[WinVM2]: PS C:\Users\PSRemoteUser\Documents>
```

### <a name="known-issues"></a><span data-ttu-id="60627-165">Problemas Conhecidos</span><span class="sxs-lookup"><span data-stu-id="60627-165">Known Issues</span></span>

1. <span data-ttu-id="60627-166">comando sudo não funcionar na sessão remota, a máquina do Linux.</span><span class="sxs-lookup"><span data-stu-id="60627-166">sudo command does not work in remote session to Linux machine.</span></span>

[Núcleo de PowerShell para Windows]: ../setup/installing-powershell-core-on-windows.md#msi
[PowerShell Core for Windows]: ../setup/installing-powershell-core-on-windows.md#msi
[PowerShell Core para Linux]: ../setup/installing-powershell-core-on-linux.md#ubuntu-1404
[PowerShell Core for Linux]: ../setup/installing-powershell-core-on-linux.md#ubuntu-1404
[Núcleo de PowerShell para MacOS]: ../setup/installing-powershell-core-on-macos.md
[PowerShell Core for MacOS]: ../setup/installing-powershell-core-on-macos.md
[Win32 OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH/releases
[Instalação]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[installation]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
