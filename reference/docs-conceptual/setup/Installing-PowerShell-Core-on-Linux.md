---
title: Instalar o PowerShell Core no Linux
description: Informações sobre como instalar o PowerShell Core em várias distribuições do Linux
ms.date: 08/06/2018
ms.openlocfilehash: a20384c768113ed2313591cfa8c29eeadd94f80f
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226003"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="a2c0b-103">Instalar o PowerShell Core no Linux</span><span class="sxs-lookup"><span data-stu-id="a2c0b-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="a2c0b-104">Suporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04] [ u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9] [ deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE dar um passo 15][opensuse], [Fedora 27][fedora], [ Fedora 28][fedora], e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="a2c0b-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="a2c0b-105">Para as distribuições de Linux que não são suportadas oficialmente, pode tentar usar a [pacote de ajuste do PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="a2c0b-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="a2c0b-106">Também pode tentar implementar os binários do PowerShell diretamente com a Linux [ `tar.gz` arquivo][tar], mas terá de configurar as dependências necessárias, com base no sistema operacional nos passos separados.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="a2c0b-107">Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="a2c0b-108">Depois do pacote está instalado, execute `pwsh` partir de um terminal.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="a2c0b-109">Instalar versões de pré-visualização</span><span class="sxs-lookup"><span data-stu-id="a2c0b-109">Installing Preview Releases</span></span>

<span data-ttu-id="a2c0b-110">Ao instalar uma versão de pré-visualização do PowerShell Core para Linux através de um repositório de pacotes, o nome do pacote é alterado de `powershell` para `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="a2c0b-111">Instalar através de transferência direta não é alterada, além do nome de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="a2c0b-112">Esta é uma tabela de comandos para instalar os pacotes de estável e pré-visualização com os vários gestores de pacote:</span><span class="sxs-lookup"><span data-stu-id="a2c0b-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="a2c0b-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="a2c0b-113">Distribution(s)</span></span>|<span data-ttu-id="a2c0b-114">Comando estável</span><span class="sxs-lookup"><span data-stu-id="a2c0b-114">Stable Command</span></span> | <span data-ttu-id="a2c0b-115">Comando de pré-visualização</span><span class="sxs-lookup"><span data-stu-id="a2c0b-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="a2c0b-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="a2c0b-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="a2c0b-117">CentOS, Red Hat</span><span class="sxs-lookup"><span data-stu-id="a2c0b-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="a2c0b-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="a2c0b-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="a2c0b-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="a2c0b-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="a2c0b-120">Instalação através do repositório do pacote - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="a2c0b-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="a2c0b-121">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="a2c0b-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="a2c0b-122">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-122">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/14.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="a2c0b-123">Superutilizador, registar-se o repositório da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="a2c0b-124">De ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` para atualizar a instalação.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="a2c0b-125">Instalação através de transferência direta - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="a2c0b-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="a2c0b-126">Transferir o pacote Debian `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="a2c0b-126">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="a2c0b-127">do [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="a2c0b-128">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="a2c0b-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="a2c0b-129">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="a2c0b-130">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="a2c0b-131">Desinstalação - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="a2c0b-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="a2c0b-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a2c0b-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="a2c0b-133">Instalação através do repositório do pacote - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a2c0b-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="a2c0b-134">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="a2c0b-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="a2c0b-135">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-135">This is the preferred method.</span></span>

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

<span data-ttu-id="a2c0b-136">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="a2c0b-137">Instalação através de transferência direta - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a2c0b-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="a2c0b-138">Transferir o pacote Debian `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="a2c0b-138">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="a2c0b-139">do [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="a2c0b-140">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="a2c0b-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="a2c0b-141">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="a2c0b-142">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="a2c0b-143">Desinstalação - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a2c0b-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="a2c0b-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a2c0b-144">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="a2c0b-145">Foi adicionado suporte para Ubuntu 18.04 após `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="a2c0b-145">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="a2c0b-146">Instalação através do repositório do pacote - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a2c0b-146">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="a2c0b-147">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="a2c0b-147">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="a2c0b-148">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-148">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="a2c0b-149">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-149">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="a2c0b-150">Instalação através de transferência direta - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a2c0b-150">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="a2c0b-151">Transferir o pacote Debian `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="a2c0b-151">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="a2c0b-152">do [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-152">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="a2c0b-153">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="a2c0b-153">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="a2c0b-154">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-154">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="a2c0b-155">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-155">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="a2c0b-156">Desinstalação - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a2c0b-156">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="a2c0b-157">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="a2c0b-157">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="a2c0b-158">Foi adicionado suporte para Ubuntu 18.10 após `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-158">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="a2c0b-159">Como 18.10 é uma compilação diária, é apenas suportada na Comunidade.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-159">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="a2c0b-160">A instalar num 18.10 é suportada através de `snapd`.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-160">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="a2c0b-161">Ver [ajustar pacote] [ snap] para obter instruções completas;</span><span class="sxs-lookup"><span data-stu-id="a2c0b-161">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="a2c0b-162">Debian 8</span><span class="sxs-lookup"><span data-stu-id="a2c0b-162">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="a2c0b-163">Instalação através do repositório do pacote - Debian 8</span><span class="sxs-lookup"><span data-stu-id="a2c0b-163">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="a2c0b-164">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="a2c0b-164">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="a2c0b-165">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-165">This is the preferred method.</span></span>

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

