---
title: Instalar o PowerShell Core no Linux
description: Informações sobre a instalação do PowerShell Core em várias distribuições do Linux
ms.date: 07/19/2019
ms.openlocfilehash: 7d7c9a9f915f0a6e735a7baec1ec56e9c205a155
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848178"
---
# <a name="installing-powershell-core-on-linux"></a>Instalar o PowerShell Core no Linux

Dá suporte ao [ubuntu 16, 4][u16], [Ubuntu 18, 4][u1804], [Ubuntu 18,10][u1810], [Ubuntu 19, 4][u1904], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27 ][fedora], [Fedora 28][fedora]e [Arch Linux][arch].

Para distribuições Linux que não têm suporte oficial, você pode tentar instalar o PowerShell usando o [pacote de snap do PowerShell][snap]. Você também pode tentar implantar binários do PowerShell diretamente usando o [ `tar.gz` arquivo][tar]do Linux, mas precisaria configurar as dependências necessárias com base no sistema operacional em etapas separadas.

Todos os pacotes estão disponíveis em nossa página de [versões][] do github. Após a instalação do pacote, execute `pwsh` a partir de um terminal.

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a>Instalando versões de visualização

Ao instalar uma versão de visualização do PowerShell Core para Linux por meio de um repositório de pacotes, `powershell` o `powershell-preview`nome do pacote é alterado de para.

A instalação por meio de download direto não é alterada, além do nome do arquivo.

A tabela a seguir contém os comandos para instalar os pacotes estáveis e de visualização usando os vários gerenciadores de pacotes:

|Distribuição (ões)|Comando estável | Comando de visualização |
|---------------|---------------|-----------------|
| Ubuntu, Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS, RedHat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Instalação por meio do repositório de pacotes – Ubuntu 16, 4

O PowerShell Core para Linux é publicado em repositórios de pacotes para facilitar a instalação e as atualizações.

O método preferencial é o seguinte:

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Como superusuário, registre o repositório da Microsoft uma vez. Após o registro, você pode atualizar o `sudo apt-get upgrade powershell`PowerShell com o.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Instalação por meio de download direto – Ubuntu 16, 4

Baixe o pacote `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` Debian da página [versões][] no computador Ubuntu.

Em seguida, no terminal, execute os seguintes comandos:

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> O `dpkg -i` comando falha com dependências não atendidas. O comando `apt-get install -f` a seguir resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.

### <a name="uninstallation---ubuntu-1604"></a>Desinstalação – Ubuntu 16, 4

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

### <a name="installation-via-package-repository---ubuntu-1804"></a>Instalação por meio do repositório de pacotes – Ubuntu 18, 4

O PowerShell Core para Linux é publicado em repositórios de pacotes para facilitar a instalação e as atualizações.

O método preferencial é o seguinte:

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Enable the "universe" repositories
sudo add-apt-repository universe

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Como superusuário, registre o repositório da Microsoft uma vez. Após o registro, você pode atualizar o `sudo apt-get upgrade powershell`PowerShell com o.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Instalação por meio de download direto – Ubuntu 18, 4

Baixe o pacote `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` Debian da página [versões][] no computador Ubuntu.

Em seguida, no terminal, execute os seguintes comandos:

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> O `dpkg -i` comando falha com dependências não atendidas. O comando `apt-get install -f` a seguir resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.

### <a name="uninstallation---ubuntu-1804"></a>Desinstalação – Ubuntu 18, 4

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18.10

A instalação tem suporte `snapd`via. Para obter instruções, consulte [snap Package][snap].

