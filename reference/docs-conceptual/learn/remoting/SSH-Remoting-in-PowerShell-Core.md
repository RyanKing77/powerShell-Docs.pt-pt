---
title: Comunicação Remota do PowerShell através de SSH
description: Comunicação remota no PowerShell Core usando SSH
ms.date: 08/14/2018
ms.openlocfilehash: d994a3888b9a372b803a65666634775a8905d63a
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372150"
---
# <a name="powershell-remoting-over-ssh"></a>Comunicação Remota do PowerShell através de SSH

## <a name="overview"></a>Descrição geral

A comunicação remota do PowerShell normalmente usa o WinRM para negociação de conexão e transporte de dados. O SSH agora está disponível para plataformas Linux e Windows e permite a verdadeira comunicação remota do PowerShell de várias plataformas.

O WinRM fornece um modelo de hospedagem robusto para sessões remotas do PowerShell. A comunicação remota baseada em SSH atualmente não dá suporte à configuração de ponto de extremidade remoto e JEA (apenas administração suficiente).

A comunicação remota do SSH permite que você faça a comunicação remota da sessão básica do PowerShell entre computadores Windows e Linux. O SSH Remoting cria um processo de host do PowerShell no computador de destino como um subsistema SSH. Eventualmente, implementaremos um modelo de hospedagem geral, semelhante ao WinRM, para dar suporte à configuração de ponto de extremidade e JEA.

Os `New-PSSession`cmdlets `Enter-PSSession`, `Invoke-Command` e agora têm um novo parâmetro definido para dar suporte a essa nova conexão remota.

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Para criar uma sessão remota, especifique o computador de destino com o `HostName` parâmetro e forneça o nome de usuário `UserName`com. Ao executar os cmdlets de forma interativa, você será solicitado a fornecer uma senha. Você também pode usar a autenticação de chave SSH usando um arquivo de chave privada `KeyFilePath` com o parâmetro.

## <a name="general-setup-information"></a>Informações gerais de instalação

O SSH deve ser instalado em todos os computadores. Instale o cliente SSH (`ssh.exe`) e o servidor (`sshd.exe`) para que você possa remoto de e para os computadores. O OpenSSH para Windows agora está disponível no Windows 10 Build 1809 e no Windows Server 2019. Para obter mais informações, consulte [OpenSSH para Windows](/windows-server/administration/openssh/openssh_overview). Para o Linux, instale o SSH (incluindo o sshd Server) apropriado para sua plataforma. Você também precisa instalar o PowerShell Core do GitHub para obter o recurso de comunicação remota do SSH. O servidor SSH deve ser configurado para criar um subsistema SSH para hospedar um processo do PowerShell no computador remoto. Você também deve configurar habilitar senha ou autenticação baseada em chave.

## <a name="set-up-on-windows-machine"></a>Configurar no computador com Windows

1. Instalar a versão mais recente do [PowerShell Core para Windows](../../install/installing-powershell-core-on-windows.md#msi)

   - Você pode saber se ele tem o suporte a comunicação remota do SSH examinando os conjuntos de parâmetros para`New-PSSession`

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. Instale o Win32 OpenSSH mais recente. Para obter instruções de instalação, consulte [instalação do OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).
3. Edite `sshd_config` o arquivo localizado `$env:ProgramData\ssh`em.

   - Verifique se a autenticação de senha está habilitada

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > Há um bug no OpenSSH para Windows que impede que os espaços funcionem em caminhos executáveis do subsistema. Para obter mais informações, consulte [este problema do GitHub](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

     Uma solução é criar um symlink para o diretório de instalação do PowerShell que não tem espaços:

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     e, em seguida, insira-o no subsistema:

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - Opcionalmente, habilitar a autenticação de chave

     ```
     PubkeyAuthentication yes
     ```

4. Reiniciar o serviço sshd

   ```powershell
   Restart-Service sshd
   ```

5. Adicione o caminho em que o OpenSSH está instalado em sua variável de ambiente Path. Por exemplo, `C:\Program Files\OpenSSH\`. Essa entrada permite que o SSH. exe seja encontrado.

## <a name="set-up-on-linux-ubuntu-1604-machine"></a>Configurar no computador Linux (Ubuntu 16, 4)

1. Instalar a compilação mais recente do [PowerShell Core para Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) do github
2. Instalar o [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) conforme necessário

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. Edite o arquivo sshd_config no local/etc/ssh

   - Verifique se a autenticação de senha está habilitada

   ```
   PasswordAuthentication yes
   ```

   - Adicionar uma entrada de subsistema do PowerShell

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - Opcionalmente, habilitar a autenticação de chave

   ```
   PubkeyAuthentication yes
   ```

4. Reiniciar o serviço sshd

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a>Configurar no computador MacOS

1. Instalar a versão mais recente do [PowerShell Core para MacOS](../../install/installing-powershell-core-on-macos.md)

   - Verifique se a comunicação remota SSH está habilitada seguindo estas etapas:
     - Abrir`System Preferences`
     - Clique em`Sharing`
     - Verificação `Remote Login` -deve-se dizer`Remote Login: On`
     - Permitir acesso aos usuários apropriados

2. Editar o `sshd_config` arquivo no local`/private/etc/ssh/sshd_config`

   - Use seu editor favorito ou

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - Verifique se a autenticação de senha está habilitada

     ```
     PasswordAuthentication yes
     ```

   - Adicionar uma entrada de subsistema do PowerShell

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - Opcionalmente, habilitar a autenticação de chave

     ```
     PubkeyAuthentication yes
     ```

3. Reiniciar o serviço sshd

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a>Autenticação

A comunicação remota do PowerShell sobre SSH depende da troca de autenticação entre o cliente SSH e o serviço SSH e não implementa nenhum esquema de autenticação em si. Isso significa que todos os esquemas de autenticação configurados, incluindo a autenticação multifator, são manipulados pelo SSH e independentes do PowerShell. Por exemplo, você pode configurar o serviço SSH para exigir autenticação de chave pública, bem como uma senha de uso único para maior segurança. A configuração da autenticação multifator está fora do escopo desta documentação. Consulte a documentação do SSH sobre como configurar corretamente a autenticação multifator e validá-la funciona fora do PowerShell antes de tentar usá-la com a comunicação remota do PowerShell.

## <a name="powershell-remoting-example"></a>Exemplo de comunicação remota do PowerShell

A maneira mais fácil de testar a comunicação remota é experimentá-la em um único computador. Neste exemplo, criamos uma sessão remota de volta para o mesmo computador Linux. Estamos usando cmdlets do PowerShell interativamente para que possamos ver prompts do SSH pedindo para verificar o computador host e solicitar uma senha. Você pode fazer a mesma coisa em um computador Windows para garantir que a comunicação remota esteja funcionando. Em seguida, remoto entre computadores alterando o nome do host.

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
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~16.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

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

O comando sudo não funciona na sessão remota para o computador Linux.

## <a name="see-also"></a>Veja Também

[PowerShell Core para Windows](../../install/installing-powershell-core-on-windows.md#msi)

[PowerShell Core para Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[PowerShell Core para MacOS](../../install/installing-powershell-core-on-macos.md)

[OpenSSH para Windows](/windows-server/administration/openssh/openssh_overview)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