<span data-ttu-id="a2c0b-166">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-166">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="a2c0b-167">Instalação através de transferência direta - Debian 8</span><span class="sxs-lookup"><span data-stu-id="a2c0b-167">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="a2c0b-168">Transferir o pacote Debian `powershell_6.1.0-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="a2c0b-168">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="a2c0b-169">partir do [versões][] página para o computador Debian.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-169">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="a2c0b-170">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="a2c0b-170">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="a2c0b-171">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-171">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="a2c0b-172">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-172">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="a2c0b-173">Desinstalação - Debian 8</span><span class="sxs-lookup"><span data-stu-id="a2c0b-173">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="a2c0b-174">Debian 9</span><span class="sxs-lookup"><span data-stu-id="a2c0b-174">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="a2c0b-175">Instalação através do repositório do pacote - Debian 9</span><span class="sxs-lookup"><span data-stu-id="a2c0b-175">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="a2c0b-176">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="a2c0b-176">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="a2c0b-177">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-177">This is the preferred method.</span></span>

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

<span data-ttu-id="a2c0b-178">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-178">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="a2c0b-179">Instalação através de transferência direta - Debian 9</span><span class="sxs-lookup"><span data-stu-id="a2c0b-179">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="a2c0b-180">Transferir o pacote Debian `powershell_6.1.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="a2c0b-180">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="a2c0b-181">partir do [versões][] página para o computador Debian.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-181">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="a2c0b-182">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="a2c0b-182">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="a2c0b-183">Desinstalação - Debian 9</span><span class="sxs-lookup"><span data-stu-id="a2c0b-183">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="a2c0b-184">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a2c0b-184">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="a2c0b-185">Este pacote também funciona no Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-185">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="a2c0b-186">Instalação através do repositório de pacotes (preferencial) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a2c0b-186">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="a2c0b-187">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="a2c0b-187">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="a2c0b-188">Depois de registar o repositório da Microsoft uma vez como Superutilizador, apenas tem de utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-188">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="a2c0b-189">Instalação através de transferência direta - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a2c0b-189">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="a2c0b-190">Usando [CentOS 7][], transfira o pacote RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="a2c0b-190">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="a2c0b-191">do [versões][] página para o computador de CentOS.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-191">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="a2c0b-192">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="a2c0b-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="a2c0b-193">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="a2c0b-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="a2c0b-194">Desinstalação - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a2c0b-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="a2c0b-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="a2c0b-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="a2c0b-197">Instalação através do repositório de pacotes (preferencial) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="a2c0b-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="a2c0b-198">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="a2c0b-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="a2c0b-199">Depois de registar o repositório da Microsoft uma vez como Superutilizador, apenas tem de utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="a2c0b-200">Instalação através de transferência direta - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="a2c0b-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="a2c0b-201">Transferir o pacote RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="a2c0b-201">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="a2c0b-202">partir do [versões][] página para o computador Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-202">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="a2c0b-203">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="a2c0b-203">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="a2c0b-204">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="a2c0b-204">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="a2c0b-205">Desinstalação - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="a2c0b-205">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="a2c0b-206">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="a2c0b-206">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="a2c0b-207">Instalação - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="a2c0b-207">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="a2c0b-208">Instalação - openSUSE dar um passo 15</span><span class="sxs-lookup"><span data-stu-id="a2c0b-208">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="a2c0b-209">Desinstalação - openSUSE 42.3, openSUSE dar um passo 15</span><span class="sxs-lookup"><span data-stu-id="a2c0b-209">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="a2c0b-210">Fedora</span><span class="sxs-lookup"><span data-stu-id="a2c0b-210">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="a2c0b-211">Fedora 28 só é suportada no PowerShell Core 6.1 e versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-211">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="a2c0b-212">Instalação através do repositório de pacotes (preferencial) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="a2c0b-212">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="a2c0b-213">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="a2c0b-213">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="a2c0b-214">Instalação através de transferência direta - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="a2c0b-214">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="a2c0b-215">Transferir o pacote RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="a2c0b-215">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="a2c0b-216">do [versões][] página na máquina Fedora.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-216">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="a2c0b-217">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="a2c0b-217">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="a2c0b-218">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="a2c0b-218">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="a2c0b-219">Desinstalação - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="a2c0b-219">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="a2c0b-220">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="a2c0b-220">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="a2c0b-221">O suporte de arquitetura é experimental.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-221">Arch support is experimental.</span></span>

