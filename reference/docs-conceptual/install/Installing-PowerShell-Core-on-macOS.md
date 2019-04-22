---
title: Instalar o PowerShell Core no macOS
description: Informações sobre como instalar o PowerShell Core no macOS
ms.date: 12/12/2018
ms.openlocfilehash: 7db8ca0cb6d13db8ce7f11b4a4b03b7d3f9b6feb
ms.sourcegitcommit: 17ce42f97e13e8b3286779dc3f583474b0357023
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/18/2019
ms.locfileid: "59293406"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="66be2-103">Instalar o PowerShell Core no macOS</span><span class="sxs-lookup"><span data-stu-id="66be2-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="66be2-104">O PowerShell Core suporta o macOS 10.12 e superior.</span><span class="sxs-lookup"><span data-stu-id="66be2-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="66be2-105">Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.</span><span class="sxs-lookup"><span data-stu-id="66be2-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="66be2-106">Depois do pacote está instalado, executar `pwsh` partir de um terminal.</span><span class="sxs-lookup"><span data-stu-id="66be2-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="66be2-107">Sobre Brew</span><span class="sxs-lookup"><span data-stu-id="66be2-107">About Brew</span></span>

<span data-ttu-id="66be2-108">[Homebrew] [ brew] é o Gestor de pacotes preferencial para macOS.</span><span class="sxs-lookup"><span data-stu-id="66be2-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="66be2-109">Se o `brew` comando não for encontrado, tem de instalar o Homebrew seguintes [suas instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="66be2-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="66be2-110">Instalação da versão estável mais recente através do Homebrew no macOS 10.12 ou superior</span><span class="sxs-lookup"><span data-stu-id="66be2-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="66be2-111">Ver [sobre Brew](#about-brew) para obter informações sobre Brew.</span><span class="sxs-lookup"><span data-stu-id="66be2-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="66be2-112">Agora, pode instalar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="66be2-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="66be2-113">Por fim, certifique-se de que a instalação está a funcionar corretamente:</span><span class="sxs-lookup"><span data-stu-id="66be2-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="66be2-114">Quando são lançadas novas versões do PowerShell, atualize viramos do Homebrew e atualize o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="66be2-114">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="66be2-115">Os comandos acima podem ser chamados a partir de um anfitrião do PowerShell (pwsh), mas, em seguida, o shell do PowerShell tem de estar encerrado e reiniciado para concluir a atualização e atualizar os valores mostrados na `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="66be2-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="66be2-116">Instalação de pré-visualização mais recente da versão através do Homebrew no macOS 10.12 ou superior</span><span class="sxs-lookup"><span data-stu-id="66be2-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="66be2-117">Ver [sobre Brew](#about-brew) para obter informações sobre Brew.</span><span class="sxs-lookup"><span data-stu-id="66be2-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="66be2-118">Depois de instalar o Homebrew, pode instalar o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66be2-118">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="66be2-119">Primeiro, instale o [versões Cask] [ cask-versions] pacote que permite instalar alternativas versões dos pacotes de cask:</span><span class="sxs-lookup"><span data-stu-id="66be2-119">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="66be2-120">Agora, pode instalar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="66be2-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="66be2-121">Por fim, certifique-se de que a instalação está a funcionar corretamente:</span><span class="sxs-lookup"><span data-stu-id="66be2-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="66be2-122">Quando são lançadas novas versões do PowerShell, atualize viramos do Homebrew e atualize o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="66be2-122">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="66be2-123">Os comandos acima podem ser chamados a partir de um anfitrião do PowerShell (pwsh), mas, em seguida, o shell do PowerShell tem de estar encerrado e reiniciado para concluir a atualização.</span><span class="sxs-lookup"><span data-stu-id="66be2-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="66be2-124">e atualize os valores mostrados na `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="66be2-124">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="66be2-125">Instalação através de transferência direta</span><span class="sxs-lookup"><span data-stu-id="66be2-125">Installation via Direct Download</span></span>

