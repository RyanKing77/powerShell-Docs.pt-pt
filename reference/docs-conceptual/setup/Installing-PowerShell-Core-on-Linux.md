# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="5cea2-101">Instalar o PowerShell Core no Linux</span><span class="sxs-lookup"><span data-stu-id="5cea2-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="5cea2-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="5cea2-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="5cea2-103">Para as distribuições do Linux que não são suportadas oficialmente, pode tentar utilizar o [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="5cea2-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="5cea2-104">Também pode tentar implementar os binários de PowerShell diretamente com o Linux [ `tar.gz` arquivo][tar], mas terá de configurar as dependências necessárias com base no SO em passos separados.</span><span class="sxs-lookup"><span data-stu-id="5cea2-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="5cea2-105">Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.</span><span class="sxs-lookup"><span data-stu-id="5cea2-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="5cea2-106">Depois do pacote está instalado, executar `pwsh` de um terminal.</span><span class="sxs-lookup"><span data-stu-id="5cea2-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="5cea2-107">Instalar versões Preview</span><span class="sxs-lookup"><span data-stu-id="5cea2-107">Installing Preview Releases</span></span>

<span data-ttu-id="5cea2-108">Ao instalar uma versão de pré-visualização de núcleo do PowerShell para o Linux através de um repositório de pacote, o nome do pacote é alterado de `powershell` para `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="5cea2-108">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="5cea2-109">A instalar através de transferência direta não se altera, diferente do nome de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="5cea2-109">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="5cea2-110">Eis uma tabela dos comandos para instalar os pacotes de estável e de pré-visualização com os vários gestores de pacote:</span><span class="sxs-lookup"><span data-stu-id="5cea2-110">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="5cea2-111">Distrobution(s)</span><span class="sxs-lookup"><span data-stu-id="5cea2-111">Distrobution(s)</span></span>|<span data-ttu-id="5cea2-112">Comando estável</span><span class="sxs-lookup"><span data-stu-id="5cea2-112">Stable Command</span></span> | <span data-ttu-id="5cea2-113">Comando de pré-visualização</span><span class="sxs-lookup"><span data-stu-id="5cea2-113">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="5cea2-114">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="5cea2-114">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="5cea2-115">CentOS, VM de RedHat</span><span class="sxs-lookup"><span data-stu-id="5cea2-115">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="5cea2-116">openSUSE</span><span class="sxs-lookup"><span data-stu-id="5cea2-116">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="5cea2-117">Fedora</span><span class="sxs-lookup"><span data-stu-id="5cea2-117">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="5cea2-118">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="5cea2-118">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="5cea2-119">Instalação através do repositório de pacote - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="5cea2-119">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="5cea2-120">PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="5cea2-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="5cea2-121">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="5cea2-121">This is the preferred method.</span></span>

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

<span data-ttu-id="5cea2-122">Como Superutilizador, registe o repositório de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5cea2-122">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="5cea2-123">De ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` para atualizar a instalação.</span><span class="sxs-lookup"><span data-stu-id="5cea2-123">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="5cea2-124">Instalação através de transferência direta - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="5cea2-124">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="5cea2-125">Transferir o pacote Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` do [versões][] página para a máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="5cea2-125">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="5cea2-126">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="5cea2-126">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="5cea2-127">O `dpkg -i` comando falha com dependências unmet.</span><span class="sxs-lookup"><span data-stu-id="5cea2-127">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="5cea2-128">O comando seguinte, `apt-get install -f` resolve estes problemas, em seguida, termina a configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5cea2-128">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="5cea2-129">Desinstalação - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="5cea2-129">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="5cea2-130">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="5cea2-130">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="5cea2-131">Instalação através do repositório de pacote - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="5cea2-131">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="5cea2-132">PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="5cea2-132">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="5cea2-133">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="5cea2-133">This is the preferred method.</span></span>

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

<span data-ttu-id="5cea2-134">Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="5cea2-134">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="5cea2-135">Instalação através de transferência direta - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="5cea2-135">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="5cea2-136">Transferir o pacote Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` do [versões][] página para a máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="5cea2-136">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="5cea2-137">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="5cea2-137">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="5cea2-138">O `dpkg -i` comando falha com dependências unmet.</span><span class="sxs-lookup"><span data-stu-id="5cea2-138">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="5cea2-139">O comando seguinte, `apt-get install -f` resolve estes problemas, em seguida, termina a configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5cea2-139">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="5cea2-140">Desinstalação - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="5cea2-140">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a><span data-ttu-id="5cea2-141">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="5cea2-141">Ubuntu 17.10</span></span>

