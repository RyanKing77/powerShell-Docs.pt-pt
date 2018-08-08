---
title: Instalar o PowerShell Core no Linux
description: Informações sobre como instalar o PowerShell Core em várias distribuições do Linux
ms.date: 08/06/2018
ms.openlocfilehash: a6b0e3003f84ea6dc99cffcc7edf1b5b6963aa21
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587453"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="daebf-103">Instalar o PowerShell Core no Linux</span><span class="sxs-lookup"><span data-stu-id="daebf-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="daebf-104">Suporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10] [ u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27 ] [ fedora], [Fedora 28][fedora], e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="daebf-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="daebf-105">Para as distribuições de Linux que não são suportadas oficialmente, pode tentar usar a [pacote de ajuste do PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="daebf-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="daebf-106">Também pode tentar implementar os binários do PowerShell diretamente com a Linux [ `tar.gz` arquivo][tar], mas terá de configurar as dependências necessárias, com base no sistema operacional nos passos separados.</span><span class="sxs-lookup"><span data-stu-id="daebf-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="daebf-107">Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.</span><span class="sxs-lookup"><span data-stu-id="daebf-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="daebf-108">Depois do pacote está instalado, execute `pwsh` partir de um terminal.</span><span class="sxs-lookup"><span data-stu-id="daebf-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="installing-preview-releases"></a><span data-ttu-id="daebf-109">Instalar versões de pré-visualização</span><span class="sxs-lookup"><span data-stu-id="daebf-109">Installing Preview Releases</span></span>

