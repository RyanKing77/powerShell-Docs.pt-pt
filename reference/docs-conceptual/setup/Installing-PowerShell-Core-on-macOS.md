---
title: Instalar o PowerShell Core no macOS
description: Informações sobre como instalar o PowerShell Core no macOS
ms.date: 08/06/2018
ms.openlocfilehash: e226cd64f8788ae74dc72fdc0cd219923b7a2cd6
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002364"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="a7d46-103">Instalar o PowerShell Core no macOS</span><span class="sxs-lookup"><span data-stu-id="a7d46-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="a7d46-104">O PowerShell Core suporta o macOS 10.12 e superior.</span><span class="sxs-lookup"><span data-stu-id="a7d46-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="a7d46-105">Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.</span><span class="sxs-lookup"><span data-stu-id="a7d46-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="a7d46-106">Depois do pacote está instalado, execute `pwsh` partir de um terminal.</span><span class="sxs-lookup"><span data-stu-id="a7d46-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="a7d46-107">Instalação da versão estável mais recente através do Homebrew no macOS 10.12 ou superior</span><span class="sxs-lookup"><span data-stu-id="a7d46-107">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="a7d46-108">[Homebrew] [ brew] é o Gestor de pacotes preferencial para macOS.</span><span class="sxs-lookup"><span data-stu-id="a7d46-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="a7d46-109">Se o `brew` comando não for encontrado, tem de instalar o Homebrew seguintes [suas instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="a7d46-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="a7d46-110">Agora, pode instalar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a7d46-110">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="a7d46-111">Por fim, certifique-se de que a instalação está a funcionar corretamente:</span><span class="sxs-lookup"><span data-stu-id="a7d46-111">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="a7d46-112">Quando são lançadas novas versões do PowerShell, basta atualizar viramos do Homebrew e atualize o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a7d46-112">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="a7d46-113">Os comandos acima podem ser chamados a partir de um anfitrião do PowerShell (pwsh), mas, em seguida, o shell do PowerShell tem de estar encerrado e reiniciado para concluir a atualização e atualizar os valores mostrados na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="a7d46-113">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="a7d46-114">Instalação de pré-visualização mais recente da versão através do Homebrew no macOS 10.12 ou superior</span><span class="sxs-lookup"><span data-stu-id="a7d46-114">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="a7d46-115">[Homebrew] [ brew] é o Gestor de pacotes preferencial para macOS.</span><span class="sxs-lookup"><span data-stu-id="a7d46-115">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="a7d46-116">Se o `brew` comando não for encontrado, tem de instalar o Homebrew seguintes [suas instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="a7d46-116">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="a7d46-117">Depois de instalar o Homebrew, instalar o PowerShell é fácil.</span><span class="sxs-lookup"><span data-stu-id="a7d46-117">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="a7d46-118">Primeiro, instale [versões Cask] [ cask-versions] que permite-lhe instalar alternativas versões dos pacotes de cask:</span><span class="sxs-lookup"><span data-stu-id="a7d46-118">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="a7d46-119">Agora, pode instalar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a7d46-119">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="a7d46-120">Por fim, certifique-se de que a instalação está a funcionar corretamente:</span><span class="sxs-lookup"><span data-stu-id="a7d46-120">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="a7d46-121">Quando são lançadas novas versões do PowerShell, basta atualizar viramos do Homebrew e atualize o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a7d46-121">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="a7d46-122">Os comandos acima podem ser chamados a partir de um anfitrião do PowerShell (pwsh), mas, em seguida, o shell do PowerShell tem de estar encerrado e reiniciado para concluir a atualização.</span><span class="sxs-lookup"><span data-stu-id="a7d46-122">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="a7d46-123">e atualize os valores mostrados na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="a7d46-123">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="a7d46-124">Instalação através de transferência direta</span><span class="sxs-lookup"><span data-stu-id="a7d46-124">Installation via Direct Download</span></span>

<span data-ttu-id="a7d46-125">Transferir o pacote PKG `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="a7d46-125">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="a7d46-126">partir do [versões][] página no seu computador macOS.</span><span class="sxs-lookup"><span data-stu-id="a7d46-126">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="a7d46-127">Pode clicar duas vezes o arquivo e siga as instruções ou instalá-lo a partir do terminal:</span><span class="sxs-lookup"><span data-stu-id="a7d46-127">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="a7d46-128">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="a7d46-128">Binary Archives</span></span>

<span data-ttu-id="a7d46-129">Binário de PowerShell `tar.gz` arquivos são fornecidos para a plataforma macOS ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="a7d46-129">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="a7d46-130">Instalar arquivos binários em macOS</span><span class="sxs-lookup"><span data-stu-id="a7d46-130">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="a7d46-131">Desinstalar o PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="a7d46-131">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="a7d46-132">Se tiver instalado o PowerShell com o Homebrew, desinstalação é fácil:</span><span class="sxs-lookup"><span data-stu-id="a7d46-132">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="a7d46-133">Se tiver instalado o PowerShell através de transferência direta, PowerShell têm de ser removido manualmente:</span><span class="sxs-lookup"><span data-stu-id="a7d46-133">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="a7d46-134">Para remover os caminhos de PowerShell adicionais, consulte a [caminhos](#paths) secção deste documento e remover o desejado os caminhos com `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="a7d46-134">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="a7d46-135">Isso não é necessário se tiver instalado com o Homebrew.</span><span class="sxs-lookup"><span data-stu-id="a7d46-135">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="a7d46-136">Caminhos</span><span class="sxs-lookup"><span data-stu-id="a7d46-136">Paths</span></span>

* <span data-ttu-id="a7d46-137">`$PSHOME` é `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="a7d46-137">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="a7d46-138">Perfis de utilizador serão lido a partir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="a7d46-138">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="a7d46-139">Perfis predefinidos serão lido a partir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="a7d46-139">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="a7d46-140">Módulos de utilizador serão lido a partir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="a7d46-140">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="a7d46-141">Módulos partilhados serão lido a partir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="a7d46-141">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="a7d46-142">Módulos padrão serão lido a partir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="a7d46-142">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="a7d46-143">Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="a7d46-143">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="a7d46-144">Os perfis de respeitam a configuração de por anfitrião do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7d46-144">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="a7d46-145">Para que os perfis de anfitrião específico padrão existe em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.</span><span class="sxs-lookup"><span data-stu-id="a7d46-145">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="a7d46-146">PowerShell respeita os [XDG Base diretório especificação] [ xdg-bds] em macOS.</span><span class="sxs-lookup"><span data-stu-id="a7d46-146">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="a7d46-147">Uma vez que macOS é uma derivação do BSD, o prefixo `/usr/local` é utilizado em vez de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="a7d46-147">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="a7d46-148">Por isso, `$PSHOME` é `/usr/local/microsoft/powershell/6.1.0/`, e o symlink é colocado em `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="a7d46-148">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a7d46-149">Recursos Adicionais</span><span class="sxs-lookup"><span data-stu-id="a7d46-149">Additional Resources</span></span>

* <span data-ttu-id="a7d46-150">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="a7d46-150">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="a7d46-151">[Repositório do Github Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="a7d46-151">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="a7d46-152">[Homebrew Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="a7d46-152">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
