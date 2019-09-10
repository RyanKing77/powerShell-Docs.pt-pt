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
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="e45cf-103">Instalar o PowerShell Core no Linux</span><span class="sxs-lookup"><span data-stu-id="e45cf-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="e45cf-104">Dá suporte ao [ubuntu 16, 4][u16], [Ubuntu 18, 4][u1804], [Ubuntu 18,10][u1810], [Ubuntu 19, 4][u1904], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27 ][fedora], [Fedora 28][fedora]e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="e45cf-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="e45cf-105">Para distribuições Linux que não têm suporte oficial, você pode tentar instalar o PowerShell usando o [pacote de snap do PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="e45cf-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="e45cf-106">Você também pode tentar implantar binários do PowerShell diretamente usando o [ `tar.gz` arquivo][tar]do Linux, mas precisaria configurar as dependências necessárias com base no sistema operacional em etapas separadas.</span><span class="sxs-lookup"><span data-stu-id="e45cf-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="e45cf-107">Todos os pacotes estão disponíveis em nossa página de [versões][] do github.</span><span class="sxs-lookup"><span data-stu-id="e45cf-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="e45cf-108">Após a instalação do pacote, execute `pwsh` a partir de um terminal.</span><span class="sxs-lookup"><span data-stu-id="e45cf-108">After the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="installing-preview-releases"></a><span data-ttu-id="e45cf-109">Instalando versões de visualização</span><span class="sxs-lookup"><span data-stu-id="e45cf-109">Installing Preview Releases</span></span>

<span data-ttu-id="e45cf-110">Ao instalar uma versão de visualização do PowerShell Core para Linux por meio de um repositório de pacotes, `powershell` o `powershell-preview`nome do pacote é alterado de para.</span><span class="sxs-lookup"><span data-stu-id="e45cf-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="e45cf-111">A instalação por meio de download direto não é alterada, além do nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="e45cf-111">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="e45cf-112">A tabela a seguir contém os comandos para instalar os pacotes estáveis e de visualização usando os vários gerenciadores de pacotes:</span><span class="sxs-lookup"><span data-stu-id="e45cf-112">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="e45cf-113">Distribuição (ões)</span><span class="sxs-lookup"><span data-stu-id="e45cf-113">Distribution(s)</span></span>|<span data-ttu-id="e45cf-114">Comando estável</span><span class="sxs-lookup"><span data-stu-id="e45cf-114">Stable Command</span></span> | <span data-ttu-id="e45cf-115">Comando de visualização</span><span class="sxs-lookup"><span data-stu-id="e45cf-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="e45cf-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="e45cf-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="e45cf-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="e45cf-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="e45cf-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="e45cf-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="e45cf-119">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e45cf-119">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="e45cf-120">Instalação por meio do repositório de pacotes – Ubuntu 16, 4</span><span class="sxs-lookup"><span data-stu-id="e45cf-120">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="e45cf-121">O PowerShell Core para Linux é publicado em repositórios de pacotes para facilitar a instalação e as atualizações.</span><span class="sxs-lookup"><span data-stu-id="e45cf-121">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="e45cf-122">O método preferencial é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e45cf-122">The preferred method is as follows:</span></span>

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

<span data-ttu-id="e45cf-123">Como superusuário, registre o repositório da Microsoft uma vez.</span><span class="sxs-lookup"><span data-stu-id="e45cf-123">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e45cf-124">Após o registro, você pode atualizar o `sudo apt-get upgrade powershell`PowerShell com o.</span><span class="sxs-lookup"><span data-stu-id="e45cf-124">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="e45cf-125">Instalação por meio de download direto – Ubuntu 16, 4</span><span class="sxs-lookup"><span data-stu-id="e45cf-125">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="e45cf-126">Baixe o pacote `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` Debian da página [versões][] no computador Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="e45cf-126">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e45cf-127">Em seguida, no terminal, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="e45cf-127">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e45cf-128">O `dpkg -i` comando falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="e45cf-128">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="e45cf-129">O comando `apt-get install -f` a seguir resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e45cf-129">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="e45cf-130">Desinstalação – Ubuntu 16, 4</span><span class="sxs-lookup"><span data-stu-id="e45cf-130">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="e45cf-131">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e45cf-131">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="e45cf-132">Instalação por meio do repositório de pacotes – Ubuntu 18, 4</span><span class="sxs-lookup"><span data-stu-id="e45cf-132">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="e45cf-133">O PowerShell Core para Linux é publicado em repositórios de pacotes para facilitar a instalação e as atualizações.</span><span class="sxs-lookup"><span data-stu-id="e45cf-133">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="e45cf-134">O método preferencial é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e45cf-134">The preferred method is as follows:</span></span>

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

<span data-ttu-id="e45cf-135">Como superusuário, registre o repositório da Microsoft uma vez.</span><span class="sxs-lookup"><span data-stu-id="e45cf-135">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e45cf-136">Após o registro, você pode atualizar o `sudo apt-get upgrade powershell`PowerShell com o.</span><span class="sxs-lookup"><span data-stu-id="e45cf-136">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="e45cf-137">Instalação por meio de download direto – Ubuntu 18, 4</span><span class="sxs-lookup"><span data-stu-id="e45cf-137">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="e45cf-138">Baixe o pacote `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` Debian da página [versões][] no computador Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="e45cf-138">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e45cf-139">Em seguida, no terminal, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="e45cf-139">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e45cf-140">O `dpkg -i` comando falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="e45cf-140">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="e45cf-141">O comando `apt-get install -f` a seguir resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e45cf-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="e45cf-142">Desinstalação – Ubuntu 18, 4</span><span class="sxs-lookup"><span data-stu-id="e45cf-142">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="e45cf-143">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="e45cf-143">Ubuntu 18.10</span></span>

<span data-ttu-id="e45cf-144">A instalação tem suporte `snapd`via.</span><span class="sxs-lookup"><span data-stu-id="e45cf-144">Installation is supported via `snapd`.</span></span> <span data-ttu-id="e45cf-145">Para obter instruções, consulte [snap Package][snap].</span><span class="sxs-lookup"><span data-stu-id="e45cf-145">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="e45cf-146">O Ubuntu 18,10 é uma [versão provisória](https://www.ubuntu.com/about/release-cycle) [com suporte da Comunidade](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="e45cf-146">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="e45cf-147">Ubuntu 19, 4</span><span class="sxs-lookup"><span data-stu-id="e45cf-147">Ubuntu 19.04</span></span>

<span data-ttu-id="e45cf-148">A instalação tem suporte `snapd`via.</span><span class="sxs-lookup"><span data-stu-id="e45cf-148">Installation is supported via `snapd`.</span></span> <span data-ttu-id="e45cf-149">Para obter instruções, consulte [snap Package][snap].</span><span class="sxs-lookup"><span data-stu-id="e45cf-149">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="e45cf-150">O Ubuntu 19, 4 é uma [versão provisória](https://www.ubuntu.com/about/release-cycle) [com suporte da Comunidade](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="e45cf-150">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="e45cf-151">Debian 8</span><span class="sxs-lookup"><span data-stu-id="e45cf-151">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="e45cf-152">Instalação por meio do repositório de pacotes – Debian 8</span><span class="sxs-lookup"><span data-stu-id="e45cf-152">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="e45cf-153">O PowerShell Core para Linux é publicado em repositórios de pacotes para facilitar a instalação e as atualizações.</span><span class="sxs-lookup"><span data-stu-id="e45cf-153">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="e45cf-154">O método preferencial é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e45cf-154">The preferred method is as follows:</span></span>

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

<span data-ttu-id="e45cf-155">Como superusuário, registre o repositório da Microsoft uma vez.</span><span class="sxs-lookup"><span data-stu-id="e45cf-155">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e45cf-156">Após o registro, você pode atualizar o `sudo apt-get upgrade powershell`PowerShell com o.</span><span class="sxs-lookup"><span data-stu-id="e45cf-156">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="e45cf-157">Debian 9</span><span class="sxs-lookup"><span data-stu-id="e45cf-157">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="e45cf-158">Instalação por meio do repositório de pacotes – Debian 9</span><span class="sxs-lookup"><span data-stu-id="e45cf-158">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="e45cf-159">O PowerShell Core para Linux é publicado em repositórios de pacotes para facilitar a instalação e as atualizações.</span><span class="sxs-lookup"><span data-stu-id="e45cf-159">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="e45cf-160">O método preferencial é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e45cf-160">The preferred method is as follows:</span></span>

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

<span data-ttu-id="e45cf-161">Como superusuário, registre o repositório da Microsoft uma vez.</span><span class="sxs-lookup"><span data-stu-id="e45cf-161">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e45cf-162">Após o registro, você pode atualizar o `sudo apt-get upgrade powershell`PowerShell com o.</span><span class="sxs-lookup"><span data-stu-id="e45cf-162">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="e45cf-163">Instalação por meio de download direto – Debian 9</span><span class="sxs-lookup"><span data-stu-id="e45cf-163">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="e45cf-164">Baixe o pacote `powershell_6.2.0-1.debian.9_amd64.deb` Debian da página [versões][] no computador Debian.</span><span class="sxs-lookup"><span data-stu-id="e45cf-164">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e45cf-165">Em seguida, no terminal, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="e45cf-165">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="e45cf-166">Desinstalação – Debian 9</span><span class="sxs-lookup"><span data-stu-id="e45cf-166">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="e45cf-167">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e45cf-167">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="e45cf-168">Este pacote funciona no Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="e45cf-168">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="e45cf-169">Instalação por meio do repositório de pacotes (preferencial) – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e45cf-169">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="e45cf-170">O PowerShell Core para Linux é publicado em repositórios oficiais da Microsoft para facilitar a instalação e as atualizações.</span><span class="sxs-lookup"><span data-stu-id="e45cf-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e45cf-171">Como superusuário, registre o repositório da Microsoft uma vez.</span><span class="sxs-lookup"><span data-stu-id="e45cf-171">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e45cf-172">Após o registro, você pode atualizar o `sudo yum update powershell`PowerShell com o.</span><span class="sxs-lookup"><span data-stu-id="e45cf-172">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="e45cf-173">Instalação por meio do download direto – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e45cf-173">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="e45cf-174">Usando o [CentOS 7][], baixe o pacote `powershell-6.2.0-1.rhel.7.x86_64.rpm` rpm da página [versões][] no computador CentOS.</span><span class="sxs-lookup"><span data-stu-id="e45cf-174">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="e45cf-175">Em seguida, no terminal, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="e45cf-175">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e45cf-176">Você pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="e45cf-176">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="e45cf-177">Desinstalação – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e45cf-177">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e45cf-179">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e45cf-179">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e45cf-180">Instalação por meio do repositório de pacotes (preferencial)-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e45cf-180">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e45cf-181">O PowerShell Core para Linux é publicado em repositórios oficiais da Microsoft para facilitar a instalação e as atualizações.</span><span class="sxs-lookup"><span data-stu-id="e45cf-181">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e45cf-182">Como superusuário, registre o repositório da Microsoft uma vez.</span><span class="sxs-lookup"><span data-stu-id="e45cf-182">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="e45cf-183">Após o registro, você pode atualizar o `sudo yum update powershell`PowerShell com o.</span><span class="sxs-lookup"><span data-stu-id="e45cf-183">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e45cf-184">Instalação por meio de download direto – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e45cf-184">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e45cf-185">Baixe o pacote `powershell-6.2.0-1.rhel.7.x86_64.rpm` rpm da página [versões][] no computador Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="e45cf-185">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="e45cf-186">Em seguida, no terminal, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="e45cf-186">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e45cf-187">Você pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="e45cf-187">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e45cf-188">Desinstalação-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e45cf-188">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="e45cf-189">openSUSE</span><span class="sxs-lookup"><span data-stu-id="e45cf-189">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="e45cf-190">Instalação-openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="e45cf-190">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="e45cf-191">Instalação-openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e45cf-191">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="e45cf-192">Desinstalação-openSUSE 42,3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e45cf-192">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="e45cf-193">Fedora</span><span class="sxs-lookup"><span data-stu-id="e45cf-193">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="e45cf-194">O Fedora 28 tem suporte apenas no PowerShell Core 6,1 e mais recente.</span><span class="sxs-lookup"><span data-stu-id="e45cf-194">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="e45cf-195">Instalação por meio do repositório de pacotes (preferencial)-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e45cf-195">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e45cf-196">O PowerShell Core para Linux é publicado em repositórios oficiais da Microsoft para facilitar a instalação e as atualizações.</span><span class="sxs-lookup"><span data-stu-id="e45cf-196">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="e45cf-197">Instalação por meio de download direto-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e45cf-197">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e45cf-198">Baixe o pacote `powershell-6.2.0-1.rhel.7.x86_64.rpm` rpm da página [versões][] no computador Fedora.</span><span class="sxs-lookup"><span data-stu-id="e45cf-198">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="e45cf-199">Em seguida, no terminal, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="e45cf-199">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e45cf-200">Você pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="e45cf-200">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="e45cf-201">Desinstalação-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e45cf-201">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="e45cf-202">Inglês de Arch</span><span class="sxs-lookup"><span data-stu-id="e45cf-202">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="e45cf-203">O suporte a Arch é experimental.</span><span class="sxs-lookup"><span data-stu-id="e45cf-203">Arch support is experimental.</span></span>

<span data-ttu-id="e45cf-204">O PowerShell está disponível no AUR (repositório do usuário do [Inglês de Arch][] ).</span><span class="sxs-lookup"><span data-stu-id="e45cf-204">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="e45cf-205">Ele pode ser compilado com a [versão marcada mais recente][arch-release]</span><span class="sxs-lookup"><span data-stu-id="e45cf-205">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="e45cf-206">Ele pode ser compilado da [última confirmação ao mestre][arch-git]</span><span class="sxs-lookup"><span data-stu-id="e45cf-206">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="e45cf-207">Ele pode ser instalado usando o [binário de versão mais recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="e45cf-207">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="e45cf-208">Os pacotes no AUR são mantidos pela Comunidade; Não há suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="e45cf-208">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="e45cf-209">Para obter mais informações sobre como instalar pacotes do AUR, consulte o [wiki do Linux em Arch](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou o [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile)da Comunidade.</span><span class="sxs-lookup"><span data-stu-id="e45cf-209">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Inglês de Arch]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="e45cf-211">Ajustar pacote</span><span class="sxs-lookup"><span data-stu-id="e45cf-211">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="e45cf-212">Sendo ajustado</span><span class="sxs-lookup"><span data-stu-id="e45cf-212">Getting snapd</span></span>

<span data-ttu-id="e45cf-213">`snapd`é necessário para executar Snaps.</span><span class="sxs-lookup"><span data-stu-id="e45cf-213">`snapd` is required to run snaps.</span></span> <span data-ttu-id="e45cf-214">Use [estas instruções](https://docs.snapcraft.io/core/install) para verificar se você `snapd` instalou o.</span><span class="sxs-lookup"><span data-stu-id="e45cf-214">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="e45cf-215">Instalação via snap</span><span class="sxs-lookup"><span data-stu-id="e45cf-215">Installation via Snap</span></span>

<span data-ttu-id="e45cf-216">O PowerShell Core para Linux é publicado no [repositório de snap](https://snapcraft.io/store) para facilitar a instalação e as atualizações.</span><span class="sxs-lookup"><span data-stu-id="e45cf-216">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="e45cf-217">O método preferencial é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e45cf-217">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="e45cf-218">Para instalar uma versão de visualização, use o seguinte método:</span><span class="sxs-lookup"><span data-stu-id="e45cf-218">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="e45cf-219">Após a instalação, o snap será atualizado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e45cf-219">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="e45cf-220">Você pode disparar uma atualização usando `sudo snap refresh powershell` o `sudo snap refresh powershell-preview`ou o.</span><span class="sxs-lookup"><span data-stu-id="e45cf-220">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="e45cf-221">Desinstalação</span><span class="sxs-lookup"><span data-stu-id="e45cf-221">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="e45cf-222">ou</span><span class="sxs-lookup"><span data-stu-id="e45cf-222">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="e45cf-223">Kali</span><span class="sxs-lookup"><span data-stu-id="e45cf-223">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="e45cf-224">Instalação-Kali</span><span class="sxs-lookup"><span data-stu-id="e45cf-224">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="e45cf-225">Desinstalação – Kali</span><span class="sxs-lookup"><span data-stu-id="e45cf-225">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="e45cf-226">Raspbian</span><span class="sxs-lookup"><span data-stu-id="e45cf-226">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="e45cf-227">O suporte a Raspbian é experimental.</span><span class="sxs-lookup"><span data-stu-id="e45cf-227">Raspbian support is experimental.</span></span>

<span data-ttu-id="e45cf-228">Atualmente, o PowerShell só tem suporte no Stretch Raspbian.</span><span class="sxs-lookup"><span data-stu-id="e45cf-228">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="e45cf-229">O CoreCLR e o PowerShell Core só funcionarão em dispositivos pi 2 e pi 3, já que outros dispositivos, como o [pi zero](https://github.com/dotnet/coreclr/issues/10605), têm um processador sem suporte.</span><span class="sxs-lookup"><span data-stu-id="e45cf-229">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="e45cf-230">Baixe o [Stretch Raspbian](https://www.raspberrypi.org/downloads/raspbian/) e siga as [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para obtê-lo no PI.</span><span class="sxs-lookup"><span data-stu-id="e45cf-230">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="e45cf-231">Instalação-Raspbian</span><span class="sxs-lookup"><span data-stu-id="e45cf-231">Installation - Raspbian</span></span>

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

<span data-ttu-id="e45cf-232">Opcionalmente, você pode criar um link simbólico para iniciar o PowerShell sem especificar o caminho para `pwsh` o binário.</span><span class="sxs-lookup"><span data-stu-id="e45cf-232">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="e45cf-233">Desinstalação – Raspbian</span><span class="sxs-lookup"><span data-stu-id="e45cf-233">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="e45cf-234">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="e45cf-234">Binary Archives</span></span>

<span data-ttu-id="e45cf-235">Os arquivos `tar.gz` binários do PowerShell são fornecidos para plataformas Linux para habilitar cenários de implantação avançada.</span><span class="sxs-lookup"><span data-stu-id="e45cf-235">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="e45cf-236">Depend</span><span class="sxs-lookup"><span data-stu-id="e45cf-236">Dependencies</span></span>

<span data-ttu-id="e45cf-237">O PowerShell cria binários portáteis para todas as distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="e45cf-237">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="e45cf-238">Mas, o tempo de execução do .NET Core requer diferentes dependências em diferentes distribuições, e o PowerShell também.</span><span class="sxs-lookup"><span data-stu-id="e45cf-238">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="e45cf-239">O gráfico a seguir mostra as dependências do .NET Core 2,0 que são oficialmente suportadas em diferentes distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="e45cf-239">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="e45cf-240">SO</span><span class="sxs-lookup"><span data-stu-id="e45cf-240">OS</span></span>                 | <span data-ttu-id="e45cf-241">Depend</span><span class="sxs-lookup"><span data-stu-id="e45cf-241">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="e45cf-242">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e45cf-242">Ubuntu 16.04</span></span>       | <span data-ttu-id="e45cf-243">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e45cf-243">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e45cf-244">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="e45cf-244">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="e45cf-245">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="e45cf-245">Ubuntu 17.10</span></span>       | <span data-ttu-id="e45cf-246">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e45cf-246">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e45cf-247">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="e45cf-247">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="e45cf-248">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e45cf-248">Ubuntu 18.04</span></span>       | <span data-ttu-id="e45cf-249">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e45cf-249">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e45cf-250">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="e45cf-250">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="e45cf-251">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="e45cf-251">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="e45cf-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e45cf-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e45cf-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e45cf-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e45cf-254">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="e45cf-254">Debian 9 (Stretch)</span></span> | <span data-ttu-id="e45cf-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e45cf-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e45cf-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="e45cf-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="e45cf-257">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e45cf-257">CentOS 7</span></span> <br> <span data-ttu-id="e45cf-258">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="e45cf-258">Oracle Linux 7</span></span> <br> <span data-ttu-id="e45cf-259">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="e45cf-259">RHEL 7</span></span> | <span data-ttu-id="e45cf-260">libunwind, libcurl, OpenSSL-bibliotecas, libicu</span><span class="sxs-lookup"><span data-stu-id="e45cf-260">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="e45cf-261">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="e45cf-261">openSUSE 42.3</span></span> | <span data-ttu-id="e45cf-262">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="e45cf-262">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="e45cf-263">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e45cf-263">openSUSE Leap 15</span></span> | <span data-ttu-id="e45cf-264">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="e45cf-264">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="e45cf-265">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="e45cf-265">Fedora 27</span></span> <br> <span data-ttu-id="e45cf-266">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e45cf-266">Fedora 28</span></span> | <span data-ttu-id="e45cf-267">libunwind, libcurl, OpenSSL-bibliotecas, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="e45cf-267">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="e45cf-268">Para implantar binários do PowerShell em distribuições Linux que não têm suporte oficial, você precisa instalar as dependências necessárias para o sistema operacional de destino em etapas separadas.</span><span class="sxs-lookup"><span data-stu-id="e45cf-268">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="e45cf-269">Por exemplo, nosso [Amazon Linux dockerfile][amazon-dockerfile] instala dependências primeiro e, em seguida, extrai `tar.gz` o arquivo do Linux.</span><span class="sxs-lookup"><span data-stu-id="e45cf-269">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="e45cf-270">Instalação-arquivos binários</span><span class="sxs-lookup"><span data-stu-id="e45cf-270">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="e45cf-271">Linux</span><span class="sxs-lookup"><span data-stu-id="e45cf-271">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="e45cf-272">Desinstalando arquivos binários</span><span class="sxs-lookup"><span data-stu-id="e45cf-272">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="e45cf-273">Caminhos</span><span class="sxs-lookup"><span data-stu-id="e45cf-273">Paths</span></span>

* <span data-ttu-id="e45cf-274">`$PSHOME`for`/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="e45cf-274">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="e45cf-275">Os perfis de usuário serão lidos de`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e45cf-275">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="e45cf-276">Os perfis padrão serão lidos de`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e45cf-276">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="e45cf-277">Os módulos de usuário serão lidos de`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e45cf-277">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e45cf-278">Os módulos compartilhados serão lidos de`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e45cf-278">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e45cf-279">Os módulos padrão serão lidos de`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="e45cf-279">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="e45cf-280">O histórico de PSReadline será gravado em`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="e45cf-280">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="e45cf-281">Os perfis respeitam a configuração por host do PowerShell, portanto, os perfis específicos do host padrão `Microsoft.PowerShell_profile.ps1` existem no mesmo local.</span><span class="sxs-lookup"><span data-stu-id="e45cf-281">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="e45cf-282">O PowerShell respeita a [especificação do diretório base xdg][xdg-bds] no Linux.</span><span class="sxs-lookup"><span data-stu-id="e45cf-282">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
