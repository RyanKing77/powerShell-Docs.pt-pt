# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="823fe-101">Instalar o PowerShell Core no macOS</span><span class="sxs-lookup"><span data-stu-id="823fe-101">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="823fe-102">O PowerShell Core suporta o macOS 10.12 e superior.</span><span class="sxs-lookup"><span data-stu-id="823fe-102">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="823fe-103">Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.</span><span class="sxs-lookup"><span data-stu-id="823fe-103">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="823fe-104">Depois do pacote está instalado, execute `pwsh` partir de um terminal.</span><span class="sxs-lookup"><span data-stu-id="823fe-104">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="823fe-105">Instalação através do Homebrew no macOS 10.12 +</span><span class="sxs-lookup"><span data-stu-id="823fe-105">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="823fe-106">[Homebrew] [ brew] é o Gestor de pacotes preferencial para macOS.</span><span class="sxs-lookup"><span data-stu-id="823fe-106">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="823fe-107">A partir de uma janela de terminal, escreva `brew` para executar o Homebrew.</span><span class="sxs-lookup"><span data-stu-id="823fe-107">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="823fe-108">Se o `brew` comando não for encontrado, tem de instalar o Homebrew seguintes [suas instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="823fe-108">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="823fe-109">Se tiver instalado o Homebrew no passado, é sempre uma boa idéia para executar "update-reposição brew" & & 'brew update'.</span><span class="sxs-lookup"><span data-stu-id="823fe-109">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="823fe-110">Versões mais antigas do Homebrew utilizado o toque em "caskroom/cask', que foi preterido e fizemos a migração para o homebrew/cask.</span><span class="sxs-lookup"><span data-stu-id="823fe-110">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="823fe-111">Obter mais informações podem ser encontradas em [Homebrew-cask][cask].</span><span class="sxs-lookup"><span data-stu-id="823fe-111">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="823fe-112">Utilize o comando de "brew toque" para listar os taps atual.</span><span class="sxs-lookup"><span data-stu-id="823fe-112">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="823fe-113">Se vir "caskroom/cask" pode usar a 'atualização brew' ter Homebrew migrar os toques.</span><span class="sxs-lookup"><span data-stu-id="823fe-113">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="823fe-114">Depois de instalado/atualizou o Homebrew, instalar o PowerShell é fácil.</span><span class="sxs-lookup"><span data-stu-id="823fe-114">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="823fe-115">Para instalar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="823fe-115">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="823fe-116">Por fim, certifique-se de que a instalação está a funcionar corretamente:</span><span class="sxs-lookup"><span data-stu-id="823fe-116">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="823fe-117">Para sair do PowerShell e retornar para bash, utilize o comando de "saída".</span><span class="sxs-lookup"><span data-stu-id="823fe-117">To exit PowerShell, and return to bash, use the 'exit' command.</span></span> 
```sh
exit
```

<span data-ttu-id="823fe-118">Quando são lançadas novas versões do PowerShell, basta atualizar viramos do Homebrew e atualize o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="823fe-118">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="823fe-119">Os comandos acima podem ser chamados a partir de um anfitrião do PowerShell (pwsh), mas, em seguida, o shell do PowerShell tem de estar encerrado e reiniciado para concluir a atualização e atualizar os valores mostrados na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="823fe-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="823fe-120">Instalar a pré-visualização através do Homebrew no macOS 10.12 +</span><span class="sxs-lookup"><span data-stu-id="823fe-120">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="823fe-121">[Homebrew] [ brew] é o Gestor de pacotes preferencial para macOS.</span><span class="sxs-lookup"><span data-stu-id="823fe-121">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="823fe-122">A partir de uma janela de terminal, escreva `brew` para executar o Homebrew.</span><span class="sxs-lookup"><span data-stu-id="823fe-122">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="823fe-123">Se o `brew` comando não for encontrado, tem de instalar o Homebrew seguintes [suas instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="823fe-123">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="823fe-124">Se tiver instalado o Homebrew no passado, é sempre uma boa idéia para executar "update-reposição brew" & & 'brew update'.</span><span class="sxs-lookup"><span data-stu-id="823fe-124">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="823fe-125">Em seguida, pressione a `versions` repositório casks para obter o pacote de pré-visualização:</span><span class="sxs-lookup"><span data-stu-id="823fe-125">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="823fe-126">Para instalar a pré-visualização do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="823fe-126">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="823fe-127">Por fim, certifique-se de que a instalação está a funcionar corretamente:</span><span class="sxs-lookup"><span data-stu-id="823fe-127">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="823fe-128">Quando são lançadas novas versões do PowerShell, basta atualizar viramos do Homebrew e atualizar pré-visualização do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="823fe-128">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="823fe-129">Os comandos acima podem ser chamados a partir de um anfitrião do PowerShell (pwsh), mas, em seguida, o shell do PowerShell tem de estar encerrado e reiniciado para concluir a atualização e atualizar os valores mostrados na $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="823fe-129">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="823fe-130">Instalação através de transferência direta</span><span class="sxs-lookup"><span data-stu-id="823fe-130">Installation via Direct Download</span></span>

