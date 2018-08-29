---
title: Comunicação Remota do PowerShell através de SSH
description: Comunicação remota do PowerShell Core através de SSH
ms.date: 08/14/2018
ms.openlocfilehash: 1de034d667aa9a377e5460e7eb474402c690cb42
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133836"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="800c0-103">Comunicação Remota do PowerShell através de SSH</span><span class="sxs-lookup"><span data-stu-id="800c0-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="800c0-104">Descrição geral</span><span class="sxs-lookup"><span data-stu-id="800c0-104">Overview</span></span>

<span data-ttu-id="800c0-105">Comunicação remota do PowerShell normalmente utiliza WinRM para negociação de ligação e transporte de dados.</span><span class="sxs-lookup"><span data-stu-id="800c0-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="800c0-106">SSH está agora disponível para plataformas Linux e Windows e permite que o verdadeira comunicação remota do PowerShell em várias plataformas.</span><span class="sxs-lookup"><span data-stu-id="800c0-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="800c0-107">WinRM fornece um modelo de hospedagem robusto para sessões remotas do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="800c0-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="800c0-108">que esta comunicação remota de baseado no SSH de implementação atualmente não suporta a configuração de ponto final remoto e JEA (administração apenas suficiente).</span><span class="sxs-lookup"><span data-stu-id="800c0-108">which this implementation SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="800c0-109">Comunicação remota do SSH permite-lhe fazer a comunicação remota do sessão PowerShell básica entre máquinas Windows e Linux.</span><span class="sxs-lookup"><span data-stu-id="800c0-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="800c0-110">Comunicação remota do SSH cria um processo de host do PowerShell no computador de destino como um subsistema SSH.</span><span class="sxs-lookup"><span data-stu-id="800c0-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span>
<span data-ttu-id="800c0-111">Eventualmente, implementaremos um modelo de hospedagem geral, semelhante ao WinRM, para suportar a configuração do ponto final e JEA.</span><span class="sxs-lookup"><span data-stu-id="800c0-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="800c0-112">O `New-PSSession`, `Enter-PSSession`, e `Invoke-Command` cmdlets têm agora um novo parâmetro definido para suportar esta nova ligação de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="800c0-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="800c0-113">Para criar uma sessão remota, tem de especificar o computador de destino com o `HostName` parâmetro e forneça o nome de utilizador com `UserName`.</span><span class="sxs-lookup"><span data-stu-id="800c0-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="800c0-114">Ao executar os cmdlets interativamente, lhe for pedida uma palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="800c0-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="800c0-115">Além disso, pode utilizar a autenticação de chave SSH através de um ficheiro de chave privado com o `KeyFilePath` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="800c0-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="800c0-116">Informações de configuração geral</span><span class="sxs-lookup"><span data-stu-id="800c0-116">General setup information</span></span>

