# <a name="installing-powershell-core-on-macos-and-linux"></a>Instalar o PowerShell Core no macOS e Linux

Suporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25 ] [ fed25], [Fedora 26][fed26], [arquitetura Linux][arch]e [macOS 10.12][mac].

Para as distribuições do Linux que não são suportadas oficialmente, pode tentar utilizar o [PowerShell AppImage][lai]. Também pode tentar implementar os binários de PowerShell diretamente com o Linux [ `tar.gz` arquivo][tar], mas terá de configurar as dependências necessárias com base no SO em passos separados.

Todos os pacotes estão disponíveis no nosso GitHub [versões][] página. Depois do pacote está instalado, executar `pwsh` de um terminal.

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fed25]: #fedora-25
[fed26]: #fedora-26
[arch]: #arch-linux
[lai]: #linux-appimage
[mac]: #macos-1012
[tar]: #binary-archives

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Instalação através do repositório de pacote - Ubuntu 14.04

PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações). Este é o método preferido.

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

Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Instalação através de transferência direta - Ubuntu 14.04

Transferir o pacote Debian `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` do [versões][] página para a máquina Ubuntu.

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> Tenha em atenção que `dpkg -i` irá falhar com dependências unmet; o comando seguinte, `apt-get install -f` resolve estes e, em seguida, termina a configurar o pacote do PowerShell.

### <a name="uninstallation---ubuntu-1404"></a>Desinstalação - Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Instalação através do repositório de pacote - Ubuntu 16.04

PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).
Este é o método preferido.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Instalação através de transferência direta - Ubuntu 16.04

Transferir o pacote Debian `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` do [versões][] página para a máquina Ubuntu:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> Tenha em atenção que `dpkg -i` irá falhar com dependências unmet; o comando seguinte, `apt-get install -f` resolve estes e, em seguida, termina a configurar o pacote do PowerShell.

### <a name="uninstallation---ubuntu-1604"></a>Desinstalação - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a>Ubuntu 17.04

### <a name="installation-via-package-repository---ubuntu-1704"></a>Instalação através do repositório de pacote - Ubuntu 17.04

PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).
Este é o método preferido.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/17.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.

### <a name="installation-via-direct-download---ubuntu-1704"></a>Instalação através de transferência direta - Ubuntu 17.04

Transferir o pacote Debian `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` do [versões][] página para a máquina Ubuntu:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> Tenha em atenção que `dpkg -i` irá falhar com dependências unmet; o comando seguinte, `apt-get install -f` resolve estes e, em seguida, termina a configurar o pacote do PowerShell.

### <a name="uninstallation---ubuntu-1704"></a>Desinstalação - Ubuntu 17.04

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Instalação através do repositório de pacote - Debian 8

PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).
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

Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.

### <a name="installation-via-direct-download---debian-8"></a>Instalação através de transferência direta - Debian 8

Transferir o pacote Debian `powershell_6.0.0-1.debian.8_amd64.deb` do [versões][] página para a máquina Debian:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> Tenha em atenção que `dpkg -i` irá falhar com dependências unmet; o comando seguinte, `apt-get install -f` resolve estes e, em seguida, termina a configurar o pacote do PowerShell.

### <a name="uninstallation---debian-8"></a>Desinstalação - Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Instalação através do repositório de pacote - Debian 9

PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).
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

Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.

### <a name="installation-via-direct-download---debian-9"></a>Instalação através de transferência direta - Debian 9

Transferir o pacote Debian `powershell_6.0.0-1.debian.9_amd64.deb` do [versões][] página para a máquina Debian:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> Tenha em atenção que `dpkg -i` irá falhar com dependências unmet; o comando seguinte, `apt-get install -f` resolve estes e, em seguida, termina a configurar o pacote do PowerShell.

### <a name="uninstallation---debian-9"></a>Desinstalação - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> Este pacote também funciona no Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Instalação através do repositório de pacote (preferencial) - CentOS 7

Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Depois de registar o repositório de Microsoft uma vez como Superutilizador, basta utilizar `sudo yum update powershell` para atualizar o PowerShell.

### <a name="installation-via-direct-download---centos-7"></a>Instalação através de transferência direta - CentOS 7