> [!NOTE]
> <span data-ttu-id="5cea2-142">Foi adicionado suporte para Ubuntu 17.04 após `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="5cea2-142">Support for Ubuntu 17.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1710"></a><span data-ttu-id="5cea2-143">Instalação através do repositório de pacote - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="5cea2-143">Installation via Package Repository - Ubuntu 17.10</span></span>

<span data-ttu-id="5cea2-144">PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="5cea2-144">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="5cea2-145">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="5cea2-145">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.10/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="5cea2-146">Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="5cea2-146">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1710"></a><span data-ttu-id="5cea2-147">Instalação através de transferência direta - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="5cea2-147">Installation via Direct Download - Ubuntu 17.10</span></span>

<span data-ttu-id="5cea2-148">Transferir o pacote Debian `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` do [versões][] página para a máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="5cea2-148">Download the Debian package `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="5cea2-149">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="5cea2-149">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="5cea2-150">O `dpkg -i` comando falha com dependências unmet.</span><span class="sxs-lookup"><span data-stu-id="5cea2-150">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="5cea2-151">O comando seguinte, `apt-get install -f` resolve estes problemas, em seguida, termina a configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5cea2-151">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="5cea2-152">Desinstalação - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="5cea2-152">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="5cea2-153">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="5cea2-153">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="5cea2-154">Foi adicionado suporte para Ubuntu 18.04 após `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="5cea2-154">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="5cea2-155">Instalação através do repositório de pacote - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="5cea2-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="5cea2-156">PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="5cea2-156">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="5cea2-157">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="5cea2-157">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="5cea2-158">Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="5cea2-158">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="5cea2-159">Instalação através de transferência direta - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="5cea2-159">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="5cea2-160">Transferir o pacote Debian `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` do [versões][] página para a máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="5cea2-160">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="5cea2-161">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="5cea2-161">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="5cea2-162">O `dpkg -i` comando falha com dependências unmet.</span><span class="sxs-lookup"><span data-stu-id="5cea2-162">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="5cea2-163">O comando seguinte, `apt-get install -f` resolve estes problemas, em seguida, termina a configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5cea2-163">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="5cea2-164">Desinstalação - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="5cea2-164">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="5cea2-165">Debian 8</span><span class="sxs-lookup"><span data-stu-id="5cea2-165">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="5cea2-166">Instalação através do repositório de pacote - Debian 8</span><span class="sxs-lookup"><span data-stu-id="5cea2-166">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="5cea2-167">PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="5cea2-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="5cea2-168">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="5cea2-168">This is the preferred method.</span></span>

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

<span data-ttu-id="5cea2-169">Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="5cea2-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="5cea2-170">Instalação através de transferência direta - Debian 8</span><span class="sxs-lookup"><span data-stu-id="5cea2-170">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="5cea2-171">Transferir o pacote Debian `powershell_6.0.2-1.debian.8_amd64.deb` do [versões][] página para a máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="5cea2-171">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="5cea2-172">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="5cea2-172">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="5cea2-173">O `dpkg -i` comando falha com dependências unmet.</span><span class="sxs-lookup"><span data-stu-id="5cea2-173">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="5cea2-174">O comando seguinte, `apt-get install -f` resolve estes problemas, em seguida, termina a configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5cea2-174">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="5cea2-175">Desinstalação - Debian 8</span><span class="sxs-lookup"><span data-stu-id="5cea2-175">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="5cea2-176">Debian 9</span><span class="sxs-lookup"><span data-stu-id="5cea2-176">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="5cea2-177">Instalação através do repositório de pacote - Debian 9</span><span class="sxs-lookup"><span data-stu-id="5cea2-177">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="5cea2-178">PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="5cea2-178">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="5cea2-179">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="5cea2-179">This is the preferred method.</span></span>

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

