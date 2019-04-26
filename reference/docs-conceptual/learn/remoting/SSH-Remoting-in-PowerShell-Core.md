---
title: Comunicação Remota do PowerShell através de SSH
description: Comunicação remota do PowerShell Core através de SSH
ms.date: 08/14/2018
ms.openlocfilehash: 1d7bcb69c7e784bf745cb5c2633106ea53f6226a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086396"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="b7493-103">Comunicação Remota do PowerShell através de SSH</span><span class="sxs-lookup"><span data-stu-id="b7493-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="b7493-104">Descrição geral</span><span class="sxs-lookup"><span data-stu-id="b7493-104">Overview</span></span>

<span data-ttu-id="b7493-105">Comunicação remota do PowerShell normalmente utiliza WinRM para negociação de ligação e transporte de dados.</span><span class="sxs-lookup"><span data-stu-id="b7493-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="b7493-106">SSH está agora disponível para plataformas Linux e Windows e permite que o verdadeira comunicação remota do PowerShell em várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="b7493-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="b7493-107">WinRM fornece um modelo de hospedagem robusto para sessões remotas do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7493-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="b7493-108">Comunicação remota baseado no SSH atualmente não suporta a configuração de ponto final remoto e JEA (administração apenas suficiente).</span><span class="sxs-lookup"><span data-stu-id="b7493-108">SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="b7493-109">Comunicação remota do SSH permite-lhe fazer a comunicação remota do sessão PowerShell básica entre máquinas Windows e Linux.</span><span class="sxs-lookup"><span data-stu-id="b7493-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="b7493-110">Comunicação remota do SSH cria um processo de host do PowerShell no computador de destino como um subsistema SSH.</span><span class="sxs-lookup"><span data-stu-id="b7493-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="b7493-111">Eventualmente, implementaremos um modelo de hospedagem geral, semelhante ao WinRM, para suportar a configuração do ponto final e JEA.</span><span class="sxs-lookup"><span data-stu-id="b7493-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="b7493-112">O `New-PSSession`, `Enter-PSSession`, e `Invoke-Command` cmdlets têm agora um novo parâmetro definido para suportar esta nova ligação de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="b7493-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="b7493-113">Para criar uma sessão remota, tem de especificar o computador de destino com o `HostName` parâmetro e forneça o nome de utilizador com `UserName`.</span><span class="sxs-lookup"><span data-stu-id="b7493-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="b7493-114">Ao executar os cmdlets interativamente, lhe for pedida uma palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="b7493-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="b7493-115">Além disso, pode utilizar a autenticação de chave SSH através de um ficheiro de chave privado com o `KeyFilePath` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b7493-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="b7493-116">Informações de configuração geral</span><span class="sxs-lookup"><span data-stu-id="b7493-116">General setup information</span></span>

