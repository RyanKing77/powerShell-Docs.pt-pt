---
title: Utilizar o Visual Studio Code para o desenvolvimento de PowerShell
description: Utilizar o Visual Studio Code para o desenvolvimento de PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 0d796460511b273771eacb03d0df4d90e1e9c322
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854400"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Utilizar o Visual Studio Code para o desenvolvimento de PowerShell

Para além da [ISE do PowerShell][ise], PowerShell também é bem suportada no Visual Studio Code.
Além disso, o ISE não é suportado com o PowerShell Core, embora o Visual Studio Code é suportada para o PowerShell Core em todas as plataformas (Windows, macOS e Linux)

Pode utilizar Visual Studio Code no Windows com o PowerShell versão 5 com o Windows 10 ou instalando [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) de nível inferior sistemas operacionais do Windows (por exemplo, Windows 8.1, etc.).

Antes de iniciá-lo, certifique-se de que PowerShell existe no seu sistema.
Para cargas de trabalho modernas no Windows, macOS e Linux, consulte:

- [Instalar o PowerShell Core no Linux][install-pscore-linux]
- [Instalar o PowerShell Core no macOS][install-pscore-macos]
- [Instalar o PowerShell Core no Windows][install-pscore-windows]

Para as cargas de trabalho tradicionais do Windows PowerShell, consulte [instalar o Windows PowerShell][install-winps].

## <a name="editing-with-visual-studio-code"></a>Edição com o Visual Studio Code

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[1. Instalar o Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview)