<span data-ttu-id="800c0-117">SSH tem de ser instalado em todas as máquinas.</span><span class="sxs-lookup"><span data-stu-id="800c0-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="800c0-118">Instalar o cliente de SSH (`ssh.exe`) e o servidor (`sshd.exe`) para que possa remoto de e para as máquinas.</span><span class="sxs-lookup"><span data-stu-id="800c0-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="800c0-119">Para Windows, instale [OpenSSH de Win32 do GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span><span class="sxs-lookup"><span data-stu-id="800c0-119">For Windows, install [Win32 OpenSSH from GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).</span></span>
<span data-ttu-id="800c0-120">Para o Linux, instale o SSH (incluindo sshd server) apropriado para sua plataforma.</span><span class="sxs-lookup"><span data-stu-id="800c0-120">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="800c0-121">Também tem de instalar o PowerShell Core a partir do GitHub para obter a funcionalidade de comunicação remota SSH.</span><span class="sxs-lookup"><span data-stu-id="800c0-121">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="800c0-122">O servidor SSH tem de ser configurado para criar um subsistema SSH para alojar um processo de PowerShell na máquina remota.</span><span class="sxs-lookup"><span data-stu-id="800c0-122">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="800c0-123">Também tem de configurar palavras-passe de ativação ou a autenticação baseada em chave.</span><span class="sxs-lookup"><span data-stu-id="800c0-123">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="800c0-124">Configurar na máquina do Windows</span><span class="sxs-lookup"><span data-stu-id="800c0-124">Set up on Windows Machine</span></span>

1. <span data-ttu-id="800c0-125">Instale a versão mais recente do [PowerShell Core para Windows]</span><span class="sxs-lookup"><span data-stu-id="800c0-125">Install the latest version of [PowerShell Core for Windows]</span></span>

   - <span data-ttu-id="800c0-126">Pode dizer que se tiver o suporte de comunicação remota SSH ao observar o parâmetro define para `New-PSSession`</span><span class="sxs-lookup"><span data-stu-id="800c0-126">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="800c0-127">Instalar a compilação mais recente do [OpenSSH de Win32] a partir do GitHub com as instruções de [instalação]</span><span class="sxs-lookup"><span data-stu-id="800c0-127">Install the latest [Win32 OpenSSH] build from GitHub using the [installation] instructions</span></span>
3. <span data-ttu-id="800c0-128">Edite o ficheiro sshd_config na localização onde instalou o OpenSSH de Win32</span><span class="sxs-lookup"><span data-stu-id="800c0-128">Edit the sshd_config file at the location where you installed Win32 OpenSSH</span></span>

   - <span data-ttu-id="800c0-129">Certifique-se de autenticação de palavra-passe está ativada</span><span class="sxs-lookup"><span data-stu-id="800c0-129">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.4/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="800c0-130">Há um bug no OpenSSH para Windows que impede que os espaços de trabalhar em caminhos de executável do subsistema.</span><span class="sxs-lookup"><span data-stu-id="800c0-130">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="800c0-131">Para obter mais informações, consulte [este problema do GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span><span class="sxs-lookup"><span data-stu-id="800c0-131">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="800c0-132">Uma solução é criar um symlink para o diretório de instalação do Powershell que não tem espaços:</span><span class="sxs-lookup"><span data-stu-id="800c0-132">One solution is to create a symlink to the Powershell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.4"
     ```

     <span data-ttu-id="800c0-133">e, em seguida, introduza-o no subsistema:</span><span class="sxs-lookup"><span data-stu-id="800c0-133">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="800c0-134">Opcionalmente, ativar a autenticação de chave</span><span class="sxs-lookup"><span data-stu-id="800c0-134">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="800c0-135">Reinicie o serviço de sshd</span><span class="sxs-lookup"><span data-stu-id="800c0-135">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="800c0-136">Adicione o caminho onde o OpenSSH é instalado para a variável de ambiente Path.</span><span class="sxs-lookup"><span data-stu-id="800c0-136">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="800c0-137">Por exemplo, `C:\Program Files\OpenSSH\`.</span><span class="sxs-lookup"><span data-stu-id="800c0-137">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="800c0-138">Esta entrada permite ssh.exe a serem encontradas.</span><span class="sxs-lookup"><span data-stu-id="800c0-138">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1404-machine"></a><span data-ttu-id="800c0-139">Configurar a máquina Linux (Ubuntu 14.04)</span><span class="sxs-lookup"><span data-stu-id="800c0-139">Set up on Linux (Ubuntu 14.04) Machine</span></span>

1. <span data-ttu-id="800c0-140">Instalar a compilação mais recente do [PowerShell Core para Linux] a partir do GitHub</span><span class="sxs-lookup"><span data-stu-id="800c0-140">Install the latest [PowerShell Core for Linux] build from GitHub</span></span>
2. <span data-ttu-id="800c0-141">Instalar o [Ubuntu SSH] conforme necessário</span><span class="sxs-lookup"><span data-stu-id="800c0-141">Install [Ubuntu SSH] as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="800c0-142">Edite o ficheiro sshd_config em /etc/ssh de localização</span><span class="sxs-lookup"><span data-stu-id="800c0-142">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="800c0-143">Certifique-se de autenticação de palavra-passe está ativada</span><span class="sxs-lookup"><span data-stu-id="800c0-143">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="800c0-144">Adicionar uma entrada de subsistema do PowerShell</span><span class="sxs-lookup"><span data-stu-id="800c0-144">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="800c0-145">Opcionalmente, ativar a autenticação de chave</span><span class="sxs-lookup"><span data-stu-id="800c0-145">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="800c0-146">Reinicie o serviço de sshd</span><span class="sxs-lookup"><span data-stu-id="800c0-146">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="800c0-147">Configurar no computador MacOS</span><span class="sxs-lookup"><span data-stu-id="800c0-147">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="800c0-148">Instalar a compilação mais recente do [PowerShell Core para MacOS]</span><span class="sxs-lookup"><span data-stu-id="800c0-148">Install the latest [PowerShell Core for MacOS] build</span></span>

   - <span data-ttu-id="800c0-149">Certifique-se de que comunicação remota SSH está ativada, seguindo estes passos:</span><span class="sxs-lookup"><span data-stu-id="800c0-149">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="800c0-150">Aberto `System Preferences`</span><span class="sxs-lookup"><span data-stu-id="800c0-150">Open `System Preferences`</span></span>
     - <span data-ttu-id="800c0-151">Clique em `Sharing`</span><span class="sxs-lookup"><span data-stu-id="800c0-151">Click on `Sharing`</span></span>
     - <span data-ttu-id="800c0-152">Verificar `Remote Login` -deverá indicar `Remote Login: On`</span><span class="sxs-lookup"><span data-stu-id="800c0-152">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="800c0-153">Permitir o acesso aos utilizadores adequados</span><span class="sxs-lookup"><span data-stu-id="800c0-153">Allow access to appropriate users</span></span>

2. <span data-ttu-id="800c0-154">Editar o `sshd_config` ficheiros no local `/private/etc/ssh/sshd_config`</span><span class="sxs-lookup"><span data-stu-id="800c0-154">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="800c0-155">Utilizar o seu editor favorito ou</span><span class="sxs-lookup"><span data-stu-id="800c0-155">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="800c0-156">Certifique-se de autenticação de palavra-passe está ativada</span><span class="sxs-lookup"><span data-stu-id="800c0-156">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="800c0-157">Adicionar uma entrada de subsistema do PowerShell</span><span class="sxs-lookup"><span data-stu-id="800c0-157">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="800c0-158">Opcionalmente, ativar a autenticação de chave</span><span class="sxs-lookup"><span data-stu-id="800c0-158">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="800c0-159">Reinicie o serviço de sshd</span><span class="sxs-lookup"><span data-stu-id="800c0-159">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a><span data-ttu-id="800c0-160">Exemplo de comunicação remota do PowerShell</span><span class="sxs-lookup"><span data-stu-id="800c0-160">PowerShell Remoting Example</span></span>

<span data-ttu-id="800c0-161">A maneira mais fácil para testar a comunicação remota é para experimentá-la numa única máquina.</span><span class="sxs-lookup"><span data-stu-id="800c0-161">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="800c0-162">Neste exemplo, vamos criar uma sessão remota para a mesma máquina do Linux.</span><span class="sxs-lookup"><span data-stu-id="800c0-162">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="800c0-163">Estamos a utilizar o PowerShell cmdlets interativamente vemos então solicita a partir do SSH, pedindo para verificar se o computador anfitrião e a pedir uma palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="800c0-163">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="800c0-164">Pode fazer a mesma coisa numa máquina do Windows para garantir a comunicação remota está a funcionar.</span><span class="sxs-lookup"><span data-stu-id="800c0-164">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="800c0-165">Em seguida, remoto entre máquinas, alterando o nome do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="800c0-165">Then remote between machines by changing the host name.</span></span>

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

### <a name="known-issues"></a><span data-ttu-id="800c0-166">Problemas Conhecidos</span><span class="sxs-lookup"><span data-stu-id="800c0-166">Known Issues</span></span>

<span data-ttu-id="800c0-167">O comando sudo não funciona na sessão remota para máquina Linux.</span><span class="sxs-lookup"><span data-stu-id="800c0-167">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="800c0-168">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="800c0-168">See Also</span></span>

[<span data-ttu-id="800c0-169">O PowerShell Core para Windows</span><span class="sxs-lookup"><span data-stu-id="800c0-169">PowerShell Core for Windows</span></span>](../setup/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="800c0-170">O PowerShell Core para Linux</span><span class="sxs-lookup"><span data-stu-id="800c0-170">PowerShell Core for Linux</span></span>](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[<span data-ttu-id="800c0-171">O PowerShell Core para MacOS</span><span class="sxs-lookup"><span data-stu-id="800c0-171">PowerShell Core for MacOS</span></span>](../setup/installing-powershell-core-on-macos.md)

[<span data-ttu-id="800c0-172">OpenSSH de Win32</span><span class="sxs-lookup"><span data-stu-id="800c0-172">Win32 OpenSSH</span></span>](https://github.com/PowerShell/Win32-OpenSSH/releases)

[<span data-ttu-id="800c0-173">instalação</span><span class="sxs-lookup"><span data-stu-id="800c0-173">installation</span></span>](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[<span data-ttu-id="800c0-174">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="800c0-174">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
