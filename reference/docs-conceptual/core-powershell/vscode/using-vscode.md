# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="ec253-101">Utilizar o código do Visual Studio para desenvolvimento de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec253-101">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="ec253-102">Para além de [ISE do PowerShell][ise], PowerShell também é bem suportado no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ec253-102">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="ec253-103">Além disso, o ISE não é suportado com o PowerShell Core, enquanto o Visual Studio Code é suportada para o principal do PowerShell em todas as plataformas (Windows, macOS e Linux)</span><span class="sxs-lookup"><span data-stu-id="ec253-103">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="ec253-104">Pode utilizar Visual Studio Code no Windows com o PowerShell versão 5 utilizando o Windows 10 ou instalando [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) de nível inferior OSs do Windows (por exemplo, Windows 8.1, etc.).</span><span class="sxs-lookup"><span data-stu-id="ec253-104">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="ec253-105">Antes de iniciá-lo, certifique-se que PowerShell existe no sistema.</span><span class="sxs-lookup"><span data-stu-id="ec253-105">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="ec253-106">Para cargas de trabalho modernas no Windows, macOS e Linux, consulte:</span><span class="sxs-lookup"><span data-stu-id="ec253-106">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="ec253-107">[Instalar o PowerShell Core no Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="ec253-107">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="ec253-108">[Instalar o PowerShell Core no macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="ec253-108">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="ec253-109">[Instalar o núcleo do PowerShell no Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="ec253-109">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="ec253-110">Para cargas de trabalho do Windows PowerShell tradicionais, consulte [instalar o Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="ec253-110">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="ec253-111">Editar com o código do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ec253-111">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="ec253-112">1. Instalar Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ec253-112">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="ec253-113">**Linux**: Siga as instruções de instalação no [a executar o VS Code no Linux](https://code.visualstudio.com/docs/setup/linux) página</span><span class="sxs-lookup"><span data-stu-id="ec253-113">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="ec253-114">**macOS**: Siga as instruções de instalação no [a executar o VS Code no macOS](https://code.visualstudio.com/docs/setup/mac) página</span><span class="sxs-lookup"><span data-stu-id="ec253-114">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec253-115">No macOS, tem de instalar OpenSSL para a extensão do PowerShell para funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="ec253-115">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
> <span data-ttu-id="ec253-116">A forma mais fácil para realizar esta tarefa é instalar [Homebrew](http://brew.sh/) e, em seguida, execute `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="ec253-116">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
> <span data-ttu-id="ec253-117">O VS Code agora pode carregar a extensão do PowerShell com êxito.</span><span class="sxs-lookup"><span data-stu-id="ec253-117">VS Code can now load the the PowerShell extension successfully.</span></span>

- <span data-ttu-id="ec253-118">**Windows**: Siga as instruções de instalação no [a executar o VS Code no Windows](https://code.visualstudio.com/docs/setup/windows) página</span><span class="sxs-lookup"><span data-stu-id="ec253-118">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="ec253-119">2. Instalação da extensão do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec253-119">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="ec253-120">Inicie o Visual Studio Code aplicações por:</span><span class="sxs-lookup"><span data-stu-id="ec253-120">Launch the Visual Studio Code app by:</span></span>
    - <span data-ttu-id="ec253-121">**Windows**: escrevendo `code` na sessão do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec253-121">**Windows**: typing `code` in your PowerShell session</span></span>
    - <span data-ttu-id="ec253-122">**Linux**: escrevendo `code` no seu terminal</span><span class="sxs-lookup"><span data-stu-id="ec253-122">**Linux**: typing `code` in your terminal</span></span>
    - <span data-ttu-id="ec253-123">**macOS**: escrevendo `code` no seu terminal</span><span class="sxs-lookup"><span data-stu-id="ec253-123">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="ec253-124">Iniciar **rápida abra** premindo **Ctrl + P** (**Cmd + P** no Mac).</span><span class="sxs-lookup"><span data-stu-id="ec253-124">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="ec253-125">Na rápida aberta, escreva `ext install powershell` e acessos **Enter**.</span><span class="sxs-lookup"><span data-stu-id="ec253-125">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="ec253-126">O **extensões** vista abre na barra lateral.</span><span class="sxs-lookup"><span data-stu-id="ec253-126">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="ec253-127">Selecione a extensão do PowerShell da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ec253-127">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="ec253-128">Deverá ver algo, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="ec253-128">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="ec253-130">Clique em de **instalar** botão na extensão do PowerShell da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ec253-130">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="ec253-131">Depois da instalação, consulte o **instalar** botão passa a **recarregar**.</span><span class="sxs-lookup"><span data-stu-id="ec253-131">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="ec253-132">Clique em **recarregar**.</span><span class="sxs-lookup"><span data-stu-id="ec253-132">Click on **Reload**.</span></span>
- <span data-ttu-id="ec253-133">Depois do Visual Studio Code tem recarregar, está pronto para editar.</span><span class="sxs-lookup"><span data-stu-id="ec253-133">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="ec253-134">Por exemplo, para criar um novo ficheiro, clique em **ficheiro -> novo**.</span><span class="sxs-lookup"><span data-stu-id="ec253-134">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="ec253-135">Para guardar, clique em **ficheiro -> guardar** e, em seguida, forneça um nome de ficheiro, vamos diga `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="ec253-135">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="ec253-136">Para fechar o ficheiro, clique no "x" junto ao nome do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="ec253-136">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="ec253-137">Para sair do Visual Studio Code, **ficheiro -> saída**.</span><span class="sxs-lookup"><span data-stu-id="ec253-137">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="ec253-138">Utilizar uma versão específica instalada do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec253-138">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="ec253-139">Se pretender utilizar uma instalação específica do PowerShell com o Visual Studio Code, terá de adicionar uma nova variável ao seu ficheiro de definições de utilizador.</span><span class="sxs-lookup"><span data-stu-id="ec253-139">If you wish to use a specific installation of PowerShell with Visual Studio Code, you need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="ec253-140">Clique em **ficheiro -> Preferências -> definições**</span><span class="sxs-lookup"><span data-stu-id="ec253-140">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="ec253-141">Aparecem dois painéis do editor.</span><span class="sxs-lookup"><span data-stu-id="ec253-141">Two editor panes appear.</span></span>
   <span data-ttu-id="ec253-142">No painel de mais à direita (`settings.json`), inserir a definição abaixo apropriado para o SO algures entre as dois chavetas (`{` e `}`) e substitua *<version>* com o instalado Versão do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ec253-142">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace *<version>* with the installed PowerShell version:</span></span>

  ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
  ```
1. <span data-ttu-id="ec253-143">Substitua a definição com o caminho para o executável pretendido do PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec253-143">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="ec253-144">Guarde o ficheiro de definições e reinicie o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ec253-144">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="ec253-145">Definições de configuração para o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ec253-145">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="ec253-146">Utilizando os passos no parágrafo anterior, pode adicionar definições de configuração no `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="ec253-146">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="ec253-147">Recomendamos as seguintes definições de configuração para o Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="ec253-147">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="ec253-148">Depuração com o código do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ec253-148">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="ec253-149">Área de trabalho não depuração</span><span class="sxs-lookup"><span data-stu-id="ec253-149">No-workspace debugging</span></span>

<span data-ttu-id="ec253-150">A partir da versão do Visual Studio Code 1.9 pode depurar scripts do PowerShell sem ter de abrir a pasta que contém o script do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec253-150">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="ec253-151">Basta abrir o ficheiro de script do PowerShell com **ficheiro -> Abra o ficheiro...** , defina um ponto de interrupção de uma linha (prima F9) e, em seguida, prima F5 para iniciar a depuração.</span><span class="sxs-lookup"><span data-stu-id="ec253-151">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="ec253-152">Deverá ver o painel de ações de depuração aparecer que lhe permite interromper o depurador, passo, retomar e pare a depuração.</span><span class="sxs-lookup"><span data-stu-id="ec253-152">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="ec253-153">A depuração de área de trabalho</span><span class="sxs-lookup"><span data-stu-id="ec253-153">Workspace debugging</span></span>

<span data-ttu-id="ec253-154">Área de trabalho depuração refere-se a depuração no contexto de uma pasta que tem aberto no Visual Studio Code utilizando **pasta aberta...**  do **ficheiro** menu.</span><span class="sxs-lookup"><span data-stu-id="ec253-154">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="ec253-155">A pasta que abrir é, geralmente, a pasta de projeto do PowerShell e/ou a raiz do repositório de Git.</span><span class="sxs-lookup"><span data-stu-id="ec253-155">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="ec253-156">Mesmo neste modo, pode começar a depurar o script do PowerShell atualmente selecionado ao basta premir F5.</span><span class="sxs-lookup"><span data-stu-id="ec253-156">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="ec253-157">No entanto, a depuração de área de trabalho permite-lhe definir configurações com várias depuração diferente de depuração apenas os ficheiros atualmente abertos.</span><span class="sxs-lookup"><span data-stu-id="ec253-157">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="ec253-158">Por exemplo, pode adicionar um configurações para:</span><span class="sxs-lookup"><span data-stu-id="ec253-158">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="ec253-159">Iniciar o depurador testes Pester</span><span class="sxs-lookup"><span data-stu-id="ec253-159">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="ec253-160">Iniciar um ficheiro específico com argumentos no depurador</span><span class="sxs-lookup"><span data-stu-id="ec253-160">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="ec253-161">Inicie uma sessão interativa no depurador</span><span class="sxs-lookup"><span data-stu-id="ec253-161">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="ec253-162">Anexar o depurador a um processo de anfitrião PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec253-162">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="ec253-163">Siga estes passos para criar o ficheiro de configuração de depuração:</span><span class="sxs-lookup"><span data-stu-id="ec253-163">Follow these steps to create your debug configuration file:</span></span>

1. <span data-ttu-id="ec253-164">Abra o **depurar** vista premindo **Ctrl + Shift + D** (**Cmd + Shift + D** no Mac).</span><span class="sxs-lookup"><span data-stu-id="ec253-164">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
1. <span data-ttu-id="ec253-165">Prima a **configurar** engrenagem ícone na barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="ec253-165">Press the **Configure** gear icon in the toolbar.</span></span>
1. <span data-ttu-id="ec253-166">Visual Studio Code pede-lhe para **selecione ambiente**.</span><span class="sxs-lookup"><span data-stu-id="ec253-166">Visual Studio Code prompts you to **Select Environment**.</span></span>
   <span data-ttu-id="ec253-167">Escolha **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="ec253-167">Choose **PowerShell**.</span></span>

   <span data-ttu-id="ec253-168">Ao fazê-lo, o Visual Studio Code cria um diretório e um ficheiro de ".vscode\launch.json" na raiz da pasta à sua área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ec253-168">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
   <span data-ttu-id="ec253-169">Este é onde está armazenada a configuração de depuração.</span><span class="sxs-lookup"><span data-stu-id="ec253-169">This is where your debug configuration is stored.</span></span> <span data-ttu-id="ec253-170">Se os ficheiros estiverem num repositório de Git, que, normalmente, pretende consolidar o ficheiro launch.json.</span><span class="sxs-lookup"><span data-stu-id="ec253-170">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
   <span data-ttu-id="ec253-171">O conteúdo do ficheiro launch.json é:</span><span class="sxs-lookup"><span data-stu-id="ec253-171">The contents of the launch.json file are:</span></span>

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

<span data-ttu-id="ec253-172">Representa os cenários comuns de depuração.</span><span class="sxs-lookup"><span data-stu-id="ec253-172">This represents the common debug scenarios.</span></span>
<span data-ttu-id="ec253-173">No entanto, quando abrir este ficheiro no editor, verá um **configuração adicionar...**  botão.</span><span class="sxs-lookup"><span data-stu-id="ec253-173">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
<span data-ttu-id="ec253-174">Pode premir neste botão para adicionar mais configurações de depuração do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec253-174">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="ec253-175">É uma configuração útil para adicionar **PowerShell: iniciar o Script**.</span><span class="sxs-lookup"><span data-stu-id="ec253-175">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
<span data-ttu-id="ec253-176">Com esta configuração, pode especificar um ficheiro específico com argumentos opcionais que deve ser iniciado sempre que premir F5 não independentemente do qual o ficheiro está atualmente ativo no editor.</span><span class="sxs-lookup"><span data-stu-id="ec253-176">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="ec253-177">Depois da configuração de depuração é estabelecida, pode selecionar que configuração que pretende utilizar durante uma sessão de depuração, selecionando um da configuração de depuração pendente no **depurar** barra de ferramentas da vista.</span><span class="sxs-lookup"><span data-stu-id="ec253-177">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="ec253-178">Existem alguns blogues que podem ser úteis ajudar a começar a utilizar a extensão de PowerShell para o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ec253-178">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code</span></span>

- <span data-ttu-id="ec253-179">Código do Visual Studio: [extensão do PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="ec253-179">Visual Studio Code: [PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="ec253-180">[Escrever e depurar scripts do PowerShell no Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="ec253-180">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="ec253-181">[Orientações de código depuração do Visual Studio][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="ec253-181">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="ec253-182">[PowerShell depuração no Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="ec253-182">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="ec253-183">[Começar com o PowerShell desenvolvimento no Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="ec253-183">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="ec253-184">[Visual Studio Code editar funcionalidades para o desenvolvimento de PowerShell – parte 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="ec253-184">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="ec253-185">[Visual Studio Code funcionalidades para o desenvolvimento de PowerShell – parte 2 de edição][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="ec253-185">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="ec253-186">[Depurar o script do PowerShell no Visual Studio Code – parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="ec253-186">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="ec253-187">[Depurar o script do PowerShell no Visual Studio Code – parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="ec253-187">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="ec253-188">Extensão de PowerShell para o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ec253-188">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="ec253-189">Código de origem a extensão de PowerShell pode ser encontrado no [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="ec253-189">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
