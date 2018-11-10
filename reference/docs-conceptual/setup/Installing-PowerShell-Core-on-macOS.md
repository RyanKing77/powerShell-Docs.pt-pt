---
title: Instalar o PowerShell Core no macOS
description: Informações sobre como instalar o PowerShell Core no macOS
ms.date: 11/02/2018
ms.openlocfilehash: 162e841bf71d708e9db84ea1bb2dbef13924783b
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998508"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="fcccb-103">Instalar o PowerShell Core no macOS</span><span class="sxs-lookup"><span data-stu-id="fcccb-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="fcccb-104">O PowerShell Core suporta o macOS 10.12 e superior.</span><span class="sxs-lookup"><span data-stu-id="fcccb-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="fcccb-105">Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.</span><span class="sxs-lookup"><span data-stu-id="fcccb-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="fcccb-106">Depois do pacote está instalado, execute `pwsh` partir de um terminal.</span><span class="sxs-lookup"><span data-stu-id="fcccb-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="fcccb-107">Sobre Brew</span><span class="sxs-lookup"><span data-stu-id="fcccb-107">About Brew</span></span>

<span data-ttu-id="fcccb-108">[Homebrew] [ brew] é o Gestor de pacotes preferencial para macOS.</span><span class="sxs-lookup"><span data-stu-id="fcccb-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="fcccb-109">Se o `brew` comando não for encontrado, tem de instalar o Homebrew seguintes [suas instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="fcccb-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="fcccb-110">Instalação da versão estável mais recente através do Homebrew no macOS 10.12 ou superior</span><span class="sxs-lookup"><span data-stu-id="fcccb-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="fcccb-111">Ver [sobre Brew](#about-brew) para obter informações sobre Brew.</span><span class="sxs-lookup"><span data-stu-id="fcccb-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="fcccb-112">Agora, pode instalar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fcccb-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="fcccb-113">Por fim, certifique-se de que a instalação está a funcionar corretamente:</span><span class="sxs-lookup"><span data-stu-id="fcccb-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="fcccb-114">Quando são lançadas novas versões do PowerShell, basta atualizar viramos do Homebrew e atualize o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fcccb-114">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="fcccb-115">Os comandos acima podem ser chamados a partir de um anfitrião do PowerShell (pwsh), mas, em seguida, o shell do PowerShell tem de estar encerrado e reiniciado para concluir a atualização e atualizar os valores mostrados na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="fcccb-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="fcccb-116">Instalação de pré-visualização mais recente da versão através do Homebrew no macOS 10.12 ou superior</span><span class="sxs-lookup"><span data-stu-id="fcccb-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="fcccb-117">Ver [sobre Brew](#about-brew) para obter informações sobre Brew.</span><span class="sxs-lookup"><span data-stu-id="fcccb-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="fcccb-118">Depois de instalar o Homebrew, instalar o PowerShell é fácil.</span><span class="sxs-lookup"><span data-stu-id="fcccb-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="fcccb-119">Primeiro, instale [versões Cask] [ cask-versions] que permite-lhe instalar alternativas versões dos pacotes de cask:</span><span class="sxs-lookup"><span data-stu-id="fcccb-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="fcccb-120">Agora, pode instalar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fcccb-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="fcccb-121">Por fim, certifique-se de que a instalação está a funcionar corretamente:</span><span class="sxs-lookup"><span data-stu-id="fcccb-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="fcccb-122">Quando são lançadas novas versões do PowerShell, basta atualizar viramos do Homebrew e atualize o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fcccb-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="fcccb-123">Os comandos acima podem ser chamados a partir de um anfitrião do PowerShell (pwsh), mas, em seguida, o shell do PowerShell tem de estar encerrado e reiniciado para concluir a atualização.</span><span class="sxs-lookup"><span data-stu-id="fcccb-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="fcccb-124">e atualize os valores mostrados na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="fcccb-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="fcccb-125">Instalação através de transferência direta</span><span class="sxs-lookup"><span data-stu-id="fcccb-125">Installation via Direct Download</span></span>

<span data-ttu-id="fcccb-126">Transferir o pacote PKG `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="fcccb-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="fcccb-127">partir do [versões][] página no seu computador macOS.</span><span class="sxs-lookup"><span data-stu-id="fcccb-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="fcccb-128">Pode clicar duas vezes o arquivo e siga as instruções ou instalá-lo a partir do terminal:</span><span class="sxs-lookup"><span data-stu-id="fcccb-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="fcccb-129">Instale [OpenSSL](#install-openssl) como isto é necessário para operações de CIM e de comunicação remota do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fcccb-129">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="fcccb-130">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="fcccb-130">Binary Archives</span></span>

<span data-ttu-id="fcccb-131">Binário de PowerShell `tar.gz` arquivos são fornecidos para a plataforma macOS ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="fcccb-131">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="fcccb-132">Instalar arquivos binários em macOS</span><span class="sxs-lookup"><span data-stu-id="fcccb-132">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.1.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="fcccb-133">Instale [OpenSSL](#install-openssl) como isto é necessário para operações de CIM e de comunicação remota do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fcccb-133">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="fcccb-134">Instalação de dependências</span><span class="sxs-lookup"><span data-stu-id="fcccb-134">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="fcccb-135">Instalar as ferramentas de linha de comandos do XCode</span><span class="sxs-lookup"><span data-stu-id="fcccb-135">Install XCode command line tools</span></span>

```shell
xcode-select -install
```

### <a name="install-openssl"></a><span data-ttu-id="fcccb-136">Instalar o OpenSSL</span><span class="sxs-lookup"><span data-stu-id="fcccb-136">Install OpenSSL</span></span>

<span data-ttu-id="fcccb-137">OpenSSL é necessário para comunicação remota do PowerShell e as operações de CIM.</span><span class="sxs-lookup"><span data-stu-id="fcccb-137">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>  <span data-ttu-id="fcccb-138">Pode instalar via MacPorts ou Brew.</span><span class="sxs-lookup"><span data-stu-id="fcccb-138">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="fcccb-139">Instalar o OpenSSL via Brew</span><span class="sxs-lookup"><span data-stu-id="fcccb-139">Install OpenSSL via Brew</span></span>

<span data-ttu-id="fcccb-140">Ver [sobre Brew](#about-brew) para obter informações sobre Brew.</span><span class="sxs-lookup"><span data-stu-id="fcccb-140">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="fcccb-141">Executar `brew install openssl` para instalar o OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="fcccb-141">Run `brew install openssl` to install OpenSSL.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="fcccb-142">Instalar o OpenSSL via MacPorts</span><span class="sxs-lookup"><span data-stu-id="fcccb-142">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="fcccb-143">Instal o [ferramentas de linha de comandos do XCode](#install-xcode-command-line-tools)</span><span class="sxs-lookup"><span data-stu-id="fcccb-143">Instal the [XCode command line tools](#install-xcode-command-line-tools)</span></span>
1. <span data-ttu-id="fcccb-144">Instale MacPorts.</span><span class="sxs-lookup"><span data-stu-id="fcccb-144">Install MacPorts.</span></span>
   <span data-ttu-id="fcccb-145">Consulte a [guia de instalação](https://guide.macports.org/chunked/installing.macports.html) se precisar de instruções.</span><span class="sxs-lookup"><span data-stu-id="fcccb-145">See the [installation guide](https://guide.macports.org/chunked/installing.macports.html) if you need instructions.</span></span>
1. <span data-ttu-id="fcccb-146">Atualizar MacPorts através da execução `sudo port selfupdate`</span><span class="sxs-lookup"><span data-stu-id="fcccb-146">Update MacPorts by running `sudo port selfupdate`</span></span>
1. <span data-ttu-id="fcccb-147">Pacotes de atualização do MacPorts através da execução `sudo port upgrade outdated`</span><span class="sxs-lookup"><span data-stu-id="fcccb-147">Upgrade MacPorts packages by running `sudo port upgrade outdated`</span></span>
1. <span data-ttu-id="fcccb-148">Instalar o OpenSSL sendo executada através da execução `sudo port instal openssl`</span><span class="sxs-lookup"><span data-stu-id="fcccb-148">Install OpenSSL by running by running `sudo port instal openssl`</span></span>
1. <span data-ttu-id="fcccb-149">As bibliotecas de uma ligação para que o PowerShell pode utilizá-lo.</span><span class="sxs-lookup"><span data-stu-id="fcccb-149">Link the libraries so that PowerShell can use it.</span></span>

```shell
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="fcccb-150">Desinstalar o PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="fcccb-150">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="fcccb-151">Se tiver instalado o PowerShell com o Homebrew, desinstalação é fácil:</span><span class="sxs-lookup"><span data-stu-id="fcccb-151">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="fcccb-152">Se tiver instalado o PowerShell através de transferência direta, PowerShell têm de ser removido manualmente:</span><span class="sxs-lookup"><span data-stu-id="fcccb-152">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="fcccb-153">Para remover os caminhos de PowerShell adicionais, consulte a [caminhos](#paths) secção deste documento e remover o desejado os caminhos com `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="fcccb-153">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="fcccb-154">Isso não é necessário se tiver instalado com o Homebrew.</span><span class="sxs-lookup"><span data-stu-id="fcccb-154">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="fcccb-155">Caminhos</span><span class="sxs-lookup"><span data-stu-id="fcccb-155">Paths</span></span>

* <span data-ttu-id="fcccb-156">`$PSHOME` é `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="fcccb-156">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="fcccb-157">Perfis de utilizador serão lido a partir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="fcccb-157">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="fcccb-158">Perfis predefinidos serão lido a partir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="fcccb-158">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="fcccb-159">Módulos de utilizador serão lido a partir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="fcccb-159">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="fcccb-160">Módulos partilhados serão lido a partir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="fcccb-160">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="fcccb-161">Módulos padrão serão lido a partir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="fcccb-161">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="fcccb-162">Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="fcccb-162">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="fcccb-163">Os perfis de respeitam a configuração de por anfitrião do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fcccb-163">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="fcccb-164">Para que os perfis de anfitrião específico padrão existe em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.</span><span class="sxs-lookup"><span data-stu-id="fcccb-164">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="fcccb-165">PowerShell respeita os [XDG Base diretório especificação] [ xdg-bds] em macOS.</span><span class="sxs-lookup"><span data-stu-id="fcccb-165">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="fcccb-166">Uma vez que macOS é uma derivação do BSD, o prefixo `/usr/local` é utilizado em vez de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="fcccb-166">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="fcccb-167">Por isso, `$PSHOME` é `/usr/local/microsoft/powershell/6.1.0/`, e a ligação simbólica é colocada em `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="fcccb-167">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="fcccb-168">Recursos Adicionais</span><span class="sxs-lookup"><span data-stu-id="fcccb-168">Additional Resources</span></span>

* <span data-ttu-id="fcccb-169">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="fcccb-169">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="fcccb-170">[Repositório do Github Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="fcccb-170">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="fcccb-171">[Homebrew Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="fcccb-171">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
