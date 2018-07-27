# <a name="installing-powershell-core-on-linux"></a>Instalar o PowerShell Core no Linux

Suporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27 ] [ fedora], [Fedora 28][fedora], e [Arch Linux][arch].

Para as distribuições de Linux que não são suportadas oficialmente, pode tentar usar a [PowerShell AppImage][lai].
Também pode tentar implementar os binários do PowerShell diretamente com a Linux [ `tar.gz` arquivo][tar], mas terá de configurar as dependências necessárias, com base no sistema operacional nos passos separados.

Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.
Depois do pacote está instalado, execute `pwsh` partir de um terminal.

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a>Instalar versões de pré-visualização

Ao instalar uma versão de pré-visualização do PowerShell Core para Linux através de um repositório de pacotes, o nome do pacote é alterado de `powershell` para `powershell-preview`.

Instalar através de transferência direta não é alterada, além do nome de ficheiro.

Esta é uma tabela de comandos para instalar os pacotes de estável e pré-visualização com os vários gestores de pacote:

|Distribution(s)|Comando estável | Comando de pré-visualização |
|---------------|---------------|-----------------|
| Ubuntu, Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS, Red Hat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| OpenSUSE |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Instalação através do repositório do pacote - Ubuntu 14.04

O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).
Este é o método preferido.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Superutilizador, registar-se o repositório da Microsoft.
De ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` para atualizar a instalação.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Instalação através de transferência direta - Ubuntu 14.04

Transferir o pacote Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` partir a [versões][] página para o computador do Ubuntu.

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> O `dpkg -i` comando falha com dependências por cumprir.
> O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.

### <a name="uninstallation---ubuntu-1404"></a>Desinstalação - Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Instalação através do repositório do pacote - Ubuntu 16.04

O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).
Este é o método preferido.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Instalação através de transferência direta - Ubuntu 16.04

Transferir o pacote Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` partir a [versões][] página para o computador do Ubuntu.

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> O `dpkg -i` comando falha com dependências por cumprir.
> O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.

### <a name="uninstallation---ubuntu-1604"></a>Desinstalação - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a>Ubuntu 17.10

> [!NOTE]
> Foi adicionado suporte para Ubuntu 17.04 após `6.1.0-preview.2`

### <a name="installation-via-package-repository---ubuntu-1710"></a>Instalação através do repositório do pacote - Ubuntu 17.10

O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).
Este é o método preferido.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.10/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.

### <a name="installation-via-direct-download---ubuntu-1710"></a>Instalação através de transferência direta - Ubuntu 17.10

Transferir o pacote Debian `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` partir a [versões][] página para o computador do Ubuntu.

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> O `dpkg -i` comando falha com dependências por cumprir.
> O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.

### <a name="uninstallation---ubuntu-1710"></a>Desinstalação - Ubuntu 17.10

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

> [!NOTE]
> Foi adicionado suporte para Ubuntu 18.04 após `6.1.0-preview.2`

### <a name="installation-via-package-repository---ubuntu-1804"></a>Instalação através do repositório do pacote - Ubuntu 18.04

O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).
Este é o método preferido.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell-preview

# Start PowerShell
pwsh-preview
```

Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Instalação através de transferência direta - Ubuntu 18.04

Transferir o pacote Debian `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` partir a [versões][] página para o computador do Ubuntu.

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> O `dpkg -i` comando falha com dependências por cumprir.
> O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.

### <a name="uninstallation---ubuntu-1804"></a>Desinstalação - Ubuntu 18.04

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Instalação através do repositório do pacote - Debian 8

O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).
Este é o método preferido.

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.

### <a name="installation-via-direct-download---debian-8"></a>Instalação através de transferência direta - Debian 8

Transferir o pacote Debian `powershell_6.0.2-1.debian.8_amd64.deb` partir a [versões][] página para o computador Debian.

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> O `dpkg -i` comando falha com dependências por cumprir.
> O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.

### <a name="uninstallation---debian-8"></a>Desinstalação - Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Instalação através do repositório do pacote - Debian 9

O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).
Este é o método preferido.

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.

### <a name="installation-via-direct-download---debian-9"></a>Instalação através de transferência direta - Debian 9

Transferir o pacote Debian `powershell_6.0.2-1.debian.9_amd64.deb` partir a [versões][] página para o computador Debian.

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Desinstalação - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> Este pacote também funciona no Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Instalação através do repositório de pacotes (preferencial) - CentOS 7

O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Depois de registar o repositório da Microsoft uma vez como Superutilizador, apenas tem de utilizar `sudo yum update powershell` para atualizar o PowerShell.

### <a name="installation-via-direct-download---centos-7"></a>Instalação através de transferência direta - CentOS 7

Usando [CentOS 7][], transfira o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` da [versões][] página para o computador de CentOS.

Em seguida, execute o seguinte no terminal:

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Também pode instalar o RPM sem a etapa intermediária de baixá-lo:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Desinstalação - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Instalação através do repositório de pacotes (preferencial) - Red Hat Enterprise Linux (RHEL) 7

O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Depois de registar o repositório da Microsoft uma vez como Superutilizador, apenas tem de utilizar `sudo yum update powershell` para atualizar o PowerShell.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Instalação através de transferência direta - Red Hat Enterprise Linux (RHEL) 7

Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` partir de [versões][] página para o computador Red Hat Enterprise Linux.

Em seguida, execute o seguinte no terminal:

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Também pode instalar o RPM sem a etapa intermediária de baixá-lo:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Desinstalação - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a>OpenSUSE 42.3

