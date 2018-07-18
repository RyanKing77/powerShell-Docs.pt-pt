
# <a name="powershell-remoting-over-ssh"></a>Comunicação Remota do PowerShell através de SSH

## <a name="overview"></a>Descrição geral

Comunicação remota do PowerShell normalmente utiliza WinRM para negociação de ligação e transporte de dados.
SSH foi escolhido para esta implementação de comunicação remota, uma vez que está agora disponível para plataformas Linux e Windows e permite que o verdadeira comunicação remota do PowerShell em várias plataformas.
No entanto, WinRM também fornece um modelo de hospedagem robusto para sessões remotas do PowerShell que essa implementação ainda não faz.
E isso significa que a configuração de ponto final remoto do PowerShell e JEA (administração Just Enough) ainda não é suportada nesta implementação.

Comunicação remota do PowerShell SSH permite-lhe fazer a comunicação remota do sessão PowerShell básica entre máquinas Windows e Linux.
Isso é feito através da criação de um PowerShell que aloja o processo no computador de destino como um subsistema SSH.
Eventualmente, isso será alterado para um modelo de hospedagem mais geral semelhante ao funcionamento de WinRM para oferecer suporte à configuração do ponto final e JEA.

O `New-PSSession`, `Enter-PSSession` e `Invoke-Command` cmdlets têm agora um novo parâmetro definido para facilitar esta nova ligação de comunicação remota

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Este novo conjunto de parâmetros vai provavelmente mudar, mas por agora permite-lhe criar SSH PSSessions que pode interagir com a partir da linha de comandos ou invocar comandos e scripts.
Especificar o computador de destino com o parâmetro de nome de anfitrião e forneça o nome de utilizador com o nome de utilizador.
Ao executar os cmdlets interativamente na linha de comandos do PowerShell, será solicitado para uma palavra-passe.
Mas também tem a opção para utilizar a autenticação de chave SSH e fornecer um caminho de ficheiro de chave privada com o parâmetro KeyFilePath.

## <a name="general-setup-information"></a>Informações de configuração geral

O SSH é necessário para ser instalado em todas as máquinas.
Deve instalar ambas as cliente (`ssh.exe`) e o servidor (`sshd.exe`) para que pode experimentar com a comunicação remota de e para as máquinas.
Para Windows terá de instalar [OpenSSH de Win32 do GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).
Para Linux terá de instalar o SSH (incluindo sshd server) apropriado para sua plataforma.
Também terá de uma compilação recente do PowerShell ou o pacote do GitHub, ter a funcionalidade de comunicação remota SSH.
Subsistemas SSH é utilizado para estabelecer um processo de PowerShell na máquina remota e o servidor SSH tem de ser configurada para isso.
Além disso terá de ativar a autenticação de palavra-passe e, opcionalmente, chave de autenticação com base.

## <a name="setup-on-windows-machine"></a>Programa de configuração na máquina do Windows

1. Instale a versão mais recente do [PowerShell Core para Windows]
   - Pode dizer que se tiver o suporte de comunicação remota SSH ao observar o parâmetro define para `New-PSSession`

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

1. Instalar a compilação mais recente do [OpenSSH de Win32] a partir do GitHub com as instruções de [instalação]
1. Edite o ficheiro sshd_config na localização onde instalou o OpenSSH de Win32
   - Certifique-se de autenticação de palavra-passe está ativada

   ```
   PasswordAuthentication yes
   ```

    ```
    Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
    ```

    > [!NOTE]
    > Há um bug no OpenSSH para Windows que impede que os espaços de trabalhar em caminhos de executável do subsistema.
    > Ver [este problema no GitHub para obter mais informações](https://github.com/PowerShell/Win32-OpenSSH/issues/784).

    Uma solução é criar um symlink para o diretório de instalação do Powershell que não contém espaços:

    ```powershell
    mklink /D c:\pwsh "C:\Program Files\PowerShell\6.0.0"
    ```

    e, em seguida, introduza-o no subsistema:

    ```
    Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
    ```

   ```
   Subsystem    powershell c:/program files/powershell/6.0.0/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   - Opcionalmente, ativar a autenticação de chave

   ```
   PubkeyAuthentication yes
   ```

1. Reinicie o serviço de sshd

   ```powershell
   Restart-Service sshd
   ```

1. Adicionar o caminho onde o OpenSSH é instalado para o seu caminho Env variável
   - Isso deve ser moldes de `C:\Program Files\OpenSSH\`
   - Este procedimento permite que o ssh.exe a serem encontradas

## <a name="setup-on-linux-ubuntu-1404-machine"></a>Programa de configuração na máquina Linux (Ubuntu 14.04)

1. Instalar a compilação mais recente do [PowerShell Core para Linux] a partir do GitHub
1. Instalar o [Ubuntu SSH] conforme necessário

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. Edite o ficheiro sshd_config em /etc/ssh de localização
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

1. Reinicie o serviço de sshd

   ```bash
   sudo service sshd restart
   ```

## <a name="setup-on-macos-machine"></a>Configurar no computador MacOS

1. Instalar a compilação mais recente do [PowerShell Core para MacOS]
   - Certifique-se de que comunicação remota SSH está ativada, seguindo estes passos:
     - Aberto `System Preferences`
     - Clique em `Sharing`
     - Verificar `Remote Login` -deverá indicar `Remote Login: On`
     - Permitir o acesso aos utilizadores adequados
1. Editar o `sshd_config` ficheiros no local `/private/etc/ssh/sshd_config`
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

1. Reinicie o serviço de sshd

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="powershell-remoting-example"></a>Exemplo de comunicação remota do PowerShell

A maneira mais fácil para testar a comunicação remota é para apenas a experimentá-la numa única máquina.
Aqui, vou criar uma sessão remota volta à mesma máquina numa caixa de Linux.
Observe que estou usando cmdlets do PowerShell num prompt de comando, para que podemos ver pedidos a partir do SSH pedindo para verificar se o computador anfitrião, bem como os pedidos de palavra-passe.
Pode fazer a mesma coisa numa máquina de Windows para assegurar a comunicação remota está a funcionar lá e remoto, em seguida, entre máquinas, simplesmente alterando o nome de anfitrião.

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

### <a name="known-issues"></a>Problemas Conhecidos

- comando sudo não funciona na sessão remota para máquina Linux.

## <a name="see-also"></a>Consulte Também

[O PowerShell Core para Windows](../setup/installing-powershell-core-on-windows.md#msi)

[O PowerShell Core para Linux](../setup/installing-powershell-core-on-linux.md#ubuntu-1404)

[O PowerShell Core para MacOS](../setup/installing-powershell-core-on-macos.md)

[OpenSSH de Win32](https://github.com/PowerShell/Win32-OpenSSH/releases)

[instalação](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)

[Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)