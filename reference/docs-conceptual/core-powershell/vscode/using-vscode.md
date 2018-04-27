# <a name="using-visual-studio-code-for-powershell-development"></a>Utilizar o código do Visual Studio para desenvolvimento de PowerShell

Para além de [ISE do PowerShell][ise], PowerShell também é bem suportado no Visual Studio Code.
Além disso, o ISE não é suportado com o PowerShell Core, enquanto o Visual Studio Code é suportada para o principal do PowerShell em todas as plataformas (Windows, macOS e Linux)

Pode utilizar Visual Studio Code no Windows com o PowerShell versão 5 utilizando o Windows 10 ou instalando [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) de nível inferior OSs do Windows (por exemplo, Windows 8.1, etc.).

Antes de iniciá-lo, certifique-se que PowerShell existe no sistema.
Para cargas de trabalho modernas no Windows, macOS e Linux, consulte:

- [Instalar o PowerShell Core no Linux][install-pscore-linux]
- [Instalar o PowerShell Core no macOS][install-pscore-macos]
- [Instalar o núcleo do PowerShell no Windows][install-pscore-windows]

Para cargas de trabalho do Windows PowerShell tradicionais, consulte [instalar o Windows PowerShell][install-winps].

## <a name="editing-with-visual-studio-code"></a>Editar com o código do Visual Studio

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[1. Instalar Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview)