> [!NOTE]
> O Ubuntu 18,10 é uma [versão provisória](https://www.ubuntu.com/about/release-cycle) [com suporte da Comunidade](../powershell-support-lifecycle.md).

## <a name="ubuntu-1904"></a>Ubuntu 19, 4

A instalação tem suporte `snapd`via. Para obter instruções, consulte [snap Package][snap].

> [!NOTE]
> O Ubuntu 19, 4 é uma [versão provisória](https://www.ubuntu.com/about/release-cycle) [com suporte da Comunidade](../powershell-support-lifecycle.md).

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Instalação por meio do repositório de pacotes – Debian 8

O PowerShell Core para Linux é publicado em repositórios de pacotes para facilitar a instalação e as atualizações.

O método preferencial é o seguinte:

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl apt-transport-https

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

Como superusuário, registre o repositório da Microsoft uma vez. Após o registro, você pode atualizar o `sudo apt-get upgrade powershell`PowerShell com o.

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Instalação por meio do repositório de pacotes – Debian 9

O PowerShell Core para Linux é publicado em repositórios de pacotes para facilitar a instalação e as atualizações.

O método preferencial é o seguinte:

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl gnupg apt-transport-https

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

Como superusuário, registre o repositório da Microsoft uma vez. Após o registro, você pode atualizar o `sudo apt-get upgrade powershell`PowerShell com o.

### <a name="installation-via-direct-download---debian-9"></a>Instalação por meio de download direto – Debian 9

Baixe o pacote `powershell_6.2.0-1.debian.9_amd64.deb` Debian da página [versões][] no computador Debian.

Em seguida, no terminal, execute os seguintes comandos:

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Desinstalação – Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> Este pacote funciona no Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Instalação por meio do repositório de pacotes (preferencial) – CentOS 7

O PowerShell Core para Linux é publicado em repositórios oficiais da Microsoft para facilitar a instalação e as atualizações.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Como superusuário, registre o repositório da Microsoft uma vez. Após o registro, você pode atualizar o `sudo yum update powershell`PowerShell com o.

### <a name="installation-via-direct-download---centos-7"></a>Instalação por meio do download direto – CentOS 7

Usando o [CentOS 7][], baixe o pacote `powershell-6.2.0-1.rhel.7.x86_64.rpm` rpm da página [versões][] no computador CentOS.

Em seguida, no terminal, execute os seguintes comandos:

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

Você pode instalar o RPM sem a etapa intermediária de baixá-lo:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Desinstalação – CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Instalação por meio do repositório de pacotes (preferencial)-Red Hat Enterprise Linux (RHEL) 7

O PowerShell Core para Linux é publicado em repositórios oficiais da Microsoft para facilitar a instalação e as atualizações.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Como superusuário, registre o repositório da Microsoft uma vez. Após o registro, você pode atualizar o `sudo yum update powershell`PowerShell com o.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Instalação por meio de download direto – Red Hat Enterprise Linux (RHEL) 7

Baixe o pacote `powershell-6.2.0-1.rhel.7.x86_64.rpm` rpm da página [versões][] no computador Red Hat Enterprise Linux.

Em seguida, no terminal, execute os seguintes comandos:

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

Você pode instalar o RPM sem a etapa intermediária de baixá-lo:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Desinstalação-Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a>openSUSE

### <a name="installation---opensuse-423"></a>Instalação-openSUSE 42,3

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a>Instalação-openSUSE Leap 15

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a>Desinstalação-openSUSE 42,3, openSUSE Leap 15

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> O Fedora 28 tem suporte apenas no PowerShell Core 6,1 e mais recente.

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>Instalação por meio do repositório de pacotes (preferencial)-Fedora 27, Fedora 28

O PowerShell Core para Linux é publicado em repositórios oficiais da Microsoft para facilitar a instalação e as atualizações.

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>Instalação por meio de download direto-Fedora 27, Fedora 28

Baixe o pacote `powershell-6.2.0-1.rhel.7.x86_64.rpm` rpm da página [versões][] no computador Fedora.

Em seguida, no terminal, execute os seguintes comandos:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

Você pode instalar o RPM sem a etapa intermediária de baixá-lo:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>Desinstalação-Fedora 27, Fedora 28

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Inglês de Arch

> [!NOTE]
> O suporte a Arch é experimental.

O PowerShell está disponível no AUR (repositório do usuário do [Inglês de Arch][] ).

* Ele pode ser compilado com a [versão marcada mais recente][arch-release]
* Ele pode ser compilado da [última confirmação ao mestre][arch-git]
* Ele pode ser instalado usando o [binário de versão mais recente][arch-bin]

Os pacotes no AUR são mantidos pela Comunidade; Não há suporte oficial.

Para obter mais informações sobre como instalar pacotes do AUR, consulte o [wiki do Linux em Arch](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou o [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile)da Comunidade.

[Inglês de Arch]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>Ajustar pacote

### <a name="getting-snapd"></a>Sendo ajustado

`snapd`é necessário para executar Snaps. Use [estas instruções](https://docs.snapcraft.io/core/install) para verificar se você `snapd` instalou o.

### <a name="installation-via-snap"></a>Instalação via snap

O PowerShell Core para Linux é publicado no [repositório de snap](https://snapcraft.io/store) para facilitar a instalação e as atualizações.

O método preferencial é o seguinte:

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

Para instalar uma versão de visualização, use o seguinte método:

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

Após a instalação, o snap será atualizado automaticamente. Você pode disparar uma atualização usando `sudo snap refresh powershell` o `sudo snap refresh powershell-preview`ou o.

### <a name="uninstallation"></a>Desinstalação

```sh
sudo snap remove powershell
```

ou

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

### <a name="installation---kali"></a>Instalação-Kali

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-6+deb9u2_amd64.deb
dpkg -i libicu57_57.1-6+deb9u2_amd64.deb
apt-get update && apt-get install -y curl gnupg apt-transport-https

# Add Microsoft public repository key to APT
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

# Add Microsoft package repository to the source list
echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" | tee /etc/apt/sources.list.d/powershell.list

# Install PowerShell package
apt-get update && apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a>Desinstalação – Kali

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> O suporte a Raspbian é experimental.

Atualmente, o PowerShell só tem suporte no Stretch Raspbian.

O CoreCLR e o PowerShell Core só funcionarão em dispositivos pi 2 e pi 3, já que outros dispositivos, como o [pi zero](https://github.com/dotnet/coreclr/issues/10605), têm um processador sem suporte.

Baixe o [Stretch Raspbian](https://www.raspberrypi.org/downloads/raspbian/) e siga as [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para obtê-lo no PI.

### <a name="installation---raspbian"></a>Instalação-Raspbian

```sh
###################################
# Prerequisites

# Update package lists
sudo apt-get update

# Install libunwind8 and libssl1.0
# Regex is used to ensure that we do not install libssl1.0-dev, as it is a variant that is not required
sudo apt-get install '^libssl1.0.[0-9]$' libunwind8 -y

###################################
# Download and extract PowerShell

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

Opcionalmente, você pode criar um link simbólico para iniciar o PowerShell sem especificar o caminho para `pwsh` o binário.

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>Desinstalação – Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Arquivos binários

Os arquivos `tar.gz` binários do PowerShell são fornecidos para plataformas Linux para habilitar cenários de implantação avançada.

### <a name="dependencies"></a>Depend

O PowerShell cria binários portáteis para todas as distribuições do Linux. Mas, o tempo de execução do .NET Core requer diferentes dependências em diferentes distribuições, e o PowerShell também.

O gráfico a seguir mostra as dependências do .NET Core 2,0 que são oficialmente suportadas em diferentes distribuições do Linux.

| SO                 | Depend |
| ------------------ | ------------ |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55 |
| Ubuntu 17,10       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 | libunwind, libcurl, OpenSSL-bibliotecas, libicu |
| openSUSE 42,3 | libcurl4, libopenssl1_0_0, libicu52_1 |
| openSUSE Leap 15 | libcurl4, libopenssl1_0_0, libicu60_2 |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, OpenSSL-bibliotecas, libicu, compat-openssl10 |

Para implantar binários do PowerShell em distribuições Linux que não têm suporte oficial, você precisa instalar as dependências necessárias para o sistema operacional de destino em etapas separadas. Por exemplo, nosso [Amazon Linux dockerfile][amazon-dockerfile] instala dependências primeiro e, em seguida, extrai `tar.gz` o arquivo do Linux.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a>Instalação-arquivos binários

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a>Desinstalando arquivos binários

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Caminhos

* `$PSHOME`for`/opt/microsoft/powershell/6.2.0/`
* Os perfis de usuário serão lidos de`~/.config/powershell/profile.ps1`
* Os perfis padrão serão lidos de`$PSHOME/profile.ps1`
* Os módulos de usuário serão lidos de`~/.local/share/powershell/Modules`
* Os módulos compartilhados serão lidos de`/usr/local/share/powershell/Modules`
* Os módulos padrão serão lidos de`$PSHOME/Modules`
* O histórico de PSReadline será gravado em`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Os perfis respeitam a configuração por host do PowerShell, portanto, os perfis específicos do host padrão `Microsoft.PowerShell_profile.ps1` existem no mesmo local.

O PowerShell respeita a [especificação do diretório base xdg][xdg-bds] no Linux.

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
