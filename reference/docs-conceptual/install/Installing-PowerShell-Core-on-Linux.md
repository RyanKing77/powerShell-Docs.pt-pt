---
title: Instalar o PowerShell Core no Linux
description: Informações sobre como instalar o PowerShell Core em várias distribuições do Linux
ms.date: 08/06/2018
ms.openlocfilehash: 06194550f4e73f9dd38f8cdc25f6c7f698cafce2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086566"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="16942-103">Instalar o PowerShell Core no Linux</span><span class="sxs-lookup"><span data-stu-id="16942-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="16942-104">Suporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04] [ u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [ dar um passo 15 do openSUSE][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="16942-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810],  [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="16942-105">Para as distribuições de Linux que não são suportadas oficialmente, pode tentar usar a [pacote de ajuste do PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="16942-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="16942-106">Também pode tentar implementar os binários do PowerShell diretamente com a Linux [ `tar.gz` arquivo][tar], mas terá de configurar as dependências necessárias, com base no sistema operacional nos passos separados.</span><span class="sxs-lookup"><span data-stu-id="16942-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="16942-107">Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.</span><span class="sxs-lookup"><span data-stu-id="16942-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="16942-108">Depois do pacote está instalado, execute `pwsh` partir de um terminal.</span><span class="sxs-lookup"><span data-stu-id="16942-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="16942-109">Instalar versões de pré-visualização</span><span class="sxs-lookup"><span data-stu-id="16942-109">Installing Preview Releases</span></span>

<span data-ttu-id="16942-110">Ao instalar uma versão de pré-visualização do PowerShell Core para Linux através de um repositório de pacotes, o nome do pacote é alterado de `powershell` para `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="16942-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="16942-111">Instalar através de transferência direta não é alterada, além do nome de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="16942-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="16942-112">Esta é uma tabela de comandos para instalar os pacotes de estável e pré-visualização com os vários gestores de pacote:</span><span class="sxs-lookup"><span data-stu-id="16942-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="16942-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="16942-113">Distribution(s)</span></span>|<span data-ttu-id="16942-114">Comando estável</span><span class="sxs-lookup"><span data-stu-id="16942-114">Stable Command</span></span> | <span data-ttu-id="16942-115">Comando de pré-visualização</span><span class="sxs-lookup"><span data-stu-id="16942-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="16942-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="16942-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="16942-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="16942-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="16942-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="16942-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="16942-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="16942-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="16942-120">Instalação através do repositório do pacote - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="16942-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="16942-121">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="16942-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="16942-122">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="16942-122">This is the preferred method.</span></span>

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

<span data-ttu-id="16942-123">Superutilizador, registar-se o repositório da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="16942-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="16942-124">De ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` para atualizar a instalação.</span><span class="sxs-lookup"><span data-stu-id="16942-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="16942-125">Instalação através de transferência direta - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="16942-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="16942-126">Transferir o pacote Debian `powershell_6.2.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="16942-126">Download the Debian package `powershell_6.2.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="16942-127">do [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="16942-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="16942-128">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="16942-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="16942-129">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="16942-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="16942-130">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16942-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="16942-131">Desinstalação - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="16942-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="16942-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="16942-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="16942-133">Instalação através do repositório do pacote - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="16942-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="16942-134">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="16942-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="16942-135">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="16942-135">This is the preferred method.</span></span>

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

<span data-ttu-id="16942-136">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="16942-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="16942-137">Instalação através de transferência direta - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="16942-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="16942-138">Transferir o pacote Debian `powershell_6.2.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="16942-138">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="16942-139">do [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="16942-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="16942-140">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="16942-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="16942-141">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="16942-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="16942-142">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16942-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="16942-143">Desinstalação - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="16942-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="16942-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="16942-144">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="16942-145">Instalação através do repositório do pacote - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="16942-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="16942-146">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="16942-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="16942-147">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="16942-147">This is the preferred method.</span></span>

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

<span data-ttu-id="16942-148">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="16942-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="16942-149">Instalação através de transferência direta - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="16942-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="16942-150">Transferir o pacote Debian `powershell_6.2.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="16942-150">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="16942-151">do [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="16942-151">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="16942-152">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="16942-152">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="16942-153">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="16942-153">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="16942-154">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16942-154">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="16942-155">Desinstalação - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="16942-155">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="16942-156">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="16942-156">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="16942-157">Como 18.10 é um [versão provisória](https://www.ubuntu.com/about/release-cycle), só é [suportada na Comunidade](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="16942-157">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="16942-158">A instalar num 18.10 é suportada através de `snapd`.</span><span class="sxs-lookup"><span data-stu-id="16942-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="16942-159">Ver [ajustar pacote] [ snap] para obter instruções completas;</span><span class="sxs-lookup"><span data-stu-id="16942-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="16942-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="16942-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="16942-161">Instalação através do repositório do pacote - Debian 8</span><span class="sxs-lookup"><span data-stu-id="16942-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="16942-162">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="16942-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="16942-163">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="16942-163">This is the preferred method.</span></span>

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

<span data-ttu-id="16942-164">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="16942-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

## <a name="debian-9"></a><span data-ttu-id="16942-165">Debian 9</span><span class="sxs-lookup"><span data-stu-id="16942-165">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="16942-166">Instalação através do repositório do pacote - Debian 9</span><span class="sxs-lookup"><span data-stu-id="16942-166">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="16942-167">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="16942-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="16942-168">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="16942-168">This is the preferred method.</span></span>

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

<span data-ttu-id="16942-169">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="16942-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="16942-170">Instalação através de transferência direta - Debian 9</span><span class="sxs-lookup"><span data-stu-id="16942-170">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="16942-171">Transferir o pacote Debian `powershell_6.2.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="16942-171">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="16942-172">partir do [versões][] página para o computador Debian.</span><span class="sxs-lookup"><span data-stu-id="16942-172">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="16942-173">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="16942-173">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="16942-174">Desinstalação - Debian 9</span><span class="sxs-lookup"><span data-stu-id="16942-174">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="16942-175">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="16942-175">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="16942-176">Este pacote também funciona no Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="16942-176">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="16942-177">Instalação através do repositório de pacotes (preferencial) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="16942-177">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="16942-178">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="16942-178">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="16942-179">Depois de registar o repositório da Microsoft uma vez como Superutilizador, apenas tem de utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16942-179">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="16942-180">Instalação através de transferência direta - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="16942-180">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="16942-181">Usando [CentOS 7][], transfira o pacote RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="16942-181">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="16942-182">do [versões][] página para o computador de CentOS.</span><span class="sxs-lookup"><span data-stu-id="16942-182">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="16942-183">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="16942-183">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="16942-184">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="16942-184">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="16942-185">Desinstalação - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="16942-185">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="16942-187">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="16942-187">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="16942-188">Instalação através do repositório de pacotes (preferencial) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="16942-188">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="16942-189">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="16942-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="16942-190">Depois de registar o repositório da Microsoft uma vez como Superutilizador, apenas tem de utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16942-190">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="16942-191">Instalação através de transferência direta - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="16942-191">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="16942-192">Transferir o pacote RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="16942-192">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="16942-193">partir do [versões][] página para o computador Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="16942-193">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="16942-194">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="16942-194">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="16942-195">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="16942-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="16942-196">Desinstalação - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="16942-196">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="16942-197">openSUSE</span><span class="sxs-lookup"><span data-stu-id="16942-197">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="16942-198">Instalação - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="16942-198">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="16942-199">Instalação - openSUSE dar um passo 15</span><span class="sxs-lookup"><span data-stu-id="16942-199">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="16942-200">Desinstalação - openSUSE 42.3, openSUSE dar um passo 15</span><span class="sxs-lookup"><span data-stu-id="16942-200">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="16942-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="16942-201">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="16942-202">Fedora 28 só é suportada no PowerShell Core 6.1 e versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="16942-202">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="16942-203">Instalação através do repositório de pacotes (preferencial) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="16942-203">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="16942-204">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="16942-204">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="16942-205">Instalação através de transferência direta - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="16942-205">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="16942-206">Transferir o pacote RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="16942-206">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="16942-207">do [versões][] página na máquina Fedora.</span><span class="sxs-lookup"><span data-stu-id="16942-207">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="16942-208">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="16942-208">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="16942-209">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="16942-209">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="16942-210">Desinstalação - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="16942-210">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="16942-211">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="16942-211">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="16942-212">O suporte de arquitetura é experimental.</span><span class="sxs-lookup"><span data-stu-id="16942-212">Arch support is experimental.</span></span>

<span data-ttu-id="16942-213">PowerShell está disponível a partir da [Arch Linux][] utilizador repositório (AUR).</span><span class="sxs-lookup"><span data-stu-id="16942-213">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="16942-214">Pode ser compilado com o [etiquetados de versão mais recente versão][arch-release]</span><span class="sxs-lookup"><span data-stu-id="16942-214">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="16942-215">Pode ser compilada a partir do [consolidação mais recente a mestre][arch-git]</span><span class="sxs-lookup"><span data-stu-id="16942-215">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="16942-216">Pode ser instalado utilizando o [binário da versão mais recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="16942-216">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="16942-217">Pacotes no AUR são mantida de Comunidade – não existe nenhum suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="16942-217">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="16942-218">Para obter mais informações sobre como instalar pacotes do AUR, consulte a [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou da Comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="16942-218">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="16942-220">Ajustar o pacote</span><span class="sxs-lookup"><span data-stu-id="16942-220">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="16942-221">Introdução snapd</span><span class="sxs-lookup"><span data-stu-id="16942-221">Getting snapd</span></span>

<span data-ttu-id="16942-222">`snapd` é necessário executar snaps.</span><span class="sxs-lookup"><span data-stu-id="16942-222">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="16942-223">Uso [estas instruções](https://docs.snapcraft.io/core/install) para se certificar de que tenha `snapd` instalado.</span><span class="sxs-lookup"><span data-stu-id="16942-223">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="16942-224">Instalação através do Snap</span><span class="sxs-lookup"><span data-stu-id="16942-224">Installation via Snap</span></span>

<span data-ttu-id="16942-225">O PowerShell Core, para o Linux, é publicado para o [Snap store](https://snapcraft.io/store) para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="16942-225">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="16942-226">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="16942-226">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="16942-227">Se quiser instalar a versão de pré-visualização, utilize o seguinte método.</span><span class="sxs-lookup"><span data-stu-id="16942-227">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="16942-228">Depois de instalar o Snap irão atualizar automaticamente, mas pode acionar uma atualização usando `sudo snap refresh powershell` ou `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="16942-228">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="16942-229">Desinstalação</span><span class="sxs-lookup"><span data-stu-id="16942-229">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="16942-230">ou</span><span class="sxs-lookup"><span data-stu-id="16942-230">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="16942-231">Kali</span><span class="sxs-lookup"><span data-stu-id="16942-231">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="16942-232">Instalação - Kali</span><span class="sxs-lookup"><span data-stu-id="16942-232">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="16942-233">Desinstalação - Kali</span><span class="sxs-lookup"><span data-stu-id="16942-233">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="16942-234">Raspbian</span><span class="sxs-lookup"><span data-stu-id="16942-234">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="16942-235">O suporte de Raspbian é experimental.</span><span class="sxs-lookup"><span data-stu-id="16942-235">Raspbian support is experimental.</span></span>

<span data-ttu-id="16942-236">Atualmente, o PowerShell só é suportado em Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="16942-236">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="16942-237">Também CoreCLR (e, portanto, o PowerShell Core) só funcionam em dispositivos de instalador de plataforma 2 e 3 de instalador de plataforma como outros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ter um processador não suportado.</span><span class="sxs-lookup"><span data-stu-id="16942-237">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="16942-238">Baixe [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e siga o [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) obtê-lo em seu Pi.</span><span class="sxs-lookup"><span data-stu-id="16942-238">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="16942-239">Instalação - Raspbian</span><span class="sxs-lookup"><span data-stu-id="16942-239">Installation - Raspbian</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="16942-240">Opcionalmente, pode criar um link simbólico para conseguir iniciar PowerShell sem especificar o caminho para o "pwsh" binário</span><span class="sxs-lookup"><span data-stu-id="16942-240">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="16942-241">Desinstalação - Raspbian</span><span class="sxs-lookup"><span data-stu-id="16942-241">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="16942-242">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="16942-242">Binary Archives</span></span>

<span data-ttu-id="16942-243">Binário de PowerShell `tar.gz` arquivos são fornecidos para plataformas Linux ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="16942-243">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="16942-244">Dependências</span><span class="sxs-lookup"><span data-stu-id="16942-244">Dependencies</span></span>

<span data-ttu-id="16942-245">PowerShell cria binários portátil para todas as distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="16942-245">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="16942-246">Mas o tempo de execução do .NET Core requer diferentes dependências em diversas distribuições e, por conseguinte, o PowerShell faz o mesmo.</span><span class="sxs-lookup"><span data-stu-id="16942-246">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="16942-247">O gráfico seguinte mostra as dependências de .NET Core 2.0 são suportadas oficialmente em distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="16942-247">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="16942-248">SO</span><span class="sxs-lookup"><span data-stu-id="16942-248">OS</span></span>                 | <span data-ttu-id="16942-249">Dependências</span><span class="sxs-lookup"><span data-stu-id="16942-249">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="16942-250">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="16942-250">Ubuntu 14.04</span></span>       | <span data-ttu-id="16942-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="16942-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="16942-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="16942-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="16942-253">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="16942-253">Ubuntu 16.04</span></span>       | <span data-ttu-id="16942-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="16942-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="16942-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="16942-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="16942-256">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="16942-256">Ubuntu 17.10</span></span>       | <span data-ttu-id="16942-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="16942-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="16942-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="16942-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="16942-259">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="16942-259">Ubuntu 18.04</span></span>       | <span data-ttu-id="16942-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="16942-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="16942-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="16942-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="16942-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="16942-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="16942-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="16942-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="16942-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="16942-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="16942-265">Debian 9 (Stretch.)</span><span class="sxs-lookup"><span data-stu-id="16942-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="16942-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="16942-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="16942-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="16942-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="16942-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="16942-268">CentOS 7</span></span> <br> <span data-ttu-id="16942-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="16942-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="16942-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="16942-270">RHEL 7</span></span> | <span data-ttu-id="16942-271">libunwind, libcurl, bibliotecas de openssl, libicu</span><span class="sxs-lookup"><span data-stu-id="16942-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="16942-272">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="16942-272">openSUSE 42.3</span></span> | <span data-ttu-id="16942-273">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="16942-273">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="16942-274">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="16942-274">openSUSE Leap 15</span></span> | <span data-ttu-id="16942-275">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="16942-275">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="16942-276">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="16942-276">Fedora 27</span></span> <br> <span data-ttu-id="16942-277">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="16942-277">Fedora 28</span></span> | <span data-ttu-id="16942-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="16942-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="16942-279">Para implementar os binários do PowerShell distribuições de Linux que não são suportados oficialmente, terá de instalar as dependências necessárias para o sistema operacional de destino nos passos separados.</span><span class="sxs-lookup"><span data-stu-id="16942-279">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="16942-280">Por exemplo, nossa [Amazon Linux dockerfile] [ amazon-dockerfile] instala as dependências primeiro e, em seguida, extrai a Linux `tar.gz` arquivo.</span><span class="sxs-lookup"><span data-stu-id="16942-280">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="16942-281">Instalação - arquivos binários</span><span class="sxs-lookup"><span data-stu-id="16942-281">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="16942-282">Linux</span><span class="sxs-lookup"><span data-stu-id="16942-282">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="16942-283">A desinstalar arquivos binários</span><span class="sxs-lookup"><span data-stu-id="16942-283">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="16942-284">Caminhos</span><span class="sxs-lookup"><span data-stu-id="16942-284">Paths</span></span>

* <span data-ttu-id="16942-285">`$PSHOME` é `/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="16942-285">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="16942-286">Perfis de utilizador serão lido a partir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="16942-286">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="16942-287">Perfis predefinidos serão lido a partir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="16942-287">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="16942-288">Módulos de utilizador serão lido a partir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="16942-288">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="16942-289">Módulos partilhados serão lido a partir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="16942-289">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="16942-290">Módulos padrão serão lido a partir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="16942-290">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="16942-291">Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="16942-291">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="16942-292">Os perfis de respeitam a configuração de por anfitrião do PowerShell, para que os perfis de anfitrião específico padrão existe em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.</span><span class="sxs-lookup"><span data-stu-id="16942-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="16942-293">PowerShell respeita os [XDG Base diretório especificação] [ xdg-bds] no Linux.</span><span class="sxs-lookup"><span data-stu-id="16942-293">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
