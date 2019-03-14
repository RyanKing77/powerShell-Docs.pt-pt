---
title: Instalar o PowerShell Core no Linux
description: Informações sobre como instalar o PowerShell Core em várias distribuições do Linux
ms.date: 08/06/2018
ms.openlocfilehash: 718be0f03f136d6eb7d78fff51abdc36f6a8f0c2
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795730"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="00ba0-103">Instalar o PowerShell Core no Linux</span><span class="sxs-lookup"><span data-stu-id="00ba0-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="00ba0-104">Suporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04] [ u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9] [ deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE dar um passo 15][opensuse], [Fedora 27][fedora], [ Fedora 28][fedora], e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="00ba0-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="00ba0-105">Para as distribuições de Linux que não são suportadas oficialmente, pode tentar usar a [pacote de ajuste do PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="00ba0-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="00ba0-106">Também pode tentar implementar os binários do PowerShell diretamente com a Linux [ `tar.gz` arquivo][tar], mas terá de configurar as dependências necessárias, com base no sistema operacional nos passos separados.</span><span class="sxs-lookup"><span data-stu-id="00ba0-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="00ba0-107">Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.</span><span class="sxs-lookup"><span data-stu-id="00ba0-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="00ba0-108">Depois do pacote está instalado, execute `pwsh` partir de um terminal.</span><span class="sxs-lookup"><span data-stu-id="00ba0-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="00ba0-109">Instalar versões de pré-visualização</span><span class="sxs-lookup"><span data-stu-id="00ba0-109">Installing Preview Releases</span></span>

