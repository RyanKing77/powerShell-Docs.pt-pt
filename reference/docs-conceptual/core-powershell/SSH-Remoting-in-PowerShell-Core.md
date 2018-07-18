
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="0106b-101">Comunicação Remota do PowerShell através de SSH</span><span class="sxs-lookup"><span data-stu-id="0106b-101">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="0106b-102">Descrição geral</span><span class="sxs-lookup"><span data-stu-id="0106b-102">Overview</span></span>

<span data-ttu-id="0106b-103">Comunicação remota do PowerShell normalmente utiliza WinRM para negociação de ligação e transporte de dados.</span><span class="sxs-lookup"><span data-stu-id="0106b-103">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span>
<span data-ttu-id="0106b-104">SSH foi escolhido para esta implementação de comunicação remota, uma vez que está agora disponível para plataformas Linux e Windows e permite que o verdadeira comunicação remota do PowerShell em várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="0106b-104">SSH was chosen for this remoting implementation since it is now available for both Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>
<span data-ttu-id="0106b-105">No entanto, WinRM também fornece um modelo de hospedagem robusto para sessões remotas do PowerShell que essa implementação ainda não faz.</span><span class="sxs-lookup"><span data-stu-id="0106b-105">However, WinRM also provides a robust hosting model for PowerShell remote sessions which this implementation does not yet do.</span></span>
<span data-ttu-id="0106b-106">E isso significa que a configuração de ponto final remoto do PowerShell e JEA (administração Just Enough) ainda não é suportada nesta implementação.</span><span class="sxs-lookup"><span data-stu-id="0106b-106">And this means that PowerShell remote endpoint configuration and JEA (Just Enough Administration) is not yet supported in this implementation.</span></span>

<span data-ttu-id="0106b-107">Comunicação remota do PowerShell SSH permite-lhe fazer a comunicação remota do sessão PowerShell básica entre máquinas Windows e Linux.</span><span class="sxs-lookup"><span data-stu-id="0106b-107">PowerShell SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span>
<span data-ttu-id="0106b-108">Isso é feito através da criação de um PowerShell que aloja o processo no computador de destino como um subsistema SSH.</span><span class="sxs-lookup"><span data-stu-id="0106b-108">This is done by creating a PowerShell hosting process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="0106b-109">Eventualmente, isso será alterado para um modelo de hospedagem mais geral semelhante ao funcionamento de WinRM para oferecer suporte à configuração do ponto final e JEA.</span><span class="sxs-lookup"><span data-stu-id="0106b-109">Eventually this will be changed to a more general hosting model similar to how WinRM works in order to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="0106b-110">O `New-PSSession`, `Enter-PSSession` e `Invoke-Command` cmdlets têm agora um novo parâmetro definido para facilitar esta nova ligação de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="0106b-110">The `New-PSSession`, `Enter-PSSession` and `Invoke-Command` cmdlets now have a new parameter set to facilitate this new remoting connection</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="0106b-111">Este novo conjunto de parâmetros vai provavelmente mudar, mas por agora permite-lhe criar SSH PSSessions que pode interagir com a partir da linha de comandos ou invocar comandos e scripts.</span><span class="sxs-lookup"><span data-stu-id="0106b-111">This new parameter set will likely change but for now allows you to create SSH PSSessions that you can interact with from the command line or invoke commands and scripts on.</span></span>
<span data-ttu-id="0106b-112">Especificar o computador de destino com o parâmetro de nome de anfitrião e forneça o nome de utilizador com o nome de utilizador.</span><span class="sxs-lookup"><span data-stu-id="0106b-112">You specify the target machine with the HostName parameter and provide the user name with UserName.</span></span>
<span data-ttu-id="0106b-113">Ao executar os cmdlets interativamente na linha de comandos do PowerShell, será solicitado para uma palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="0106b-113">When running the cmdlets interactively at the PowerShell command line you will be prompted for a password.</span></span>
<span data-ttu-id="0106b-114">Mas também tem a opção para utilizar a autenticação de chave SSH e fornecer um caminho de ficheiro de chave privada com o parâmetro KeyFilePath.</span><span class="sxs-lookup"><span data-stu-id="0106b-114">But you also have the option to use SSH key authentication and provide a private key file path with the KeyFilePath parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="0106b-115">Informações de configuração geral</span><span class="sxs-lookup"><span data-stu-id="0106b-115">General setup information</span></span>