<span data-ttu-id="823fe-131">Transferir o pacote PKG `powershell-6.0.2-osx.10.12-x64.pkg` partir do [versões][] página no seu computador macOS.</span><span class="sxs-lookup"><span data-stu-id="823fe-131">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="823fe-132">Pode clicar duas vezes o arquivo e siga as instruções ou instalá-lo a partir do terminal:</span><span class="sxs-lookup"><span data-stu-id="823fe-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="823fe-133">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="823fe-133">Binary Archives</span></span>

<span data-ttu-id="823fe-134">Binário de PowerShell `tar.gz` arquivos são fornecidos para macOS e Linux plataformas para ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="823fe-134">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="823fe-135">Instalar arquivos binários em macOS</span><span class="sxs-lookup"><span data-stu-id="823fe-135">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="823fe-136">Desinstalar o PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="823fe-136">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="823fe-137">Se tiver instalado o PowerShell com o Homebrew, desinstalação é fácil:</span><span class="sxs-lookup"><span data-stu-id="823fe-137">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="823fe-138">Se tiver instalado o PowerShell através de transferência direta, PowerShell têm de ser removido manualmente:</span><span class="sxs-lookup"><span data-stu-id="823fe-138">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="823fe-139">Para remover os caminhos de PowerShell adicionais, consulte a [caminhos][] secção deste documento e remover o desejado os caminhos com `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="823fe-139">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="823fe-140">Isso não é necessário se tiver instalado com o Homebrew.</span><span class="sxs-lookup"><span data-stu-id="823fe-140">This is not necessary if you installed with Homebrew.</span></span>

[Caminhos]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="823fe-142">Caminhos</span><span class="sxs-lookup"><span data-stu-id="823fe-142">Paths</span></span>

* <span data-ttu-id="823fe-143">`$PSHOME` é `/usr/local/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="823fe-143">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="823fe-144">Perfis de utilizador serão lido a partir `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="823fe-144">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="823fe-145">Perfis predefinidos serão lido a partir `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="823fe-145">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="823fe-146">Módulos de utilizador serão lido a partir `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="823fe-146">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="823fe-147">Módulos partilhados serão lido a partir `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="823fe-147">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="823fe-148">Módulos padrão serão lido a partir `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="823fe-148">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="823fe-149">Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="823fe-149">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="823fe-150">Os perfis de respeitam a configuração de por anfitrião do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="823fe-150">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="823fe-151">Para que os perfis de anfitrião específico padrão existe em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.</span><span class="sxs-lookup"><span data-stu-id="823fe-151">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="823fe-152">PowerShell respeita os [XDG Base diretório especificação] [ xdg-bds] em macOS.</span><span class="sxs-lookup"><span data-stu-id="823fe-152">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="823fe-153">Uma vez que macOS é uma derivação do BSD, o prefixo `/usr/local` é utilizado em vez de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="823fe-153">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="823fe-154">Por isso, `$PSHOME` é `/usr/local/microsoft/powershell/6.0.2/`, e o symlink é colocado em `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="823fe-154">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="823fe-155">Recursos Adicionais</span><span class="sxs-lookup"><span data-stu-id="823fe-155">Additional Resources</span></span>

* <span data-ttu-id="823fe-156">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="823fe-156">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="823fe-157">[Repositório do Github Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="823fe-157">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="823fe-158">[Homebrew Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="823fe-158">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