<span data-ttu-id="5cea2-180">Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="5cea2-180">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="5cea2-181">Instalação através de transferência direta - Debian 9</span><span class="sxs-lookup"><span data-stu-id="5cea2-181">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="5cea2-182">Transferir o pacote Debian `powershell_6.0.2-1.debian.9_amd64.deb` do [versões][] página para a máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="5cea2-182">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="5cea2-183">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="5cea2-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="5cea2-184">Desinstalação - Debian 9</span><span class="sxs-lookup"><span data-stu-id="5cea2-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="5cea2-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="5cea2-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="5cea2-186">Este pacote também funciona no Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="5cea2-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="5cea2-187">Instalação através do repositório de pacote (preferencial) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="5cea2-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="5cea2-188">Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="5cea2-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="5cea2-189">Depois de registar o repositório de Microsoft uma vez como Superutilizador, basta utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5cea2-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="5cea2-190">Instalação através de transferência direta - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="5cea2-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="5cea2-191">Utilizar [CentOS 7][], transfira o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina do CentOS.</span><span class="sxs-lookup"><span data-stu-id="5cea2-191">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="5cea2-192">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="5cea2-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="5cea2-193">Também pode instalar o RPM sem o passo intermédio de transferindo-a:</span><span class="sxs-lookup"><span data-stu-id="5cea2-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="5cea2-194">Desinstalação - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="5cea2-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="5cea2-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="5cea2-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="5cea2-197">Instalação através do repositório de pacote (preferencial) - 7 do Red Hat Enterprise Linux (RHEL)</span><span class="sxs-lookup"><span data-stu-id="5cea2-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="5cea2-198">Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="5cea2-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="5cea2-199">Depois de registar o repositório de Microsoft uma vez como Superutilizador, basta utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5cea2-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="5cea2-200">Instalação através de transferência direta - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="5cea2-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="5cea2-201">Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina do Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="5cea2-201">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="5cea2-202">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="5cea2-202">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="5cea2-203">Também pode instalar o RPM sem o passo intermédio de transferindo-a:</span><span class="sxs-lookup"><span data-stu-id="5cea2-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="5cea2-204">Desinstalação - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="5cea2-204">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="5cea2-205">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="5cea2-205">OpenSUSE 42.2</span></span>