Utilizar [CentOS 7][], transfira o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina do CentOS:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Em seguida, execute o seguinte no terminal:

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Também pode instalar o RPM sem o passo intermédio de transferindo-a:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Desinstalação - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Instalação através do repositório de pacote (preferencial) - 7 do Red Hat Enterprise Linux (RHEL)

Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Depois de registar o repositório de Microsoft uma vez como Superutilizador, basta utilizar `sudo yum update powershell` para atualizar o PowerShell.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Instalação através de transferência direta - Red Hat Enterprise Linux (RHEL) 7

Transferir o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina do Red Hat Enterprise Linux:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

Em seguida, execute o seguinte no terminal:

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Também pode instalar o RPM sem o passo intermédio de transferindo-a:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Desinstalação - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42.2

> **Nota:** ao instalar o PowerShell Core, `zypper` pode comunicar o seguinte erro:
>
> ```text
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> Neste caso, certifique-se de que um ecrã compatível com `libcurl` biblioteca encontra-se ao verificar que o seguinte comando mostra o `libcurl4` pacote como instalado:
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> Em seguida, escolha o `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solução quando instalar o `powershell` pacote.

### <a name="installation-via-package-repository-preferred---opensuse-422"></a>Instalação através do repositório de pacote (preferencial) - OpenSUSE 42.2

Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a>Instalação através de transferência direta - OpenSUSE 42.2

Transferir o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina OpenSUSE:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Também pode instalar o RPM sem o passo intermédio de transferindo-a:

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a>Desinstalação - OpenSUSE 42.2

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a>Fedora 25

### <a name="installation-via-package-repository-preferred---fedora-25"></a>Instalação através do repositório de pacote (preferencial) - Fedora 25

Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-25"></a>Instalação através de transferência direta - Fedora 25

Transferir o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina Fedora:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Em seguida, execute o seguinte no terminal:

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Também pode instalar o RPM sem o passo intermédio de transferindo-a:

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a>Uninstallation - Fedora 25

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a>Fedora 26

### <a name="installation-via-package-repository-preferred---fedora-26"></a>Instalação através do repositório de pacote (preferencial) - Fedora 26

Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).

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

### <a name="installation-via-direct-download---fedora-26"></a>Instalação através de transferência direta - Fedora 26

Transferir o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina Fedora:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Em seguida, execute o seguinte no terminal:

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Também pode instalar o RPM sem o passo intermédio de transferindo-a:

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a>Uninstallation - Fedora 26

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

PowerShell está disponível a partir de [arquitetura Linux][] utilizador repositório (AUR).

* Pode ser compilada com a [mais recente etiquetados versão][arch-release]
* Pode ser compilado do [consolidação mais recente mestre][arch-git]
* Pode ser instalado utilizando o [binário da versão mais recente][arch-bin]

Pacotes no AUR Comunidade mantida - não são suportadas oficial.

