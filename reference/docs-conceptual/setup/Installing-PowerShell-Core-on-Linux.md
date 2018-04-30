# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="49517-101">Instalar o PowerShell Core no Linux</span><span class="sxs-lookup"><span data-stu-id="49517-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="49517-102">Suporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25 ] [ fed25], [Fedora 26][fed26], e [arquitetura Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="49517-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], and [Arch Linux][arch].</span></span>

<span data-ttu-id="49517-103">Para as distribuições do Linux que não são suportadas oficialmente, pode tentar utilizar o [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="49517-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="49517-104">Também pode tentar implementar os binários de PowerShell diretamente com o Linux [ `tar.gz` arquivo][tar], mas terá de configurar as dependências necessárias com base no SO em passos separados.</span><span class="sxs-lookup"><span data-stu-id="49517-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="49517-105">Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.</span><span class="sxs-lookup"><span data-stu-id="49517-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="49517-106">Depois do pacote está instalado, executar `pwsh` de um terminal.</span><span class="sxs-lookup"><span data-stu-id="49517-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

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
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="49517-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="49517-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="49517-108">Instalação através do repositório de pacote - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="49517-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="49517-109">PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="49517-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="49517-110">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="49517-110">This is the preferred method.</span></span>

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

<span data-ttu-id="49517-111">Como Superutilizador, registe o repositório de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="49517-111">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="49517-112">De ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` para atualizar a instalação.</span><span class="sxs-lookup"><span data-stu-id="49517-112">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="49517-113">Instalação através de transferência direta - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="49517-113">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="49517-114">Transferir o pacote Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` do [versões][] página para a máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="49517-114">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="49517-115">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="49517-115">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="49517-116">Tenha em atenção que `dpkg -i` irá falhar com dependências unmet; o comando seguinte, `apt-get install -f` resolve estes e, em seguida, termina a configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49517-116">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="49517-117">Desinstalação - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="49517-117">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="49517-118">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="49517-118">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="49517-119">Instalação através do repositório de pacote - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="49517-119">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="49517-120">PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="49517-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="49517-121">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="49517-121">This is the preferred method.</span></span>

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

<span data-ttu-id="49517-122">Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="49517-122">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="49517-123">Instalação através de transferência direta - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="49517-123">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="49517-124">Transferir o pacote Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` do [versões][] página para a máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="49517-124">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="49517-125">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="49517-125">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="49517-126">Tenha em atenção que `dpkg -i` irá falhar com dependências unmet; o comando seguinte, `apt-get install -f` resolve estes e, em seguida, termina a configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49517-126">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="49517-127">Desinstalação - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="49517-127">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="49517-128">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="49517-128">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="49517-129">Instalação através do repositório de pacote - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="49517-129">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="49517-130">PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="49517-130">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="49517-131">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="49517-131">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="49517-132">Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="49517-132">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="49517-133">Instalação através de transferência direta - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="49517-133">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="49517-134">Transferir o pacote Debian `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` do [versões][] página para a máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="49517-134">Download the Debian package `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="49517-135">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="49517-135">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="49517-136">Tenha em atenção que `dpkg -i` irá falhar com dependências unmet; o comando seguinte, `apt-get install -f` resolve estes e, em seguida, termina a configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49517-136">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="49517-137">Desinstalação - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="49517-137">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="49517-138">Debian 8</span><span class="sxs-lookup"><span data-stu-id="49517-138">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="49517-139">Instalação através do repositório de pacote - Debian 8</span><span class="sxs-lookup"><span data-stu-id="49517-139">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="49517-140">PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="49517-140">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="49517-141">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="49517-141">This is the preferred method.</span></span>

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

<span data-ttu-id="49517-142">Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="49517-142">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="49517-143">Instalação através de transferência direta - Debian 8</span><span class="sxs-lookup"><span data-stu-id="49517-143">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="49517-144">Transferir o pacote Debian `powershell_6.0.2-1.debian.8_amd64.deb` do [versões][] página para a máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="49517-144">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="49517-145">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="49517-145">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="49517-146">Tenha em atenção que `dpkg -i` irá falhar com dependências unmet.</span><span class="sxs-lookup"><span data-stu-id="49517-146">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="49517-147">O comando seguinte, `apt-get install -f` resolve estes e, em seguida, termina a configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49517-147">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="49517-148">Desinstalação - Debian 8</span><span class="sxs-lookup"><span data-stu-id="49517-148">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="49517-149">Debian 9</span><span class="sxs-lookup"><span data-stu-id="49517-149">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="49517-150">Instalação através do repositório de pacote - Debian 9</span><span class="sxs-lookup"><span data-stu-id="49517-150">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="49517-151">PowerShell Core, para o Linux, é publicado para repositórios de pacote de instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="49517-151">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="49517-152">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="49517-152">This is the preferred method.</span></span>

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

<span data-ttu-id="49517-153">Depois de registar o repositório de Microsoft uma vez como Superutilizador, de ora em diante, apenas terá de utilizar `sudo apt-get upgrade powershell` atualizá-lo.</span><span class="sxs-lookup"><span data-stu-id="49517-153">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="49517-154">Instalação através de transferência direta - Debian 9</span><span class="sxs-lookup"><span data-stu-id="49517-154">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="49517-155">Transferir o pacote Debian `powershell_6.0.2-1.debian.9_amd64.deb` do [versões][] página para a máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="49517-155">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="49517-156">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="49517-156">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="49517-157">Tenha em atenção que `dpkg -i` irá falhar com dependências unmet.</span><span class="sxs-lookup"><span data-stu-id="49517-157">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="49517-158">O comando seguinte, `apt-get install -f` resolve estes e, em seguida, termina a configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49517-158">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="49517-159">Desinstalação - Debian 9</span><span class="sxs-lookup"><span data-stu-id="49517-159">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="49517-160">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="49517-160">CentOS 7</span></span>

> <span data-ttu-id="49517-161">Este pacote também funciona no Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="49517-161">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="49517-162">Instalação através do repositório de pacote (preferencial) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="49517-162">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="49517-163">Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="49517-163">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="49517-164">Depois de registar o repositório de Microsoft uma vez como Superutilizador, basta utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49517-164">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="49517-165">Instalação através de transferência direta - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="49517-165">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="49517-166">Utilizar [CentOS 7][], transfira o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina do CentOS.</span><span class="sxs-lookup"><span data-stu-id="49517-166">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="49517-167">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="49517-167">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="49517-168">Também pode instalar o RPM sem o passo intermédio de transferindo-a:</span><span class="sxs-lookup"><span data-stu-id="49517-168">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="49517-169">Desinstalação - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="49517-169">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="49517-171">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="49517-171">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="49517-172">Instalação através do repositório de pacote (preferencial) - 7 do Red Hat Enterprise Linux (RHEL)</span><span class="sxs-lookup"><span data-stu-id="49517-172">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="49517-173">Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="49517-173">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="49517-174">Depois de registar o repositório de Microsoft uma vez como Superutilizador, basta utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49517-174">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="49517-175">Instalação através de transferência direta - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="49517-175">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="49517-176">Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina do Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="49517-176">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="49517-177">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="49517-177">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="49517-178">Também pode instalar o RPM sem o passo intermédio de transferindo-a:</span><span class="sxs-lookup"><span data-stu-id="49517-178">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="49517-179">Desinstalação - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="49517-179">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="49517-180">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="49517-180">OpenSUSE 42.2</span></span>

> [!NOTE]
> <span data-ttu-id="49517-181">Ao instalar o PowerShell Core, `zypper` pode comunicar o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="49517-181">When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="49517-182">Neste caso, certifique-se de que um ecrã compatível com `libcurl` biblioteca encontra-se ao verificar que o seguinte comando mostra o `libcurl4` pacote como instalado:</span><span class="sxs-lookup"><span data-stu-id="49517-182">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="49517-183">Em seguida, escolha o `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solução quando instalar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49517-183">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="49517-184">Instalação através do repositório de pacote (preferencial) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="49517-184">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="49517-185">Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="49517-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="49517-186">Instalação através de transferência direta - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="49517-186">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="49517-187">Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="49517-187">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="49517-188">Também pode instalar o RPM sem o passo intermédio de transferindo-a:</span><span class="sxs-lookup"><span data-stu-id="49517-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="49517-189">Desinstalação - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="49517-189">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="49517-190">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="49517-190">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="49517-191">Instalação através do repositório de pacote (preferencial) - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="49517-191">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="49517-192">Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="49517-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="49517-193">Instalação através de transferência direta - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="49517-193">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="49517-194">Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina Fedora.</span><span class="sxs-lookup"><span data-stu-id="49517-194">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="49517-195">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="49517-195">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="49517-196">Também pode instalar o RPM sem o passo intermédio de transferindo-a:</span><span class="sxs-lookup"><span data-stu-id="49517-196">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="49517-197">Desinstalação - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="49517-197">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="49517-198">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="49517-198">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="49517-199">Instalação através do repositório de pacote (preferencial) - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="49517-199">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="49517-200">Núcleo de PowerShell para Linux é publicado para repositórios de Microsoft oficiais para instalação fácil (e para atualizações).</span><span class="sxs-lookup"><span data-stu-id="49517-200">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="49517-201">Instalação através de transferência direta - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="49517-201">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="49517-202">Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` do [versões][] página para a máquina Fedora.</span><span class="sxs-lookup"><span data-stu-id="49517-202">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="49517-203">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="49517-203">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="49517-204">Também pode instalar o RPM sem o passo intermédio de transferindo-a:</span><span class="sxs-lookup"><span data-stu-id="49517-204">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="49517-205">Desinstalação - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="49517-205">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="49517-206">Arquitetura de Linux</span><span class="sxs-lookup"><span data-stu-id="49517-206">Arch Linux</span></span>

<span data-ttu-id="49517-207">PowerShell está disponível a partir de [arquitetura Linux][] utilizador repositório (AUR).</span><span class="sxs-lookup"><span data-stu-id="49517-207">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="49517-208">Pode ser compilada com a [mais recente etiquetados versão][arch-release]</span><span class="sxs-lookup"><span data-stu-id="49517-208">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="49517-209">Pode ser compilado do [consolidação mais recente mestre][arch-git]</span><span class="sxs-lookup"><span data-stu-id="49517-209">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="49517-210">Pode ser instalado utilizando o [binário da versão mais recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="49517-210">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="49517-211">Pacotes no AUR Comunidade mantida - não são suportadas oficial.</span><span class="sxs-lookup"><span data-stu-id="49517-211">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="49517-212">Para obter mais informações sobre como instalar pacotes do AUR, consulte o [arquitetura Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou Comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="49517-212">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[arquitetura Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="49517-214">AppImage do Linux</span><span class="sxs-lookup"><span data-stu-id="49517-214">Linux AppImage</span></span>

<span data-ttu-id="49517-215">Com uma distribuição Linux recente, transfira o AppImage `powershell-6.0.1-x86_64.AppImage` do [versões][] página para a máquina do Linux.</span><span class="sxs-lookup"><span data-stu-id="49517-215">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="49517-216">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="49517-216">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="49517-217">O [AppImage][] permite-lhe executar o PowerShell sem instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="49517-217">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="49517-218">É uma aplicação portátil que bundles PowerShell e as respetivas dependências (incluindo as dependências do .NET Core system) para um pacote coesa.</span><span class="sxs-lookup"><span data-stu-id="49517-218">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="49517-219">Este pacote é um binário único que funciona independentemente da distribuição de Linux do utilizador.</span><span class="sxs-lookup"><span data-stu-id="49517-219">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="49517-221">Kali</span><span class="sxs-lookup"><span data-stu-id="49517-221">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="49517-222">Instalação</span><span class="sxs-lookup"><span data-stu-id="49517-222">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="49517-223">Executar o PowerShell no Kali mais recente (Kali GNU/Linux sucessiva) sem instalar</span><span class="sxs-lookup"><span data-stu-id="49517-223">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="49517-224">Desinstalação - Kali</span><span class="sxs-lookup"><span data-stu-id="49517-224">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="49517-225">Raspbian</span><span class="sxs-lookup"><span data-stu-id="49517-225">Raspbian</span></span>

<span data-ttu-id="49517-226">Atualmente, o PowerShell só é suportado em Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="49517-226">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="49517-227">Também CoreCLR (e, consequentemente, PowerShell Core) funcionará apenas em dispositivos Pi 2 e Pi 3 como outros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), tem um processador não suportado.</span><span class="sxs-lookup"><span data-stu-id="49517-227">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="49517-228">Transferir [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e siga o [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) obtê-lo no seu Pi.</span><span class="sxs-lookup"><span data-stu-id="49517-228">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="49517-229">Instalação</span><span class="sxs-lookup"><span data-stu-id="49517-229">Installation</span></span>

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

<span data-ttu-id="49517-230">Opcionalmente, pode criar uma ligação simbólica para conseguir iniciar PowerShell sem especificar o caminho para o "pwsh" binário</span><span class="sxs-lookup"><span data-stu-id="49517-230">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="49517-231">Desinstalação - Raspbian</span><span class="sxs-lookup"><span data-stu-id="49517-231">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="49517-232">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="49517-232">Binary Archives</span></span>

<span data-ttu-id="49517-233">PowerShell binário `tar.gz` arquivos são fornecidos para plataformas Linux ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="49517-233">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="49517-234">Dependências</span><span class="sxs-lookup"><span data-stu-id="49517-234">Dependencies</span></span>

<span data-ttu-id="49517-235">PowerShell compila binários portátil para todas as distribuições de Linux.</span><span class="sxs-lookup"><span data-stu-id="49517-235">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="49517-236">Mas o tempo de execução de .NET Core requer diferentes dependências em diversas distribuições e, por conseguinte, o PowerShell tem a mesma.</span><span class="sxs-lookup"><span data-stu-id="49517-236">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="49517-237">O gráfico seguinte mostra as dependências de .NET Core 2.0 oficialmente são suportadas em diversas distribuições de Linux.</span><span class="sxs-lookup"><span data-stu-id="49517-237">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="49517-238">SO</span><span class="sxs-lookup"><span data-stu-id="49517-238">OS</span></span>                 | <span data-ttu-id="49517-239">Dependências</span><span class="sxs-lookup"><span data-stu-id="49517-239">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="49517-240">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="49517-240">Ubuntu 14.04</span></span>       | <span data-ttu-id="49517-241">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="49517-241">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="49517-242">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="49517-242">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="49517-243">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="49517-243">Ubuntu 16.04</span></span>       | <span data-ttu-id="49517-244">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="49517-244">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="49517-245">libcurl3 libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="49517-245">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="49517-246">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="49517-246">Ubuntu 17.04</span></span>       | <span data-ttu-id="49517-247">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="49517-247">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="49517-248">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="49517-248">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="49517-249">8 debian (Jessie)</span><span class="sxs-lookup"><span data-stu-id="49517-249">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="49517-250">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="49517-250">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="49517-251">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="49517-251">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="49517-252">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="49517-252">Debian 9 (Stretch)</span></span> | <span data-ttu-id="49517-253">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="49517-253">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="49517-254">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="49517-254">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="49517-255">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="49517-255">CentOS 7</span></span> <br> <span data-ttu-id="49517-256">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="49517-256">Oracle Linux 7</span></span> <br> <span data-ttu-id="49517-257">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="49517-257">RHEL 7</span></span> <br> <span data-ttu-id="49517-258">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="49517-258">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="49517-259">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="49517-259">Fedora 25</span></span> | <span data-ttu-id="49517-260">libunwind, libcurl, bibliotecas de openssl, libicu</span><span class="sxs-lookup"><span data-stu-id="49517-260">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="49517-261">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="49517-261">Fedora 26</span></span>          | <span data-ttu-id="49517-262">libunwind libcurl, bibliotecas de openssl, libicu, openssl10 de compatibilidade</span><span class="sxs-lookup"><span data-stu-id="49517-262">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="49517-263">Para implementar os binários do PowerShell nas distribuições de Linux que não são suportados oficialmente, terá de instalar as dependências necessárias para o SO de destino nos passos separados.</span><span class="sxs-lookup"><span data-stu-id="49517-263">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="49517-264">Por exemplo, a nossa [Amazon Linux dockerfile] [ amazon-dockerfile] instala dependências primeiro e, em seguida, extrai o Linux `tar.gz` arquivo.</span><span class="sxs-lookup"><span data-stu-id="49517-264">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="49517-265">Instalação - arquivos binários</span><span class="sxs-lookup"><span data-stu-id="49517-265">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="49517-266">Linux</span><span class="sxs-lookup"><span data-stu-id="49517-266">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="49517-267">Desinstalação arquivos binários</span><span class="sxs-lookup"><span data-stu-id="49517-267">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="49517-268">Caminhos</span><span class="sxs-lookup"><span data-stu-id="49517-268">Paths</span></span>

* <span data-ttu-id="49517-269">`$PSHOME` é `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="49517-269">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="49517-270">Perfis de utilizador serão lida a partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="49517-270">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="49517-271">Serão possível ler perfis predefinidos `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="49517-271">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="49517-272">Módulos de utilizador serão lida a partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="49517-272">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="49517-273">Módulos partilhados irão ler a partir do `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="49517-273">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="49517-274">Módulos de predefinido serão possível ler a partir do `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="49517-274">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="49517-275">Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="49517-275">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="49517-276">Os perfis respeitem a configuração de por anfitrião do PowerShell, pelo que os perfis de anfitrião específico predefinido não existe em `Microsoft.PowerShell_profile.ps1` nas localizações da mesmas.</span><span class="sxs-lookup"><span data-stu-id="49517-276">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="49517-277">PowerShell respeita o [XDG Base diretório especificação] [ xdg-bds] no Linux.</span><span class="sxs-lookup"><span data-stu-id="49517-277">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
