# <a name="installing-powershell-core-on-linux"></a>Instalar o PowerShell Core no Linux

Suporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25 ] [ fed25], [Fedora 26][fed26], e [arquitetura Linux][arch].

Para as distribuições do Linux que não são suportadas oficialmente, pode tentar utilizar o [PowerShell AppImage][lai].
Também pode tentar implementar os binários de PowerShell diretamente com o Linux [ `tar.gz` arquivo][tar], mas terá de configurar as dependências necessárias com base no SO em passos separados.

Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.
Depois do pacote está instalado, executar `pwsh` de um terminal.

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
[tar]: #binary-archives

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Instalação através do repositório de pacote - Ubuntu 14.04

PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).
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

Como Superutilizador, registe o repositório de Microsoft.
De ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` para atualizar a instalação.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Instalação através de transferência direta - Ubuntu 14.04

Transferir o pacote Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` do [versões][] página para a máquina Ubuntu.

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
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
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Instalação através de transferência direta - Ubuntu 16.04

Transferir o pacote Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` do [versões][] página para a máquina Ubuntu.

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
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
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.

### <a name="installation-via-direct-download---ubuntu-1704"></a>Instalação através de transferência direta - Ubuntu 17.04

Transferir o pacote Debian `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` do [versões][] página para a máquina Ubuntu.

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
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

Transferir o pacote Debian `powershell_6.0.2-1.debian.8_amd64.deb` do [versões][] página para a máquina Debian.

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Tenha em atenção que `dpkg -i` irá falhar com dependências unmet.
> O comando seguinte, `apt-get install -f` resolve estes e, em seguida, termina a configurar o pacote do PowerShell.

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

Transferir o pacote Debian `powershell_6.0.2-1.debian.9_amd64.deb` do [versões][] página para a máquina Debian.

Em seguida, execute o seguinte no terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Tenha em atenção que `dpkg -i` irá falhar com dependências unmet.
> O comando seguinte, `apt-get install -f` resolve estes e, em seguida, termina a configurar o pacote do PowerShell.

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

Utilizar [CentOS 7][], transfira o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina do CentOS.

Em seguida, execute o seguinte no terminal:

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Também pode instalar o RPM sem o passo intermédio de transferindo-a:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
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

Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina do Red Hat Enterprise Linux.

Em seguida, execute o seguinte no terminal:

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Também pode instalar o RPM sem o passo intermédio de transferindo-a:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Desinstalação - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42.2

> [!NOTE]
> Ao instalar o PowerShell Core, `zypper` pode comunicar o seguinte erro:
>
> ```Output
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
> Em seguida, escolha o `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solução quando instalar o pacote do PowerShell.

### <a name="installation-via-package-repository-preferred---opensuse-422"></a>Instalação através do repositório de pacote (preferencial) - OpenSUSE 42.2

Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a>Instalação através de transferência direta - OpenSUSE 42.2

Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina OpenSUSE.

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Também pode instalar o RPM sem o passo intermédio de transferindo-a:

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
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

Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina Fedora.

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Em seguida, execute o seguinte no terminal:

```sh
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Também pode instalar o RPM sem o passo intermédio de transferindo-a:

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a>Desinstalação - Fedora 25

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

Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina Fedora.

Em seguida, execute o seguinte no terminal:

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Também pode instalar o RPM sem o passo intermédio de transferindo-a:

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a>Desinstalação - Fedora 26

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arquitetura de Linux

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

Com uma distribuição Linux recente, transfira o AppImage `powershell-6.0.1-x86_64.AppImage` do [versões][] página para a máquina do Linux.

Em seguida, execute o seguinte no terminal:

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

O [AppImage][] permite-lhe executar o PowerShell sem instalá-lo.
É uma aplicação portátil que bundles PowerShell e as respetivas dependências (incluindo as dependências do .NET Core system) para um pacote coesa.
Este pacote é um binário único que funciona independentemente da distribuição de Linux do utilizador.

[appimage]: http://appimage.org/

## <a name="kali"></a>Kali

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>Executar o PowerShell no Kali mais recente (Kali GNU/Linux sucessiva) sem instalar

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

Atualmente, o PowerShell só é suportado em Raspbian Stretch.

Também CoreCLR (e, consequentemente, PowerShell Core) funcionará apenas em dispositivos Pi 2 e Pi 3 como outros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), tem um processador não suportado.

Transferir [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e siga o [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) obtê-lo no seu Pi.

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

Opcionalmente, pode criar uma ligação simbólica para conseguir iniciar PowerShell sem especificar o caminho para o "pwsh" binário

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

PowerShell binário `tar.gz` arquivos são fornecidos para plataformas Linux ativar cenários de implementação avançada.

### <a name="dependencies"></a>Dependências

PowerShell compila binários portátil para todas as distribuições de Linux.
Mas o tempo de execução de .NET Core requer diferentes dependências em diversas distribuições e, por conseguinte, o PowerShell tem a mesma.

O gráfico seguinte mostra as dependências de .NET Core 2.0 oficialmente são suportadas em diversas distribuições de Linux.

| SO                 | Dependências |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3 libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| 8 debian (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42.2 <br> Fedora 25 | libunwind, libcurl, bibliotecas de openssl, libicu |
| Fedora 26          | libunwind libcurl, bibliotecas de openssl, libicu, openssl10 de compatibilidade |

Para implementar os binários do PowerShell nas distribuições de Linux que não são suportados oficialmente, terá de instalar as dependências necessárias para o SO de destino nos passos separados.
Por exemplo, a nossa [Amazon Linux dockerfile] [ amazon-dockerfile] instala dependências primeiro e, em seguida, extrai o Linux `tar.gz` arquivo.

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

### <a name="uninstalling-binary-archives"></a>Desinstalação arquivos binários

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Caminhos

* `$PSHOME` é `/opt/microsoft/powershell/6.0.2/`
* Perfis de utilizador serão lida a partir de `~/.config/powershell/profile.ps1`
* Serão possível ler perfis predefinidos `$PSHOME/profile.ps1`
* Módulos de utilizador serão lida a partir de `~/.local/share/powershell/Modules`
* Módulos partilhados irão ler a partir do `/usr/local/share/powershell/Modules`
* Módulos de predefinido serão possível ler a partir do `$PSHOME/Modules`
* Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Os perfis respeitem a configuração de por anfitrião do PowerShell, pelo que os perfis de anfitrião específico predefinido não existe em `Microsoft.PowerShell_profile.ps1` nas localizações da mesmas.

PowerShell respeita o [XDG Base diretório especificação] [ xdg-bds] no Linux.

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