<span data-ttu-id="a2c0b-222">PowerShell está disponível a partir da [Arch Linux][] utilizador repositório (AUR).</span><span class="sxs-lookup"><span data-stu-id="a2c0b-222">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="a2c0b-223">Pode ser compilado com o [etiquetados de versão mais recente versão][arch-release]</span><span class="sxs-lookup"><span data-stu-id="a2c0b-223">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="a2c0b-224">Pode ser compilada a partir do [consolidação mais recente a mestre][arch-git]</span><span class="sxs-lookup"><span data-stu-id="a2c0b-224">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="a2c0b-225">Pode ser instalado utilizando o [binário da versão mais recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="a2c0b-225">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="a2c0b-226">Pacotes no AUR são mantida de Comunidade – não existe nenhum suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-226">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="a2c0b-227">Para obter mais informações sobre como instalar pacotes do AUR, consulte a [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou da Comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="a2c0b-227">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="a2c0b-229">Ajustar o pacote</span><span class="sxs-lookup"><span data-stu-id="a2c0b-229">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="a2c0b-230">Introdução snapd</span><span class="sxs-lookup"><span data-stu-id="a2c0b-230">Getting snapd</span></span>

<span data-ttu-id="a2c0b-231">`snapd` é necessário executar snaps.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-231">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="a2c0b-232">Uso [estas instruções](https://docs.snapcraft.io/core/install) para se certificar de que tenha `snapd` instalado.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-232">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="a2c0b-233">Instalação através do Snap</span><span class="sxs-lookup"><span data-stu-id="a2c0b-233">Installation via Snap</span></span>

<span data-ttu-id="a2c0b-234">O PowerShell Core, para o Linux, é publicado para o [Snap store](https://snapcraft.io/store) para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="a2c0b-234">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="a2c0b-235">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-235">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="a2c0b-236">Se quiser instalar a versão de pré-visualização, utilize o seguinte método.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-236">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="a2c0b-237">Depois de instalar o Snap irão atualizar automaticamente, mas pode acionar uma atualização usando `sudo snap refresh powershell` ou `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-237">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="a2c0b-238">Desinstalação</span><span class="sxs-lookup"><span data-stu-id="a2c0b-238">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="a2c0b-239">ou</span><span class="sxs-lookup"><span data-stu-id="a2c0b-239">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="a2c0b-240">Kali</span><span class="sxs-lookup"><span data-stu-id="a2c0b-240">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="a2c0b-241">Instalação - Kali</span><span class="sxs-lookup"><span data-stu-id="a2c0b-241">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-9_amd64.deb
dpkg -i libicu57_57.1-9_amd64.deb
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

### <a name="uninstallation---kali"></a><span data-ttu-id="a2c0b-242">Desinstalação - Kali</span><span class="sxs-lookup"><span data-stu-id="a2c0b-242">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="a2c0b-243">Raspbian</span><span class="sxs-lookup"><span data-stu-id="a2c0b-243">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="a2c0b-244">O suporte de Raspbian é experimental.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-244">Raspbian support is experimental.</span></span>

<span data-ttu-id="a2c0b-245">Atualmente, o PowerShell só é suportado em Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-245">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="a2c0b-246">Também CoreCLR (e, portanto, o PowerShell Core) só funcionam em dispositivos de instalador de plataforma 2 e 3 de instalador de plataforma como outros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ter um processador não suportado.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-246">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="a2c0b-247">Baixe [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e siga o [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) obtê-lo em seu Pi.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-247">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="a2c0b-248">Instalação - Raspbian</span><span class="sxs-lookup"><span data-stu-id="a2c0b-248">Installation - Raspbian</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.1.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="a2c0b-249">Opcionalmente, pode criar um link simbólico para conseguir iniciar PowerShell sem especificar o caminho para o "pwsh" binário</span><span class="sxs-lookup"><span data-stu-id="a2c0b-249">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="a2c0b-250">Desinstalação - Raspbian</span><span class="sxs-lookup"><span data-stu-id="a2c0b-250">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="a2c0b-251">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="a2c0b-251">Binary Archives</span></span>

<span data-ttu-id="a2c0b-252">Binário de PowerShell `tar.gz` arquivos são fornecidos para plataformas Linux ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-252">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="a2c0b-253">Dependências</span><span class="sxs-lookup"><span data-stu-id="a2c0b-253">Dependencies</span></span>

<span data-ttu-id="a2c0b-254">PowerShell cria binários portátil para todas as distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-254">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="a2c0b-255">Mas o tempo de execução do .NET Core requer diferentes dependências em diversas distribuições e, por conseguinte, o PowerShell faz o mesmo.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-255">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="a2c0b-256">O gráfico seguinte mostra as dependências de .NET Core 2.0 são suportadas oficialmente em distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-256">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="a2c0b-257">SO</span><span class="sxs-lookup"><span data-stu-id="a2c0b-257">OS</span></span>                 | <span data-ttu-id="a2c0b-258">Dependências</span><span class="sxs-lookup"><span data-stu-id="a2c0b-258">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="a2c0b-259">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="a2c0b-259">Ubuntu 14.04</span></span>       | <span data-ttu-id="a2c0b-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="a2c0b-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a2c0b-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="a2c0b-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="a2c0b-262">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a2c0b-262">Ubuntu 16.04</span></span>       | <span data-ttu-id="a2c0b-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="a2c0b-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a2c0b-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="a2c0b-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="a2c0b-265">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="a2c0b-265">Ubuntu 17.10</span></span>       | <span data-ttu-id="a2c0b-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="a2c0b-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a2c0b-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="a2c0b-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="a2c0b-268">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a2c0b-268">Ubuntu 18.04</span></span>       | <span data-ttu-id="a2c0b-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="a2c0b-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a2c0b-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="a2c0b-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="a2c0b-271">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="a2c0b-271">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="a2c0b-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="a2c0b-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a2c0b-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="a2c0b-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="a2c0b-274">Debian 9 (Stretch.)</span><span class="sxs-lookup"><span data-stu-id="a2c0b-274">Debian 9 (Stretch)</span></span> | <span data-ttu-id="a2c0b-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="a2c0b-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a2c0b-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="a2c0b-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="a2c0b-277">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a2c0b-277">CentOS 7</span></span> <br> <span data-ttu-id="a2c0b-278">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="a2c0b-278">Oracle Linux 7</span></span> <br> <span data-ttu-id="a2c0b-279">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="a2c0b-279">RHEL 7</span></span> | <span data-ttu-id="a2c0b-280">libunwind, libcurl, bibliotecas de openssl, libicu</span><span class="sxs-lookup"><span data-stu-id="a2c0b-280">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="a2c0b-281">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="a2c0b-281">openSUSE 42.3</span></span> | <span data-ttu-id="a2c0b-282">libcurl4 libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="a2c0b-282">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="a2c0b-283">dar um passo 15 do openSUSE</span><span class="sxs-lookup"><span data-stu-id="a2c0b-283">openSUSE Leap 15</span></span> | <span data-ttu-id="a2c0b-284">libcurl4 libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="a2c0b-284">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="a2c0b-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="a2c0b-285">Fedora 27</span></span> <br> <span data-ttu-id="a2c0b-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="a2c0b-286">Fedora 28</span></span> | <span data-ttu-id="a2c0b-287">libunwind, libcurl, bibliotecas de openssl, libicu, openssl10 de compatibilidade</span><span class="sxs-lookup"><span data-stu-id="a2c0b-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="a2c0b-288">Para implementar os binários do PowerShell distribuições de Linux que não são suportados oficialmente, terá de instalar as dependências necessárias para o sistema operacional de destino nos passos separados.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="a2c0b-289">Por exemplo, nossa [Amazon Linux dockerfile] [ amazon-dockerfile] instala as dependências primeiro e, em seguida, extrai a Linux `tar.gz` arquivo.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="a2c0b-290">Instalação - arquivos binários</span><span class="sxs-lookup"><span data-stu-id="a2c0b-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="a2c0b-291">Linux</span><span class="sxs-lookup"><span data-stu-id="a2c0b-291">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="a2c0b-292">A desinstalar arquivos binários</span><span class="sxs-lookup"><span data-stu-id="a2c0b-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="a2c0b-293">Caminhos</span><span class="sxs-lookup"><span data-stu-id="a2c0b-293">Paths</span></span>

* <span data-ttu-id="a2c0b-294">`$PSHOME` é `/opt/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="a2c0b-294">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="a2c0b-295">Perfis de utilizador serão lido a partir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="a2c0b-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="a2c0b-296">Perfis predefinidos serão lido a partir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="a2c0b-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="a2c0b-297">Módulos de utilizador serão lido a partir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="a2c0b-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="a2c0b-298">Módulos partilhados serão lido a partir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="a2c0b-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="a2c0b-299">Módulos padrão serão lido a partir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="a2c0b-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="a2c0b-300">Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="a2c0b-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="a2c0b-301">Os perfis de respeitam a configuração de por anfitrião do PowerShell, para que os perfis de anfitrião específico padrão existe em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="a2c0b-302">PowerShell respeita os [XDG Base diretório especificação] [ xdg-bds] no Linux.</span><span class="sxs-lookup"><span data-stu-id="a2c0b-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