<span data-ttu-id="b7493-117">SSH tem de ser instalado em todas as máquinas.</span><span class="sxs-lookup"><span data-stu-id="b7493-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="b7493-118">Instalar o cliente de SSH (`ssh.exe`) e o servidor (`sshd.exe`) para que possa remoto de e para as máquinas.</span><span class="sxs-lookup"><span data-stu-id="b7493-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="b7493-119">OpenSSH para o Windows agora se encontram disponíveis na compilação 1809 do Windows 10 e Windows Server 2019.</span><span class="sxs-lookup"><span data-stu-id="b7493-119">OpenSSH for Windows is now availabe in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="b7493-120">Para obter mais informações, consulte [OpenSSH para Windows](/windows-server/administration/openssh/openssh_overview).</span><span class="sxs-lookup"><span data-stu-id="b7493-120">For more information, see [OpenSSH for Windows](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="b7493-121">Para o Linux, instale o SSH (incluindo sshd server) apropriado para sua plataforma.</span><span class="sxs-lookup"><span data-stu-id="b7493-121">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="b7493-122">Também tem de instalar o PowerShell Core a partir do GitHub para obter a funcionalidade de comunicação remota SSH.</span><span class="sxs-lookup"><span data-stu-id="b7493-122">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="b7493-123">O servidor SSH tem de ser configurado para criar um subsistema SSH para alojar um processo de PowerShell na máquina remota.</span><span class="sxs-lookup"><span data-stu-id="b7493-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="b7493-124">Também tem de configurar palavras-passe de ativação ou a autenticação baseada em chave.</span><span class="sxs-lookup"><span data-stu-id="b7493-124">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="b7493-125">Configurar na máquina do Windows</span><span class="sxs-lookup"><span data-stu-id="b7493-125">Set up on Windows Machine</span></span>

1. <span data-ttu-id="b7493-126">Instale a versão mais recente do [PowerShell Core para Windows](../../install/installing-powershell-core-on-windows.md#msi)</span><span class="sxs-lookup"><span data-stu-id="b7493-126">Install the latest version of [PowerShell Core for Windows](../../install/installing-powershell-core-on-windows.md#msi)</span></span>

   - <span data-ttu-id="b7493-127">Pode dizer que se tiver o suporte de comunicação remota SSH ao observar o parâmetro define para `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="b7493-127">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="b7493-128">Instale os OpenSSH de Win32 mais recente.</span><span class="sxs-lookup"><span data-stu-id="b7493-128">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="b7493-129">Para obter instruções de instalação, consulte [instalação de OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span><span class="sxs-lookup"><span data-stu-id="b7493-129">For installation instructions, see [Installation of OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>
3. <span data-ttu-id="b7493-130">Editar a `sshd_config` arquivo localizado em `$env:ProgramData\ssh`.</span><span class="sxs-lookup"><span data-stu-id="b7493-130">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   - <span data-ttu-id="b7493-131">Certifique-se de autenticação de palavra-passe está ativada</span><span class="sxs-lookup"><span data-stu-id="b7493-131">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="b7493-132">Há um bug no OpenSSH para Windows que impede que os espaços de trabalhar em caminhos de executável do subsistema.</span><span class="sxs-lookup"><span data-stu-id="b7493-132">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="b7493-133">Para obter mais informações, consulte [este problema do GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="b7493-133">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="b7493-134">Uma solução é criar um symlink para o diretório de instalação do PowerShell que não tem espaços:</span><span class="sxs-lookup"><span data-stu-id="b7493-134">One solution is to create a symlink to the PowerShell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     <span data-ttu-id="b7493-135">e, em seguida, introduza-o no subsistema:</span><span class="sxs-lookup"><span data-stu-id="b7493-135">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="b7493-136">Opcionalmente, ativar a autenticação de chave</span><span class="sxs-lookup"><span data-stu-id="b7493-136">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="b7493-137">Reinicie o serviço de sshd</span><span class="sxs-lookup"><span data-stu-id="b7493-137">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="b7493-138">Adicione o caminho onde o OpenSSH é instalado para a variável de ambiente Path.</span><span class="sxs-lookup"><span data-stu-id="b7493-138">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="b7493-139">Por exemplo, `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="b7493-139">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="b7493-140">Esta entrada permite ssh.exe a serem encontradas.</span><span class="sxs-lookup"><span data-stu-id="b7493-140">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="b7493-141">Configurar a máquina Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="b7493-141">Set up on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="b7493-142">Instalar a versão mais recente [PowerShell Core para Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1404) incorporar a partir do GitHub</span><span class="sxs-lookup"><span data-stu-id="b7493-142">Install the latest [PowerShell Core for Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1404) build from GitHub</span></span>
2. <span data-ttu-id="b7493-143">Instale [SSH do Ubuntu](https://help.ubuntu.com/lts/serverguide/openssh-server.html) conforme necessário</span><span class="sxs-lookup"><span data-stu-id="b7493-143">Install [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="b7493-144">Edite o ficheiro sshd_config em /etc/ssh de localização</span><span class="sxs-lookup"><span data-stu-id="b7493-144">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="b7493-145">Certifique-se de autenticação de palavra-passe está ativada</span><span class="sxs-lookup"><span data-stu-id="b7493-145">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="b7493-146">Adicionar uma entrada de subsistema do PowerShell</span><span class="sxs-lookup"><span data-stu-id="b7493-146">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="b7493-147">Opcionalmente, ativar a autenticação de chave</span><span class="sxs-lookup"><span data-stu-id="b7493-147">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="b7493-148">Reinicie o serviço de sshd</span><span class="sxs-lookup"><span data-stu-id="b7493-148">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="b7493-149">Configurar no computador MacOS</span><span class="sxs-lookup"><span data-stu-id="b7493-149">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="b7493-150">Instalar a versão mais recente [PowerShell Core para MacOS](../../install/installing-powershell-core-on-macos.md) criar</span><span class="sxs-lookup"><span data-stu-id="b7493-150">Install the latest [PowerShell Core for MacOS](../../install/installing-powershell-core-on-macos.md) build</span></span>

   - <span data-ttu-id="b7493-151">Certifique-se de que comunicação remota SSH está ativada, seguindo estes passos:</span><span class="sxs-lookup"><span data-stu-id="b7493-151">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="b7493-152">abrir `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="b7493-152">Open `System Preferences`</span></span>
     - <span data-ttu-id="b7493-153">Clique em `Sharing`</span><span class="sxs-lookup"><span data-stu-id="b7493-153">Click on `Sharing`</span></span>
     - <span data-ttu-id="b7493-154">Verificar `Remote Login` -deverá indicar `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="b7493-154">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="b7493-155">Permitir o acesso aos utilizadores adequados</span><span class="sxs-lookup"><span data-stu-id="b7493-155">Allow access to appropriate users</span></span>

2. <span data-ttu-id="b7493-156">Editar o `sshd_config` ficheiros no local `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="b7493-156">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="b7493-157">Utilizar o seu editor favorito ou</span><span class="sxs-lookup"><span data-stu-id="b7493-157">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="b7493-158">Certifique-se de autenticação de palavra-passe está ativada</span><span class="sxs-lookup"><span data-stu-id="b7493-158">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="b7493-159">Adicionar uma entrada de subsistema do PowerShell</span><span class="sxs-lookup"><span data-stu-id="b7493-159">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="b7493-160">Opcionalmente, ativar a autenticação de chave</span><span class="sxs-lookup"><span data-stu-id="b7493-160">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="b7493-161">Reinicie o serviço de sshd</span><span class="sxs-lookup"><span data-stu-id="b7493-161">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="b7493-162">Autenticação</span><span class="sxs-lookup"><span data-stu-id="b7493-162">Authentication</span></span>

<span data-ttu-id="b7493-163">Comunicação remota do PowerShell através de SSH conta com a troca de autenticação entre o cliente SSH e o serviço SSH e não implementa qualquer esquemas de autenticação em si.</span><span class="sxs-lookup"><span data-stu-id="b7493-163">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span>
<span data-ttu-id="b7493-164">Isso significa que quaisquer esquemas de autenticação configurado, incluindo multi-factor authentication é manipulado por SSH e independente do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7493-164">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span>
<span data-ttu-id="b7493-165">Por exemplo, pode configurar o serviço SSH para exigir autenticação de chave pública, bem como uma palavra-passe Monouso para maior segurança.</span><span class="sxs-lookup"><span data-stu-id="b7493-165">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span>
<span data-ttu-id="b7493-166">Configuração da autenticação multifator está fora do escopo desta documentação.</span><span class="sxs-lookup"><span data-stu-id="b7493-166">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span>
<span data-ttu-id="b7493-167">Consulte a documentação para SSH sobre como configurar a autenticação multifator e validá-la funciona fora do PowerShell antes de tentar usá-lo com o PowerShell remoting corretamente.</span><span class="sxs-lookup"><span data-stu-id="b7493-167">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="b7493-168">Exemplo de comunicação remota do PowerShell</span><span class="sxs-lookup"><span data-stu-id="b7493-168">PowerShell Remoting Example</span></span>

<span data-ttu-id="b7493-169">A maneira mais fácil para testar a comunicação remota é para experimentá-la numa única máquina.</span><span class="sxs-lookup"><span data-stu-id="b7493-169">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="b7493-170">Neste exemplo, vamos criar uma sessão remota para a mesma máquina do Linux.</span><span class="sxs-lookup"><span data-stu-id="b7493-170">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="b7493-171">Estamos a utilizar o PowerShell cmdlets interativamente vemos então solicita a partir do SSH, pedindo para verificar se o computador anfitrião e a pedir uma palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="b7493-171">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="b7493-172">Pode fazer a mesma coisa numa máquina do Windows para garantir a comunicação remota está a funcionar.</span><span class="sxs-lookup"><span data-stu-id="b7493-172">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="b7493-173">Em seguida, remoto entre máquinas, alterando o nome do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="b7493-173">Then remote between machines by changing the host name.</span></span>

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
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
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

### <a name="known-issues"></a><span data-ttu-id="b7493-174">Problemas Conhecidos</span><span class="sxs-lookup"><span data-stu-id="b7493-174">Known Issues</span></span>

<span data-ttu-id="b7493-175">O comando sudo não funciona na sessão remota para máquina Linux.</span><span class="sxs-lookup"><span data-stu-id="b7493-175">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7493-176">Veja Também</span><span class="sxs-lookup"><span data-stu-id="b7493-176">See Also</span></span>

[<span data-ttu-id="b7493-177">O PowerShell Core para Windows</span><span class="sxs-lookup"><span data-stu-id="b7493-177">PowerShell Core for Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="b7493-178">O PowerShell Core para Linux</span><span class="sxs-lookup"><span data-stu-id="b7493-178">PowerShell Core for Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="b7493-179">O PowerShell Core para MacOS</span><span class="sxs-lookup"><span data-stu-id="b7493-179">PowerShell Core for MacOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="b7493-180">OpenSSH para Windows</span><span class="sxs-lookup"><span data-stu-id="b7493-180">OpenSSH for Windows</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="b7493-181">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="b7493-181">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