Para obter mais informações sobre como instalar pacotes do AUR, consulte o [arquitetura Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou Comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[arquitetura Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a>AppImage do Linux

Com uma distribuição Linux recente, transfira o AppImage `powershell-6.0.0-x86_64.AppImage` do [versões][] página para a máquina do Linux.

Em seguida, execute o seguinte no terminal:

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

O [AppImage][] permite-lhe executar o PowerShell sem instalá-lo. É uma aplicação portátil que bundles PowerShell e as respetivas dependências (incluindo as dependências do .NET Core system) para um pacote coesa. Este pacote funciona independentemente da distribuição de Linux do utilizador, não sendo único binário.

[appimage]: http://appimage.org/

## <a name="macos-1012"></a>macOS 10.12

### <a name="installation-via-homebrew-preferred---macos-1012"></a>Instalação via Homebrew (preferido) - macOS 10.12

[Homebrew] [ brew] é o Gestor de pacote em falta para macOS. Se o `brew` comandos não for encontrado, tem de instalar o seguinte Homebrew [as instruções][brew].

Assim que instalou Homebrew, instalar o PowerShell é fácil. Em primeiro lugar, instalar [Homebrew Cask][cask], como tal, pode instalar mais pacotes:

```sh
brew tap caskroom/cask
```

Agora, pode instalar o PowerShell:

```sh
brew cask install powershell
```

Quando são lançadas novas versões do PowerShell, basta atualizar formulae do Homebrew e atualizar o PowerShell:

```sh
brew update
brew cask reinstall powershell
```

> Nota: porque de [este problema nos Cask](https://github.com/caskroom/homebrew-cask/issues/29301), atualmente, possui fazer reinstalar a atualização.

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a>Instalação através de transferência direta - macOS 10.12

Utilizar macOS 10.12, transfira o pacote PKG `powershell-6.0.0-osx.10.12-x64.pkg` do [versões][] página para a máquina macOS.

Faça duplo clique o ficheiro e siga as instruções ou instalá-lo no terminal:

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a>Desinstalação - macOS 10.12

Se tiver instalado o PowerShell com Homebrew, é fácil a desinstalação:

```sh
brew cask uninstall powershell
```

Se tiver instalado o PowerShell através de transferência direta, PowerShell tem de retirar manualmente:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Para desinstalar os caminhos de PowerShell adicionais (por exemplo, o caminho do perfil de utilizador). consulte o [caminhos] [ paths] secção abaixo neste documento e remova o pretendido os caminhos com `sudo rm`. (Nota: não é necessário se tiver instalado com Homebrew.)

[paths]:#paths

## <a name="kali"></a>Kali

### <a name="installation"></a>Instalação

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Download & Install PowerShell
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>Executar o PowerShell no Kali mais recente (Kali GNU/Linux sucessiva) sem instalar

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>Desinstalação - Kali

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a>Raspbian

Atualmente, o PowerShell só é suportado em Raspbian Stretch.

### <a name="installation"></a>Instalação

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a>Desinstalação - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Arquivos binários

PowerShell binário `tar.gz` arquivos são fornecidos para macOS e plataformas Linux para ativar cenários de implementação avançada.

### <a name="dependencies"></a>Dependências

Para Linux, PowerShell baseia-se o portátil binários para todas as distribuições de Linux.
Mas o tempo de execução de .NET Core requer diferentes dependências em diversas distribuições e, por conseguinte, o PowerShell tem a mesma.

O gráfico seguinte mostra as dependências do .NET Core 2.0 em diversas distribuições de Linux que são suportadas oficialmente.

| SO                 | Dependências |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| 8 debian (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42.2 <br> Fedora 25 | libunwind, libcurl, bibliotecas de openssl, libicu |
| Fedora 26          | libunwind libcurl, bibliotecas de openssl, libicu, openssl10 de compatibilidade |

Para implementar os binários do PowerShell nas distribuições de Linux que não são suportados oficialmente, terá de instalar as dependências necessárias para o SO de destino nos passos separados. Por exemplo, a nossa [Amazon Linux dockerfile] [ amazon-dockerfile] instala dependências primeiro e, em seguida, extrai o Linux `tar.gz` arquivo.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Instalação - arquivos binários

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a>macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a>Desinstalação - arquivos binários

#### <a name="linux"></a>Linux

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a>macOS

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a>Caminhos

* `$PSHOME` é `/opt/microsoft/powershell/6.0.0/`
* Perfis de utilizador serão lida a partir de `~/.config/powershell/profile.ps1`
* Serão possível ler perfis predefinidos `$PSHOME/profile.ps1`
* Módulos de utilizador serão lida a partir de `~/.local/share/powershell/Modules`
* Módulos partilhados irão ler a partir do `/usr/local/share/powershell/Modules`
* Módulos de predefinido serão possível ler a partir do `$PSHOME/Modules`
* Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Os perfis respeitem a configuração de por anfitrião do PowerShell, pelo que os perfis de anfitrião específico predefinido não existe em `Microsoft.PowerShell_profile.ps1` nas localizações da mesmas.

No Linux e macOS, o [XDG Base diretório especificação] [ xdg-bds] é respeitado.

Tenha em atenção que porque macOS é uma derivação do BSD, em vez de `/opt`, é o prefixo utilizado `/usr/local`. Assim, `$PSHOME` é `/usr/local/microsoft/powershell/6.0.0/`, e o symlink é colocado em `/usr/local/bin/pwsh`.

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html