- **Linux**: Siga as instruções de instalação do [executar o VS Code no Linux](https://code.visualstudio.com/docs/setup/linux) página

- **macOS**: Siga as instruções de instalação do [executar o VS Code no macOS](https://code.visualstudio.com/docs/setup/mac) página

  > [!IMPORTANT]
  > No macOS, tem de instalar o OpenSSL para a extensão de PowerShell funcione corretamente.
  > A maneira mais fácil de realizar isso é instalar [Homebrew](https://brew.sh/) e, em seguida, execute `brew install openssl`.
  > VS Code agora pode carregar a extensão de PowerShell com êxito.

- **Windows**: Siga as instruções de instalação do [executar o VS Code no Windows](https://code.visualstudio.com/docs/setup/windows) página

### <a name="2-installing-powershell-extension"></a>2. Instalar a extensão de PowerShell

- Lançamento do Visual Studio Code aplicação por:
  - **Windows**: escrever `code` na sessão do PowerShell
  - **Linux**: escrever `code` no seu terminal
  - **macOS**: escrever `code` no seu terminal

- Inicie **Quick Open** pressionando **Ctrl + P** (**Cmd + P** no Mac).
- Em Quick Open, escreva `ext install powershell` e prima **Enter**.
- O **extensões** é aberta uma vista na barra do lado. Selecione a extensão de PowerShell da Microsoft.
  Deverá ver algo, conforme mostrado abaixo:

  ![VSCode](../../images/vscode.png)

- Clique nas **instalar** botão na extensão de PowerShell, da Microsoft.
- Depois da instalação, consulte a **instale** botão passa a **recarregar**.
  Clique em **recarregar**.
- Depois do Visual Studio Code tem recarregar, está pronto para edição.

Por exemplo, para criar um novo ficheiro, clique em **arquivo -> novo**.
Para guardar, clique em **ficheiro -> Save** e, em seguida, forneça um nome de ficheiro, vamos dizer `HelloWorld.ps1`.
Para fechar o ficheiro, clique em "x" junto ao nome do ficheiro.
Para sair do Visual Studio Code **ficheiro -> saída**.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>Instalação da extensão de PowerShell em sistemas restritos

Alguns sistemas são configurados de forma que requer que todas as assinaturas de código a ser verificado e, portanto, requer os serviços de Editor do PowerShell ser aprovado manualmente para ser executado no sistema.
Uma atualização de política de grupo que altera a política de execução é das causas prováveis se tiver instalado a extensão de PowerShell, mas Contatando um erro, como:

```
Language server startup failed.
```

Para aprovar manualmente os serviços de Editor do PowerShell e, portanto, a extensão de PowerShell para VSCode, abra o PowerShell linha de comandos e execute:

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Lhe for pedido com "You want to executar software a partir deste publicador não fidedigno?"
Tipo de `R` para executar o ficheiro. Em seguida, abra o Visual Studio Code e verifique se a extensão de PowerShell está a funcionar corretamente. Se ainda tiver problemas de introdução, fale na [GitHub](https://github.com/PowerShell/vscode-powershell/issues).

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>Escolher uma versão do PowerShell para utilizar com a extensão

Com o PowerShell Core, a instalação lado a lado com o Windows PowerShell, é agora possível para uma versão específica do PowerShell com a extensão de PowerShell. Utilize o seguinte estes passos para escolher a versão:

1. Abra o palete de comando (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> no Windows e Linux, <kbd>Cmd</kbd> + <kbd>Shift</kbd>+<kbd>P</kbd> no macOS).
1. Procure "Session".
1. Clique em "PowerShell: Mostre Menu de sessão".
1. Escolha a versão do PowerShell que pretende utilizar na lista - por exemplo, "PowerShell"principal".

>[!IMPORTANT]
> Esta funcionalidade analisa alguns caminhos bem conhecidos em diferentes sistemas operativos para detetar localizações de instalação do PowerShell. Se tiver instalado o PowerShell para uma localização não típico, ela poderá não aparecem inicialmente no Menu de sessão. Pode estender o menu de sessão por [adicionar seus próprios caminhos personalizados](#adding-your-own-powershell-paths-to-the-session-menu) conforme descrito abaixo.

>[!NOTE]
> Existe outra forma de obter ao menu de sessão. Quando um ficheiro do PowerShell está aberto no seu editor, verá um número de versão verde na inferior direito. Clicar neste número de versão irão direcioná-lo para o menu de sessão.

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>Adicionar seus próprios caminhos de PowerShell para o menu de sessão

Pode adicionar outros caminhos de executáveis do PowerShell para o menu de sessão através de uma definição do VS Code.

Adicionar um item à lista `powershell.powerShellAdditionalExePaths` ou criar a lista, se não existir na sua `settings.json`:

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],
    
    // other settings...
}
```

Cada item tem de ter:

* `exePath`: O caminho para o `pwsh` ou `powershell` executável.
* `versionName`: O texto que aparecerá no menu de sessão.

Pode definir a versão do PowerShell de predefinida para utilizar com o `powershell.powerShellDefaultVersion` definição por definição esta opção para o texto apresentado no menu de sessão (também conhecido como o `versionName` na definição de último):

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],
    
    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",
    
    // other settings...
}
```

Assim que tiver configurado esta definição, reinicie o Visual Studio Code ou utilizar o o "desenvolvedor: Recarregue a janela"comando palete ação para recarregar a janela de vscode atual.

Se abrir o menu de sessão, verá agora sua versões adicionais do PowerShell!

> [!NOTE]
> Se criar PowerShell da origem, esta é uma excelente forma de testar sua compilação local do PowerShell.

#### <a name="configuration-settings-for-visual-studio-code"></a>Definições de configuração para o Visual Studio Code

Utilize os passos no parágrafo anterior pode adicionar definições de configuração no `settings.json`.

Recomendamos as seguintes definições de configuração para o Visual Studio Code:

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Se não pretender que estas definições afetam todos os tipos de ficheiros, VSCode também permite que configurações por idioma. Criar uma configuração específica de idioma ao colocar configurações `[<language-name>]` campo. Por exemplo:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Para obter mais informações sobre o ficheiro codificação no VS Code, consulte [compreender a codificação do ficheiro](understanding-file-encoding.md).

## <a name="debugging-with-visual-studio-code"></a>Depuração com o Visual Studio Code

### <a name="no-workspace-debugging"></a>Área de trabalho de não depuração

A partir da versão do Visual Studio Code 1.9 pode depurar scripts do PowerShell sem ter de abrir a pasta que contém o script do PowerShell. Abra o ficheiro de script do PowerShell com **ficheiro -> abrir o ficheiro...** , defina um ponto de interrupção numa linha (pressionar o F9) e, em seguida, prima F5 para iniciar a depuração. Deverá ver o painel de ações de depuração aparecer que permite que invadir o depurador, passo, resume e stop depuração.

### <a name="workspace-debugging"></a>Depuração de área de trabalho

Depuração de área de trabalho refere-se a depuração no contexto de uma pasta que abriu o no Visual Studio Code com **Abrir pasta...**  partir de **ficheiro** menu.
A pasta que abrir é, normalmente, a pasta do projeto do PowerShell e/ou a raiz do repositório de Git.

Mesmo neste modo, pode começar a depurar o script do PowerShell atualmente selecionado, simplesmente pressionando F5.
No entanto, a depuração de área de trabalho permite-lhe definir várias configurações de depuração que não seja de depuração apenas os ficheiros atualmente abertos.
Por exemplo, pode adicionar um configurações para:

- Inicie os testes de Pester no depurador
- Iniciar um arquivo específico com argumentos no depurador
- Iniciar uma sessão interativa no depurador
- Anexar o depurador a um processo de anfitrião do PowerShell

Siga estes passos para criar o arquivo de configuração de depuração:

  1. Abra o **depurar** vista pressionando **Ctrl + Shift + D** (**Cmd + Shift + D** no Mac).
  2. Prima a **configurar** ícone de engrenagem na barra de ferramentas.
  3. Pede-lhe para Visual Studio Code **selecionar ambiente**. Escolher **PowerShell**.

  Ao fazê-lo, o código do Visual Studio cria um diretório e um arquivo de ".vscode\launch.json" na raiz da sua pasta de área de trabalho.
  Isso é onde está armazenada a sua configuração de depuração. Se os ficheiros estiverem num repositório de Git, normalmente pretende consolidar o ficheiro Launch JSON.
  O conteúdo do ficheiro Launch JSON é:

  ```json
  {
    "version": "0.2.0",
    "configurations": [
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Launch (current file)",
            "script": "${file}",
            "args": [],
            "cwd": "${file}"
        },
        {
            "type": "PowerShell",
            "request": "attach",
            "name": "PowerShell Attach to Host Process",
            "processId": "${command.PickPSHostProcess}",
            "runspaceId": 1
        },
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Interactive Session",
            "cwd": "${workspaceRoot}"
        }
    ]
  }
  ```

  Isso representa os cenários comuns de depuração.
  No entanto, quando abrir esse arquivo no editor, verá um **configuração adicionar...**  botão.
  Pode pressionar este botão para adicionar mais configurações de depuração do PowerShell. É uma configuração útil para adicionar **PowerShell: Inicie o Script**.
  Com esta configuração, pode especificar um ficheiro específico com os argumentos opcionais que deve ser iniciado sempre que pressionar F5, independentemente da qual arquivo atualmente ativo no editor.

  Depois da configuração de depuração é estabelecida, pode selecionar que configuração que pretende utilizar durante uma sessão de depuração, selecionando uma na configuração de depuração menu pendente na **depurar** barra de ferramentas da exibição.

Existem alguns blogs que podem ser úteis para começar a utilizar a extensão de PowerShell para Visual Studio Code:

- [Extensão de PowerShell][ps-extension]
- [Escreva e Depure os scripts do PowerShell no Visual Studio Code][debug]
- [Depuração de diretrizes de código do Visual Studio][vscode-guide]
- [Depuração do PowerShell no Visual Studio Code][ps-vscode]
- [Introdução ao desenvolvimento do PowerShell no Visual Studio Code][getting-started]
- [Visual Studio Code, edição de recursos para desenvolvimento do PowerShell – parte 1][editing-part1]
- [Visual Studio Code, edição de recursos para desenvolvimento do PowerShell – parte 2][editing-part2]
- [Script do PowerShell depuração no Visual Studio Code – parte 1][debugging-part1]
- [Script do PowerShell depuração no Visual Studio Code – parte 2][debugging-part2]

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a>Extensão de PowerShell para Visual Studio Code

Código-fonte a extensão de PowerShell pode ser encontrado no [GitHub](https://github.com/PowerShell/vscode-powershell).
