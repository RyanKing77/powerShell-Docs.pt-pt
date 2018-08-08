---
title: Instalar o PowerShell Core no macOS
description: Informações sobre como instalar o PowerShell Core no macOS
ms.date: 08/06/2018
ms.openlocfilehash: ff1814d95b3ca3fa8497069dff249fd2ad5576ef
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587470"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="20f79-103">Instalar o PowerShell Core no macOS</span><span class="sxs-lookup"><span data-stu-id="20f79-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="20f79-104">O PowerShell Core suporta o macOS 10.12 e superior.</span><span class="sxs-lookup"><span data-stu-id="20f79-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="20f79-105">Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.</span><span class="sxs-lookup"><span data-stu-id="20f79-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="20f79-106">Depois do pacote está instalado, execute `pwsh` partir de um terminal.</span><span class="sxs-lookup"><span data-stu-id="20f79-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="20f79-107">Instalação através do Homebrew no macOS 10.12 +</span><span class="sxs-lookup"><span data-stu-id="20f79-107">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="20f79-108">[Homebrew] [ brew] é o Gestor de pacotes preferencial para macOS.</span><span class="sxs-lookup"><span data-stu-id="20f79-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="20f79-109">A partir de uma janela de terminal, escreva `brew` para executar o Homebrew.</span><span class="sxs-lookup"><span data-stu-id="20f79-109">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="20f79-110">Se o `brew` comando não for encontrado, tem de instalar o Homebrew seguintes [suas instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="20f79-110">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="20f79-111">Se tiver instalado o Homebrew no passado, é sempre uma boa idéia para executar "update-reposição brew" & & 'brew update'.</span><span class="sxs-lookup"><span data-stu-id="20f79-111">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="20f79-112">Versões mais antigas do Homebrew utilizado o toque em "caskroom/cask', que foi preterido e fizemos a migração para o homebrew/cask.</span><span class="sxs-lookup"><span data-stu-id="20f79-112">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="20f79-113">Obter mais informações podem ser encontradas em [Homebrew-cask][cask].</span><span class="sxs-lookup"><span data-stu-id="20f79-113">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="20f79-114">Utilize o comando de "brew toque" para listar os taps atual.</span><span class="sxs-lookup"><span data-stu-id="20f79-114">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="20f79-115">Se vir "caskroom/cask" pode usar a 'atualização brew' ter Homebrew migrar os toques.</span><span class="sxs-lookup"><span data-stu-id="20f79-115">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="20f79-116">Depois de instalado/atualizou o Homebrew, instalar o PowerShell é fácil.</span><span class="sxs-lookup"><span data-stu-id="20f79-116">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="20f79-117">Para instalar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="20f79-117">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="20f79-118">Por fim, certifique-se de que a instalação está a funcionar corretamente:</span><span class="sxs-lookup"><span data-stu-id="20f79-118">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="20f79-119">Para sair do PowerShell e retornar para bash, utilize o comando de "saída".</span><span class="sxs-lookup"><span data-stu-id="20f79-119">To exit PowerShell, and return to bash, use the 'exit' command.</span></span>
```sh
exit
```

<span data-ttu-id="20f79-120">Quando são lançadas novas versões do PowerShell, basta atualizar viramos do Homebrew e atualize o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="20f79-120">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="20f79-121">Os comandos acima podem ser chamados a partir de um anfitrião do PowerShell (pwsh), mas, em seguida, o shell do PowerShell tem de estar encerrado e reiniciado para concluir a atualização e atualizar os valores mostrados na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="20f79-121">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="20f79-122">Instalar a pré-visualização através do Homebrew no macOS 10.12 +</span><span class="sxs-lookup"><span data-stu-id="20f79-122">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="20f79-123">[Homebrew] [ brew] é o Gestor de pacotes preferencial para macOS.</span><span class="sxs-lookup"><span data-stu-id="20f79-123">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="20f79-124">A partir de uma janela de terminal, escreva `brew` para executar o Homebrew.</span><span class="sxs-lookup"><span data-stu-id="20f79-124">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="20f79-125">Se o `brew` comando não for encontrado, tem de instalar o Homebrew seguintes [suas instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="20f79-125">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="20f79-126">Se tiver instalado o Homebrew no passado, é sempre uma boa idéia para executar "update-reposição brew" & & 'brew update'.</span><span class="sxs-lookup"><span data-stu-id="20f79-126">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="20f79-127">Em seguida, pressione a `versions` repositório casks para obter o pacote de pré-visualização:</span><span class="sxs-lookup"><span data-stu-id="20f79-127">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="20f79-128">Para instalar a pré-visualização do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="20f79-128">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="20f79-129">Por fim, certifique-se de que a instalação está a funcionar corretamente:</span><span class="sxs-lookup"><span data-stu-id="20f79-129">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="20f79-130">Quando são lançadas novas versões do PowerShell, basta atualizar viramos do Homebrew e atualizar pré-visualização do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="20f79-130">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="20f79-131">Os comandos acima podem ser chamados a partir de um anfitrião do PowerShell (pwsh), mas, em seguida, o shell do PowerShell tem de estar encerrado e reiniciado para concluir a atualização e atualizar os valores mostrados na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="20f79-131">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="20f79-132">Instalação através de transferência direta</span><span class="sxs-lookup"><span data-stu-id="20f79-132">Installation via Direct Download</span></span>

<span data-ttu-id="20f79-133">Transferir o pacote PKG `powershell-6.0.2-osx.10.12-x64.pkg` partir do [versões][] página no seu computador macOS.</span><span class="sxs-lookup"><span data-stu-id="20f79-133">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="20f79-134">Pode clicar duas vezes o arquivo e siga as instruções ou instalá-lo a partir do terminal:</span><span class="sxs-lookup"><span data-stu-id="20f79-134">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="20f79-135">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="20f79-135">Binary Archives</span></span>

<span data-ttu-id="20f79-136">Binário de PowerShell `tar.gz` arquivos são fornecidos para macOS e Linux plataformas para ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="20f79-136">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="20f79-137">Instalar arquivos binários em macOS</span><span class="sxs-lookup"><span data-stu-id="20f79-137">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="20f79-138">Desinstalar o PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="20f79-138">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="20f79-139">Se tiver instalado o PowerShell com o Homebrew, desinstalação é fácil:</span><span class="sxs-lookup"><span data-stu-id="20f79-139">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="20f79-140">Se tiver instalado o PowerShell através de transferência direta, PowerShell têm de ser removido manualmente:</span><span class="sxs-lookup"><span data-stu-id="20f79-140">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="20f79-141">Para remover os caminhos de PowerShell adicionais, consulte a [caminhos][] secção deste documento e remover o desejado os caminhos com `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="20f79-141">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="20f79-142">Isso não é necessário se tiver instalado com o Homebrew.</span><span class="sxs-lookup"><span data-stu-id="20f79-142">This is not necessary if you installed with Homebrew.</span></span>

[Caminhos]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="20f79-144">Caminhos</span><span class="sxs-lookup"><span data-stu-id="20f79-144">Paths</span></span>

* <span data-ttu-id="20f79-145">`$PSHOME` é `/usr/local/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="20f79-145">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="20f79-146">Perfis de utilizador serão lido a partir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="20f79-146">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="20f79-147">Perfis predefinidos serão lido a partir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="20f79-147">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="20f79-148">Módulos de utilizador serão lido a partir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="20f79-148">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="20f79-149">Módulos partilhados serão lido a partir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="20f79-149">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="20f79-150">Módulos padrão serão lido a partir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="20f79-150">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="20f79-151">Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="20f79-151">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="20f79-152">Os perfis de respeitam a configuração de por anfitrião do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20f79-152">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="20f79-153">Para que os perfis de anfitrião específico padrão existe em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.</span><span class="sxs-lookup"><span data-stu-id="20f79-153">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="20f79-154">PowerShell respeita os [XDG Base diretório especificação] [ xdg-bds] em macOS.</span><span class="sxs-lookup"><span data-stu-id="20f79-154">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="20f79-155">Uma vez que macOS é uma derivação do BSD, o prefixo `/usr/local` é utilizado em vez de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="20f79-155">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="20f79-156">Por isso, `$PSHOME` é `/usr/local/microsoft/powershell/6.0.2/`, e o symlink é colocado em `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="20f79-156">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="20f79-157">Recursos Adicionais</span><span class="sxs-lookup"><span data-stu-id="20f79-157">Additional Resources</span></span>

* <span data-ttu-id="20f79-158">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="20f79-158">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="20f79-159">[Repositório do Github Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="20f79-159">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="20f79-160">[Homebrew Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="20f79-160">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
