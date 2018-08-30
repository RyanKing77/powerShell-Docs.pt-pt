---
title: Instalar o PowerShell Core no Linux
description: Informações sobre como instalar o PowerShell Core em várias distribuições do Linux
ms.date: 08/06/2018
ms.openlocfilehash: 0a1f30ef75a0feeb97df9a35a08d6b0d3edaeccf
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133839"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="dc506-103">Instalar o PowerShell Core no Linux</span><span class="sxs-lookup"><span data-stu-id="dc506-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="dc506-104">Suporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10] [ u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27 ] [ fedora], [Fedora 28][fedora], e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="dc506-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="dc506-105">Para as distribuições de Linux que não são suportadas oficialmente, pode tentar usar a [pacote de ajuste do PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="dc506-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="dc506-106">Também pode tentar implementar os binários do PowerShell diretamente com a Linux [ `tar.gz` arquivo][tar], mas terá de configurar as dependências necessárias, com base no sistema operacional nos passos separados.</span><span class="sxs-lookup"><span data-stu-id="dc506-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="dc506-107">Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.</span><span class="sxs-lookup"><span data-stu-id="dc506-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="dc506-108">Depois do pacote está instalado, execute `pwsh` partir de um terminal.</span><span class="sxs-lookup"><span data-stu-id="dc506-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u18]: #ubuntu-1810
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="dc506-109">Instalar versões de pré-visualização</span><span class="sxs-lookup"><span data-stu-id="dc506-109">Installing Preview Releases</span></span>