<span data-ttu-id="5cea2-206">Ao instalar o PowerShell Core, `zypper` pode comunicar o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="5cea2-206">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="5cea2-207">Neste caso, certifique-se de que um ecrã compatível com `libcurl` biblioteca encontra-se ao verificar que o seguinte comando mostra o `libcurl4` pacote como instalado:</span><span class="sxs-lookup"><span data-stu-id="5cea2-207">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="5cea2-208">Em seguida, escolha o `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solução quando instalar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5cea2-208">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="5cea2-209">Instalação através do repositório de pacote (preferencial) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="5cea2-209">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="5cea2-210">Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="5cea2-210">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="5cea2-211">Instalação através de transferência direta - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="5cea2-211">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="5cea2-212">Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="5cea2-212">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="5cea2-213">Também pode instalar o RPM sem o passo intermédio de transferindo-a:</span><span class="sxs-lookup"><span data-stu-id="5cea2-213">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="5cea2-214">Desinstalação - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="5cea2-214">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="5cea2-215">Fedora</span><span class="sxs-lookup"><span data-stu-id="5cea2-215">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="5cea2-216">Fedora 28 só é suportada no PowerShell Core 6.1 e mais recentes.</span><span class="sxs-lookup"><span data-stu-id="5cea2-216">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="5cea2-217">Instalação através do pacote repositório (preferencial) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="5cea2-217">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="5cea2-218">Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="5cea2-218">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="5cea2-219">Instalação através de transferência direta - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="5cea2-219">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="5cea2-220">Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina Fedora.</span><span class="sxs-lookup"><span data-stu-id="5cea2-220">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="5cea2-221">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="5cea2-221">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="5cea2-222">Também pode instalar o RPM sem o passo intermédio de transferindo-a:</span><span class="sxs-lookup"><span data-stu-id="5cea2-222">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="5cea2-223">Desinstalação - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="5cea2-223">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="5cea2-224">Arquitetura de Linux</span><span class="sxs-lookup"><span data-stu-id="5cea2-224">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="5cea2-225">Suporte de arquitetura é experimental.</span><span class="sxs-lookup"><span data-stu-id="5cea2-225">Arch support is experimental.</span></span>

<span data-ttu-id="5cea2-226">PowerShell está disponível a partir de [arquitetura Linux][] utilizador repositório (AUR).</span><span class="sxs-lookup"><span data-stu-id="5cea2-226">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="5cea2-227">Pode ser compilada com a [mais recente etiquetados versão][arch-release]</span><span class="sxs-lookup"><span data-stu-id="5cea2-227">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="5cea2-228">Pode ser compilado do [consolidação mais recente mestre][arch-git]</span><span class="sxs-lookup"><span data-stu-id="5cea2-228">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="5cea2-229">Pode ser instalado utilizando o [binário da versão mais recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="5cea2-229">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="5cea2-230">Pacotes no AUR Comunidade mantida - não são suportadas oficial.</span><span class="sxs-lookup"><span data-stu-id="5cea2-230">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="5cea2-231">Para obter mais informações sobre como instalar pacotes do AUR, consulte o [arquitetura Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou Comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="5cea2-231">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[arquitetura Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="5cea2-233">AppImage do Linux</span><span class="sxs-lookup"><span data-stu-id="5cea2-233">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="5cea2-234">Suporte de AppImage é experimental</span><span class="sxs-lookup"><span data-stu-id="5cea2-234">AppImage support is experimental</span></span>

<span data-ttu-id="5cea2-235">Com uma distribuição Linux recente, transfira o AppImage `powershell-6.0.1-x86_64.AppImage` do [versões][] página para a máquina do Linux.</span><span class="sxs-lookup"><span data-stu-id="5cea2-235">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="5cea2-236">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="5cea2-236">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="5cea2-237">O [AppImage][] permite-lhe executar o PowerShell sem instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="5cea2-237">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="5cea2-238">É uma aplicação portátil que bundles PowerShell e as respetivas dependências (incluindo as dependências do .NET Core system) para um pacote coesa.</span><span class="sxs-lookup"><span data-stu-id="5cea2-238">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="5cea2-239">Este pacote é um binário único que funciona independentemente da distribuição de Linux do utilizador.</span><span class="sxs-lookup"><span data-stu-id="5cea2-239">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="5cea2-241">Kali</span><span class="sxs-lookup"><span data-stu-id="5cea2-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="5cea2-242">O suporte de Kali está experimental.</span><span class="sxs-lookup"><span data-stu-id="5cea2-242">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="5cea2-243">Instalação</span><span class="sxs-lookup"><span data-stu-id="5cea2-243">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="5cea2-244">Executar o PowerShell no Kali mais recente (Kali GNU/Linux sucessiva) sem instalar</span><span class="sxs-lookup"><span data-stu-id="5cea2-244">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="5cea2-245">Desinstalação - Kali</span><span class="sxs-lookup"><span data-stu-id="5cea2-245">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="5cea2-246">Raspbian</span><span class="sxs-lookup"><span data-stu-id="5cea2-246">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="5cea2-247">O suporte de Raspbian está experimental.</span><span class="sxs-lookup"><span data-stu-id="5cea2-247">Raspbian support is experimental.</span></span>

<span data-ttu-id="5cea2-248">Atualmente, o PowerShell só é suportado em Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="5cea2-248">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="5cea2-249">Também CoreCLR (e, consequentemente, PowerShell Core) funcionará apenas em dispositivos Pi 2 e Pi 3 como outros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), tem um processador não suportado.</span><span class="sxs-lookup"><span data-stu-id="5cea2-249">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="5cea2-250">Transferir [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e siga o [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) obtê-lo no seu Pi.</span><span class="sxs-lookup"><span data-stu-id="5cea2-250">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="5cea2-251">Instalação</span><span class="sxs-lookup"><span data-stu-id="5cea2-251">Installation</span></span>

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

<span data-ttu-id="5cea2-252">Opcionalmente, pode criar uma ligação simbólica para conseguir iniciar PowerShell sem especificar o caminho para o "pwsh" binário</span><span class="sxs-lookup"><span data-stu-id="5cea2-252">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="5cea2-253">Desinstalação - Raspbian</span><span class="sxs-lookup"><span data-stu-id="5cea2-253">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="5cea2-254">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="5cea2-254">Binary Archives</span></span>

<span data-ttu-id="5cea2-255">PowerShell binário `tar.gz` arquivos são fornecidos para plataformas Linux ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="5cea2-255">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="5cea2-256">Dependências</span><span class="sxs-lookup"><span data-stu-id="5cea2-256">Dependencies</span></span>

<span data-ttu-id="5cea2-257">PowerShell compila binários portátil para todas as distribuições de Linux.</span><span class="sxs-lookup"><span data-stu-id="5cea2-257">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="5cea2-258">Mas o tempo de execução de .NET Core requer diferentes dependências em diversas distribuições e, por conseguinte, o PowerShell tem a mesma.</span><span class="sxs-lookup"><span data-stu-id="5cea2-258">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="5cea2-259">O gráfico seguinte mostra as dependências de .NET Core 2.0 oficialmente são suportadas em diversas distribuições de Linux.</span><span class="sxs-lookup"><span data-stu-id="5cea2-259">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="5cea2-260">SO</span><span class="sxs-lookup"><span data-stu-id="5cea2-260">OS</span></span>                 | <span data-ttu-id="5cea2-261">Dependências</span><span class="sxs-lookup"><span data-stu-id="5cea2-261">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="5cea2-262">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="5cea2-262">Ubuntu 14.04</span></span>       | <span data-ttu-id="5cea2-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="5cea2-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="5cea2-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="5cea2-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="5cea2-265">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="5cea2-265">Ubuntu 16.04</span></span>       | <span data-ttu-id="5cea2-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="5cea2-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="5cea2-267">libcurl3 libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="5cea2-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="5cea2-268">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="5cea2-268">Ubuntu 17.10</span></span>       | <span data-ttu-id="5cea2-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="5cea2-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="5cea2-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="5cea2-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="5cea2-271">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="5cea2-271">Ubuntu 18.04</span></span>       | <span data-ttu-id="5cea2-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="5cea2-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="5cea2-273">libcurl3 libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="5cea2-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="5cea2-274">8 debian (Jessie)</span><span class="sxs-lookup"><span data-stu-id="5cea2-274">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="5cea2-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="5cea2-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="5cea2-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="5cea2-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="5cea2-277">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="5cea2-277">Debian 9 (Stretch)</span></span> | <span data-ttu-id="5cea2-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="5cea2-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="5cea2-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="5cea2-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="5cea2-280">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="5cea2-280">CentOS 7</span></span> <br> <span data-ttu-id="5cea2-281">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="5cea2-281">Oracle Linux 7</span></span> <br> <span data-ttu-id="5cea2-282">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="5cea2-282">RHEL 7</span></span> <br> <span data-ttu-id="5cea2-283">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="5cea2-283">OpenSUSE 42.2</span></span> | <span data-ttu-id="5cea2-284">libunwind, libcurl, bibliotecas de openssl, libicu</span><span class="sxs-lookup"><span data-stu-id="5cea2-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="5cea2-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="5cea2-285">Fedora 27</span></span> <br> <span data-ttu-id="5cea2-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="5cea2-286">Fedora 28</span></span> | <span data-ttu-id="5cea2-287">libunwind libcurl, bibliotecas de openssl, libicu, openssl10 de compatibilidade</span><span class="sxs-lookup"><span data-stu-id="5cea2-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="5cea2-288">Para implementar os binários do PowerShell nas distribuições de Linux que não são suportados oficialmente, terá de instalar as dependências necessárias para o SO de destino nos passos separados.</span><span class="sxs-lookup"><span data-stu-id="5cea2-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="5cea2-289">Por exemplo, a nossa [Amazon Linux dockerfile] [ amazon-dockerfile] instala dependências primeiro e, em seguida, extrai o Linux `tar.gz` arquivo.</span><span class="sxs-lookup"><span data-stu-id="5cea2-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="5cea2-290">Instalação - arquivos binários</span><span class="sxs-lookup"><span data-stu-id="5cea2-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="5cea2-291">Linux</span><span class="sxs-lookup"><span data-stu-id="5cea2-291">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="5cea2-292">Desinstalação arquivos binários</span><span class="sxs-lookup"><span data-stu-id="5cea2-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="5cea2-293">Caminhos</span><span class="sxs-lookup"><span data-stu-id="5cea2-293">Paths</span></span>

* <span data-ttu-id="5cea2-294">`$PSHOME` é `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="5cea2-294">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="5cea2-295">Perfis de utilizador serão lida a partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="5cea2-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="5cea2-296">Serão possível ler perfis predefinidos `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="5cea2-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="5cea2-297">Módulos de utilizador serão lida a partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="5cea2-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="5cea2-298">Módulos partilhados irão ler a partir do `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="5cea2-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="5cea2-299">Módulos de predefinido serão possível ler a partir do `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="5cea2-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="5cea2-300">Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="5cea2-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="5cea2-301">Os perfis respeitem a configuração de por anfitrião do PowerShell, pelo que os perfis de anfitrião específico predefinido não existe em `Microsoft.PowerShell_profile.ps1` nas localizações da mesmas.</span><span class="sxs-lookup"><span data-stu-id="5cea2-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="5cea2-302">PowerShell respeita o [XDG Base diretório especificação] [ xdg-bds] no Linux.</span><span class="sxs-lookup"><span data-stu-id="5cea2-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