<span data-ttu-id="66be2-126">Transferir o pacote PKG `powershell-6.2.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="66be2-126">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="66be2-127">partir do [versões][] página no seu computador macOS.</span><span class="sxs-lookup"><span data-stu-id="66be2-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="66be2-128">Pode clicar duas vezes o arquivo e siga as instruções ou instalá-lo a partir do terminal:</span><span class="sxs-lookup"><span data-stu-id="66be2-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="66be2-129">Instale [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="66be2-129">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="66be2-130">OpenSSL é necessário para comunicação remota do PowerShell e as operações de CIM.</span><span class="sxs-lookup"><span data-stu-id="66be2-130">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="66be2-131">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="66be2-131">Binary Archives</span></span>

<span data-ttu-id="66be2-132">Binário de PowerShell `tar.gz` arquivos são fornecidos para a plataforma macOS ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="66be2-132">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="66be2-133">Instalar arquivos binários em macOS</span><span class="sxs-lookup"><span data-stu-id="66be2-133">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.2.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="66be2-134">Instale [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="66be2-134">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="66be2-135">OpenSSL é necessário para comunicação remota do PowerShell e as operações de CIM.</span><span class="sxs-lookup"><span data-stu-id="66be2-135">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="66be2-136">Instalação de dependências</span><span class="sxs-lookup"><span data-stu-id="66be2-136">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="66be2-137">Instalar as ferramentas de linha de comandos do XCode</span><span class="sxs-lookup"><span data-stu-id="66be2-137">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="66be2-138">Instalar o OpenSSL</span><span class="sxs-lookup"><span data-stu-id="66be2-138">Install OpenSSL</span></span>

<span data-ttu-id="66be2-139">OpenSSL é necessário para comunicação remota do PowerShell e as operações de CIM.</span><span class="sxs-lookup"><span data-stu-id="66be2-139">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="66be2-140">Pode instalar via MacPorts ou Brew.</span><span class="sxs-lookup"><span data-stu-id="66be2-140">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="66be2-141">Instalar o OpenSSL via Brew</span><span class="sxs-lookup"><span data-stu-id="66be2-141">Install OpenSSL via Brew</span></span>

<span data-ttu-id="66be2-142">Ver [sobre Brew](#about-brew) para obter informações sobre Brew.</span><span class="sxs-lookup"><span data-stu-id="66be2-142">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="66be2-143">Para instalar o OpenSSL, execute `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="66be2-143">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="66be2-144">Instalar o OpenSSL via MacPorts</span><span class="sxs-lookup"><span data-stu-id="66be2-144">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="66be2-145">Instalar o [ferramentas de linha de comandos do XCode](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="66be2-145">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="66be2-146">Instale MacPorts.</span><span class="sxs-lookup"><span data-stu-id="66be2-146">Install MacPorts.</span></span>
   <span data-ttu-id="66be2-147">Se precisar de instruções, consulte a [guia de instalação](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="66be2-147">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="66be2-148">Atualizar MacPorts executando `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="66be2-148">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="66be2-149">Atualizar pacotes de MacPorts executando `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="66be2-149">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="66be2-150">Instalar o OpenSSL executando `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="66be2-150">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="66be2-151">Ligar as bibliotecas para que fiquem disponíveis para o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="66be2-151">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="66be2-152">Desinstalar o PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="66be2-152">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="66be2-153">Se tiver instalado o PowerShell com o Homebrew, utilize o seguinte comando para desinstalar:</span><span class="sxs-lookup"><span data-stu-id="66be2-153">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="66be2-154">Se tiver instalado o PowerShell através de transferência direta, PowerShell têm de ser removido manualmente:</span><span class="sxs-lookup"><span data-stu-id="66be2-154">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="66be2-155">Para remover os caminhos de PowerShell adicionais, consulte a [caminhos](#paths) secção deste documento e remover os caminhos com `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="66be2-155">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="66be2-156">Isso não é necessário se tiver instalado com o Homebrew.</span><span class="sxs-lookup"><span data-stu-id="66be2-156">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="66be2-157">Caminhos</span><span class="sxs-lookup"><span data-stu-id="66be2-157">Paths</span></span>

* <span data-ttu-id="66be2-158">`$PSHOME` é `/usr/local/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="66be2-158">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="66be2-159">Perfis de utilizador serão lido a partir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="66be2-159">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="66be2-160">Perfis predefinidos serão lido a partir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="66be2-160">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="66be2-161">Módulos de utilizador serão lido a partir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="66be2-161">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="66be2-162">Módulos partilhados serão lido a partir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="66be2-162">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="66be2-163">Módulos padrão serão lido a partir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="66be2-163">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="66be2-164">Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="66be2-164">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="66be2-165">Os perfis de respeitam a configuração de por anfitrião do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66be2-165">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="66be2-166">Para que o perfil de anfitrião específico predefinido existe em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.</span><span class="sxs-lookup"><span data-stu-id="66be2-166">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="66be2-167">PowerShell respeita os [XDG Base diretório especificação] [ xdg-bds] em macOS.</span><span class="sxs-lookup"><span data-stu-id="66be2-167">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="66be2-168">Uma vez que macOS é uma derivação do BSD, o prefixo `/usr/local` é utilizado em vez de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="66be2-168">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="66be2-169">Por isso, `$PSHOME` é `/usr/local/microsoft/powershell/6.2.0/`, e a ligação simbólica é colocada em `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="66be2-169">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="66be2-170">Recursos Adicionais</span><span class="sxs-lookup"><span data-stu-id="66be2-170">Additional Resources</span></span>

* <span data-ttu-id="66be2-171">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="66be2-171">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="66be2-172">[Repositório do Github Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="66be2-172">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="66be2-173">[Homebrew Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="66be2-173">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