<span data-ttu-id="dc506-110">Ao instalar uma versão de pré-visualização do PowerShell Core para Linux através de um repositório de pacotes, o nome do pacote é alterado de `powershell` para `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="dc506-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="dc506-111">Instalar através de transferência direta não é alterada, além do nome de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="dc506-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="dc506-112">Esta é uma tabela de comandos para instalar os pacotes de estável e pré-visualização com os vários gestores de pacote:</span><span class="sxs-lookup"><span data-stu-id="dc506-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="dc506-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="dc506-113">Distribution(s)</span></span>|<span data-ttu-id="dc506-114">Comando estável</span><span class="sxs-lookup"><span data-stu-id="dc506-114">Stable Command</span></span> | <span data-ttu-id="dc506-115">Comando de pré-visualização</span><span class="sxs-lookup"><span data-stu-id="dc506-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="dc506-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="dc506-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="dc506-117">CentOS, Red Hat</span><span class="sxs-lookup"><span data-stu-id="dc506-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="dc506-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="dc506-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="dc506-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="dc506-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="dc506-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="dc506-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="dc506-121">Instalação através do repositório do pacote - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="dc506-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="dc506-122">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="dc506-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="dc506-123">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="dc506-123">This is the preferred method.</span></span>

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

<span data-ttu-id="dc506-124">Superutilizador, registar-se o repositório da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dc506-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="dc506-125">De ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` para atualizar a instalação.</span><span class="sxs-lookup"><span data-stu-id="dc506-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="dc506-126">Instalação através de transferência direta - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="dc506-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="dc506-127">Transferir o pacote Debian `powershell_6.0.3-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="dc506-127">Download the Debian package `powershell_6.0.3-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="dc506-128">do [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="dc506-128">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="dc506-129">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="dc506-129">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.3-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="dc506-130">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="dc506-130">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="dc506-131">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc506-131">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="dc506-132">Desinstalação - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="dc506-132">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="dc506-133">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="dc506-133">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="dc506-134">Instalação através do repositório do pacote - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="dc506-134">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="dc506-135">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="dc506-135">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="dc506-136">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="dc506-136">This is the preferred method.</span></span>

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

<span data-ttu-id="dc506-137">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="dc506-137">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="dc506-138">Instalação através de transferência direta - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="dc506-138">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="dc506-139">Transferir o pacote Debian `powershell_6.0.3-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="dc506-139">Download the Debian package `powershell_6.0.3-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="dc506-140">do [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="dc506-140">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="dc506-141">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="dc506-141">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.3-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="dc506-142">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="dc506-142">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="dc506-143">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc506-143">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="dc506-144">Desinstalação - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="dc506-144">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="dc506-145">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="dc506-145">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="dc506-146">Foi adicionado suporte para Ubuntu 18.04 após `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="dc506-146">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="dc506-147">Instalação através do repositório do pacote - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="dc506-147">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="dc506-148">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="dc506-148">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="dc506-149">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="dc506-149">This is the preferred method.</span></span>

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

<span data-ttu-id="dc506-150">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="dc506-150">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="dc506-151">Instalação através de transferência direta - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="dc506-151">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="dc506-152">Transferir o pacote Debian `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="dc506-152">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="dc506-153">do [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="dc506-153">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="dc506-154">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="dc506-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="dc506-155">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="dc506-155">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="dc506-156">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc506-156">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="dc506-157">Desinstalação - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="dc506-157">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="dc506-158">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="dc506-158">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="dc506-159">Foi adicionado suporte para Ubuntu 18.10 após `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="dc506-159">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="dc506-160">Como 18.10 é uma compilação diária, é apenas suportada na Comunidade.</span><span class="sxs-lookup"><span data-stu-id="dc506-160">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="dc506-161">A instalar num 18.10 é suportada através de `snapd`.</span><span class="sxs-lookup"><span data-stu-id="dc506-161">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="dc506-162">Ver [ajustar pacote] [ snap] para obter instruções completas;</span><span class="sxs-lookup"><span data-stu-id="dc506-162">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="dc506-163">Debian 8</span><span class="sxs-lookup"><span data-stu-id="dc506-163">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="dc506-164">Instalação através do repositório do pacote - Debian 8</span><span class="sxs-lookup"><span data-stu-id="dc506-164">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="dc506-165">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="dc506-165">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="dc506-166">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="dc506-166">This is the preferred method.</span></span>

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

<span data-ttu-id="dc506-167">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="dc506-167">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="dc506-168">Instalação através de transferência direta - Debian 8</span><span class="sxs-lookup"><span data-stu-id="dc506-168">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="dc506-169">Transferir o pacote Debian `powershell_6.0.3-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="dc506-169">Download the Debian package `powershell_6.0.3-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="dc506-170">partir do [versões][] página para o computador Debian.</span><span class="sxs-lookup"><span data-stu-id="dc506-170">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="dc506-171">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="dc506-171">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.3-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="dc506-172">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="dc506-172">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="dc506-173">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc506-173">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="dc506-174">Desinstalação - Debian 8</span><span class="sxs-lookup"><span data-stu-id="dc506-174">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="dc506-175">Debian 9</span><span class="sxs-lookup"><span data-stu-id="dc506-175">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="dc506-176">Instalação através do repositório do pacote - Debian 9</span><span class="sxs-lookup"><span data-stu-id="dc506-176">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="dc506-177">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="dc506-177">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="dc506-178">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="dc506-178">This is the preferred method.</span></span>

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

<span data-ttu-id="dc506-179">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="dc506-179">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="dc506-180">Instalação através de transferência direta - Debian 9</span><span class="sxs-lookup"><span data-stu-id="dc506-180">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="dc506-181">Transferir o pacote Debian `powershell_6.0.3-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="dc506-181">Download the Debian package `powershell_6.0.3-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="dc506-182">partir do [versões][] página para o computador Debian.</span><span class="sxs-lookup"><span data-stu-id="dc506-182">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="dc506-183">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="dc506-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.3-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="dc506-184">Desinstalação - Debian 9</span><span class="sxs-lookup"><span data-stu-id="dc506-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="dc506-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dc506-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="dc506-186">Este pacote também funciona no Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="dc506-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="dc506-187">Instalação através do repositório de pacotes (preferencial) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dc506-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="dc506-188">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="dc506-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="dc506-189">Depois de registar o repositório da Microsoft uma vez como Superutilizador, apenas tem de utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc506-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="dc506-190">Instalação através de transferência direta - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dc506-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="dc506-191">Usando [CentOS 7][], transfira o pacote RPM `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="dc506-191">Using [CentOS 7][], download the RPM package `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="dc506-192">do [versões][] página para o computador de CentOS.</span><span class="sxs-lookup"><span data-stu-id="dc506-192">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="dc506-193">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="dc506-193">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="dc506-194">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="dc506-194">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.3/powershell-6.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="dc506-195">Desinstalação - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dc506-195">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="dc506-197">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="dc506-197">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="dc506-198">Instalação através do repositório de pacotes (preferencial) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="dc506-198">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="dc506-199">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="dc506-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="dc506-200">Depois de registar o repositório da Microsoft uma vez como Superutilizador, apenas tem de utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc506-200">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="dc506-201">Instalação através de transferência direta - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="dc506-201">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="dc506-202">Transferir o pacote RPM `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="dc506-202">Download the RPM package `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="dc506-203">partir do [versões][] página para o computador Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="dc506-203">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="dc506-204">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="dc506-204">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="dc506-205">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="dc506-205">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.3/powershell-6.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="dc506-206">Desinstalação - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="dc506-206">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="dc506-207">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="dc506-207">OpenSUSE 42.3</span></span>

<span data-ttu-id="dc506-208">Quando instalar o PowerShell Core, `zypper` pode reportar o erro seguinte:</span><span class="sxs-lookup"><span data-stu-id="dc506-208">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="dc506-209">Neste caso, certifique-se de que um ecrã compatível com `libcurl` biblioteca está presente, verificando que o seguinte comando mostra o `libcurl4` como instalado o pacote:</span><span class="sxs-lookup"><span data-stu-id="dc506-209">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="dc506-210">Em seguida, escolha o `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solução ao instalar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc506-210">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="dc506-211">Instalação através do repositório de pacotes (preferencial) - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="dc506-211">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="dc506-212">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="dc506-212">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="dc506-213">Instalação através de transferência direta - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="dc506-213">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="dc506-214">Transferir o pacote RPM `powershell-6.0.3-1.rhel.7.x86_64.rpm` partir a [versões][] página na máquina OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="dc506-214">Download the RPM package `powershell-6.0.3-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="dc506-215">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="dc506-215">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.3/powershell-6.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="dc506-216">Desinstalação - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="dc506-216">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="dc506-217">Fedora</span><span class="sxs-lookup"><span data-stu-id="dc506-217">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="dc506-218">Fedora 28 só é suportada no PowerShell Core 6.1 e versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="dc506-218">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="dc506-219">Instalação através do repositório de pacotes (preferencial) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="dc506-219">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="dc506-220">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="dc506-220">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="dc506-221">Instalação através de transferência direta - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="dc506-221">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="dc506-222">Transferir o pacote RPM `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="dc506-222">Download the RPM package `powershell-6.0.3-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="dc506-223">do [versões][] página na máquina Fedora.</span><span class="sxs-lookup"><span data-stu-id="dc506-223">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="dc506-224">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="dc506-224">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="dc506-225">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="dc506-225">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="dc506-226">Desinstalação - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="dc506-226">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="dc506-227">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="dc506-227">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="dc506-228">O suporte de arquitetura é experimental.</span><span class="sxs-lookup"><span data-stu-id="dc506-228">Arch support is experimental.</span></span>

<span data-ttu-id="dc506-229">PowerShell está disponível a partir da [Arch Linux][] utilizador repositório (AUR).</span><span class="sxs-lookup"><span data-stu-id="dc506-229">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="dc506-230">Pode ser compilado com o [etiquetados de versão mais recente versão][arch-release]</span><span class="sxs-lookup"><span data-stu-id="dc506-230">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="dc506-231">Pode ser compilada a partir do [consolidação mais recente a mestre][arch-git]</span><span class="sxs-lookup"><span data-stu-id="dc506-231">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="dc506-232">Pode ser instalado utilizando o [binário da versão mais recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="dc506-232">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="dc506-233">Pacotes no AUR são mantida de Comunidade – não existe nenhum suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="dc506-233">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="dc506-234">Para obter mais informações sobre como instalar pacotes do AUR, consulte a [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou da Comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="dc506-234">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="dc506-236">Ajustar o pacote</span><span class="sxs-lookup"><span data-stu-id="dc506-236">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="dc506-237">Introdução snapd</span><span class="sxs-lookup"><span data-stu-id="dc506-237">Getting snapd</span></span>

<span data-ttu-id="dc506-238">`snapd` é necessário executar snaps.</span><span class="sxs-lookup"><span data-stu-id="dc506-238">`snapd` is required to run snaps.</span></span>  <span data-ttu-id="dc506-239">Uso [estas instruções](https://docs.snapcraft.io/core/install) para se certificar de que tenha `snapd` instalado.</span><span class="sxs-lookup"><span data-stu-id="dc506-239">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="dc506-240">Instalação através do Snap</span><span class="sxs-lookup"><span data-stu-id="dc506-240">Installation via Snap</span></span>

<span data-ttu-id="dc506-241">O PowerShell Core, para o Linux, é publicado para o [Snap store](https://snapcraft.io/store) para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="dc506-241">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="dc506-242">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="dc506-242">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="dc506-243">Depois de instalar o Snap irão atualizar automaticamente, mas pode acionar uma atualização usando `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="dc506-243">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="dc506-244">Desinstalação</span><span class="sxs-lookup"><span data-stu-id="dc506-244">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="linux-appimage"></a><span data-ttu-id="dc506-245">AppImage do Linux</span><span class="sxs-lookup"><span data-stu-id="dc506-245">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="dc506-246">Suporte de AppImage é experimental</span><span class="sxs-lookup"><span data-stu-id="dc506-246">AppImage support is experimental</span></span>

<span data-ttu-id="dc506-247">Utilizando uma distribuição Linux recente, Baixe o AppImage `powershell-6.0.1-x86_64.AppImage` partir do [versões][] página na máquina Linux.</span><span class="sxs-lookup"><span data-stu-id="dc506-247">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="dc506-248">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="dc506-248">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="dc506-249">O [AppImage][] permite-lhe executar o PowerShell sem instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="dc506-249">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="dc506-250">É um aplicativo portáteis que agrupa o PowerShell e as respetivas dependências (incluindo as dependências do sistema de .NET Core) num único pacote coeso.</span><span class="sxs-lookup"><span data-stu-id="dc506-250">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="dc506-251">Este pacote é um único binário que funciona de forma independente da distribuição de Linux do utilizador.</span><span class="sxs-lookup"><span data-stu-id="dc506-251">This package is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="dc506-253">Kali</span><span class="sxs-lookup"><span data-stu-id="dc506-253">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="dc506-254">O suporte de Kali é experimental.</span><span class="sxs-lookup"><span data-stu-id="dc506-254">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="dc506-255">Instalação</span><span class="sxs-lookup"><span data-stu-id="dc506-255">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.3-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="dc506-256">Executar o PowerShell sem instalá-lo no Kali mais recente (implementar Kali GNU/Linux)</span><span class="sxs-lookup"><span data-stu-id="dc506-256">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="dc506-257">Desinstalação - Kali</span><span class="sxs-lookup"><span data-stu-id="dc506-257">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="dc506-258">Raspbian</span><span class="sxs-lookup"><span data-stu-id="dc506-258">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="dc506-259">O suporte de Raspbian é experimental.</span><span class="sxs-lookup"><span data-stu-id="dc506-259">Raspbian support is experimental.</span></span>

<span data-ttu-id="dc506-260">Atualmente, o PowerShell só é suportado em Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="dc506-260">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="dc506-261">Também CoreCLR (e, portanto, o PowerShell Core) só funcionam em dispositivos de instalador de plataforma 2 e 3 de instalador de plataforma como outros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ter um processador não suportado.</span><span class="sxs-lookup"><span data-stu-id="dc506-261">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="dc506-262">Baixe [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e siga o [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) obtê-lo em seu Pi.</span><span class="sxs-lookup"><span data-stu-id="dc506-262">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="dc506-263">Instalação</span><span class="sxs-lookup"><span data-stu-id="dc506-263">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.3/powershell-6.0.3-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.3-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="dc506-264">Opcionalmente, pode criar um link simbólico para conseguir iniciar PowerShell sem especificar o caminho para o "pwsh" binário</span><span class="sxs-lookup"><span data-stu-id="dc506-264">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="dc506-265">Desinstalação - Raspbian</span><span class="sxs-lookup"><span data-stu-id="dc506-265">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="dc506-266">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="dc506-266">Binary Archives</span></span>

<span data-ttu-id="dc506-267">Binário de PowerShell `tar.gz` arquivos são fornecidos para plataformas Linux ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="dc506-267">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="dc506-268">Dependências</span><span class="sxs-lookup"><span data-stu-id="dc506-268">Dependencies</span></span>

<span data-ttu-id="dc506-269">PowerShell cria binários portátil para todas as distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="dc506-269">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="dc506-270">Mas o tempo de execução do .NET Core requer diferentes dependências em diversas distribuições e, por conseguinte, o PowerShell faz o mesmo.</span><span class="sxs-lookup"><span data-stu-id="dc506-270">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="dc506-271">O gráfico seguinte mostra as dependências de .NET Core 2.0 são suportadas oficialmente em distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="dc506-271">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="dc506-272">SO</span><span class="sxs-lookup"><span data-stu-id="dc506-272">OS</span></span>                 | <span data-ttu-id="dc506-273">Dependências</span><span class="sxs-lookup"><span data-stu-id="dc506-273">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="dc506-274">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="dc506-274">Ubuntu 14.04</span></span>       | <span data-ttu-id="dc506-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="dc506-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dc506-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="dc506-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="dc506-277">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="dc506-277">Ubuntu 16.04</span></span>       | <span data-ttu-id="dc506-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="dc506-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dc506-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="dc506-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="dc506-280">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="dc506-280">Ubuntu 17.10</span></span>       | <span data-ttu-id="dc506-281">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="dc506-281">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dc506-282">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="dc506-282">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="dc506-283">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="dc506-283">Ubuntu 18.04</span></span>       | <span data-ttu-id="dc506-284">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="dc506-284">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dc506-285">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="dc506-285">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="dc506-286">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="dc506-286">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="dc506-287">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="dc506-287">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dc506-288">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="dc506-288">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="dc506-289">Debian 9 (Stretch.)</span><span class="sxs-lookup"><span data-stu-id="dc506-289">Debian 9 (Stretch)</span></span> | <span data-ttu-id="dc506-290">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="dc506-290">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="dc506-291">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="dc506-291">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="dc506-292">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="dc506-292">CentOS 7</span></span> <br> <span data-ttu-id="dc506-293">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="dc506-293">Oracle Linux 7</span></span> <br> <span data-ttu-id="dc506-294">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="dc506-294">RHEL 7</span></span> <br> <span data-ttu-id="dc506-295">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="dc506-295">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="dc506-296">libunwind, libcurl, bibliotecas de openssl, libicu</span><span class="sxs-lookup"><span data-stu-id="dc506-296">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="dc506-297">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="dc506-297">Fedora 27</span></span> <br> <span data-ttu-id="dc506-298">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="dc506-298">Fedora 28</span></span> | <span data-ttu-id="dc506-299">libunwind, libcurl, bibliotecas de openssl, libicu, openssl10 de compatibilidade</span><span class="sxs-lookup"><span data-stu-id="dc506-299">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="dc506-300">Para implementar os binários do PowerShell distribuições de Linux que não são suportados oficialmente, terá de instalar as dependências necessárias para o sistema operacional de destino nos passos separados.</span><span class="sxs-lookup"><span data-stu-id="dc506-300">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="dc506-301">Por exemplo, nossa [Amazon Linux dockerfile] [ amazon-dockerfile] instala as dependências primeiro e, em seguida, extrai a Linux `tar.gz` arquivo.</span><span class="sxs-lookup"><span data-stu-id="dc506-301">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="dc506-302">Instalação - arquivos binários</span><span class="sxs-lookup"><span data-stu-id="dc506-302">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="dc506-303">Linux</span><span class="sxs-lookup"><span data-stu-id="dc506-303">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="dc506-304">A desinstalar arquivos binários</span><span class="sxs-lookup"><span data-stu-id="dc506-304">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="dc506-305">Caminhos</span><span class="sxs-lookup"><span data-stu-id="dc506-305">Paths</span></span>

* <span data-ttu-id="dc506-306">`$PSHOME` é `/opt/microsoft/powershell/6.0.3/`</span><span class="sxs-lookup"><span data-stu-id="dc506-306">`$PSHOME` is `/opt/microsoft/powershell/6.0.3/`</span></span>
* <span data-ttu-id="dc506-307">Perfis de utilizador serão lido a partir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="dc506-307">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="dc506-308">Perfis predefinidos serão lido a partir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="dc506-308">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="dc506-309">Módulos de utilizador serão lido a partir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="dc506-309">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="dc506-310">Módulos partilhados serão lido a partir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="dc506-310">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="dc506-311">Módulos padrão serão lido a partir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="dc506-311">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="dc506-312">Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="dc506-312">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="dc506-313">Os perfis de respeitam a configuração de por anfitrião do PowerShell, para que os perfis de anfitrião específico padrão existe em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.</span><span class="sxs-lookup"><span data-stu-id="dc506-313">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="dc506-314">PowerShell respeita os [XDG Base diretório especificação] [ xdg-bds] no Linux.</span><span class="sxs-lookup"><span data-stu-id="dc506-314">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