<span data-ttu-id="0106b-116">O SSH é necessário para ser instalado em todas as máquinas.</span><span class="sxs-lookup"><span data-stu-id="0106b-116">SSH is required to be installed on all machines.</span></span>
<span data-ttu-id="0106b-117">Deve instalar ambas as cliente (`ssh.exe`) e o servidor (`sshd.exe`) para que pode experimentar com a comunicação remota de e para as máquinas.</span><span class="sxs-lookup"><span data-stu-id="0106b-117">You should install both client (`ssh.exe`) and server (`sshd.exe`) so that you can experiment with remoting to and from the machines.</span></span>
<span data-ttu-id="0106b-118">Para Windows terá de instalar [OpenSSH de Win32 do GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="0106b-118">For Windows you will need to install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="0106b-119">Para Linux terá de instalar o SSH (incluindo sshd server) apropriado para sua plataforma.</span><span class="sxs-lookup"><span data-stu-id="0106b-119">For Linux you will need to install SSH (including sshd server) appropriate to your platform.</span></span>
<span data-ttu-id="0106b-120">Também terá de uma compilação recente do PowerShell ou o pacote do GitHub, ter a funcionalidade de comunicação remota SSH.</span><span class="sxs-lookup"><span data-stu-id="0106b-120">You will also need a recent PowerShell build or package from GitHub having the SSH remoting feature.</span></span>
<span data-ttu-id="0106b-121">Subsistemas SSH é utilizado para estabelecer um processo de PowerShell na máquina remota e o servidor SSH tem de ser configurada para isso.</span><span class="sxs-lookup"><span data-stu-id="0106b-121">SSH subsystems is used to establish a PowerShell process on the remote machine and the SSH server will need to be configured for that.</span></span>
<span data-ttu-id="0106b-122">Além disso terá de ativar a autenticação de palavra-passe e, opcionalmente, chave de autenticação com base.</span><span class="sxs-lookup"><span data-stu-id="0106b-122">In addition you will need to enable password authentication and optionally key based authentication.</span></span>

## <a name="setup-on-windows-machine"></a><span data-ttu-id="0106b-123">Programa de configuração na máquina do Windows</span><span class="sxs-lookup"><span data-stu-id="0106b-123">Setup on Windows Machine</span></span>

1. <span data-ttu-id="0106b-124">Instale a versão mais recente do [PowerShell Core para Windows]</span><span class="sxs-lookup"><span data-stu-id="0106b-124">Install the latest version of [PowerShell Core for Windows]</span></span>
   - <span data-ttu-id="0106b-125">Pode dizer que se tiver o suporte de comunicação remota SSH ao observar o parâmetro define para `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="0106b-125">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

1. <span data-ttu-id="0106b-126">Instalar a compilação mais recente do [OpenSSH de Win32] a partir do GitHub com as instruções de [instalação]</span><span class="sxs-lookup"><span data-stu-id="0106b-126">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
1. <span data-ttu-id="0106b-127">Edite o ficheiro sshd_config na localização onde instalou o OpenSSH de Win32</span><span class="sxs-lookup"><span data-stu-id="0106b-127">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>
   - <span data-ttu-id="0106b-128">Certifique-se de autenticação de palavra-passe está ativada</span><span class="sxs-lookup"><span data-stu-id="0106b-128">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    > [!NOTE]
    > <span data-ttu-id="0106b-129">Há um bug no OpenSSH para Windows que impede que os espaços de trabalhar em caminhos de executável do subsistema.</span><span class="sxs-lookup"><span data-stu-id="0106b-129">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span>
    > <span data-ttu-id="0106b-130">Ver [este problema no GitHub para obter mais informações](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="0106b-130">See [this issue on GitHub for more information](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

    <span data-ttu-id="0106b-131">Uma solução é criar um symlink para o diretório de instalação do Powershell que não contém espaços:</span><span class="sxs-lookup"><span data-stu-id="0106b-131">One solution is to create a symlink to the Powershell installation directory that does not contain spaces:</span></span>

    ```powershell
    mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
    ```

    <span data-ttu-id="0106b-132">e, em seguida, introduza-o no subsistema:</span><span class="sxs-lookup"><span data-stu-id="0106b-132">and then enter it in the subsystem:</span></span>

    ```
    Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
    ```

   ```
   Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="0106b-133">Opcionalmente, ativar a autenticação de chave</span><span class="sxs-lookup"><span data-stu-id="0106b-133">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="0106b-134">Reinicie o serviço de sshd</span><span class="sxs-lookup"><span data-stu-id="0106b-134">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

1. <span data-ttu-id="0106b-135">Adicionar o caminho onde o OpenSSH é instalado para o seu caminho Env variável</span><span class="sxs-lookup"><span data-stu-id="0106b-135">Add the path where OpenSSH is installed to your Path Env Variable</span></span>
   - <span data-ttu-id="0106b-136">Isso deve ser moldes de `C:\Program Files\OpenSSH\`</span><span class="sxs-lookup"><span data-stu-id="0106b-136">This should be along the lines of `C:\Program Files\OpenSSH\`</span></span>
   - <span data-ttu-id="0106b-137">Este procedimento permite que o ssh.exe a serem encontradas</span><span class="sxs-lookup"><span data-stu-id="0106b-137">This allows for the ssh.exe to be found</span></span>

## <a name="setup-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="0106b-138">Programa de configuração na máquina Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="0106b-138">Setup on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="0106b-139">Instalar a compilação mais recente do [PowerShell Core para Linux] a partir do GitHub</span><span class="sxs-lookup"><span data-stu-id="0106b-139">Install the latest [PowerShell Core for Linux] build from GitHub</span></span>
1. <span data-ttu-id="0106b-140">Instalar o [Ubuntu SSH] conforme necessário</span><span class="sxs-lookup"><span data-stu-id="0106b-140">Install [Ubuntu SSH] as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. <span data-ttu-id="0106b-141">Edite o ficheiro sshd_config em /etc/ssh de localização</span><span class="sxs-lookup"><span data-stu-id="0106b-141">Edit the sshd_config file at location /etc/ssh</span></span>
   - <span data-ttu-id="0106b-142">Certifique-se de autenticação de palavra-passe está ativada</span><span class="sxs-lookup"><span data-stu-id="0106b-142">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="0106b-143">Adicionar uma entrada de subsistema do PowerShell</span><span class="sxs-lookup"><span data-stu-id="0106b-143">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="0106b-144">Opcionalmente, ativar a autenticação de chave</span><span class="sxs-lookup"><span data-stu-id="0106b-144">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="0106b-145">Reinicie o serviço de sshd</span><span class="sxs-lookup"><span data-stu-id="0106b-145">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="setup-on-macos-machine"></a><span data-ttu-id="0106b-146">Configurar no computador MacOS</span><span class="sxs-lookup"><span data-stu-id="0106b-146">Setup on MacOS Machine</span></span>

1. <span data-ttu-id="0106b-147">Instalar a compilação mais recente do [PowerShell Core para MacOS]</span><span class="sxs-lookup"><span data-stu-id="0106b-147">Install the latest [PowerShell Core for MacOS] build</span></span>
   - <span data-ttu-id="0106b-148">Certifique-se de que comunicação remota SSH está ativada, seguindo estes passos:</span><span class="sxs-lookup"><span data-stu-id="0106b-148">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="0106b-149">Aberto `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="0106b-149">Open `System Preferences`</span></span>
     - <span data-ttu-id="0106b-150">Clique em `Sharing`</span><span class="sxs-lookup"><span data-stu-id="0106b-150">Click on `Sharing`</span></span>
     - <span data-ttu-id="0106b-151">Verificar `Remote Login` -deverá indicar `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="0106b-151">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="0106b-152">Permitir o acesso aos utilizadores adequados</span><span class="sxs-lookup"><span data-stu-id="0106b-152">Allow access to appropriate users</span></span>
1. <span data-ttu-id="0106b-153">Editar o `sshd_config` ficheiros no local `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="0106b-153">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>
   - <span data-ttu-id="0106b-154">Utilizar o seu editor favorito ou</span><span class="sxs-lookup"><span data-stu-id="0106b-154">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="0106b-155">Certifique-se de autenticação de palavra-passe está ativada</span><span class="sxs-lookup"><span data-stu-id="0106b-155">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="0106b-156">Adicionar uma entrada de subsistema do PowerShell</span><span class="sxs-lookup"><span data-stu-id="0106b-156">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="0106b-157">Opcionalmente, ativar a autenticação de chave</span><span class="sxs-lookup"><span data-stu-id="0106b-157">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

1. <span data-ttu-id="0106b-158">Reinicie o serviço de sshd</span><span class="sxs-lookup"><span data-stu-id="0106b-158">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="0106b-159">Exemplo de comunicação remota do PowerShell</span><span class="sxs-lookup"><span data-stu-id="0106b-159">PowerShell Remoting Example</span></span>

<span data-ttu-id="0106b-160">A maneira mais fácil para testar a comunicação remota é para apenas a experimentá-la numa única máquina.</span><span class="sxs-lookup"><span data-stu-id="0106b-160">The easiest way to test remoting is to just try it on a single machine.</span></span>
<span data-ttu-id="0106b-161">Aqui, vou criar uma sessão remota volta à mesma máquina numa caixa de Linux.</span><span class="sxs-lookup"><span data-stu-id="0106b-161">Here I will create a remote session back to the same machine on a Linux box.</span></span>
<span data-ttu-id="0106b-162">Observe que estou usando cmdlets do PowerShell num prompt de comando, para que podemos ver pedidos a partir do SSH pedindo para verificar se o computador anfitrião, bem como os pedidos de palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="0106b-162">Notice that I am using PowerShell cmdlets from a command prompt so we see prompts from SSH asking to verify the host computer as well as password prompts.</span></span>
<span data-ttu-id="0106b-163">Pode fazer a mesma coisa numa máquina de Windows para assegurar a comunicação remota está a funcionar lá e remoto, em seguida, entre máquinas, simplesmente alterando o nome de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="0106b-163">You can do the same thing on a Windows machine to ensure remoting is working there and then remote between machines by simply changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            UbuntuVM1       RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1
```

```powershell
#
# Linux to Windows
#
Enter-PSSession -HostName WinVM1 -UserName PTestName
```

```output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```output
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

### <a name="known-issues"></a><span data-ttu-id="0106b-164">Problemas Conhecidos</span><span class="sxs-lookup"><span data-stu-id="0106b-164">Known Issues</span></span>

- <span data-ttu-id="0106b-165">comando sudo não funciona na sessão remota para máquina Linux.</span><span class="sxs-lookup"><span data-stu-id="0106b-165">sudo command does not work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="0106b-166">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="0106b-166">See Also</span></span>

[<span data-ttu-id="0106b-167">O PowerShell Core para Windows</span><span class="sxs-lookup"><span data-stu-id="0106b-167">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="0106b-168">O PowerShell Core para Linux</span><span class="sxs-lookup"><span data-stu-id="0106b-168">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="0106b-169">O PowerShell Core para MacOS</span><span class="sxs-lookup"><span data-stu-id="0106b-169">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="0106b-170">OpenSSH de Win32</span><span class="sxs-lookup"><span data-stu-id="0106b-170">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="0106b-171">instalação</span><span class="sxs-lookup"><span data-stu-id="0106b-171">installation</span></span>](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[<span data-ttu-id="0106b-172">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="0106b-172">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)