Quando instalar o PowerShell Core, `zypper` pode reportar o erro seguinte:

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

Neste caso, certifique-se de que um ecrã compatível com `libcurl` biblioteca está presente, verificando que o seguinte comando mostra o `libcurl4` como instalado o pacote:

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

Em seguida, escolha o `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solução ao instalar o pacote do PowerShell.

### <a name="installation-via-package-repository-preferred---opensuse-423"></a>Instalação através do repositório de pacotes (preferencial) - OpenSUSE 42.3

O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Repository
zypper ar https://packages.microsoft.com/rhel/7/prod/

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-423"></a>Instalação através de transferência direta - OpenSUSE 42.3

Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` partir a [versões][] página na máquina OpenSUSE.

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Também pode instalar o RPM sem a etapa intermediária de baixá-lo:

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a>Desinstalação - OpenSUSE 42.3

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28 só é suportada no PowerShell Core 6.1 e versões mais recentes.

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>Instalação através do repositório de pacotes (preferencial) - Fedora 27, Fedora 28

O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>Instalação através de transferência direta - Fedora 27, Fedora 28

Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` partir a [versões][] página na máquina Fedora.

Em seguida, execute o seguinte no terminal:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Também pode instalar o RPM sem a etapa intermediária de baixá-lo:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>Desinstalação - Fedora 27, Fedora 28

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

> [!NOTE]
> O suporte de arquitetura é experimental.

PowerShell está disponível a partir da [Arch Linux][] utilizador repositório (AUR).

* Pode ser compilado com o [etiquetados de versão mais recente versão][arch-release]
* Pode ser compilada a partir do [consolidação mais recente a mestre][arch-git]
* Pode ser instalado utilizando o [binário da versão mais recente][arch-bin]

Pacotes no AUR são mantida de Comunidade – não existe nenhum suporte oficial.

Para obter mais informações sobre como instalar pacotes do AUR, consulte a [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou da Comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a>AppImage do Linux

> [!NOTE]
> Suporte de AppImage é experimental

Utilizando uma distribuição Linux recente, Baixe o AppImage `powershell-6.0.1-x86_64.AppImage` partir do [versões][] página na máquina Linux.

Em seguida, execute o seguinte no terminal:

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

O [AppImage][] permite-lhe executar o PowerShell sem instalá-lo.
É um aplicativo portáteis que agrupa o PowerShell e as respetivas dependências (incluindo as dependências do sistema de .NET Core) num único pacote coeso.
Este pacote é um único binário que funciona de forma independente da distribuição de Linux do utilizador.

[appimage]: http://appimage.org/

## <a name="kali"></a>Kali

> [!NOTE]
> O suporte de Kali é experimental.

### <a name="installation"></a>Instalação

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>Executar o PowerShell sem instalá-lo no Kali mais recente (implementar Kali GNU/Linux)

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>Desinstalação - Kali

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> O suporte de Raspbian é experimental.

Atualmente, o PowerShell só é suportado em Raspbian Stretch.

Também CoreCLR (e, portanto, o PowerShell Core) só funcionam em dispositivos de instalador de plataforma 2 e 3 de instalador de plataforma como outros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ter um processador não suportado.

Baixe [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e siga o [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) obtê-lo em seu Pi.

### <a name="installation"></a>Instalação

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

Opcionalmente, pode criar um link simbólico para conseguir iniciar PowerShell sem especificar o caminho para o "pwsh" binário

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>Desinstalação - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Arquivos binários

Binário de PowerShell `tar.gz` arquivos são fornecidos para plataformas Linux ativar cenários de implementação avançada.

### <a name="dependencies"></a>Dependências

PowerShell cria binários portátil para todas as distribuições do Linux.
Mas o tempo de execução do .NET Core requer diferentes dependências em diversas distribuições e, por conseguinte, o PowerShell faz o mesmo.

O gráfico seguinte mostra as dependências de .NET Core 2.0 são suportadas oficialmente em distribuições do Linux.

| SO                 | Dependências |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.10       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch.) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE OpenSUSE 42.3 | libunwind, libcurl, bibliotecas de openssl, libicu |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, bibliotecas de openssl, libicu, openssl10 de compatibilidade |

Para implementar os binários do PowerShell distribuições de Linux que não são suportados oficialmente, terá de instalar as dependências necessárias para o sistema operacional de destino nos passos separados.
Por exemplo, nossa [Amazon Linux dockerfile] [ amazon-dockerfile] instala as dependências primeiro e, em seguida, extrai a Linux `tar.gz` arquivo.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Instalação - arquivos binários

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.2/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a>A desinstalar arquivos binários

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Caminhos

* `$PSHOME` é `/opt/microsoft/powershell/6.0.2/`
* Perfis de utilizador serão lido a partir `~/.config/powershell/profile.ps1`
* Perfis predefinidos serão lido a partir `$PSHOME/profile.ps1`
* Módulos de utilizador serão lido a partir `~/.local/share/powershell/Modules`
* Módulos partilhados serão lido a partir `/usr/local/share/powershell/Modules`
* Módulos padrão serão lido a partir `$PSHOME/Modules`
* Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Os perfis de respeitam a configuração de por anfitrião do PowerShell, para que os perfis de anfitrião específico padrão existe em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.

PowerShell respeita os [XDG Base diretório especificação] [ xdg-bds] no Linux.

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
