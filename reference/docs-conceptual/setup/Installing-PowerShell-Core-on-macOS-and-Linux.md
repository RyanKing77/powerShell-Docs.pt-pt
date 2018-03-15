# <a name="installing-powershell-core-on-macos-and-linux"></a><span data-ttu-id="e616a-101">Instalar o PowerShell Core no macOS e Linux</span><span class="sxs-lookup"><span data-stu-id="e616a-101">Installing PowerShell Core on macOS and Linux</span></span>

<span data-ttu-id="e616a-102">Suporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25 ] [ fed25], [Fedora 26][fed26], [arquitetura Linux][arch]e [macOS 10.12][mac].</span><span class="sxs-lookup"><span data-stu-id="e616a-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch], and [macOS 10.12][mac].</span></span>

<span data-ttu-id="e616a-103">Para as distribuições do Linux que não são suportadas oficialmente, pode tentar utilizar o [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="e616a-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span> <span data-ttu-id="e616a-104">Também pode tentar implementar os binários de PowerShell diretamente com o Linux [ `tar.gz` arquivo][tar], mas terá de configurar as dependências necessárias com base no SO em passos separados.</span><span class="sxs-lookup"><span data-stu-id="e616a-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="e616a-105">Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.</span><span class="sxs-lookup"><span data-stu-id="e616a-105">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="e616a-106">Depois do pacote está instalado, executar `pwsh` de um terminal.</span><span class="sxs-lookup"><span data-stu-id="e616a-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

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
[mac]: #macos-1012
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="e616a-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e616a-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="e616a-108">Instalação através do repositório de pacote - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e616a-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="e616a-109">PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="e616a-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span> <span data-ttu-id="e616a-110">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="e616a-110">This is the preferred method.</span></span>

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

<span data-ttu-id="e616a-111">Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="e616a-111">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="e616a-112">Instalação através de transferência direta - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e616a-112">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="e616a-113">Transferir o pacote Debian `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` do [versões][] página para a máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="e616a-113">Download the Debian package `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

<span data-ttu-id="e616a-114">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="e616a-114">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e616a-115">Tenha em atenção que `dpkg -i` irá falhar com dependências unmet; o comando seguinte, `apt-get install -f` resolve estes e, em seguida, termina a configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e616a-115">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="e616a-116">Desinstalação - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e616a-116">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="e616a-117">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e616a-117">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="e616a-118">Instalação através do repositório de pacote - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e616a-118">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="e616a-119">PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="e616a-119">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e616a-120">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="e616a-120">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e616a-121">Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="e616a-121">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="e616a-122">Instalação através de transferência direta - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e616a-122">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="e616a-123">Transferir o pacote Debian `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` do [versões][] página para a máquina Ubuntu:</span><span class="sxs-lookup"><span data-stu-id="e616a-123">Download the Debian package `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

<span data-ttu-id="e616a-124">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="e616a-124">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e616a-125">Tenha em atenção que `dpkg -i` irá falhar com dependências unmet; o comando seguinte, `apt-get install -f` resolve estes e, em seguida, termina a configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e616a-125">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="e616a-126">Desinstalação - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e616a-126">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="e616a-127">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="e616a-127">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="e616a-128">Instalação através do repositório de pacote - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="e616a-128">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="e616a-129">PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="e616a-129">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e616a-130">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="e616a-130">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/17.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e616a-131">Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="e616a-131">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="e616a-132">Instalação através de transferência direta - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="e616a-132">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="e616a-133">Transferir o pacote Debian `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` do [versões][] página para a máquina Ubuntu:</span><span class="sxs-lookup"><span data-stu-id="e616a-133">Download the Debian package `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

<span data-ttu-id="e616a-134">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="e616a-134">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e616a-135">Tenha em atenção que `dpkg -i` irá falhar com dependências unmet; o comando seguinte, `apt-get install -f` resolve estes e, em seguida, termina a configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e616a-135">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="e616a-136">Desinstalação - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="e616a-136">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="e616a-137">Debian 8</span><span class="sxs-lookup"><span data-stu-id="e616a-137">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="e616a-138">Instalação através do repositório de pacote - Debian 8</span><span class="sxs-lookup"><span data-stu-id="e616a-138">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="e616a-139">PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="e616a-139">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e616a-140">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="e616a-140">This is the preferred method.</span></span>

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

<span data-ttu-id="e616a-141">Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="e616a-141">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="e616a-142">Instalação através de transferência direta - Debian 8</span><span class="sxs-lookup"><span data-stu-id="e616a-142">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="e616a-143">Transferir o pacote Debian `powershell_6.0.0-1.debian.8_amd64.deb` do [versões][] página para a máquina Debian:</span><span class="sxs-lookup"><span data-stu-id="e616a-143">Download the Debian package `powershell_6.0.0-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

<span data-ttu-id="e616a-144">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="e616a-144">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e616a-145">Tenha em atenção que `dpkg -i` irá falhar com dependências unmet; o comando seguinte, `apt-get install -f` resolve estes e, em seguida, termina a configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e616a-145">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="e616a-146">Desinstalação - Debian 8</span><span class="sxs-lookup"><span data-stu-id="e616a-146">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="e616a-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="e616a-147">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="e616a-148">Instalação através do repositório de pacote - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e616a-148">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="e616a-149">PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="e616a-149">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e616a-150">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="e616a-150">This is the preferred method.</span></span>

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

<span data-ttu-id="e616a-151">Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="e616a-151">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="e616a-152">Instalação através de transferência direta - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e616a-152">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="e616a-153">Transferir o pacote Debian `powershell_6.0.0-1.debian.9_amd64.deb` do [versões][] página para a máquina Debian:</span><span class="sxs-lookup"><span data-stu-id="e616a-153">Download the Debian package `powershell_6.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="e616a-154">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="e616a-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e616a-155">Tenha em atenção que `dpkg -i` irá falhar com dependências unmet; o comando seguinte, `apt-get install -f` resolve estes e, em seguida, termina a configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e616a-155">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="e616a-156">Desinstalação - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e616a-156">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="e616a-157">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e616a-157">CentOS 7</span></span>

> <span data-ttu-id="e616a-158">Este pacote também funciona no Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="e616a-158">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="e616a-159">Instalação através do repositório de pacote (preferencial) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e616a-159">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="e616a-160">Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="e616a-160">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e616a-161">Depois de registar o repositório de Microsoft uma vez como Superutilizador, basta utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e616a-161">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="e616a-162">Instalação através de transferência direta - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e616a-162">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="e616a-163">Utilizar [CentOS 7][], transfira o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina do CentOS:</span><span class="sxs-lookup"><span data-stu-id="e616a-163">Using [CentOS 7][], download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e616a-164">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="e616a-164">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e616a-165">Também pode instalar o RPM sem o passo intermédio de transferindo-a:</span><span class="sxs-lookup"><span data-stu-id="e616a-165">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="e616a-166">Desinstalação - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e616a-166">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e616a-168">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e616a-168">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e616a-169">Instalação através do repositório de pacote (preferencial) - 7 do Red Hat Enterprise Linux (RHEL)</span><span class="sxs-lookup"><span data-stu-id="e616a-169">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e616a-170">Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="e616a-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e616a-171">Depois de registar o repositório de Microsoft uma vez como Superutilizador, basta utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e616a-171">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e616a-172">Instalação através de transferência direta - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e616a-172">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e616a-173">Transferir o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina do Red Hat Enterprise Linux:</span><span class="sxs-lookup"><span data-stu-id="e616a-173">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="e616a-174">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="e616a-174">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e616a-175">Também pode instalar o RPM sem o passo intermédio de transferindo-a:</span><span class="sxs-lookup"><span data-stu-id="e616a-175">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e616a-176">Desinstalação - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e616a-176">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="e616a-177">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e616a-177">OpenSUSE 42.2</span></span>

> <span data-ttu-id="e616a-178">**Nota:** ao instalar o PowerShell Core, `zypper` pode comunicar o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="e616a-178">**Note:** When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```text
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="e616a-179">Neste caso, certifique-se de que um ecrã compatível com `libcurl` biblioteca encontra-se ao verificar que o seguinte comando mostra o `libcurl4` pacote como instalado:</span><span class="sxs-lookup"><span data-stu-id="e616a-179">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="e616a-180">Em seguida, escolha o `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solução quando instalar o `powershell` pacote.</span><span class="sxs-lookup"><span data-stu-id="e616a-180">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the `powershell` package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="e616a-181">Instalação através do repositório de pacote (preferencial) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e616a-181">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="e616a-182">Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="e616a-182">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="e616a-183">Instalação através de transferência direta - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e616a-183">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="e616a-184">Transferir o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina OpenSUSE:</span><span class="sxs-lookup"><span data-stu-id="e616a-184">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e616a-185">Também pode instalar o RPM sem o passo intermédio de transferindo-a:</span><span class="sxs-lookup"><span data-stu-id="e616a-185">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="e616a-186">Desinstalação - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e616a-186">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="e616a-187">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="e616a-187">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="e616a-188">Instalação através do repositório de pacote (preferencial) - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="e616a-188">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="e616a-189">Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="e616a-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="e616a-190">Instalação através de transferência direta - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="e616a-190">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="e616a-191">Transferir o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina Fedora:</span><span class="sxs-lookup"><span data-stu-id="e616a-191">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e616a-192">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="e616a-192">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e616a-193">Também pode instalar o RPM sem o passo intermédio de transferindo-a:</span><span class="sxs-lookup"><span data-stu-id="e616a-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="e616a-194">Uninstallation - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="e616a-194">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="e616a-195">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="e616a-195">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="e616a-196">Instalação através do repositório de pacote (preferencial) - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="e616a-196">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="e616a-197">Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="e616a-197">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="e616a-198">Instalação através de transferência direta - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="e616a-198">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="e616a-199">Transferir o pacote RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina Fedora:</span><span class="sxs-lookup"><span data-stu-id="e616a-199">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e616a-200">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="e616a-200">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e616a-201">Também pode instalar o RPM sem o passo intermédio de transferindo-a:</span><span class="sxs-lookup"><span data-stu-id="e616a-201">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="e616a-202">Uninstallation - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="e616a-202">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="e616a-203">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="e616a-203">Arch Linux</span></span>

<span data-ttu-id="e616a-204">PowerShell está disponível a partir de [arquitetura Linux][] utilizador repositório (AUR).</span><span class="sxs-lookup"><span data-stu-id="e616a-204">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="e616a-205">Pode ser compilada com a [mais recente etiquetados versão][arch-release]</span><span class="sxs-lookup"><span data-stu-id="e616a-205">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="e616a-206">Pode ser compilado do [consolidação mais recente mestre][arch-git]</span><span class="sxs-lookup"><span data-stu-id="e616a-206">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="e616a-207">Pode ser instalado utilizando o [binário da versão mais recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="e616a-207">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="e616a-208">Pacotes no AUR Comunidade mantida - não são suportadas oficial.</span><span class="sxs-lookup"><span data-stu-id="e616a-208">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="e616a-209">Para obter mais informações sobre como instalar pacotes do AUR, consulte o [arquitetura Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou Comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="e616a-209">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[arquitetura Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="e616a-211">AppImage do Linux</span><span class="sxs-lookup"><span data-stu-id="e616a-211">Linux AppImage</span></span>

<span data-ttu-id="e616a-212">Com uma distribuição Linux recente, transfira o AppImage `powershell-6.0.0-x86_64.AppImage` do [versões][] página para a máquina do Linux.</span><span class="sxs-lookup"><span data-stu-id="e616a-212">Using a recent Linux distribution, download the AppImage `powershell-6.0.0-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="e616a-213">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="e616a-213">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

<span data-ttu-id="e616a-214">O [AppImage][] permite-lhe executar o PowerShell sem instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="e616a-214">The [AppImage][] lets you run PowerShell without installing it.</span></span> <span data-ttu-id="e616a-215">É uma aplicação portátil que bundles PowerShell e as respetivas dependências (incluindo as dependências do .NET Core system) para um pacote coesa.</span><span class="sxs-lookup"><span data-stu-id="e616a-215">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span> <span data-ttu-id="e616a-216">Este pacote funciona independentemente da distribuição de Linux do utilizador, não sendo único binário.</span><span class="sxs-lookup"><span data-stu-id="e616a-216">This package works independently of the user's Linux distribution, and is a single binary.</span></span>

[appimage]: http://appimage.org/

## <a name="macos-1012"></a><span data-ttu-id="e616a-218">macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="e616a-218">macOS 10.12</span></span>

### <a name="installation-via-homebrew-preferred---macos-1012"></a><span data-ttu-id="e616a-219">Instalação via Homebrew (preferido) - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="e616a-219">Installation via Homebrew (preferred) - macOS 10.12</span></span>

<span data-ttu-id="e616a-220">[Homebrew] [ brew] é o Gestor de pacote em falta para macOS.</span><span class="sxs-lookup"><span data-stu-id="e616a-220">[Homebrew][brew] is the missing package manager for macOS.</span></span> <span data-ttu-id="e616a-221">Se o `brew` comandos não for encontrado, tem de instalar o seguinte Homebrew [as instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="e616a-221">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="e616a-222">Assim que instalou Homebrew, instalar o PowerShell é fácil.</span><span class="sxs-lookup"><span data-stu-id="e616a-222">Once you've installed Homebrew, installing PowerShell is easy.</span></span> <span data-ttu-id="e616a-223">Em primeiro lugar, instalar [Homebrew Cask][cask], como tal, pode instalar mais pacotes:</span><span class="sxs-lookup"><span data-stu-id="e616a-223">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="e616a-224">Agora, pode instalar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e616a-224">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="e616a-225">Quando são lançadas novas versões do PowerShell, basta atualizar formulae do Homebrew e atualizar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e616a-225">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask reinstall powershell
```

> <span data-ttu-id="e616a-226">Nota: porque de [este problema nos Cask](https://github.com/caskroom/homebrew-cask/issues/29301), atualmente, possui fazer reinstalar a atualização.</span><span class="sxs-lookup"><span data-stu-id="e616a-226">Note: because of [this issue in Cask](https://github.com/caskroom/homebrew-cask/issues/29301), you currently have to do a reinstall to upgrade.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a><span data-ttu-id="e616a-227">Instalação através de transferência direta - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="e616a-227">Installation via Direct Download - macOS 10.12</span></span>

<span data-ttu-id="e616a-228">Utilizar macOS 10.12, transfira o pacote PKG `powershell-6.0.0-osx.10.12-x64.pkg` do [versões][] página para a máquina macOS.</span><span class="sxs-lookup"><span data-stu-id="e616a-228">Using macOS 10.12, download the PKG package `powershell-6.0.0-osx.10.12-x64.pkg` from the [releases][] page onto the macOS machine.</span></span>

<span data-ttu-id="e616a-229">Faça duplo clique o ficheiro e siga as instruções ou instalá-lo no terminal:</span><span class="sxs-lookup"><span data-stu-id="e616a-229">Either double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a><span data-ttu-id="e616a-230">Desinstalação - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="e616a-230">Uninstallation - macOS 10.12</span></span>

<span data-ttu-id="e616a-231">Se tiver instalado o PowerShell com Homebrew, é fácil a desinstalação:</span><span class="sxs-lookup"><span data-stu-id="e616a-231">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="e616a-232">Se tiver instalado o PowerShell através de transferência direta, PowerShell tem de retirar manualmente:</span><span class="sxs-lookup"><span data-stu-id="e616a-232">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="e616a-233">Para desinstalar os caminhos de PowerShell adicionais (por exemplo, o caminho do perfil de utilizador). consulte o [caminhos] [ paths] secção abaixo neste documento e remova o pretendido os caminhos com `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="e616a-233">To uninstall the additional PowerShell paths (such as the user profile path) please see the [paths][paths] section below in this document and remove the desired the paths with `sudo rm`.</span></span> <span data-ttu-id="e616a-234">(Nota: não é necessário se tiver instalado com Homebrew.)</span><span class="sxs-lookup"><span data-stu-id="e616a-234">(Note: this is not necessary if you installed with Homebrew.)</span></span>

[paths]:#paths

## <a name="kali"></a><span data-ttu-id="e616a-235">Kali</span><span class="sxs-lookup"><span data-stu-id="e616a-235">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="e616a-236">Instalação</span><span class="sxs-lookup"><span data-stu-id="e616a-236">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Download & Install PowerShell
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="e616a-237">Executar o PowerShell no Kali mais recente (Kali GNU/Linux sucessiva) sem instalar</span><span class="sxs-lookup"><span data-stu-id="e616a-237">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="e616a-238">Desinstalação - Kali</span><span class="sxs-lookup"><span data-stu-id="e616a-238">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a><span data-ttu-id="e616a-239">Raspbian</span><span class="sxs-lookup"><span data-stu-id="e616a-239">Raspbian</span></span>

<span data-ttu-id="e616a-240">Atualmente, o PowerShell só é suportado em Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="e616a-240">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

### <a name="installation"></a><span data-ttu-id="e616a-241">Instalação</span><span class="sxs-lookup"><span data-stu-id="e616a-241">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="e616a-242">Desinstalação - Raspbian</span><span class="sxs-lookup"><span data-stu-id="e616a-242">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="e616a-243">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="e616a-243">Binary Archives</span></span>

<span data-ttu-id="e616a-244">PowerShell binário `tar.gz` arquivos são fornecidos para macOS e plataformas Linux para ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="e616a-244">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="e616a-245">Dependências</span><span class="sxs-lookup"><span data-stu-id="e616a-245">Dependencies</span></span>

<span data-ttu-id="e616a-246">Para Linux, PowerShell baseia-se o portátil binários para todas as distribuições de Linux.</span><span class="sxs-lookup"><span data-stu-id="e616a-246">For Linux, PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="e616a-247">Mas o tempo de execução de .NET Core requer diferentes dependências em diversas distribuições e, por conseguinte, o PowerShell tem a mesma.</span><span class="sxs-lookup"><span data-stu-id="e616a-247">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="e616a-248">O gráfico seguinte mostra as dependências do .NET Core 2.0 em diversas distribuições de Linux que são suportadas oficialmente.</span><span class="sxs-lookup"><span data-stu-id="e616a-248">The following chart shows the .NET Core 2.0 dependencies on different Linux distributions that are officially supported.</span></span>

| <span data-ttu-id="e616a-249">SO</span><span class="sxs-lookup"><span data-stu-id="e616a-249">OS</span></span>                 | <span data-ttu-id="e616a-250">Dependências</span><span class="sxs-lookup"><span data-stu-id="e616a-250">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="e616a-251">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e616a-251">Ubuntu 14.04</span></span>       | <span data-ttu-id="e616a-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e616a-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e616a-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e616a-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e616a-254">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e616a-254">Ubuntu 16.04</span></span>       | <span data-ttu-id="e616a-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e616a-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e616a-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="e616a-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="e616a-257">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="e616a-257">Ubuntu 17.04</span></span>       | <span data-ttu-id="e616a-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e616a-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e616a-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="e616a-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="e616a-260">8 debian (Jessie)</span><span class="sxs-lookup"><span data-stu-id="e616a-260">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="e616a-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e616a-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e616a-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e616a-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e616a-263">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="e616a-263">Debian 9 (Stretch)</span></span> | <span data-ttu-id="e616a-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e616a-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e616a-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="e616a-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="e616a-266">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e616a-266">CentOS 7</span></span> <br> <span data-ttu-id="e616a-267">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="e616a-267">Oracle Linux 7</span></span> <br> <span data-ttu-id="e616a-268">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="e616a-268">RHEL 7</span></span> <br> <span data-ttu-id="e616a-269">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e616a-269">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="e616a-270">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="e616a-270">Fedora 25</span></span> | <span data-ttu-id="e616a-271">libunwind, libcurl, bibliotecas de openssl, libicu</span><span class="sxs-lookup"><span data-stu-id="e616a-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="e616a-272">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="e616a-272">Fedora 26</span></span>          | <span data-ttu-id="e616a-273">libunwind libcurl, bibliotecas de openssl, libicu, openssl10 de compatibilidade</span><span class="sxs-lookup"><span data-stu-id="e616a-273">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="e616a-274">Para implementar os binários do PowerShell nas distribuições de Linux que não são suportados oficialmente, terá de instalar as dependências necessárias para o SO de destino nos passos separados.</span><span class="sxs-lookup"><span data-stu-id="e616a-274">In order to deploy PowerShell binaries on Linux distributions that are not officially supported, you would need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="e616a-275">Por exemplo, a nossa [Amazon Linux dockerfile] [ amazon-dockerfile] instala dependências primeiro e, em seguida, extrai o Linux `tar.gz` arquivo.</span><span class="sxs-lookup"><span data-stu-id="e616a-275">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="e616a-276">Instalação - arquivos binários</span><span class="sxs-lookup"><span data-stu-id="e616a-276">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="e616a-277">Linux</span><span class="sxs-lookup"><span data-stu-id="e616a-277">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a><span data-ttu-id="e616a-278">macOS</span><span class="sxs-lookup"><span data-stu-id="e616a-278">macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a><span data-ttu-id="e616a-279">Desinstalação - arquivos binários</span><span class="sxs-lookup"><span data-stu-id="e616a-279">Uninstallation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="e616a-280">Linux</span><span class="sxs-lookup"><span data-stu-id="e616a-280">Linux</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a><span data-ttu-id="e616a-281">macOS</span><span class="sxs-lookup"><span data-stu-id="e616a-281">macOS</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="e616a-282">Caminhos</span><span class="sxs-lookup"><span data-stu-id="e616a-282">Paths</span></span>

* <span data-ttu-id="e616a-283">`$PSHOME` é `/opt/microsoft/powershell/6.0.0/`</span><span class="sxs-lookup"><span data-stu-id="e616a-283">`$PSHOME` is `/opt/microsoft/powershell/6.0.0/`</span></span>
* <span data-ttu-id="e616a-284">Perfis de utilizador serão lida a partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e616a-284">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="e616a-285">Serão possível ler perfis predefinidos `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e616a-285">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="e616a-286">Módulos de utilizador serão lida a partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e616a-286">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e616a-287">Módulos partilhados irão ler a partir do `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e616a-287">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e616a-288">Módulos de predefinido serão possível ler a partir do `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="e616a-288">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="e616a-289">Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="e616a-289">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="e616a-290">Os perfis respeitem a configuração de por anfitrião do PowerShell, pelo que os perfis de anfitrião específico predefinido não existe em `Microsoft.PowerShell_profile.ps1` nas localizações da mesmas.</span><span class="sxs-lookup"><span data-stu-id="e616a-290">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="e616a-291">No Linux e macOS, o [XDG Base diretório especificação] [ xdg-bds] é respeitado.</span><span class="sxs-lookup"><span data-stu-id="e616a-291">On Linux and macOS, the [XDG Base Directory Specification][xdg-bds] is respected.</span></span>

<span data-ttu-id="e616a-292">Tenha em atenção que porque macOS é uma derivação do BSD, em vez de `/opt`, é o prefixo utilizado `/usr/local`.</span><span class="sxs-lookup"><span data-stu-id="e616a-292">Note that because macOS is a derivation of BSD, instead of `/opt`, the prefix used is `/usr/local`.</span></span> <span data-ttu-id="e616a-293">Assim, `$PSHOME` é `/usr/local/microsoft/powershell/6.0.0/`, e o symlink é colocado em `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="e616a-293">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
