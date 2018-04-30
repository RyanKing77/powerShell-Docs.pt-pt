# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="5ed13-101">Instalar o PowerShell Core no macOS</span><span class="sxs-lookup"><span data-stu-id="5ed13-101">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="5ed13-102">PowerShell Core suporta macOS 10.12 e planos superiores.</span><span class="sxs-lookup"><span data-stu-id="5ed13-102">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="5ed13-103">Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.</span><span class="sxs-lookup"><span data-stu-id="5ed13-103">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="5ed13-104">Depois do pacote está instalado, executar `pwsh` de um terminal.</span><span class="sxs-lookup"><span data-stu-id="5ed13-104">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="5ed13-105">Instalação via Homebrew no macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="5ed13-105">Installation via Homebrew on macOS 10.12</span></span>

<span data-ttu-id="5ed13-106">[Homebrew] [ brew] é o Gestor de pacotes preferencial para macOS.</span><span class="sxs-lookup"><span data-stu-id="5ed13-106">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="5ed13-107">Se o `brew` comandos não for encontrado, tem de instalar o seguinte Homebrew [as instruções][brew].</span><span class="sxs-lookup"><span data-stu-id="5ed13-107">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="5ed13-108">Assim que instalou Homebrew, instalar o PowerShell é fácil.</span><span class="sxs-lookup"><span data-stu-id="5ed13-108">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="5ed13-109">Em primeiro lugar, instalar [Homebrew Cask][cask], como tal, pode instalar mais pacotes:</span><span class="sxs-lookup"><span data-stu-id="5ed13-109">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="5ed13-110">Agora, pode instalar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5ed13-110">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="5ed13-111">Por fim, certifique-se de que a instalação está a funcionar corretamente:</span><span class="sxs-lookup"><span data-stu-id="5ed13-111">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="5ed13-112">Quando são lançadas novas versões do PowerShell, basta atualizar formulae do Homebrew e atualizar o PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5ed13-112">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="5ed13-113">Os comandos acima podem ser chamados a partir de um anfitrião do PowerShell (pwsh), mas, em seguida, a shell de PowerShell tem de ser terminada e reiniciada para concluir a atualização.</span><span class="sxs-lookup"><span data-stu-id="5ed13-113">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="5ed13-114">e atualize os valores apresentados nas $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="5ed13-114">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download"></a><span data-ttu-id="5ed13-115">Instalação através de transferência direta</span><span class="sxs-lookup"><span data-stu-id="5ed13-115">Installation via Direct Download</span></span>

<span data-ttu-id="5ed13-116">Transferir o pacote PKG `powershell-6.0.2-osx.10.12-x64.pkg` do [versões][] página na máquina macOS.</span><span class="sxs-lookup"><span data-stu-id="5ed13-116">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="5ed13-117">Pode faça duplo clique o ficheiro e siga as instruções ou instalá-lo no terminal:</span><span class="sxs-lookup"><span data-stu-id="5ed13-117">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="5ed13-118">Arquivos binários</span><span class="sxs-lookup"><span data-stu-id="5ed13-118">Binary Archives</span></span>

<span data-ttu-id="5ed13-119">PowerShell binário `tar.gz` arquivos são fornecidos para macOS e plataformas Linux para ativar cenários de implementação avançada.</span><span class="sxs-lookup"><span data-stu-id="5ed13-119">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="5ed13-120">Instalar arquivos binários no macOS</span><span class="sxs-lookup"><span data-stu-id="5ed13-120">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="5ed13-121">A desinstalação do PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="5ed13-121">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="5ed13-122">Se tiver instalado o PowerShell com Homebrew, é fácil a desinstalação:</span><span class="sxs-lookup"><span data-stu-id="5ed13-122">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="5ed13-123">Se tiver instalado o PowerShell através de transferência direta, PowerShell tem de retirar manualmente:</span><span class="sxs-lookup"><span data-stu-id="5ed13-123">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="5ed13-124">Para remover os caminhos de PowerShell adicionais, consulte o [caminhos][] secção deste documento e remover os caminhos de utilizar o pretendido `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="5ed13-124">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="5ed13-125">Não é necessário se tiver instalado com Homebrew.</span><span class="sxs-lookup"><span data-stu-id="5ed13-125">This is not necessary if you installed with Homebrew.</span></span>

[caminhos]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="5ed13-127">Caminhos</span><span class="sxs-lookup"><span data-stu-id="5ed13-127">Paths</span></span>

* <span data-ttu-id="5ed13-128">`$PSHOME` é `/opt/microsoft/powershell/6.0.0/`</span><span class="sxs-lookup"><span data-stu-id="5ed13-128">`$PSHOME` is `/opt/microsoft/powershell/6.0.0/`</span></span>
* <span data-ttu-id="5ed13-129">Perfis de utilizador serão lida a partir de `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="5ed13-129">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="5ed13-130">Serão possível ler perfis predefinidos `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="5ed13-130">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="5ed13-131">Módulos de utilizador serão lida a partir de `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="5ed13-131">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="5ed13-132">Módulos partilhados irão ler a partir do `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="5ed13-132">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="5ed13-133">Módulos de predefinido serão possível ler a partir do `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="5ed13-133">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="5ed13-134">Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="5ed13-134">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="5ed13-135">Os perfis respeitem a configuração de por anfitrião do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5ed13-135">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="5ed13-136">Para os perfis de anfitrião específico predefinido não existe em `Microsoft.PowerShell_profile.ps1` nas localizações da mesmas.</span><span class="sxs-lookup"><span data-stu-id="5ed13-136">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="5ed13-137">PowerShell respeita o [XDG Base diretório especificação] [ xdg-bds] no macOS.</span><span class="sxs-lookup"><span data-stu-id="5ed13-137">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="5ed13-138">Porque macOS é uma derivação do BSD, o prefixo `/usr/local` é utilizado em vez de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="5ed13-138">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="5ed13-139">Assim, `$PSHOME` é `/usr/local/microsoft/powershell/6.0.0/`, e o symlink é colocado em `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="5ed13-139">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