- **Linux**: Siga as instruções de instalação no [a executar o VS Code no Linux](https://code.visualstudio.com/docs/setup/linux) página

- **macOS**: Siga as instruções de instalação no [a executar o VS Code no macOS](https://code.visualstudio.com/docs/setup/mac) página

> [!IMPORTANT]
> No macOS, tem de instalar OpenSSL para a extensão do PowerShell para funcionar corretamente.
> A forma mais fácil para realizar esta tarefa é instalar [Homebrew](http://brew.sh/) e, em seguida, execute `brew install openssl`.
> A extensão do PowerShell irá agora ser capaz de ser carregada com êxito.

- **Windows**: Siga as instruções de instalação no [a executar o VS Code no Windows](https://code.visualstudio.com/docs/setup/windows) página

### <a name="2-installing-powershell-extension"></a>2. Instalação da extensão do PowerShell

- Inicie o Visual Studio Code aplicações por:
    - **Windows**: escrevendo `code` na sessão do PowerShell
    - **Linux**: escrevendo `code` no seu terminal
    - **macOS**: escrevendo `code` no seu terminal

- Iniciar **rápida abra** premindo **Ctrl + P** (**Cmd + P** no Mac).
- Na rápida aberta, escreva `ext install powershell` e acessos **Enter**.
- O **extensões** vista abrirá na barra lateral. Selecione a extensão do PowerShell da Microsoft.
  Verá algo, conforme mostrado abaixo:

  ![VSCode](../../images/vscode.png)

- Clique em de **instalar** botão na extensão do PowerShell da Microsoft.
- Depois da instalação, verá o **instalar** botão passa a **recarregar**.
  Clique em **recarregar**.
- Depois do Visual Studio Code tem recarregar, está pronto para editar.

Por exemplo, para criar um novo ficheiro, clique em **ficheiro -> novo**.
Para guardar, clique em **ficheiro -> guardar** e, em seguida, forneça um nome de ficheiro, vamos diga `HelloWorld.ps1`.
Para fechar o ficheiro, clique no "x" junto ao nome do ficheiro.
Para sair do Visual Studio Code, **ficheiro -> saída**.

#### <a name="using-a-specific-installed-version-of-powershell"></a>Utilizar uma versão específica instalada do PowerShell

Se pretender utilizar uma instalação específica do PowerShell com o Visual Studio Code, terá de adicionar uma nova variável ao seu ficheiro de definições de utilizador.

1. Clique em **ficheiro -> Preferências -> definições**
1. Serão apresentada a dois painéis do editor.
   No painel de mais à direita (`settings.json`), inserir a definição abaixo apropriado para o SO algures entre as dois chavetas (`{` e `}`) e substitua *<version>* com o instalado Versão do PowerShell:

  ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
  ```
1. Substitua a definição com o caminho para o executável pretendido do PowerShell
1. Guarde o ficheiro de definições e reinicie o Visual Studio Code

#### <a name="configuration-settings-for-visual-studio-code"></a>Definições de configuração para o Visual Studio Code

Utilizando os passos no parágrafo anterior, pode adicionar definições de configuração no `settings.json`.

Recomendamos as seguintes definições de configuração para o Visual Studio Code:

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a>Depuração com o código do Visual Studio

### <a name="no-workspace-debugging"></a>Área de trabalho não depuração

A partir da versão do Visual Studio Code 1.9 pode depurar scripts do PowerShell sem ter de abrir a pasta que contém o script do PowerShell.
Basta abrir o ficheiro de script do PowerShell com **ficheiro -> Abra o ficheiro...** , defina um ponto de interrupção de uma linha (prima F9) e, em seguida, prima F5 para iniciar a depuração.
Verá o painel de ações de depuração aparecer que lhe permite interromper o depurador, passo, retomar e pare a depuração.

### <a name="workspace-debugging"></a>A depuração de área de trabalho

Área de trabalho depuração refere-se a depuração no contexto de uma pasta que tem aberto no Visual Studio Code utilizando **pasta aberta...**  do **ficheiro** menu.
A pasta que abrir é, geralmente, a pasta de projeto do PowerShell e/ou a raiz do repositório de Git.

Mesmo neste modo, pode começar a depurar o script do PowerShell atualmente selecionado ao basta premir F5.
No entanto, a depuração de área de trabalho permite-lhe definir configurações com várias depuração diferente de depuração apenas os ficheiros atualmente abertos.
Por exemplo, pode adicionar um configurações para:

- Iniciar o depurador testes Pester
- Iniciar um ficheiro específico com argumentos no depurador
- Inicie uma sessão interativa no depurador
- Anexar o depurador a um processo de anfitrião PowerShell

Siga estes passos para criar o ficheiro de configuração de depuração:

1. Abra o **depurar** vista premindo **Ctrl + Shift + D** (**Cmd + Shift + D** no Mac).
1. Prima a **configurar** engrenagem ícone na barra de ferramentas.
1. Visual Studio Code solicitará a **selecione ambiente**.
   Escolha **PowerShell**.

   Ao fazê-lo, o Visual Studio Code cria um diretório e um ficheiro de ".vscode\launch.json" na raiz da pasta à sua área de trabalho.
   Este é onde está armazenada a configuração de depuração. Se os ficheiros estiverem num repositório de Git, normalmente, irá querer consolidar o ficheiro launch.json.
   O conteúdo do ficheiro launch.json é:

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

Representa os cenários comuns de depuração.
No entanto, quando abrir este ficheiro no editor, verá um **configuração adicionar...**  botão.
Pode premir neste botão para adicionar mais configurações de depuração do PowerShell. É uma configuração útil para adicionar **PowerShell: iniciar o Script**.
Com esta configuração, pode especificar um ficheiro específico com argumentos opcionais que deve ser iniciado sempre que premir F5 não independentemente do qual o ficheiro está atualmente ativo no editor.

Depois da configuração de depuração é estabelecida, pode selecionar que configuração que pretende utilizar durante uma sessão de depuração, selecionando um da configuração de depuração pendente no **depurar** barra de ferramentas da vista.

Existem alguns blogues que podem ser úteis ajudar a começar a utilizar a extensão de PowerShell para o Visual Studio Code

- Código do Visual Studio: [extensão do PowerShell][ps-extension]
- [Escrever e depurar scripts do PowerShell no Visual Studio Code][debug]
- [Orientações de código depuração do Visual Studio][vscode-guide]
- [PowerShell depuração no Visual Studio Code][ps-vscode]
- [Começar com o PowerShell desenvolvimento no Visual Studio Code][getting-started]
- [Visual Studio Code editar funcionalidades para o desenvolvimento de PowerShell – parte 1][editing-part1]
- [Visual Studio Code funcionalidades para o desenvolvimento de PowerShell – parte 2 de edição][editing-part2]
- [Depurar o script do PowerShell no Visual Studio Code – parte 1][debugging-part1]
- [Depurar o script do PowerShell no Visual Studio Code – parte 2][debugging-part2]

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]:https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]:https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]:https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]:https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]:https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a>Extensão de PowerShell para o Visual Studio Code

Código de origem a extensão de PowerShell pode ser encontrado no [GitHub](https://github.com/PowerShell/vscode-powershell).