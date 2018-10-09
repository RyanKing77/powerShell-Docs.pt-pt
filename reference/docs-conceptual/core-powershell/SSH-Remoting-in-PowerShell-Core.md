---
title: Comunicação Remota do PowerShell através de SSH
description: Comunicação remota do PowerShell Core através de SSH
ms.date: 08/14/2018
ms.openlocfilehash: 84c3896fe28847beb03e930f933bb4a9dfad397f
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851242"
---
# <a name="powershell-remoting-over-ssh"></a>Comunicação Remota do PowerShell através de SSH

## <a name="overview"></a>Descrição geral

Comunicação remota do PowerShell normalmente utiliza WinRM para negociação de ligação e transporte de dados. SSH está agora disponível para plataformas Linux e Windows e permite que o verdadeira comunicação remota do PowerShell em várias plataformas.

WinRM fornece um modelo de hospedagem robusto para sessões remotas do PowerShell. que esta comunicação remota de baseado no SSH de implementação atualmente não suporta a configuração de ponto final remoto e JEA (administração apenas suficiente).

Comunicação remota do SSH permite-lhe fazer a comunicação remota do sessão PowerShell básica entre máquinas Windows e Linux. Comunicação remota do SSH cria um processo de host do PowerShell no computador de destino como um subsistema SSH.
Eventualmente, implementaremos um modelo de hospedagem geral, semelhante ao WinRM, para suportar a configuração do ponto final e JEA.

O `New-PSSession`, `Enter-PSSession`, e `Invoke-Command` cmdlets têm agora um novo parâmetro definido para suportar esta nova ligação de comunicação remota.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Para criar uma sessão remota, tem de especificar o computador de destino com o `HostName` parâmetro e forneça o nome de utilizador com `UserName`. Ao executar os cmdlets interativamente, lhe for pedida uma palavra-passe. Além disso, pode utilizar a autenticação de chave SSH através de um ficheiro de chave privado com o `KeyFilePath` parâmetro.

## <a name="general-setup-information"></a>Informações de configuração geral

SSH tem de ser instalado em todas as máquinas. Instalar o cliente de SSH (`ssh.exe`) e o servidor (`sshd.exe`) para que possa remoto de e para as máquinas. Para Windows, instale [OpenSSH de Win32 do GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).
Para o Linux, instale o SSH (incluindo sshd server) apropriado para sua plataforma. Também tem de instalar o PowerShell Core a partir do GitHub para obter a funcionalidade de comunicação remota SSH. O servidor SSH tem de ser configurado para criar um subsistema SSH para alojar um processo de PowerShell na máquina remota. Também tem de configurar palavras-passe de ativação ou a autenticação baseada em chave.

## <a name="set-up-on-windows-machine"></a>Configurar na máquina do Windows

1. Instale a versão mais recente do [PowerShell Core para Windows](../setup/installing-powershell-core-on-windows.md#msi)

   - Pode dizer que se tiver o suporte de comunicação remota SSH ao observar o parâmetro define para `New-PSSession`

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. Instalar a versão mais recente [OpenSSH de Win32](https://github.com/PowerShell/Win32-OpenSSH/releases) incorporar a partir do GitHub com o [instalação](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH) instruções
3. Edite o ficheiro sshd_config na localização onde instalou o OpenSSH de Win32

   - Certifique-se de autenticação de palavra-passe está ativada

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6.0.4/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > Há um bug no OpenSSH para Windows que impede que os espaços de trabalhar em caminhos de executável do subsistema. Para obter mais informações, consulte [este problema do GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

     Uma solução é criar um symlink para o diretório de instalação do Powershell que não tem espaços:

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.4"
     ```

     e, em seguida, introduza-o no subsistema:

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - Opcionalmente, ativar a autenticação de chave

     ```
     PubkeyAuthentication yes
     ```

4. Reinicie o serviço de sshd

   ```powershell
   Restart-Service sshd
   ```

5. Adicione o caminho onde o OpenSSH é instalado para a variável de ambiente Path. Por exemplo, `C:\Program Files\OpenSSH\`. Esta entrada permite ssh.exe a serem encontradas.

## <a name="set-up-on-linux-ubuntu-1404-machine"></a>Configurar a máquina Linux (Ubuntu 14.04)

1. Instalar a versão mais recente [PowerShell Core para Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404) incorporar a partir do GitHub
2. Instale [SSH do Ubuntu](https://help.ubuntu.com/lts/serverguide/openssh-server.html) conforme necessário

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. Edite o ficheiro sshd_config em /etc/ssh de localização

   - Certifique-se de autenticação de palavra-passe está ativada

   ```
   PasswordAuthentication yes
   ```

   - Adicionar uma entrada de subsistema do PowerShell

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - Opcionalmente, ativar a autenticação de chave

   ```
   PubkeyAuthentication yes
   ```

4. Reinicie o serviço de sshd

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a>Configurar no computador MacOS

1. Instalar a versão mais recente [PowerShell Core para MacOS](../setup/installing-powershell-core-on-macos.md) criar

   - Certifique-se de que comunicação remota SSH está ativada, seguindo estes passos:
     - Aberto `System Preferences`
     - Clique em `Sharing`
     - Verificar `Remote Login` -deverá indicar `Remote Login: On`
     - Permitir o acesso aos utilizadores adequados

2. Editar o `sshd_config` ficheiros no local `/private/etc/ssh/sshd_config`

   - Utilizar o seu editor favorito ou

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - Certifique-se de autenticação de palavra-passe está ativada

     ```
     PasswordAuthentication yes
     ```

   - Adicionar uma entrada de subsistema do PowerShell

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - Opcionalmente, ativar a autenticação de chave

     ```
     PubkeyAuthentication yes
     ```

3. Reinicie o serviço de sshd

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>Autenticação

Comunicação remota do PowerShell através de SSH conta com a troca de autenticação entre o cliente SSH e o serviço SSH e não implementa qualquer esquemas de autenticação em si.
Isso significa que quaisquer esquemas de autenticação configurado, incluindo multi-factor authentication é manipulado por SSH e independente do PowerShell.
Por exemplo, pode configurar o serviço SSH para exigir autenticação de chave pública, bem como uma palavra-passe Monouso para maior segurança.
Configuração da autenticação multifator está fora do escopo desta documentação.
Consulte a documentação para SSH sobre como configurar a autenticação multifator e validá-la funciona fora do PowerShell antes de tentar usá-lo com o PowerShell remoting corretamente.

## <a name="powershell-remoting-example"></a>Exemplo de comunicação remota do PowerShell

A maneira mais fácil para testar a comunicação remota é para experimentá-la numa única máquina. Neste exemplo, vamos criar uma sessão remota para a mesma máquina do Linux. Estamos a utilizar o PowerShell cmdlets interativamente vemos então solicita a partir do SSH, pedindo para verificar se o computador anfitrião e a pedir uma palavra-passe. Pode fazer a mesma coisa numa máquina do Windows para garantir a comunicação remota está a funcionar. Em seguida, remoto entre máquinas, alterando o nome do anfitrião.

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

### <a name="known-issues"></a>Problemas Conhecidos

O comando sudo não funciona na sessão remota para máquina Linux.

## <a name="see-also"></a>Consulte Também

[O PowerShell Core para Windows](../setup/installing-powershell-core-on-windows.md#msi)

[O PowerShell Core para Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[O PowerShell Core para MacOS](../setup/installing-powershell-core-on-macos.md)

[OpenSSH de Win32](https://github.com/PowerShell/Win32-OpenSSH/releases)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)