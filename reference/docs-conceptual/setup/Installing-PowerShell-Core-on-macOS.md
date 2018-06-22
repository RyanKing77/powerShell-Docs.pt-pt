# <a name="installing-powershell-core-on-macos"></a>Instalar o PowerShell Core no macOS

PowerShell Core suporta macOS 10.12 e planos superiores.
Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.
Depois do pacote está instalado, executar `pwsh` de um terminal.

### <a name="installation-via-homebrew-on-macos-1012"></a>Instalação via Homebrew no macOS 10.12

[Homebrew] [ brew] é o Gestor de pacotes preferencial para macOS.
Se o `brew` comandos não for encontrado, tem de instalar o seguinte Homebrew [as instruções][brew].

Assim que instalou Homebrew, instalar o PowerShell é fácil.
Em primeiro lugar, instalar [Homebrew Cask][cask], como tal, pode instalar mais pacotes:

```sh
brew tap caskroom/cask
```

Agora, pode instalar o PowerShell:

```sh
brew cask install powershell
```

Por fim, certifique-se de que a instalação está a funcionar corretamente:

```sh
pwsh
```

Quando são lançadas novas versões do PowerShell, basta atualizar formulae do Homebrew e atualizar o PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Os comandos acima podem ser chamados a partir de um anfitrião do PowerShell (pwsh), mas, em seguida, a shell de PowerShell tem de ser terminada e reiniciada para concluir a atualização e atualize os valores apresentados nas $PSVersionTable.

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download"></a>Instalação através de transferência direta

Transferir o pacote PKG `powershell-6.0.2-osx.10.12-x64.pkg` do [versões][] página na máquina macOS.

Pode faça duplo clique o ficheiro e siga as instruções ou instalá-lo no terminal:

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a>Arquivos binários

PowerShell binário `tar.gz` arquivos são fornecidos para macOS e plataformas Linux para ativar cenários de implementação avançada.

### <a name="installing-binary-archives-on-macos"></a>Instalar arquivos binários no macOS

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

## <a name="uninstalling-powershell-core"></a>A desinstalação do PowerShell Core

Se tiver instalado o PowerShell com Homebrew, é fácil a desinstalação:

```sh
brew cask uninstall powershell
```

Se tiver instalado o PowerShell através de transferência direta, PowerShell tem de retirar manualmente:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Para remover os caminhos de PowerShell adicionais, consulte o [caminhos][] secção deste documento e remover os caminhos de utilizar o pretendido `sudo rm`.

> [!NOTE]
> Não é necessário se tiver instalado com Homebrew.

[caminhos]:#paths

## <a name="paths"></a>Caminhos

* `$PSHOME` é `/usr/local/microsoft/powershell/6.0.2/`
* Perfis de utilizador serão lida a partir de `~/.config/powershell/profile.ps1`
* Serão possível ler perfis predefinidos `$PSHOME/profile.ps1`
* Módulos de utilizador serão lida a partir de `~/.local/share/powershell/Modules`
* Módulos partilhados irão ler a partir do `/usr/local/share/powershell/Modules`
* Módulos de predefinido serão possível ler a partir do `$PSHOME/Modules`
* Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Os perfis respeitem a configuração de por anfitrião do PowerShell.
Para os perfis de anfitrião específico predefinido não existe em `Microsoft.PowerShell_profile.ps1` nas localizações da mesmas.

PowerShell respeita o [XDG Base diretório especificação] [ xdg-bds] no macOS.

Porque macOS é uma derivação do BSD, o prefixo `/usr/local` é utilizado em vez de `/opt`.
Assim, `$PSHOME` é `/usr/local/microsoft/powershell/6.0.2/`, e o symlink é colocado em `/usr/local/bin/pwsh`.

[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
