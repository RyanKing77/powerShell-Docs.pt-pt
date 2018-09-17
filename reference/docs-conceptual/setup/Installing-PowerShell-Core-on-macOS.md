---
title: Instalar o PowerShell Core no macOS
description: Informações sobre como instalar o PowerShell Core no macOS
ms.date: 08/06/2018
ms.openlocfilehash: 042c933dfa83f3ab52e315036e4f817145116d00
ms.sourcegitcommit: aa41249f153bbc6e11667ade60c878980c15abc6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/14/2018
ms.locfileid: "45611492"
---
# <a name="installing-powershell-core-on-macos"></a>Instalar o PowerShell Core no macOS

O PowerShell Core suporta o macOS 10.12 e superior.
Todos os pacotes estão disponíveis no nosso GitHub [versões][] página.
Depois do pacote está instalado, execute `pwsh` partir de um terminal.

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>Instalação da versão estável mais recente através do Homebrew no macOS 10.12 ou superior

[Homebrew] [ brew] é o Gestor de pacotes preferencial para macOS.
Se o `brew` comando não for encontrado, tem de instalar o Homebrew seguintes [suas instruções][brew].

Agora, pode instalar o PowerShell:

```sh
brew cask install powershell
```

Por fim, certifique-se de que a instalação está a funcionar corretamente:

```sh
pwsh
```

Quando são lançadas novas versões do PowerShell, basta atualizar viramos do Homebrew e atualize o PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Os comandos acima podem ser chamados a partir de um anfitrião do PowerShell (pwsh), mas, em seguida, o shell do PowerShell tem de estar encerrado e reiniciado para concluir a atualização.
> e atualize os valores mostrados na $PSVersionTable.

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Instalação de pré-visualização mais recente da versão através do Homebrew no macOS 10.12 ou superior

[Homebrew] [ brew] é o Gestor de pacotes preferencial para macOS.
Se o `brew` comando não for encontrado, tem de instalar o Homebrew seguintes [suas instruções][brew].

Depois de instalar o Homebrew, instalar o PowerShell é fácil.
Primeiro, instale [versões Cask] [ cask-versions] que permite-lhe instalar alternativas versões dos pacotes de cask:

```sh
brew tap homebrew/cask-versions
```

Agora, pode instalar o PowerShell:

```sh
brew cask install powershell-preview
```

Por fim, certifique-se de que a instalação está a funcionar corretamente:

```sh
pwsh-preview
```

Quando são lançadas novas versões do PowerShell, basta atualizar viramos do Homebrew e atualize o PowerShell:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Os comandos acima podem ser chamados a partir de um anfitrião do PowerShell (pwsh), mas, em seguida, o shell do PowerShell tem de estar encerrado e reiniciado para concluir a atualização.
> e atualize os valores mostrados na $PSVersionTable.

## <a name="installation-via-direct-download"></a>Instalação através de transferência direta

Transferir o pacote PKG `powershell-6.1.0-osx-x64.pkg`
partir do [versões][] página no seu computador macOS.

Pode clicar duas vezes o arquivo e siga as instruções ou instalá-lo a partir do terminal:

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a>Arquivos binários

Binário de PowerShell `tar.gz` arquivos são fornecidos para a plataforma macOS ativar cenários de implementação avançada.

### <a name="installing-binary-archives-on-macos"></a>Instalar arquivos binários em macOS

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

## <a name="uninstalling-powershell-core"></a>Desinstalar o PowerShell Core

Se tiver instalado o PowerShell com o Homebrew, desinstalação é fácil:

```sh
brew cask uninstall powershell
```

Se tiver instalado o PowerShell através de transferência direta, PowerShell têm de ser removido manualmente:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Para remover os caminhos de PowerShell adicionais, consulte a [caminhos](#paths) secção deste documento e remover o desejado os caminhos com `sudo rm`.

> [!NOTE]
> Isso não é necessário se tiver instalado com o Homebrew.

## <a name="paths"></a>Caminhos

* `$PSHOME` é `/usr/local/microsoft/powershell/6.1.0/`
* Perfis de utilizador serão lido a partir `~/.config/powershell/profile.ps1`
* Perfis predefinidos serão lido a partir `$PSHOME/profile.ps1`
* Módulos de utilizador serão lido a partir `~/.local/share/powershell/Modules`
* Módulos partilhados serão lido a partir `/usr/local/share/powershell/Modules`
* Módulos padrão serão lido a partir `$PSHOME/Modules`
* Histórico de PSReadline será gravado para `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Os perfis de respeitam a configuração de por anfitrião do PowerShell.
Para que os perfis de anfitrião específico padrão existe em `Microsoft.PowerShell_profile.ps1` nos mesmos locais.

PowerShell respeita os [XDG Base diretório especificação] [ xdg-bds] em macOS.

Uma vez que macOS é uma derivação do BSD, o prefixo `/usr/local` é utilizado em vez de `/opt`.
Por isso, `$PSHOME` é `/usr/local/microsoft/powershell/6.1.0/`, e o symlink é colocado em `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Recursos Adicionais

* [Homebrew Web][brew]
* [Repositório do Github Homebrew][GitHub]
* [Homebrew Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versões]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
