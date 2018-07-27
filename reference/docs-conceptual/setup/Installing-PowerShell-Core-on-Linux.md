# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="8b2af-101">Instalar o PowerShell Core no Linux</span><span class="sxs-lookup"><span data-stu-id="8b2af-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="8b2af-102">Suporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27 ] [ fedora], [Fedora 28][fedora], e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="8b2af-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="8b2af-103">Para as distribuições de Linux que não são suportadas oficialmente, pode tentar usar a [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="8b2af-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="8b2af-104">Também pode tentar implementar os binários do PowerShell diretamente com a Linux [ `tar.gz` arquivo][tar], mas terá de configurar as dependências necessárias, com base no sistema operacional nos passos separados.</span><span class="sxs-lookup"><span data-stu-id="8b2af-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="8b2af-105">Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.</span><span class="sxs-lookup"><span data-stu-id="8b2af-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="8b2af-106">Depois do pacote está instalado, execute `pwsh` partir de um terminal.</span><span class="sxs-lookup"><span data-stu-id="8b2af-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="8b2af-107">Instalar versões de pré-visualização</span><span class="sxs-lookup"><span data-stu-id="8b2af-107">Installing Preview Releases</span></span>

<span data-ttu-id="8b2af-108">Ao instalar uma versão de pré-visualização do PowerShell Core para Linux através de um repositório de pacotes, o nome do pacote é alterado de `powershell` para `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="8b2af-108">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="8b2af-109">Instalar através de transferência direta não é alterada, além do nome de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="8b2af-109">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="8b2af-110">Esta é uma tabela de comandos para instalar os pacotes de estável e pré-visualização com os vários gestores de pacote:</span><span class="sxs-lookup"><span data-stu-id="8b2af-110">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="8b2af-111">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="8b2af-111">Distribution(s)</span></span>|<span data-ttu-id="8b2af-112">Comando estável</span><span class="sxs-lookup"><span data-stu-id="8b2af-112">Stable Command</span></span> | <span data-ttu-id="8b2af-113">Comando de pré-visualização</span><span class="sxs-lookup"><span data-stu-id="8b2af-113">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="8b2af-114">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="8b2af-114">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="8b2af-115">CentOS, Red Hat</span><span class="sxs-lookup"><span data-stu-id="8b2af-115">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="8b2af-116">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="8b2af-116">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="8b2af-117">Fedora</span><span class="sxs-lookup"><span data-stu-id="8b2af-117">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="8b2af-118">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="8b2af-118">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="8b2af-119">Instalação através do repositório do pacote - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="8b2af-119">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="8b2af-120">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="8b2af-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="8b2af-121">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="8b2af-121">This is the preferred method.</span></span>

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

<span data-ttu-id="8b2af-122">Superutilizador, registar-se o repositório da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8b2af-122">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="8b2af-123">De ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` para atualizar a instalação.</span><span class="sxs-lookup"><span data-stu-id="8b2af-123">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="8b2af-124">Instalação através de transferência direta - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="8b2af-124">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="8b2af-125">Transferir o pacote Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` partir a [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="8b2af-125">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="8b2af-126">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="8b2af-126">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="8b2af-127">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="8b2af-127">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="8b2af-128">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b2af-128">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="8b2af-129">Desinstalação - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="8b2af-129">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="8b2af-130">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="8b2af-130">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="8b2af-131">Instalação através do repositório do pacote - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="8b2af-131">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="8b2af-132">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="8b2af-132">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="8b2af-133">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="8b2af-133">This is the preferred method.</span></span>

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

<span data-ttu-id="8b2af-134">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="8b2af-134">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="8b2af-135">Instalação através de transferência direta - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="8b2af-135">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="8b2af-136">Transferir o pacote Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` partir a [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="8b2af-136">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="8b2af-137">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="8b2af-137">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="8b2af-138">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="8b2af-138">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="8b2af-139">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b2af-139">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="8b2af-140">Desinstalação - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="8b2af-140">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a><span data-ttu-id="8b2af-141">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="8b2af-141">Ubuntu 17.10</span></span>

> [!NOTE]
> <span data-ttu-id="8b2af-142">Foi adicionado suporte para Ubuntu 17.04 após `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="8b2af-142">Support for Ubuntu 17.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1710"></a><span data-ttu-id="8b2af-143">Instalação através do repositório do pacote - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="8b2af-143">Installation via Package Repository - Ubuntu 17.10</span></span>

<span data-ttu-id="8b2af-144">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="8b2af-144">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="8b2af-145">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="8b2af-145">This is the preferred method.</span></span>

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

<span data-ttu-id="8b2af-146">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="8b2af-146">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1710"></a><span data-ttu-id="8b2af-147">Instalação através de transferência direta - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="8b2af-147">Installation via Direct Download - Ubuntu 17.10</span></span>

<span data-ttu-id="8b2af-148">Transferir o pacote Debian `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` partir a [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="8b2af-148">Download the Debian package `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="8b2af-149">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="8b2af-149">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="8b2af-150">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="8b2af-150">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="8b2af-151">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b2af-151">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="8b2af-152">Desinstalação - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="8b2af-152">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="8b2af-153">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="8b2af-153">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="8b2af-154">Foi adicionado suporte para Ubuntu 18.04 após `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="8b2af-154">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="8b2af-155">Instalação através do repositório do pacote - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="8b2af-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="8b2af-156">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="8b2af-156">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="8b2af-157">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="8b2af-157">This is the preferred method.</span></span>

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

<span data-ttu-id="8b2af-158">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="8b2af-158">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="8b2af-159">Instalação através de transferência direta - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="8b2af-159">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="8b2af-160">Transferir o pacote Debian `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` partir a [versões][] página para o computador do Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="8b2af-160">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="8b2af-161">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="8b2af-161">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="8b2af-162">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="8b2af-162">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="8b2af-163">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b2af-163">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="8b2af-164">Desinstalação - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="8b2af-164">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="8b2af-165">Debian 8</span><span class="sxs-lookup"><span data-stu-id="8b2af-165">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="8b2af-166">Instalação através do repositório do pacote - Debian 8</span><span class="sxs-lookup"><span data-stu-id="8b2af-166">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="8b2af-167">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="8b2af-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="8b2af-168">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="8b2af-168">This is the preferred method.</span></span>

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

<span data-ttu-id="8b2af-169">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="8b2af-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="8b2af-170">Instalação através de transferência direta - Debian 8</span><span class="sxs-lookup"><span data-stu-id="8b2af-170">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="8b2af-171">Transferir o pacote Debian `powershell_6.0.2-1.debian.8_amd64.deb` partir a [versões][] página para o computador Debian.</span><span class="sxs-lookup"><span data-stu-id="8b2af-171">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="8b2af-172">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="8b2af-172">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="8b2af-173">O `dpkg -i` comando falha com dependências por cumprir.</span><span class="sxs-lookup"><span data-stu-id="8b2af-173">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="8b2af-174">O comando seguinte, `apt-get install -f` resolve esses problemas, em seguida, terminar de configurar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b2af-174">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="8b2af-175">Desinstalação - Debian 8</span><span class="sxs-lookup"><span data-stu-id="8b2af-175">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="8b2af-176">Debian 9</span><span class="sxs-lookup"><span data-stu-id="8b2af-176">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="8b2af-177">Instalação através do repositório do pacote - Debian 9</span><span class="sxs-lookup"><span data-stu-id="8b2af-177">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="8b2af-178">O PowerShell Core, para o Linux, é publicado para repositórios de pacote para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="8b2af-178">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="8b2af-179">Este é o método preferido.</span><span class="sxs-lookup"><span data-stu-id="8b2af-179">This is the preferred method.</span></span>

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

<span data-ttu-id="8b2af-180">Depois de registar o repositório da Microsoft uma vez como Superutilizador, de ora em diante, apenas tem de utilizar `sudo apt-get upgrade powershell` atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="8b2af-180">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="8b2af-181">Instalação através de transferência direta - Debian 9</span><span class="sxs-lookup"><span data-stu-id="8b2af-181">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="8b2af-182">Transferir o pacote Debian `powershell_6.0.2-1.debian.9_amd64.deb` partir a [versões][] página para o computador Debian.</span><span class="sxs-lookup"><span data-stu-id="8b2af-182">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="8b2af-183">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="8b2af-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="8b2af-184">Desinstalação - Debian 9</span><span class="sxs-lookup"><span data-stu-id="8b2af-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="8b2af-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="8b2af-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="8b2af-186">Este pacote também funciona no Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="8b2af-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="8b2af-187">Instalação através do repositório de pacotes (preferencial) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="8b2af-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="8b2af-188">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="8b2af-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="8b2af-189">Depois de registar o repositório da Microsoft uma vez como Superutilizador, apenas tem de utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b2af-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="8b2af-190">Instalação através de transferência direta - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="8b2af-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="8b2af-191">Usando [CentOS 7][], transfira o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` da [versões][] página para o computador de CentOS.</span><span class="sxs-lookup"><span data-stu-id="8b2af-191">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="8b2af-192">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="8b2af-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="8b2af-193">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="8b2af-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="8b2af-194">Desinstalação - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="8b2af-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="8b2af-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="8b2af-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="8b2af-197">Instalação através do repositório de pacotes (preferencial) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="8b2af-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="8b2af-198">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="8b2af-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="8b2af-199">Depois de registar o repositório da Microsoft uma vez como Superutilizador, apenas tem de utilizar `sudo yum update powershell` para atualizar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b2af-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="8b2af-200">Instalação através de transferência direta - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="8b2af-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="8b2af-201">Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` partir de [versões][] página para o computador Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="8b2af-201">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="8b2af-202">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="8b2af-202">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="8b2af-203">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="8b2af-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="8b2af-204">Desinstalação - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="8b2af-204">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="8b2af-205">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="8b2af-205">OpenSUSE 42.3</span></span>

<span data-ttu-id="8b2af-206">Quando instalar o PowerShell Core, `zypper` pode reportar o erro seguinte:</span><span class="sxs-lookup"><span data-stu-id="8b2af-206">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="8b2af-207">Neste caso, certifique-se de que um ecrã compatível com `libcurl` biblioteca está presente, verificando que o seguinte comando mostra o `libcurl4` como instalado o pacote:</span><span class="sxs-lookup"><span data-stu-id="8b2af-207">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="8b2af-208">Em seguida, escolha o `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solução ao instalar o pacote do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b2af-208">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="8b2af-209">Instalação através do repositório de pacotes (preferencial) - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="8b2af-209">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="8b2af-210">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="8b2af-210">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="8b2af-211">Instalação através de transferência direta - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="8b2af-211">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="8b2af-212">Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` partir a [versões][] página na máquina OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="8b2af-212">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="8b2af-213">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="8b2af-213">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="8b2af-214">Desinstalação - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="8b2af-214">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="8b2af-215">Fedora</span><span class="sxs-lookup"><span data-stu-id="8b2af-215">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="8b2af-216">Fedora 28 só é suportada no PowerShell Core 6.1 e versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="8b2af-216">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="8b2af-217">Instalação através do repositório de pacotes (preferencial) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="8b2af-217">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="8b2af-218">O PowerShell Core para Linux é publicado para repositórios de Microsoft oficiais para uma instalação simples (e atualizações).</span><span class="sxs-lookup"><span data-stu-id="8b2af-218">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="8b2af-219">Instalação através de transferência direta - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="8b2af-219">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="8b2af-220">Transferir o pacote RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` partir a [versões][] página na máquina Fedora.</span><span class="sxs-lookup"><span data-stu-id="8b2af-220">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="8b2af-221">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="8b2af-221">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="8b2af-222">Também pode instalar o RPM sem a etapa intermediária de baixá-lo:</span><span class="sxs-lookup"><span data-stu-id="8b2af-222">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="8b2af-223">Desinstalação - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="8b2af-223">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="8b2af-224">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="8b2af-224">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="8b2af-225">O suporte de arquitetura é experimental.</span><span class="sxs-lookup"><span data-stu-id="8b2af-225">Arch support is experimental.</span></span>

<span data-ttu-id="8b2af-226">PowerShell está disponível a partir da [Arch Linux][] utilizador repositório (AUR).</span><span class="sxs-lookup"><span data-stu-id="8b2af-226">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="8b2af-227">Pode ser compilado com o [etiquetados de versão mais recente versão][arch-release]</span><span class="sxs-lookup"><span data-stu-id="8b2af-227">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="8b2af-228">Pode ser compilada a partir do [consolidação mais recente a mestre][arch-git]</span><span class="sxs-lookup"><span data-stu-id="8b2af-228">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="8b2af-229">Pode ser instalado utilizando o [binário da versão mais recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="8b2af-229">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="8b2af-230">Pacotes no AUR são mantida de Comunidade – não existe nenhum suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="8b2af-230">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="8b2af-231">Para obter mais informações sobre como instalar pacotes do AUR, consulte a [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) ou da Comunidade [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="8b2af-231">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="8b2af-233">AppImage do Linux</span><span class="sxs-lookup"><span data-stu-id="8b2af-233">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="8b2af-234">Suporte de AppImage é experimental</span><span class="sxs-lookup"><span data-stu-id="8b2af-234">AppImage support is experimental</span></span>

<span data-ttu-id="8b2af-235">Utilizando uma distribuição Linux recente, Baixe o AppImage `powershell-6.0.1-x86_64.AppImage` partir do [versões][] página na máquina Linux.</span><span class="sxs-lookup"><span data-stu-id="8b2af-235">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="8b2af-236">Em seguida, execute o seguinte no terminal:</span><span class="sxs-lookup"><span data-stu-id="8b2af-236">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="8b2af-237">O [AppImage][] permite-lhe executar o PowerShell sem instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="8b2af-237">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="8b2af-238">É um aplicativo portáteis que agrupa o PowerShell e as respetivas dependências (incluindo as dependências do sistema de .NET Core) num único pacote coeso.</span><span class="sxs-lookup"><span data-stu-id="8b2af-238">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="8b2af-239">Este pacote é um único binário que funciona de forma independente da distribuição de Linux do utilizador.</span><span class="sxs-lookup"><span data-stu-id="8b2af-239">This package is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="8b2af-241">Kali</span><span class="sxs-lookup"><span data-stu-id="8b2af-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="8b2af-242">O suporte de Kali é experimental.</span><span class="sxs-lookup"><span data-stu-id="8b2af-242">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="8b2af-243">Instalação</span><span class="sxs-lookup"><span data-stu-id="8b2af-243">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="8b2af-244">Executar o PowerShell sem instalá-lo no Kali mais recente (implementar Kali GNU/Linux)</span><span class="sxs-lookup"><span data-stu-id="8b2af-244">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="8b2af-245">Desinstalação - Kali</span><span class="sxs-lookup"><span data-stu-id="8b2af-245">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="8b2af-246">Raspbian</span><span class="sxs-lookup"><span data-stu-id="8b2af-246">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="8b2af-247">O suporte de Raspbian é experimental.</span><span class="sxs-lookup"><span data-stu-id="8b2af-247">Raspbian support is experimental.</span></span>

<span data-ttu-id="8b2af-248">Atualmente, o PowerShell só é suportado em Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="8b2af-248">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="8b2af-249">Também CoreCLR (e, portanto, o PowerShell Core) só funcionam em dispositivos de instalador de plataforma 2 e 3 de instalador de plataforma como outros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), ter um processador não suportado.</span><span class="sxs-lookup"><span data-stu-id="8b2af-249">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="8b2af-250">Baixe [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e siga o [instruções de instalação](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) obtê-lo em seu Pi.</span><span class="sxs-lookup"><span data-stu-id="8b2af-250">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="8b2af-251">Instalação</span><span class="sxs-lookup"><span data-stu-id="8b2af-251">Installation</span></span>

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

<span data-ttu-id="8b2af-252">Opcionalmente, pode criar um link simbólico para conseguir iniciar PowerShell sem especificar o caminho para o "pwsh" binário</span><span class="sxs-lookup"><span data-stu-id="8b2af-252">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="8b2af-253">Desinstalação - Raspbian</span><span class="sxs-lookup"><span data-stu-id="8b2af-253">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="8b2af-254">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="8b2af-254">Binary Archives</span></span>

<span data-ttu-id="8b2af-255">Binário de PowerShell `tar.gz` arquivos são fornecidos para plataformas Linux ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="8b2af-255">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="8b2af-256">Dependências</span><span class="sxs-lookup"><span data-stu-id="8b2af-256">Dependencies</span></span>

<span data-ttu-id="8b2af-257">PowerShell cria binários portátil para todas as distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="8b2af-257">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="8b2af-258">Mas o tempo de execução do .NET Core requer diferentes dependências em diversas distribuições e, por conseguinte, o PowerShell faz o mesmo.</span><span class="sxs-lookup"><span data-stu-id="8b2af-258">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="8b2af-259">O gráfico seguinte mostra as dependências de .NET Core 2.0 são suportadas oficialmente em distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="8b2af-259">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="8b2af-260">SO</span><span class="sxs-lookup"><span data-stu-id="8b2af-260">OS</span></span>                 | <span data-ttu-id="8b2af-261">Dependências</span><span class="sxs-lookup"><span data-stu-id="8b2af-261">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="8b2af-262">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="8b2af-262">Ubuntu 14.04</span></span>       | <span data-ttu-id="8b2af-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="8b2af-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="8b2af-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="8b2af-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="8b2af-265">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="8b2af-265">Ubuntu 16.04</span></span>       | <span data-ttu-id="8b2af-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="8b2af-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="8b2af-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="8b2af-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="8b2af-268">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="8b2af-268">Ubuntu 17.10</span></span>       | <span data-ttu-id="8b2af-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="8b2af-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="8b2af-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="8b2af-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="8b2af-271">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="8b2af-271">Ubuntu 18.04</span></span>       | <span data-ttu-id="8b2af-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="8b2af-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="8b2af-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="8b2af-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="8b2af-274">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="8b2af-274">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="8b2af-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="8b2af-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="8b2af-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="8b2af-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="8b2af-277">Debian 9 (Stretch.)</span><span class="sxs-lookup"><span data-stu-id="8b2af-277">Debian 9 (Stretch)</span></span> | <span data-ttu-id="8b2af-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="8b2af-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="8b2af-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="8b2af-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="8b2af-280">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="8b2af-280">CentOS 7</span></span> <br> <span data-ttu-id="8b2af-281">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="8b2af-281">Oracle Linux 7</span></span> <br> <span data-ttu-id="8b2af-282">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="8b2af-282">RHEL 7</span></span> <br> <span data-ttu-id="8b2af-283">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="8b2af-283">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="8b2af-284">libunwind, libcurl, bibliotecas de openssl, libicu</span><span class="sxs-lookup"><span data-stu-id="8b2af-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="8b2af-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="8b2af-285">Fedora 27</span></span> <br> <span data-ttu-id="8b2af-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="8b2af-286">Fedora 28</span></span> | <span data-ttu-id="8b2af-287">libunwind, libcurl, bibliotecas de openssl, libicu, openssl10 de compatibilidade</span><span class="sxs-lookup"><span data-stu-id="8b2af-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="8b2af-288">Para implementar os binários do PowerShell distribuições de Linux que não são suportados oficialmente, terá de instalar as dependências necessárias para o sistema operacional de destino nos passos separados.</span><span class="sxs-lookup"><span data-stu-id="8b2af-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="8b2af-289">Por exemplo, nossa [Amazon Linux dockerfile] [ amazon-dockerfile] instala as dependências primeiro e, em seguida, extrai a Linux `tar.gz` arquivo.</span><span class="sxs-lookup"><span data-stu-id="8b2af-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="8b2af-290">Instalação - arquivos binários</span><span class="sxs-lookup"><span data-stu-id="8b2af-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="8b2af-291">Linux</span><span class="sxs-lookup"><span data-stu-id="8b2af-291">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="8b2af-292">A desinstalar arquivos binários</span><span class="sxs-lookup"><span data-stu-id="8b2af-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="8b2af-293">Caminhos</span><span class="sxs-lookup"><span data-stu-id="8b2af-293">Paths</span></span>

* <span data-ttu-id="8b2af-294">`$PSHOME` é `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="8b2af-294">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="8b2af-295">Perfis de utilizador serão lido a partir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="8b2af-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="8b2af-296">Perfis predefinidos serão lido a partir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="8b2af-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="8b2af-297">Módulos de utilizador serão lido a partir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="8b2af-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="8b2af-298">Módulos partilhados serão lido a partir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="8b2af-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="8b2af-299">Módulos padrão serão lido a partir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="8b2af-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="8b2af-300">Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="8b2af-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="8b2af-301">Os perfis de respeitam a configuração de por anfitrião do PowerShell, para que os perfis de anfitrião específico padrão existe em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.</span><span class="sxs-lookup"><span data-stu-id="8b2af-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="8b2af-302">PowerShell respeita os [XDG Base diretório especificação] [ xdg-bds] no Linux.</span><span class="sxs-lookup"><span data-stu-id="8b2af-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
