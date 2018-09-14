---
title: Instalar o PowerShell Core no macOS
description: Informações sobre como instalar o PowerShell Core no macOS
ms.date: 08/06/2018
ms.openlocfilehash: 50b8dbbf26f02580e4be45978c926d5337da6b63
ms.sourcegitcommit: b235c58b34d23317076540631f5cf83f1f309c0d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45557165"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="450bf-103">Instalar o PowerShell Core no macOS</span><span class="sxs-lookup"><span data-stu-id="450bf-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="450bf-104">O PowerShell Core suporta o macOS 10.12 e superior.</span><span class="sxs-lookup"><span data-stu-id="450bf-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="450bf-105">Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.</span><span class="sxs-lookup"><span data-stu-id="450bf-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="450bf-106">Depois do pacote está instalado, execute `pwsh` partir de um terminal.</span><span class="sxs-lookup"><span data-stu-id="450bf-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="450bf-107">Instalação de pré-visualização mais recente da versão através do Homebrew no macOS 10.12 ou superior</span><span class="sxs-lookup"><span data-stu-id="450bf-107">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="450bf-108">[Homebrew] [ brew] é o Gestor de pacotes preferencial para macOS.</span><span class="sxs-lookup"><span data-stu-id="450bf-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="450bf-109">Se o `brew` comando não for encontrado, tem de instalar o Homebrew seguintes [suas instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="450bf-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="450bf-110">Depois de instalar o Homebrew, instalar o PowerShell é fácil.</span><span class="sxs-lookup"><span data-stu-id="450bf-110">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="450bf-111">Primeiro, instale [Homebrew-Cask][cask], por isso, pode instalar mais pacotes e instalar [Cask-versões] [cask-version], que lhe permite instalar alternativas versões dos pacotes:</span><span class="sxs-lookup"><span data-stu-id="450bf-111">First, install [Homebrew-Cask][cask], so you can install more packages and install [Cask-Versions][cask-version] which lets you install alternative versions of packages:</span></span>

```sh
brew tap caskroom/cask
brew tap caskroom/versions
```

<span data-ttu-id="450bf-112">Agora, pode instalar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="450bf-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="450bf-113">Por fim, certifique-se de que a instalação está a funcionar corretamente:</span><span class="sxs-lookup"><span data-stu-id="450bf-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="450bf-114">Quando são lançadas novas versões do PowerShell, basta atualizar viramos do Homebrew e atualize o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="450bf-114">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="450bf-115">Os comandos acima podem ser chamados a partir de um anfitrião do PowerShell (pwsh), mas, em seguida, o shell do PowerShell tem de estar encerrado e reiniciado para concluir a atualização.</span><span class="sxs-lookup"><span data-stu-id="450bf-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="450bf-116">e atualize os valores mostrados na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="450bf-116">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions

### <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="450bf-117">Instalação de pré-visualização mais recente da versão através do Homebrew no macOS 10.12 ou superior</span><span class="sxs-lookup"><span data-stu-id="450bf-117">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="450bf-118">[Homebrew] [ brew] é o Gestor de pacotes preferencial para macOS.</span><span class="sxs-lookup"><span data-stu-id="450bf-118">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="450bf-119">Se o `brew` comando não for encontrado, tem de instalar o Homebrew seguintes [suas instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="450bf-119">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="450bf-120">Depois de instalar o Homebrew, instalar o PowerShell é fácil.</span><span class="sxs-lookup"><span data-stu-id="450bf-120">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="450bf-121">Primeiro, instale [Homebrew-Cask][cask], por isso, pode instalar mais pacotes e instalar [Cask-versões] [cask-version], que lhe permite instalar alternativas versões dos pacotes:</span><span class="sxs-lookup"><span data-stu-id="450bf-121">First, install [Homebrew-Cask][cask], so you can install more packages and install [Cask-Versions][cask-version] which lets you install alternative versions of packages:</span></span>

```sh
brew tap caskroom/cask
brew tap caskroom/versions
```

<span data-ttu-id="450bf-122">Agora, pode instalar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="450bf-122">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="450bf-123">Por fim, certifique-se de que a instalação está a funcionar corretamente:</span><span class="sxs-lookup"><span data-stu-id="450bf-123">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="450bf-124">Quando são lançadas novas versões do PowerShell, basta atualizar viramos do Homebrew e atualize o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="450bf-124">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="450bf-125">Os comandos acima podem ser chamados a partir de um anfitrião do PowerShell (pwsh), mas, em seguida, o shell do PowerShell tem de estar encerrado e reiniciado para concluir a atualização.</span><span class="sxs-lookup"><span data-stu-id="450bf-125">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="450bf-126">e atualize os valores mostrados na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="450bf-126">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions

### <a name="installation-via-direct-download"></a><span data-ttu-id="450bf-127">Instalação através de transferência direta</span><span class="sxs-lookup"><span data-stu-id="450bf-127">Installation via Direct Download</span></span>

<span data-ttu-id="450bf-128">Transferir o pacote PKG `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="450bf-128">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="450bf-129">partir do [versões][] página no seu computador macOS.</span><span class="sxs-lookup"><span data-stu-id="450bf-129">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="450bf-130">Pode clicar duas vezes o arquivo e siga as instruções ou instalá-lo a partir do terminal:</span><span class="sxs-lookup"><span data-stu-id="450bf-130">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="450bf-131">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="450bf-131">Binary Archives</span></span>

<span data-ttu-id="450bf-132">Binário de PowerShell `tar.gz` arquivos são fornecidos para macOS e Linux plataformas para ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="450bf-132">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="450bf-133">Instalar arquivos binários em macOS</span><span class="sxs-lookup"><span data-stu-id="450bf-133">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="450bf-134">Desinstalar o PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="450bf-134">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="450bf-135">Se tiver instalado o PowerShell com o Homebrew, desinstalação é fácil:</span><span class="sxs-lookup"><span data-stu-id="450bf-135">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="450bf-136">Se tiver instalado o PowerShell através de transferência direta, PowerShell têm de ser removido manualmente:</span><span class="sxs-lookup"><span data-stu-id="450bf-136">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="450bf-137">Para remover os caminhos de PowerShell adicionais, consulte a [caminhos][] secção deste documento e remover o desejado os caminhos com `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="450bf-137">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="450bf-138">Isso não é necessário se tiver instalado com o Homebrew.</span><span class="sxs-lookup"><span data-stu-id="450bf-138">This is not necessary if you installed with Homebrew.</span></span>

[Caminhos]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="450bf-140">Caminhos</span><span class="sxs-lookup"><span data-stu-id="450bf-140">Paths</span></span>

* <span data-ttu-id="450bf-141">`$PSHOME` é `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="450bf-141">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="450bf-142">Perfis de utilizador serão lido a partir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="450bf-142">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="450bf-143">Perfis predefinidos serão lido a partir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="450bf-143">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="450bf-144">Módulos de utilizador serão lido a partir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="450bf-144">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="450bf-145">Módulos partilhados serão lido a partir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="450bf-145">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="450bf-146">Módulos padrão serão lido a partir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="450bf-146">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="450bf-147">Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="450bf-147">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="450bf-148">Os perfis de respeitam a configuração de por anfitrião do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="450bf-148">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="450bf-149">Para que os perfis de anfitrião específico padrão existe em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.</span><span class="sxs-lookup"><span data-stu-id="450bf-149">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="450bf-150">PowerShell respeita os [XDG Base diretório especificação] [ xdg-bds] em macOS.</span><span class="sxs-lookup"><span data-stu-id="450bf-150">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="450bf-151">Uma vez que macOS é uma derivação do BSD, o prefixo `/usr/local` é utilizado em vez de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="450bf-151">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="450bf-152">Por isso, `$PSHOME` é `/usr/local/microsoft/powershell/6.1.0/`, e o symlink é colocado em `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="450bf-152">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="450bf-153">Recursos Adicionais</span><span class="sxs-lookup"><span data-stu-id="450bf-153">Additional Resources</span></span>

* <span data-ttu-id="450bf-154">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="450bf-154">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="450bf-155">[Repositório do Github Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="450bf-155">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="450bf-156">[Homebrew Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="450bf-156">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
