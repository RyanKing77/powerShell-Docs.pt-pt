---
title: Instalar o PowerShell Core no Linux
description: Informações sobre a instalação do PowerShell Core em várias distribuições do Linux
ms.date: 07/19/2019
ms.openlocfilehash: 929b153ef784f3203cd31a0e2fc52e744a07532f
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372191"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="d18b1-103">Instalar o PowerShell Core no Linux</span><span class="sxs-lookup"><span data-stu-id="d18b1-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="d18b1-104">Dá suporte ao [Ubuntu 16, 4][u16], [Ubuntu 18.04][u1804], [Ubuntu 18,10][u1810], [Debian 9][deb9],
 [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE Leap 15][opensuse] , [Fedora 27][fedora], [Fedora 28][Fedora]e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="d18b1-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9],
 [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="d18b1-105">Para distribuições Linux que não têm suporte oficial, você pode tentar instalar o PowerShell usando o [pacote de snap do PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="d18b1-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="d18b1-106">Você também pode tentar implantar binários do PowerShell diretamente usando o [ `tar.gz` arquivo][tar]do Linux, mas precisaria configurar as dependências necessárias com base no sistema operacional em etapas separadas.</span><span class="sxs-lookup"><span data-stu-id="d18b1-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="d18b1-107">Todos os pacotes estão disponíveis em nossa página de [versões][] do github.</span><span class="sxs-lookup"><span data-stu-id="d18b1-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="d18b1-108">Após a instalação do pacote, execute `pwsh` a partir de um terminal.</span><span class="sxs-lookup"><span data-stu-id="d18b1-108">After the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="installing-preview-releases"></a><span data-ttu-id="d18b1-109">Instalando versões de visualização</span><span class="sxs-lookup"><span data-stu-id="d18b1-109">Installing Preview Releases</span></span>

<span data-ttu-id="d18b1-110">Ao instalar uma versão de visualização do PowerShell Core para Linux por meio de um repositório de pacotes, `powershell` o `powershell-preview`nome do pacote é alterado de para.</span><span class="sxs-lookup"><span data-stu-id="d18b1-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="d18b1-111">A instalação por meio de download direto não é alterada, além do nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="d18b1-111">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="d18b1-112">A tabela a seguir contém os comandos para instalar os pacotes estáveis e de visualização usando os vários gerenciadores de pacotes:</span><span class="sxs-lookup"><span data-stu-id="d18b1-112">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="d18b1-113">Distribuição (ões)</span><span class="sxs-lookup"><span data-stu-id="d18b1-113">Distribution(s)</span></span>|<span data-ttu-id="d18b1-114">Comando estável</span><span class="sxs-lookup"><span data-stu-id="d18b1-114">Stable Command</span></span> | <span data-ttu-id="d18b1-115">Comando de visualização</span><span class="sxs-lookup"><span data-stu-id="d18b1-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="d18b1-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="d18b1-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="d18b1-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="d18b1-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="d18b1-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="d18b1-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="d18b1-119">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d18b1-119">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="d18b1-120">Instalação por meio do repositório de pacotes – Ubuntu 16, 4</span><span class="sxs-lookup"><span data-stu-id="d18b1-120">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="d18b1-121">O PowerShell Core para Linux é publicado em repositórios de pacotes para facilitar a instalação e as atualizações.</span><span class="sxs-lookup"><span data-stu-id="d18b1-121">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d18b1-122">O método preferencial é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d18b1-122">The preferred method is as follows:</span></span>

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

<span data-ttu-id="d18b1-123">Como superusuário, registre o repositório da Microsoft uma vez.</span><span class="sxs-lookup"><span data-stu-id="d18b1-123">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d18b1-124">Após o registro, você pode atualizar o `sudo apt-get upgrade powershell`PowerShell com o.</span><span class="sxs-lookup"><span data-stu-id="d18b1-124">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="d18b1-125">Instalação por meio de download direto – Ubuntu 16, 4</span><span class="sxs-lookup"><span data-stu-id="d18b1-125">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="d18b1-126">Baixe o pacote `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` Debian da página [versões][] no computador Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="d18b1-126">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="d18b1-127">Em seguida, no terminal, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="d18b1-127">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="d18b1-128">O `dpkg -i` comando falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="d18b1-128">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="d18b1-129">O comando `apt-get install -f` a seguir resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d18b1-129">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="d18b1-130">Desinstalação – Ubuntu 16, 4</span><span class="sxs-lookup"><span data-stu-id="d18b1-130">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="d18b1-131">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d18b1-131">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="d18b1-132">Instalação por meio do repositório de pacotes – Ubuntu 18, 4</span><span class="sxs-lookup"><span data-stu-id="d18b1-132">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="d18b1-133">O PowerShell Core para Linux é publicado em repositórios de pacotes para facilitar a instalação e as atualizações.</span><span class="sxs-lookup"><span data-stu-id="d18b1-133">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d18b1-134">O método preferencial é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d18b1-134">The preferred method is as follows:</span></span>

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

<span data-ttu-id="d18b1-135">Como superusuário, registre o repositório da Microsoft uma vez.</span><span class="sxs-lookup"><span data-stu-id="d18b1-135">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d18b1-136">Após o registro, você pode atualizar o `sudo apt-get upgrade powershell`PowerShell com o.</span><span class="sxs-lookup"><span data-stu-id="d18b1-136">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="d18b1-137">Instalação por meio de download direto – Ubuntu 18, 4</span><span class="sxs-lookup"><span data-stu-id="d18b1-137">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="d18b1-138">Baixe o pacote `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` Debian da página [versões][] no computador Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="d18b1-138">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="d18b1-139">Em seguida, no terminal, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="d18b1-139">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="d18b1-140">O `dpkg -i` comando falha com dependências não atendidas.</span><span class="sxs-lookup"><span data-stu-id="d18b1-140">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="d18b1-141">O comando `apt-get install -f` a seguir resolve esses problemas e, em seguida, conclui a configuração do pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d18b1-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="d18b1-142">Desinstalação – Ubuntu 18, 4</span><span class="sxs-lookup"><span data-stu-id="d18b1-142">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="d18b1-143">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="d18b1-143">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="d18b1-144">Como 18,10 é uma [versão provisória](https://www.ubuntu.com/about/release-cycle), só [há suporte para a Comunidade](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="d18b1-144">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="d18b1-145">Há suporte para a instalação do `snapd`em 18,10 via.</span><span class="sxs-lookup"><span data-stu-id="d18b1-145">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="d18b1-146">Consulte [snap Package][snap] para obter instruções completas;</span><span class="sxs-lookup"><span data-stu-id="d18b1-146">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="d18b1-147">Debian 8</span><span class="sxs-lookup"><span data-stu-id="d18b1-147">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="d18b1-148">Instalação por meio do repositório de pacotes – Debian 8</span><span class="sxs-lookup"><span data-stu-id="d18b1-148">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="d18b1-149">O PowerShell Core, para Linux, é publicado em repositórios de pacotes para facilitar a instalação e as atualizações.</span><span class="sxs-lookup"><span data-stu-id="d18b1-149">PowerShell Core, for Linux, is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d18b1-150">O método preferencial é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d18b1-150">The preferred method is as follows:</span></span>

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

<span data-ttu-id="d18b1-151">Como superusuário, registre o repositório da Microsoft uma vez.</span><span class="sxs-lookup"><span data-stu-id="d18b1-151">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d18b1-152">Após o registro, você pode atualizar o `sudo apt-get upgrade powershell`PowerShell com o.</span><span class="sxs-lookup"><span data-stu-id="d18b1-152">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="d18b1-153">Debian 9</span><span class="sxs-lookup"><span data-stu-id="d18b1-153">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="d18b1-154">Instalação por meio do repositório de pacotes – Debian 9</span><span class="sxs-lookup"><span data-stu-id="d18b1-154">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="d18b1-155">O PowerShell Core para Linux é publicado em repositórios de pacotes para facilitar a instalação e as atualizações.</span><span class="sxs-lookup"><span data-stu-id="d18b1-155">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="d18b1-156">O método preferencial é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d18b1-156">The preferred method is as follows:</span></span>

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

<span data-ttu-id="d18b1-157">Como superusuário, registre o repositório da Microsoft uma vez.</span><span class="sxs-lookup"><span data-stu-id="d18b1-157">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d18b1-158">Após o registro, você pode atualizar o `sudo apt-get upgrade powershell`PowerShell com o.</span><span class="sxs-lookup"><span data-stu-id="d18b1-158">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="d18b1-159">Instalação por meio de download direto – Debian 9</span><span class="sxs-lookup"><span data-stu-id="d18b1-159">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="d18b1-160">Baixe o pacote `powershell_6.2.0-1.debian.9_amd64.deb` Debian da página [versões][] no computador Debian.</span><span class="sxs-lookup"><span data-stu-id="d18b1-160">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="d18b1-161">Em seguida, no terminal, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="d18b1-161">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="d18b1-162">Desinstalação – Debian 9</span><span class="sxs-lookup"><span data-stu-id="d18b1-162">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="d18b1-163">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d18b1-163">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="d18b1-164">Este pacote funciona no Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="d18b1-164">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="d18b1-165">Instalação por meio do repositório de pacotes (preferencial) – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d18b1-165">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="d18b1-166">O PowerShell Core para Linux é publicado em repositórios oficiais da Microsoft para facilitar a instalação e as atualizações.</span><span class="sxs-lookup"><span data-stu-id="d18b1-166">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="d18b1-167">Como superusuário, registre o repositório da Microsoft uma vez.</span><span class="sxs-lookup"><span data-stu-id="d18b1-167">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d18b1-168">Após o registro, você pode atualizar o `sudo yum update powershell`PowerShell com o.</span><span class="sxs-lookup"><span data-stu-id="d18b1-168">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="d18b1-169">Instalação por meio do download direto – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d18b1-169">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="d18b1-170">Usando o [CentOS 7][], baixe o pacote `powershell-6.2.0-1.rhel.7.x86_64.rpm` rpm da página [versões][] no computador CentOS.</span><span class="sxs-lookup"><span data-stu-id="d18b1-170">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="d18b1-171">Em seguida, no terminal, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="d18b1-171">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="d18b1-172">Você pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="d18b1-172">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="d18b1-173">Desinstalação – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d18b1-173">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d18b1-175">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="d18b1-175">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d18b1-176">Instalação por meio do repositório de pacotes (preferencial)-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="d18b1-176">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="d18b1-177">O PowerShell Core para Linux é publicado em repositórios oficiais da Microsoft para facilitar a instalação e as atualizações.</span><span class="sxs-lookup"><span data-stu-id="d18b1-177">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="d18b1-178">Como superusuário, registre o repositório da Microsoft uma vez.</span><span class="sxs-lookup"><span data-stu-id="d18b1-178">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="d18b1-179">Após o registro, você pode atualizar o `sudo yum update powershell`PowerShell com o.</span><span class="sxs-lookup"><span data-stu-id="d18b1-179">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d18b1-180">Instalação por meio de download direto – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="d18b1-180">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="d18b1-181">Baixe o pacote `powershell-6.2.0-1.rhel.7.x86_64.rpm` rpm da página [versões][] no computador Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="d18b1-181">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="d18b1-182">Em seguida, no terminal, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="d18b1-182">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="d18b1-183">Você pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="d18b1-183">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="d18b1-184">Desinstalação-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="d18b1-184">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="d18b1-185">openSUSE</span><span class="sxs-lookup"><span data-stu-id="d18b1-185">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="d18b1-186">Instalação-openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="d18b1-186">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="d18b1-187">Instalação-openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="d18b1-187">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="d18b1-188">Desinstalação-openSUSE 42,3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="d18b1-188">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="d18b1-189">Fedora</span><span class="sxs-lookup"><span data-stu-id="d18b1-189">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="d18b1-190">O Fedora 28 tem suporte apenas no PowerShell Core 6,1 e mais recente.</span><span class="sxs-lookup"><span data-stu-id="d18b1-190">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="d18b1-191">Instalação por meio do repositório de pacotes (preferencial)-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="d18b1-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="d18b1-192">O PowerShell Core para Linux é publicado em repositórios oficiais da Microsoft para facilitar a instalação e as atualizações.</span><span class="sxs-lookup"><span data-stu-id="d18b1-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="d18b1-193">Instalação por meio de download direto-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="d18b1-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="d18b1-194">Baixe o pacote `powershell-6.2.0-1.rhel.7.x86_64.rpm` rpm da página [versões][] no computador Fedora.</span><span class="sxs-lookup"><span data-stu-id="d18b1-194">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="d18b1-195">Em seguida, no terminal, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="d18b1-195">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="d18b1-196">Você pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="d18b1-196">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="d18b1-197">Desinstalação-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="d18b1-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="d18b1-198">Inglês de Arch</span><span class="sxs-lookup"><span data-stu-id="d18b1-198">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="d18b1-199">O suporte a Arch é experimental.</span><span class="sxs-lookup"><span data-stu-id="d18b1-199">Arch support is experimental.</span></span>

<span data-ttu-id="d18b1-200">O PowerShell está disponível no AUR (repositório do usuário do [Inglês de Arch][] ).</span><span class="sxs-lookup"><span data-stu-id="d18b1-200">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="d18b1-201">Ele pode ser compilado com a [versão marcada mais recente][arch-release]</span><span class="sxs-lookup"><span data-stu-id="d18b1-201">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="d18b1-202">Ele pode ser compilado da [última confirmação ao mestre][arch-git]</span><span class="sxs-lookup"><span data-stu-id="d18b1-202">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="d18b1-203">Ele pode ser instalado usando o [binário de versão mais recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="d18b1-203">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="d18b1-204">Os pacotes no AUR são mantidos pela Comunidade; Não há suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="d18b1-204">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="d18b1-205">Para obter mais informações sobre como instalar pacotes do AUR, consulte o [wiki do Linux em Arch](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou o [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile)da Comunidade.</span><span class="sxs-lookup"><span data-stu-id="d18b1-205">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Inglês de Arch]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="d18b1-207">Ajustar pacote</span><span class="sxs-lookup"><span data-stu-id="d18b1-207">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="d18b1-208">Sendo ajustado</span><span class="sxs-lookup"><span data-stu-id="d18b1-208">Getting snapd</span></span>

<span data-ttu-id="d18b1-209">`snapd`é necessário para executar Snaps.</span><span class="sxs-lookup"><span data-stu-id="d18b1-209">`snapd` is required to run snaps.</span></span> <span data-ttu-id="d18b1-210">Use [estas instruções](https://docs.snapcraft.io/core/install) para verificar se você `snapd` instalou o.</span><span class="sxs-lookup"><span data-stu-id="d18b1-210">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="d18b1-211">Instalação via snap</span><span class="sxs-lookup"><span data-stu-id="d18b1-211">Installation via Snap</span></span>

<span data-ttu-id="d18b1-212">O PowerShell Core para Linux é publicado no [repositório de snap](https://snapcraft.io/store) para facilitar a instalação e as atualizações.</span><span class="sxs-lookup"><span data-stu-id="d18b1-212">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="d18b1-213">O método preferencial é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d18b1-213">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="d18b1-214">Para instalar uma versão de visualização, use o seguinte método:</span><span class="sxs-lookup"><span data-stu-id="d18b1-214">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="d18b1-215">Após a instalação, o snap será atualizado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d18b1-215">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="d18b1-216">Você pode disparar uma atualização usando `sudo snap refresh powershell` o `sudo snap refresh powershell-preview`ou o.</span><span class="sxs-lookup"><span data-stu-id="d18b1-216">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="d18b1-217">Desinstalação</span><span class="sxs-lookup"><span data-stu-id="d18b1-217">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="d18b1-218">ou</span><span class="sxs-lookup"><span data-stu-id="d18b1-218">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="d18b1-219">Kali</span><span class="sxs-lookup"><span data-stu-id="d18b1-219">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="d18b1-220">Instalação-Kali</span><span class="sxs-lookup"><span data-stu-id="d18b1-220">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="d18b1-221">Desinstalação – Kali</span><span class="sxs-lookup"><span data-stu-id="d18b1-221">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="d18b1-222">Raspbian</span><span class="sxs-lookup"><span data-stu-id="d18b1-222">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="d18b1-223">O suporte a Raspbian é experimental.</span><span class="sxs-lookup"><span data-stu-id="d18b1-223">Raspbian support is experimental.</span></span>

<span data-ttu-id="d18b1-224">Atualmente, o PowerShell só tem suporte no Stretch Raspbian.</span><span class="sxs-lookup"><span data-stu-id="d18b1-224">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="d18b1-225">O CoreCLR e o PowerShell Core só funcionarão em dispositivos pi 2 e pi 3, já que outros dispositivos, como o [pi zero](https://github.com/dotnet/coreclr/issues/10605), têm um processador sem suporte.</span><span class="sxs-lookup"><span data-stu-id="d18b1-225">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="d18b1-226">Baixe o [Stretch Raspbian](https://www.raspberrypi.org/downloads/raspbian/) e siga as [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para obtê-lo no PI.</span><span class="sxs-lookup"><span data-stu-id="d18b1-226">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="d18b1-227">Instalação-Raspbian</span><span class="sxs-lookup"><span data-stu-id="d18b1-227">Installation - Raspbian</span></span>

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

<span data-ttu-id="d18b1-228">Opcionalmente, você pode criar um link simbólico para iniciar o PowerShell sem especificar o caminho para `pwsh` o binário.</span><span class="sxs-lookup"><span data-stu-id="d18b1-228">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="d18b1-229">Desinstalação – Raspbian</span><span class="sxs-lookup"><span data-stu-id="d18b1-229">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="d18b1-230">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="d18b1-230">Binary Archives</span></span>

<span data-ttu-id="d18b1-231">Os arquivos `tar.gz` binários do PowerShell são fornecidos para plataformas Linux para habilitar cenários de implantação avançada.</span><span class="sxs-lookup"><span data-stu-id="d18b1-231">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="d18b1-232">Depend</span><span class="sxs-lookup"><span data-stu-id="d18b1-232">Dependencies</span></span>

<span data-ttu-id="d18b1-233">O PowerShell cria binários portáteis para todas as distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="d18b1-233">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="d18b1-234">Mas, o tempo de execução do .NET Core requer diferentes dependências em diferentes distribuições, e o PowerShell também.</span><span class="sxs-lookup"><span data-stu-id="d18b1-234">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="d18b1-235">O gráfico a seguir mostra as dependências do .NET Core 2,0 que são oficialmente suportadas em diferentes distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="d18b1-235">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="d18b1-236">SO</span><span class="sxs-lookup"><span data-stu-id="d18b1-236">OS</span></span>                 | <span data-ttu-id="d18b1-237">Depend</span><span class="sxs-lookup"><span data-stu-id="d18b1-237">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="d18b1-238">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="d18b1-238">Ubuntu 16.04</span></span>       | <span data-ttu-id="d18b1-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="d18b1-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d18b1-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="d18b1-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="d18b1-241">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="d18b1-241">Ubuntu 17.10</span></span>       | <span data-ttu-id="d18b1-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="d18b1-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d18b1-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="d18b1-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="d18b1-244">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="d18b1-244">Ubuntu 18.04</span></span>       | <span data-ttu-id="d18b1-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="d18b1-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d18b1-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="d18b1-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="d18b1-247">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="d18b1-247">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="d18b1-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="d18b1-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d18b1-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="d18b1-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="d18b1-250">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="d18b1-250">Debian 9 (Stretch)</span></span> | <span data-ttu-id="d18b1-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="d18b1-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="d18b1-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="d18b1-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="d18b1-253">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d18b1-253">CentOS 7</span></span> <br> <span data-ttu-id="d18b1-254">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="d18b1-254">Oracle Linux 7</span></span> <br> <span data-ttu-id="d18b1-255">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="d18b1-255">RHEL 7</span></span> | <span data-ttu-id="d18b1-256">libunwind, libcurl, OpenSSL-bibliotecas, libicu</span><span class="sxs-lookup"><span data-stu-id="d18b1-256">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="d18b1-257">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="d18b1-257">openSUSE 42.3</span></span> | <span data-ttu-id="d18b1-258">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="d18b1-258">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="d18b1-259">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="d18b1-259">openSUSE Leap 15</span></span> | <span data-ttu-id="d18b1-260">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="d18b1-260">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="d18b1-261">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="d18b1-261">Fedora 27</span></span> <br> <span data-ttu-id="d18b1-262">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="d18b1-262">Fedora 28</span></span> | <span data-ttu-id="d18b1-263">libunwind, libcurl, OpenSSL-bibliotecas, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="d18b1-263">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="d18b1-264">Para implantar binários do PowerShell em distribuições Linux que não têm suporte oficial, você precisa instalar as dependências necessárias para o sistema operacional de destino em etapas separadas.</span><span class="sxs-lookup"><span data-stu-id="d18b1-264">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="d18b1-265">Por exemplo, nosso [Amazon Linux dockerfile][amazon-dockerfile] instala dependências primeiro e, em seguida, extrai `tar.gz` o arquivo do Linux.</span><span class="sxs-lookup"><span data-stu-id="d18b1-265">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="d18b1-266">Instalação-arquivos binários</span><span class="sxs-lookup"><span data-stu-id="d18b1-266">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="d18b1-267">Linux</span><span class="sxs-lookup"><span data-stu-id="d18b1-267">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="d18b1-268">Desinstalando arquivos binários</span><span class="sxs-lookup"><span data-stu-id="d18b1-268">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="d18b1-269">Caminhos</span><span class="sxs-lookup"><span data-stu-id="d18b1-269">Paths</span></span>

* <span data-ttu-id="d18b1-270">`$PSHOME`for`/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="d18b1-270">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="d18b1-271">Os perfis de usuário serão lidos de`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="d18b1-271">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="d18b1-272">Os perfis padrão serão lidos de`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="d18b1-272">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="d18b1-273">Os módulos de usuário serão lidos de`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="d18b1-273">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="d18b1-274">Os módulos compartilhados serão lidos de`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="d18b1-274">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="d18b1-275">Os módulos padrão serão lidos de`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="d18b1-275">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="d18b1-276">O histórico de PSReadline será gravado em`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="d18b1-276">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="d18b1-277">Os perfis respeitam a configuração por host do PowerShell, portanto, os perfis específicos do host padrão `Microsoft.PowerShell_profile.ps1` existem no mesmo local.</span><span class="sxs-lookup"><span data-stu-id="d18b1-277">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="d18b1-278">O PowerShell respeita a [especificação do diretório base xdg][xdg-bds] no Linux.</span><span class="sxs-lookup"><span data-stu-id="d18b1-278">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
