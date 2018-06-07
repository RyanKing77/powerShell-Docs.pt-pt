# <a name="powershell-remoting-over-ssh"></a>Comunicação Remota do PowerShell através de SSH

## <a name="overview"></a>Descrição geral

Comunicação remota do PowerShell normalmente utiliza WinRM para negociação de ligação e o transporte de dados.
SSH foi escolhido para esta implementação de sistema de interação remota porque esta está agora disponível para plataformas Linux e Windows e permite a comunicação remota do PowerShell do multiplataformas verdadeira.
No entanto, WinRM também fornece um modelo de alojamento robusto para sessões remotas do PowerShell que esta implementação não ainda.
E isto significa que a configuração de ponto final remoto do PowerShell e JEA (apenas suficiente administração) ainda não é suportado nesta implementação.

Comunicação remota do PowerShell SSH permite-lhe fazer a comunicação remota do sessão PowerShell básica entre máquinas Windows e Linux.
Isto é feito através da criação de um processo no computador de destino como um subsistema SSH de alojamento de PowerShell.
Eventualmente, este será alterado para um modelo de alojamento mais geral semelhante ao funcionamento da WinRM para suportar a configuração de ponto final e JEA.

Os cmdlets New-PSSession, Enter-PSSession e Invoke-Command agora tem um novo parâmetro definido para facilitar esta nova ligação de comunicação remota

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Este novo conjunto de parâmetros, provavelmente, será alterado, mas por agora permite-lhe criar SSH PSSessions que pode interagir com a linha de comandos ou invocar comandos e scripts no.
Especificar o computador de destino com o parâmetro de nome de anfitrião e forneça o nome de utilizador com o nome de utilizador.
Ao executar os cmdlets interativamente na linha de comandos do PowerShell lhe-á uma palavra-passe.
Mas também tem a opção para utilizar a autenticação de chave SSH e forneça um caminho de ficheiro de chave privada com o parâmetro KeyFilePath.

## <a name="general-setup-information"></a>Informações de configuração geral

SSH é necessário para ser instalado em todas as máquinas.
Deve instalar o cliente (ssh.exe) e o servidor (sshd.exe) para que pode experimentar a gestão remota de e para as máquinas.
Para o Windows, terá de instalar [Win32 OpenSSH a partir do GitHub](https://github.com/PowerShell/Win32-OpenSSH/releases).
Para Linux, terá de instalar o SSH (incluindo sshd server) adequado à sua plataforma.
Também precisa de uma compilação de PowerShell recente ou o pacote a partir do GitHub, ter a funcionalidade de comunicação remota SSH.
Subsistemas SSH é utilizado para estabelecer um processo do PowerShell no computador remoto e o servidor SSH terão de ser configurado para tal.
Além disso, terá de ativar a autenticação de palavra-passe e, opcionalmente, chave de autenticação com base em.

## <a name="setup-on-windows-machine"></a>A configuração no computador do Windows

1. Instale a versão mais recente do [núcleo de PowerShell para Windows]
    - Pode saber que se tiver o suporte de comunicação remota SSH ao observar o parâmetro define para New-PSSession

    ```powershell
    PS> Get-Command New-PSSession -syntax
    New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
    ```

1. Instalar a versão mais recente [O Win32 OpenSSH] incorporar a partir do GitHub utilizando o [instalação] instruções
1. Edite o ficheiro de sshd_config na localização onde instalou Win32 OpenSSH
    - Certifique-se a autenticação de palavra-passe está ativada

    ```
    PasswordAuthentication yes
    ```

    - Adicionar uma entrada de subsistema de PowerShell, substitua `c:/program files/powershell/6.0.0/pwsh.exe` com o caminho correto para a versão que pretende utilizar

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

1. Adicione o caminho onde OpenSSH está instalado o seu caminho Env variável
    - Isto deve ser juntamente as linhas de `C:\Program Files\OpenSSH\`
    - Este procedimento permite que o ssh.exe ser encontrado

## <a name="setup-on-linux-ubuntu-1404-machine"></a>A configuração no computador Linux (Ubuntu 14.04)

1. Instalar a versão mais recente [PowerShell para Linux] incorporar a partir do GitHub
1. Instalar [Ubuntu SSH] conforme necessário

    ```bash
    sudo apt install openssh-client
    sudo apt install openssh-server
    ```

1. Edite o ficheiro de sshd_config na localização /etc/ssh
    - Certifique-se a autenticação de palavra-passe está ativada

    ```
    PasswordAuthentication yes
    ```

    - Adicionar uma entrada de subsistema de PowerShell

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

## <a name="setup-on-macos-machine"></a>No MacOS máquina o programa de configuração

1. Instalar a versão mais recente [PowerShell para MacOS] criar
    - Certifique-se a que comunicação remota SSH está ativada, seguindo estes passos:
      - Abrir `System Preferences`
      - Clique em `Sharing`
      - Verifique `Remote Login` -deverá indicar `Remote Login: On`
      - Permitir o acesso aos utilizadores adequados
1. Editar o `sshd_config` ficheiro na localização `/private/etc/ssh/sshd_config`
    - Utilizar o seu editor favorito ou

    ```bash
    sudo nano /private/etc/ssh/sshd_config
    ```

    - Certifique-se a autenticação de palavra-passe está ativada

    ```
    PasswordAuthentication yes
    ```

    - Adicionar uma entrada de subsistema de PowerShell

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

A forma mais fácil para testar a comunicação remota é experimente apenas num único computador.
Aqui crio uma sessão remota para a mesma máquina na caixa de Linux.
Tenha em atenção que estiver a utilizar os cmdlets do PowerShell a partir de uma linha de comandos para vemos pede ao utilizador a partir do SSH que solicitam a certifique-se de que o computador anfitrião, bem como os pedidos de palavra-passe.
Pode fazê-lo a mesma coisa num computador Windows para assegurar a gestão remota está a funcionar existe e, em seguida, remoto entre máquinas alterando simplesmente o nome de anfitrião.

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

### <a name="known-issues"></a>Problemas Conhecidos

1. comando sudo não funcionar na sessão remota, a máquina do Linux.

[Núcleo de PowerShell para Windows]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi
[O Win32 OpenSSH]: https://github.com/PowerShell/Win32-OpenSSH/releases
[Instalação]: https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH
[PowerShell para Linux]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#ubuntu-1404
[Ubuntu SSH]: https://help.ubuntu.com/lts/serverguide/openssh-server.html
[PowerShell para MacOS]: https://github.com/PowerShell/PowerShell/blob/master/docs/installation/macos.md#macos-1012