<span data-ttu-id="00ba0-110">Ao instalar uma versão de pré-visualização do PowerShell Core para Linux através de um repositório de pacotes, o nome do pacote é alterado de `powershell` para `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="00ba0-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="00ba0-111">Instalar através de transferência direta não é alterada, além do nome de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="00ba0-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="00ba0-112">Esta é uma tabela de comandos para instalar os pacotes de estável e pré-visualização com os vários gestores de pacote:</span><span class="sxs-lookup"><span data-stu-id="00ba0-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="00ba0-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="00ba0-113">Distribution(s)</span></span>|<span data-ttu-id="00ba0-114">Comando estável</span><span class="sxs-lookup"><span data-stu-id="00ba0-114">Stable Command</span></span> | <span data-ttu-id="00ba0-115">Comando de pré-visualização</span><span class="sxs-lookup"><span data-stu-id="00ba0-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="00ba0-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="00ba0-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="00ba0-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="00ba0-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="00ba0-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="00ba0-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="00ba0-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="00ba0-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="00ba0-120">Instalação através do repositório do pacote - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="00ba0-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="00ba0-121">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="00ba0-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="00ba0-122">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="00ba0-122">This is the preferred method.</span></span>

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

<span data-ttu-id="00ba0-123">Superutilizador, registar-se o repositório da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="00ba0-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="00ba0-124">De ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` para atualizar a instalação.</span><span class="sxs-lookup"><span data-stu-id="00ba0-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="00ba0-125">Instalação através de transferência direta - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="00ba0-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="00ba0-126">Transferir o pacote Debian `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="00ba0-126">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="00ba0-127">do [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="00ba0-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="00ba0-128">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="00ba0-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="00ba0-129">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="00ba0-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="00ba0-130">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00ba0-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="00ba0-131">Desinstalação - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="00ba0-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="00ba0-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="00ba0-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="00ba0-133">Instalação através do repositório do pacote - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="00ba0-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="00ba0-134">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="00ba0-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="00ba0-135">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="00ba0-135">This is the preferred method.</span></span>

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

<span data-ttu-id="00ba0-136">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="00ba0-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="00ba0-137">Instalação através de transferência direta - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="00ba0-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="00ba0-138">Transferir o pacote Debian `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="00ba0-138">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="00ba0-139">do [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="00ba0-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="00ba0-140">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="00ba0-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="00ba0-141">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="00ba0-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="00ba0-142">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00ba0-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="00ba0-143">Desinstalação - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="00ba0-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="00ba0-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="00ba0-144">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="00ba0-145">Instalação através do repositório do pacote - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="00ba0-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="00ba0-146">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="00ba0-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="00ba0-147">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="00ba0-147">This is the preferred method.</span></span>

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

<span data-ttu-id="00ba0-148">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="00ba0-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="00ba0-149">Instalação através de transferência direta - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="00ba0-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="00ba0-150">Transferir o pacote Debian `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="00ba0-150">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="00ba0-151">do [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="00ba0-151">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="00ba0-152">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="00ba0-152">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="00ba0-153">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="00ba0-153">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="00ba0-154">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00ba0-154">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="00ba0-155">Desinstalação - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="00ba0-155">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="00ba0-156">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="00ba0-156">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="00ba0-157">Como 18.10 é um [versão provisória](https://www.ubuntu.com/about/release-cycle), só é [suportada na Comunidade](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="00ba0-157">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="00ba0-158">A instalar num 18.10 é suportada através de `snapd`.</span><span class="sxs-lookup"><span data-stu-id="00ba0-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="00ba0-159">Ver [ajustar pacote] [ snap] para obter instruções completas;</span><span class="sxs-lookup"><span data-stu-id="00ba0-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="00ba0-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="00ba0-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="00ba0-161">Instalação através do repositório do pacote - Debian 8</span><span class="sxs-lookup"><span data-stu-id="00ba0-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="00ba0-162">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="00ba0-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="00ba0-163">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="00ba0-163">This is the preferred method.</span></span>

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

<span data-ttu-id="00ba0-164">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="00ba0-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="00ba0-165">Instalação através de transferência direta - Debian 8</span><span class="sxs-lookup"><span data-stu-id="00ba0-165">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="00ba0-166">Transferir o pacote Debian `powershell_6.1.0-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="00ba0-166">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="00ba0-167">partir do [versões][] página para o computador Debian.</span><span class="sxs-lookup"><span data-stu-id="00ba0-167">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="00ba0-168">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="00ba0-168">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="00ba0-169">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="00ba0-169">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="00ba0-170">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00ba0-170">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="00ba0-171">Desinstalação - Debian 8</span><span class="sxs-lookup"><span data-stu-id="00ba0-171">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="00ba0-172">Debian 9</span><span class="sxs-lookup"><span data-stu-id="00ba0-172">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="00ba0-173">Instalação através do repositório do pacote - Debian 9</span><span class="sxs-lookup"><span data-stu-id="00ba0-173">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="00ba0-174">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="00ba0-174">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="00ba0-175">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="00ba0-175">This is the preferred method.</span></span>

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

<span data-ttu-id="00ba0-176">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="00ba0-176">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="00ba0-177">Instalação através de transferência direta - Debian 9</span><span class="sxs-lookup"><span data-stu-id="00ba0-177">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="00ba0-178">Transferir o pacote Debian `powershell_6.1.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="00ba0-178">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="00ba0-179">partir do [versões][] página para o computador Debian.</span><span class="sxs-lookup"><span data-stu-id="00ba0-179">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="00ba0-180">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="00ba0-180">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="00ba0-181">Desinstalação - Debian 9</span><span class="sxs-lookup"><span data-stu-id="00ba0-181">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="00ba0-182">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="00ba0-182">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="00ba0-183">Este pacote também funciona no Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="00ba0-183">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="00ba0-184">Instalação através do repositório de pacotes (preferencial) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="00ba0-184">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="00ba0-185">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="00ba0-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="00ba0-186">Depois de registar o repositório da Microsoft uma vez como Superutilizador, apenas tem de utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00ba0-186">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="00ba0-187">Instalação através de transferência direta - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="00ba0-187">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="00ba0-188">Usando [CentOS 7][], transfira o pacote RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="00ba0-188">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="00ba0-189">do [versões][] página para o computador de CentOS.</span><span class="sxs-lookup"><span data-stu-id="00ba0-189">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="00ba0-190">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="00ba0-190">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="00ba0-191">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="00ba0-191">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="00ba0-192">Desinstalação - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="00ba0-192">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="00ba0-194">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="00ba0-194">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="00ba0-195">Instalação através do repositório de pacotes (preferencial) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="00ba0-195">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="00ba0-196">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="00ba0-196">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="00ba0-197">Depois de registar o repositório da Microsoft uma vez como Superutilizador, apenas tem de utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00ba0-197">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="00ba0-198">Instalação através de transferência direta - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="00ba0-198">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="00ba0-199">Transferir o pacote RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="00ba0-199">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="00ba0-200">partir do [versões][] página para o computador Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="00ba0-200">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="00ba0-201">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="00ba0-201">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="00ba0-202">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="00ba0-202">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="00ba0-203">Desinstalação - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="00ba0-203">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="00ba0-204">openSUSE</span><span class="sxs-lookup"><span data-stu-id="00ba0-204">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="00ba0-205">Instalação - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="00ba0-205">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="00ba0-206">Instalação - openSUSE dar um passo 15</span><span class="sxs-lookup"><span data-stu-id="00ba0-206">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="00ba0-207">Desinstalação - openSUSE 42.3, openSUSE dar um passo 15</span><span class="sxs-lookup"><span data-stu-id="00ba0-207">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="00ba0-208">Fedora</span><span class="sxs-lookup"><span data-stu-id="00ba0-208">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="00ba0-209">Fedora 28 só é suportada no PowerShell Core 6.1 e versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="00ba0-209">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="00ba0-210">Instalação através do repositório de pacotes (preferencial) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="00ba0-210">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="00ba0-211">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="00ba0-211">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="00ba0-212">Instalação através de transferência direta - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="00ba0-212">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="00ba0-213">Transferir o pacote RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="00ba0-213">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="00ba0-214">do [versões][] página na máquina Fedora.</span><span class="sxs-lookup"><span data-stu-id="00ba0-214">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="00ba0-215">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="00ba0-215">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="00ba0-216">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="00ba0-216">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="00ba0-217">Desinstalação - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="00ba0-217">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="00ba0-218">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="00ba0-218">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="00ba0-219">O suporte de arquitetura é experimental.</span><span class="sxs-lookup"><span data-stu-id="00ba0-219">Arch support is experimental.</span></span>

<span data-ttu-id="00ba0-220">PowerShell está disponível a partir da [Arch Linux][] utilizador repositório (AUR).</span><span class="sxs-lookup"><span data-stu-id="00ba0-220">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="00ba0-221">Pode ser compilado com o [etiquetados de versão mais recente versão][arch-release]</span><span class="sxs-lookup"><span data-stu-id="00ba0-221">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="00ba0-222">Pode ser compilada a partir do [consolidação mais recente a mestre][arch-git]</span><span class="sxs-lookup"><span data-stu-id="00ba0-222">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="00ba0-223">Pode ser instalado utilizando o [binário da versão mais recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="00ba0-223">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="00ba0-224">Pacotes no AUR são mantida de Comunidade – não existe nenhum suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="00ba0-224">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="00ba0-225">Para obter mais informações sobre como instalar pacotes do AUR, consulte a [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou da Comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="00ba0-225">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="00ba0-227">Ajustar o pacote</span><span class="sxs-lookup"><span data-stu-id="00ba0-227">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="00ba0-228">Introdução snapd</span><span class="sxs-lookup"><span data-stu-id="00ba0-228">Getting snapd</span></span>

<span data-ttu-id="00ba0-229">`snapd` é necessário executar snaps.</span><span class="sxs-lookup"><span data-stu-id="00ba0-229">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="00ba0-230">Uso [estas instruções](https://docs.snapcraft.io/core/install) para se certificar de que tenha `snapd` instalado.</span><span class="sxs-lookup"><span data-stu-id="00ba0-230">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="00ba0-231">Instalação através do Snap</span><span class="sxs-lookup"><span data-stu-id="00ba0-231">Installation via Snap</span></span>

<span data-ttu-id="00ba0-232">O PowerShell Core, para o Linux, é publicado para o [Snap store](https://snapcraft.io/store) para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="00ba0-232">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="00ba0-233">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="00ba0-233">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="00ba0-234">Se quiser instalar a versão de pré-visualização, utilize o seguinte método.</span><span class="sxs-lookup"><span data-stu-id="00ba0-234">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="00ba0-235">Depois de instalar o Snap irão atualizar automaticamente, mas pode acionar uma atualização usando `sudo snap refresh powershell` ou `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="00ba0-235">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="00ba0-236">Desinstalação</span><span class="sxs-lookup"><span data-stu-id="00ba0-236">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="00ba0-237">ou</span><span class="sxs-lookup"><span data-stu-id="00ba0-237">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="00ba0-238">Kali</span><span class="sxs-lookup"><span data-stu-id="00ba0-238">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="00ba0-239">Instalação - Kali</span><span class="sxs-lookup"><span data-stu-id="00ba0-239">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="00ba0-240">Desinstalação - Kali</span><span class="sxs-lookup"><span data-stu-id="00ba0-240">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="00ba0-241">Raspbian</span><span class="sxs-lookup"><span data-stu-id="00ba0-241">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="00ba0-242">O suporte de Raspbian é experimental.</span><span class="sxs-lookup"><span data-stu-id="00ba0-242">Raspbian support is experimental.</span></span>

<span data-ttu-id="00ba0-243">Atualmente, o PowerShell só é suportado em Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="00ba0-243">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="00ba0-244">Também CoreCLR (e, portanto, o PowerShell Core) só funcionam em dispositivos de instalador de plataforma 2 e 3 de instalador de plataforma como outros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ter um processador não suportado.</span><span class="sxs-lookup"><span data-stu-id="00ba0-244">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="00ba0-245">Baixe [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e siga o [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) obtê-lo em seu Pi.</span><span class="sxs-lookup"><span data-stu-id="00ba0-245">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="00ba0-246">Instalação - Raspbian</span><span class="sxs-lookup"><span data-stu-id="00ba0-246">Installation - Raspbian</span></span>

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

<span data-ttu-id="00ba0-247">Opcionalmente, pode criar um link simbólico para conseguir iniciar PowerShell sem especificar o caminho para o "pwsh" binário</span><span class="sxs-lookup"><span data-stu-id="00ba0-247">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="00ba0-248">Desinstalação - Raspbian</span><span class="sxs-lookup"><span data-stu-id="00ba0-248">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="00ba0-249">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="00ba0-249">Binary Archives</span></span>

<span data-ttu-id="00ba0-250">Binário de PowerShell `tar.gz` arquivos são fornecidos para plataformas Linux ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="00ba0-250">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="00ba0-251">Dependências</span><span class="sxs-lookup"><span data-stu-id="00ba0-251">Dependencies</span></span>

<span data-ttu-id="00ba0-252">PowerShell cria binários portátil para todas as distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="00ba0-252">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="00ba0-253">Mas o tempo de execução do .NET Core requer diferentes dependências em diversas distribuições e, por conseguinte, o PowerShell faz o mesmo.</span><span class="sxs-lookup"><span data-stu-id="00ba0-253">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="00ba0-254">O gráfico seguinte mostra as dependências de .NET Core 2.0 são suportadas oficialmente em distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="00ba0-254">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="00ba0-255">SO</span><span class="sxs-lookup"><span data-stu-id="00ba0-255">OS</span></span>                 | <span data-ttu-id="00ba0-256">Dependências</span><span class="sxs-lookup"><span data-stu-id="00ba0-256">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="00ba0-257">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="00ba0-257">Ubuntu 14.04</span></span>       | <span data-ttu-id="00ba0-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="00ba0-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="00ba0-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="00ba0-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="00ba0-260">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="00ba0-260">Ubuntu 16.04</span></span>       | <span data-ttu-id="00ba0-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="00ba0-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="00ba0-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="00ba0-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="00ba0-263">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="00ba0-263">Ubuntu 17.10</span></span>       | <span data-ttu-id="00ba0-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="00ba0-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="00ba0-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="00ba0-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="00ba0-266">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="00ba0-266">Ubuntu 18.04</span></span>       | <span data-ttu-id="00ba0-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="00ba0-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="00ba0-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="00ba0-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="00ba0-269">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="00ba0-269">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="00ba0-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="00ba0-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="00ba0-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="00ba0-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="00ba0-272">Debian 9 (Stretch.)</span><span class="sxs-lookup"><span data-stu-id="00ba0-272">Debian 9 (Stretch)</span></span> | <span data-ttu-id="00ba0-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="00ba0-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="00ba0-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="00ba0-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="00ba0-275">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="00ba0-275">CentOS 7</span></span> <br> <span data-ttu-id="00ba0-276">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="00ba0-276">Oracle Linux 7</span></span> <br> <span data-ttu-id="00ba0-277">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="00ba0-277">RHEL 7</span></span> | <span data-ttu-id="00ba0-278">libunwind, libcurl, bibliotecas de openssl, libicu</span><span class="sxs-lookup"><span data-stu-id="00ba0-278">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="00ba0-279">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="00ba0-279">openSUSE 42.3</span></span> | <span data-ttu-id="00ba0-280">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="00ba0-280">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="00ba0-281">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="00ba0-281">openSUSE Leap 15</span></span> | <span data-ttu-id="00ba0-282">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="00ba0-282">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="00ba0-283">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="00ba0-283">Fedora 27</span></span> <br> <span data-ttu-id="00ba0-284">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="00ba0-284">Fedora 28</span></span> | <span data-ttu-id="00ba0-285">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="00ba0-285">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="00ba0-286">Para implementar os binários do PowerShell distribuições de Linux que não são suportados oficialmente, terá de instalar as dependências necessárias para o sistema operacional de destino nos passos separados.</span><span class="sxs-lookup"><span data-stu-id="00ba0-286">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="00ba0-287">Por exemplo, nossa [Amazon Linux dockerfile] [ amazon-dockerfile] instala as dependências primeiro e, em seguida, extrai a Linux `tar.gz` arquivo.</span><span class="sxs-lookup"><span data-stu-id="00ba0-287">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="00ba0-288">Instalação - arquivos binários</span><span class="sxs-lookup"><span data-stu-id="00ba0-288">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="00ba0-289">Linux</span><span class="sxs-lookup"><span data-stu-id="00ba0-289">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="00ba0-290">A desinstalar arquivos binários</span><span class="sxs-lookup"><span data-stu-id="00ba0-290">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="00ba0-291">Caminhos</span><span class="sxs-lookup"><span data-stu-id="00ba0-291">Paths</span></span>

* <span data-ttu-id="00ba0-292">`$PSHOME` é `/opt/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="00ba0-292">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="00ba0-293">Perfis de utilizador serão lido a partir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="00ba0-293">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="00ba0-294">Perfis predefinidos serão lido a partir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="00ba0-294">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="00ba0-295">Módulos de utilizador serão lido a partir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="00ba0-295">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="00ba0-296">Módulos partilhados serão lido a partir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="00ba0-296">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="00ba0-297">Módulos padrão serão lido a partir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="00ba0-297">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="00ba0-298">Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="00ba0-298">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="00ba0-299">Os perfis de respeitam a configuração de por anfitrião do PowerShell, para que os perfis de anfitrião específico padrão existe em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.</span><span class="sxs-lookup"><span data-stu-id="00ba0-299">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="00ba0-300">PowerShell respeita os [XDG Base diretório especificação] [ xdg-bds] no Linux.</span><span class="sxs-lookup"><span data-stu-id="00ba0-300">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