<span data-ttu-id="daebf-110">Ao instalar uma versão de pré-visualização do PowerShell Core para Linux através de um repositório de pacotes, o nome do pacote é alterado de `powershell` para `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="daebf-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="daebf-111">Instalar através de transferência direta não é alterada, além do nome de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="daebf-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="daebf-112">Esta é uma tabela de comandos para instalar os pacotes de estável e pré-visualização com os vários gestores de pacote:</span><span class="sxs-lookup"><span data-stu-id="daebf-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="daebf-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="daebf-113">Distribution(s)</span></span>|<span data-ttu-id="daebf-114">Comando estável</span><span class="sxs-lookup"><span data-stu-id="daebf-114">Stable Command</span></span> | <span data-ttu-id="daebf-115">Comando de pré-visualização</span><span class="sxs-lookup"><span data-stu-id="daebf-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="daebf-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="daebf-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="daebf-117">CentOS, Red Hat</span><span class="sxs-lookup"><span data-stu-id="daebf-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="daebf-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="daebf-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="daebf-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="daebf-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="daebf-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="daebf-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="daebf-121">Instalação através do repositório do pacote - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="daebf-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="daebf-122">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="daebf-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="daebf-123">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="daebf-123">This is the preferred method.</span></span>

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

<span data-ttu-id="daebf-124">Superutilizador, registar-se o repositório da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="daebf-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="daebf-125">De ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` para atualizar a instalação.</span><span class="sxs-lookup"><span data-stu-id="daebf-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="daebf-126">Instalação através de transferência direta - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="daebf-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="daebf-127">Transferir o pacote Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` partir a [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="daebf-127">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="daebf-128">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="daebf-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="daebf-129">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="daebf-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="daebf-130">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="daebf-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="daebf-131">Desinstalação - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="daebf-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="daebf-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="daebf-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="daebf-133">Instalação através do repositório do pacote - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="daebf-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="daebf-134">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="daebf-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="daebf-135">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="daebf-135">This is the preferred method.</span></span>

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

<span data-ttu-id="daebf-136">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="daebf-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="daebf-137">Instalação através de transferência direta - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="daebf-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="daebf-138">Transferir o pacote Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` partir a [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="daebf-138">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="daebf-139">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="daebf-139">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="daebf-140">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="daebf-140">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="daebf-141">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="daebf-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="daebf-142">Desinstalação - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="daebf-142">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="daebf-143">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="daebf-143">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="daebf-144">Foi adicionado suporte para Ubuntu 18.04 após `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="daebf-144">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="daebf-145">Instalação através do repositório do pacote - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="daebf-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="daebf-146">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="daebf-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="daebf-147">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="daebf-147">This is the preferred method.</span></span>

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

<span data-ttu-id="daebf-148">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="daebf-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="daebf-149">Instalação através de transferência direta - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="daebf-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="daebf-150">Transferir o pacote Debian `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` partir a [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="daebf-150">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="daebf-151">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="daebf-151">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="daebf-152">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="daebf-152">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="daebf-153">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="daebf-153">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="daebf-154">Desinstalação - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="daebf-154">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="daebf-155">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="daebf-155">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="daebf-156">Foi adicionado suporte para Ubuntu 18.10 após `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="daebf-156">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="daebf-157">Como 18.10 é uma compilação diária, é apenas suportada na Comunidade.</span><span class="sxs-lookup"><span data-stu-id="daebf-157">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="daebf-158">A instalar num 18.10 é suportada através de `snapd`.</span><span class="sxs-lookup"><span data-stu-id="daebf-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="daebf-159">Ver [ajustar pacote] [ snap] para obter instruções completas;</span><span class="sxs-lookup"><span data-stu-id="daebf-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="daebf-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="daebf-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="daebf-161">Instalação através do repositório do pacote - Debian 8</span><span class="sxs-lookup"><span data-stu-id="daebf-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="daebf-162">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="daebf-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="daebf-163">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="daebf-163">This is the preferred method.</span></span>

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

<span data-ttu-id="daebf-164">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="daebf-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="daebf-165">Instalação através de transferência direta - Debian 8</span><span class="sxs-lookup"><span data-stu-id="daebf-165">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="daebf-166">Transferir o pacote Debian `powershell_6.0.2-1.debian.8_amd64.deb` partir a [versões][] página para o computador Debian.</span><span class="sxs-lookup"><span data-stu-id="daebf-166">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="daebf-167">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="daebf-167">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="daebf-168">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="daebf-168">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="daebf-169">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="daebf-169">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="daebf-170">Desinstalação - Debian 8</span><span class="sxs-lookup"><span data-stu-id="daebf-170">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="daebf-171">Debian 9</span><span class="sxs-lookup"><span data-stu-id="daebf-171">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="daebf-172">Instalação através do repositório do pacote - Debian 9</span><span class="sxs-lookup"><span data-stu-id="daebf-172">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="daebf-173">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="daebf-173">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="daebf-174">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="daebf-174">This is the preferred method.</span></span>

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

<span data-ttu-id="daebf-175">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="daebf-175">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="daebf-176">Instalação através de transferência direta - Debian 9</span><span class="sxs-lookup"><span data-stu-id="daebf-176">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="daebf-177">Transferir o pacote Debian `powershell_6.0.2-1.debian.9_amd64.deb` partir a [versões][] página para o computador Debian.</span><span class="sxs-lookup"><span data-stu-id="daebf-177">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="daebf-178">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="daebf-178">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="daebf-179">Desinstalação - Debian 9</span><span class="sxs-lookup"><span data-stu-id="daebf-179">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="daebf-180">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="daebf-180">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="daebf-181">Este pacote também funciona no Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="daebf-181">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="daebf-182">Instalação através do repositório de pacotes (preferencial) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="daebf-182">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="daebf-183">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="daebf-183">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="daebf-184">Depois de registar o repositório da Microsoft uma vez como Superutilizador, apenas tem de utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="daebf-184">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="daebf-185">Instalação através de transferência direta - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="daebf-185">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="daebf-186">Usando [CentOS 7][], transfira o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` da [versões][] página para o computador de CentOS.</span><span class="sxs-lookup"><span data-stu-id="daebf-186">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="daebf-187">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="daebf-187">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="daebf-188">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="daebf-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="daebf-189">Desinstalação - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="daebf-189">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="daebf-191">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="daebf-191">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="daebf-192">Instalação através do repositório de pacotes (preferencial) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="daebf-192">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="daebf-193">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="daebf-193">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="daebf-194">Depois de registar o repositório da Microsoft uma vez como Superutilizador, apenas tem de utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="daebf-194">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="daebf-195">Instalação através de transferência direta - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="daebf-195">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="daebf-196">Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` partir de [versões][] página para o computador Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="daebf-196">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="daebf-197">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="daebf-197">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="daebf-198">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="daebf-198">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="daebf-199">Desinstalação - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="daebf-199">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="daebf-200">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="daebf-200">OpenSUSE 42.3</span></span>

<span data-ttu-id="daebf-201">Quando instalar o PowerShell Core, `zypper` pode reportar o erro seguinte:</span><span class="sxs-lookup"><span data-stu-id="daebf-201">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="daebf-202">Neste caso, certifique-se de que um ecrã compatível com `libcurl` biblioteca está presente, verificando que o seguinte comando mostra o `libcurl4` como instalado o pacote:</span><span class="sxs-lookup"><span data-stu-id="daebf-202">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="daebf-203">Em seguida, escolha o `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solução ao instalar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="daebf-203">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="daebf-204">Instalação através do repositório de pacotes (preferencial) - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="daebf-204">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="daebf-205">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="daebf-205">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="daebf-206">Instalação através de transferência direta - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="daebf-206">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="daebf-207">Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` partir a [versões][] página na máquina OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="daebf-207">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="daebf-208">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="daebf-208">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="daebf-209">Desinstalação - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="daebf-209">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="daebf-210">Fedora</span><span class="sxs-lookup"><span data-stu-id="daebf-210">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="daebf-211">Fedora 28 só é suportada no PowerShell Core 6.1 e versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="daebf-211">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="daebf-212">Instalação através do repositório de pacotes (preferencial) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="daebf-212">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="daebf-213">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="daebf-213">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="daebf-214">Instalação através de transferência direta - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="daebf-214">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="daebf-215">Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` partir a [versões][] página na máquina Fedora.</span><span class="sxs-lookup"><span data-stu-id="daebf-215">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="daebf-216">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="daebf-216">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="daebf-217">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="daebf-217">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="daebf-218">Desinstalação - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="daebf-218">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="daebf-219">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="daebf-219">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="daebf-220">O suporte de arquitetura é experimental.</span><span class="sxs-lookup"><span data-stu-id="daebf-220">Arch support is experimental.</span></span>

<span data-ttu-id="daebf-221">PowerShell está disponível a partir da [Arch Linux][] utilizador repositório (AUR).</span><span class="sxs-lookup"><span data-stu-id="daebf-221">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="daebf-222">Pode ser compilado com o [etiquetados de versão mais recente versão][arch-release]</span><span class="sxs-lookup"><span data-stu-id="daebf-222">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="daebf-223">Pode ser compilada a partir do [consolidação mais recente a mestre][arch-git]</span><span class="sxs-lookup"><span data-stu-id="daebf-223">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="daebf-224">Pode ser instalado utilizando o [binário da versão mais recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="daebf-224">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="daebf-225">Pacotes no AUR são mantida de Comunidade – não existe nenhum suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="daebf-225">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="daebf-226">Para obter mais informações sobre como instalar pacotes do AUR, consulte a [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou da Comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="daebf-226">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="daebf-228">Ajustar o pacote</span><span class="sxs-lookup"><span data-stu-id="daebf-228">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="daebf-229">Introdução snapd</span><span class="sxs-lookup"><span data-stu-id="daebf-229">Getting snapd</span></span>

<span data-ttu-id="daebf-230">`snapd` é necessário executar snaps.</span><span class="sxs-lookup"><span data-stu-id="daebf-230">`snapd` is required to run snaps.</span></span>  <span data-ttu-id="daebf-231">Uso [estas instruções](https://docs.snapcraft.io/core/install) para se certificar de que tenha `snapd` instalado.</span><span class="sxs-lookup"><span data-stu-id="daebf-231">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="daebf-232">Instalação através do Snap</span><span class="sxs-lookup"><span data-stu-id="daebf-232">Installation via Snap</span></span>

<span data-ttu-id="daebf-233">O PowerShell Core, para o Linux, é publicado para o [Snap store](https://snapcraft.io/store) para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="daebf-233">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="daebf-234">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="daebf-234">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="daebf-235">Depois de instalar o Snap irão atualizar automaticamente, mas pode acionar uma atualização usando `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="daebf-235">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="daebf-236">Desinstalação</span><span class="sxs-lookup"><span data-stu-id="daebf-236">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="linux-appimage"></a><span data-ttu-id="daebf-237">AppImage do Linux</span><span class="sxs-lookup"><span data-stu-id="daebf-237">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="daebf-238">Suporte de AppImage é experimental</span><span class="sxs-lookup"><span data-stu-id="daebf-238">AppImage support is experimental</span></span>

<span data-ttu-id="daebf-239">Utilizando uma distribuição Linux recente, Baixe o AppImage `powershell-6.0.1-x86_64.AppImage` partir do [versões][] página na máquina Linux.</span><span class="sxs-lookup"><span data-stu-id="daebf-239">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="daebf-240">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="daebf-240">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="daebf-241">O [AppImage][] permite-lhe executar o PowerShell sem instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="daebf-241">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="daebf-242">É um aplicativo portáteis que agrupa o PowerShell e as respetivas dependências (incluindo as dependências do sistema de .NET Core) num único pacote coeso.</span><span class="sxs-lookup"><span data-stu-id="daebf-242">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="daebf-243">Este pacote é um único binário que funciona de forma independente da distribuição de Linux do utilizador.</span><span class="sxs-lookup"><span data-stu-id="daebf-243">This package is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="daebf-245">Kali</span><span class="sxs-lookup"><span data-stu-id="daebf-245">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="daebf-246">O suporte de Kali é experimental.</span><span class="sxs-lookup"><span data-stu-id="daebf-246">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="daebf-247">Instalação</span><span class="sxs-lookup"><span data-stu-id="daebf-247">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="daebf-248">Executar o PowerShell sem instalá-lo no Kali mais recente (implementar Kali GNU/Linux)</span><span class="sxs-lookup"><span data-stu-id="daebf-248">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="daebf-249">Desinstalação - Kali</span><span class="sxs-lookup"><span data-stu-id="daebf-249">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="daebf-250">Raspbian</span><span class="sxs-lookup"><span data-stu-id="daebf-250">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="daebf-251">O suporte de Raspbian é experimental.</span><span class="sxs-lookup"><span data-stu-id="daebf-251">Raspbian support is experimental.</span></span>

<span data-ttu-id="daebf-252">Atualmente, o PowerShell só é suportado em Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="daebf-252">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="daebf-253">Também CoreCLR (e, portanto, o PowerShell Core) só funcionam em dispositivos de instalador de plataforma 2 e 3 de instalador de plataforma como outros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ter um processador não suportado.</span><span class="sxs-lookup"><span data-stu-id="daebf-253">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="daebf-254">Baixe [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e siga o [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) obtê-lo em seu Pi.</span><span class="sxs-lookup"><span data-stu-id="daebf-254">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="daebf-255">Instalação</span><span class="sxs-lookup"><span data-stu-id="daebf-255">Installation</span></span>

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

<span data-ttu-id="daebf-256">Opcionalmente, pode criar um link simbólico para conseguir iniciar PowerShell sem especificar o caminho para o "pwsh" binário</span><span class="sxs-lookup"><span data-stu-id="daebf-256">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="daebf-257">Desinstalação - Raspbian</span><span class="sxs-lookup"><span data-stu-id="daebf-257">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="daebf-258">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="daebf-258">Binary Archives</span></span>

<span data-ttu-id="daebf-259">Binário de PowerShell `tar.gz` arquivos são fornecidos para plataformas Linux ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="daebf-259">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="daebf-260">Dependências</span><span class="sxs-lookup"><span data-stu-id="daebf-260">Dependencies</span></span>

<span data-ttu-id="daebf-261">PowerShell cria binários portátil para todas as distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="daebf-261">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="daebf-262">Mas o tempo de execução do .NET Core requer diferentes dependências em diversas distribuições e, por conseguinte, o PowerShell faz o mesmo.</span><span class="sxs-lookup"><span data-stu-id="daebf-262">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="daebf-263">O gráfico seguinte mostra as dependências de .NET Core 2.0 são suportadas oficialmente em distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="daebf-263">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="daebf-264">SO</span><span class="sxs-lookup"><span data-stu-id="daebf-264">OS</span></span>                 | <span data-ttu-id="daebf-265">Dependências</span><span class="sxs-lookup"><span data-stu-id="daebf-265">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="daebf-266">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="daebf-266">Ubuntu 14.04</span></span>       | <span data-ttu-id="daebf-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="daebf-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="daebf-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="daebf-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="daebf-269">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="daebf-269">Ubuntu 16.04</span></span>       | <span data-ttu-id="daebf-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="daebf-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="daebf-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="daebf-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="daebf-272">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="daebf-272">Ubuntu 17.10</span></span>       | <span data-ttu-id="daebf-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="daebf-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="daebf-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="daebf-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="daebf-275">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="daebf-275">Ubuntu 18.04</span></span>       | <span data-ttu-id="daebf-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="daebf-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="daebf-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="daebf-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="daebf-278">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="daebf-278">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="daebf-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="daebf-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="daebf-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="daebf-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="daebf-281">Debian 9 (Stretch.)</span><span class="sxs-lookup"><span data-stu-id="daebf-281">Debian 9 (Stretch)</span></span> | <span data-ttu-id="daebf-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="daebf-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="daebf-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="daebf-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="daebf-284">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="daebf-284">CentOS 7</span></span> <br> <span data-ttu-id="daebf-285">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="daebf-285">Oracle Linux 7</span></span> <br> <span data-ttu-id="daebf-286">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="daebf-286">RHEL 7</span></span> <br> <span data-ttu-id="daebf-287">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="daebf-287">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="daebf-288">libunwind, libcurl, bibliotecas de openssl, libicu</span><span class="sxs-lookup"><span data-stu-id="daebf-288">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="daebf-289">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="daebf-289">Fedora 27</span></span> <br> <span data-ttu-id="daebf-290">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="daebf-290">Fedora 28</span></span> | <span data-ttu-id="daebf-291">libunwind, libcurl, bibliotecas de openssl, libicu, openssl10 de compatibilidade</span><span class="sxs-lookup"><span data-stu-id="daebf-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="daebf-292">Para implementar os binários do PowerShell distribuições de Linux que não são suportados oficialmente, terá de instalar as dependências necessárias para o sistema operacional de destino nos passos separados.</span><span class="sxs-lookup"><span data-stu-id="daebf-292">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="daebf-293">Por exemplo, nossa [Amazon Linux dockerfile] [ amazon-dockerfile] instala as dependências primeiro e, em seguida, extrai a Linux `tar.gz` arquivo.</span><span class="sxs-lookup"><span data-stu-id="daebf-293">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="daebf-294">Instalação - arquivos binários</span><span class="sxs-lookup"><span data-stu-id="daebf-294">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="daebf-295">Linux</span><span class="sxs-lookup"><span data-stu-id="daebf-295">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="daebf-296">A desinstalar arquivos binários</span><span class="sxs-lookup"><span data-stu-id="daebf-296">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="daebf-297">Caminhos</span><span class="sxs-lookup"><span data-stu-id="daebf-297">Paths</span></span>

* <span data-ttu-id="daebf-298">`$PSHOME` é `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="daebf-298">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="daebf-299">Perfis de utilizador serão lido a partir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="daebf-299">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="daebf-300">Perfis predefinidos serão lido a partir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="daebf-300">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="daebf-301">Módulos de utilizador serão lido a partir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="daebf-301">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="daebf-302">Módulos partilhados serão lido a partir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="daebf-302">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="daebf-303">Módulos padrão serão lido a partir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="daebf-303">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="daebf-304">Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="daebf-304">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="daebf-305">Os perfis de respeitam a configuração de por anfitrião do PowerShell, para que os perfis de anfitrião específico padrão existe em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.</span><span class="sxs-lookup"><span data-stu-id="daebf-305">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="daebf-306">PowerShell respeita os [XDG Base diretório especificação] [ xdg-bds] no Linux.</span><span class="sxs-lookup"><span data-stu-id="daebf-306">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
