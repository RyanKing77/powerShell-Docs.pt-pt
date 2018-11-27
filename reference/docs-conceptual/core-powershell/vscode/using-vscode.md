---
title: Utilizar o Visual Studio Code para o desenvolvimento de PowerShell
description: Utilizar o Visual Studio Code para o desenvolvimento de PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 6433a875c233283f94d70c7acd7d394c73029b6d
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320453"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="1b1bf-103">Utilizar o Visual Studio Code para o desenvolvimento de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b1bf-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="1b1bf-104">Para além da [ISE do PowerShell][ise], PowerShell também é bem suportada no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="1b1bf-105">Além disso, o ISE não é suportado com o PowerShell Core, embora o Visual Studio Code é suportada para o PowerShell Core em todas as plataformas (Windows, macOS e Linux)</span><span class="sxs-lookup"><span data-stu-id="1b1bf-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="1b1bf-106">Pode utilizar Visual Studio Code no Windows com o PowerShell versão 5 com o Windows 10 ou instalando [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) de nível inferior sistemas operacionais do Windows (por exemplo, Windows 8.1, etc.).</span><span class="sxs-lookup"><span data-stu-id="1b1bf-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="1b1bf-107">Antes de iniciá-lo, certifique-se de que PowerShell existe no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="1b1bf-108">Para cargas de trabalho modernas no Windows, macOS e Linux, consulte:</span><span class="sxs-lookup"><span data-stu-id="1b1bf-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="1b1bf-109">[Instalar o PowerShell Core no Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="1b1bf-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="1b1bf-110">[Instalar o PowerShell Core no macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="1b1bf-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="1b1bf-111">[Instalar o PowerShell Core no Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="1b1bf-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="1b1bf-112">Para as cargas de trabalho tradicionais do Windows PowerShell, consulte [instalar o Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="1b1bf-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="1b1bf-113">Edição com o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1b1bf-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="1b1bf-114">1. Instalar o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1b1bf-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="1b1bf-115">**Linux**: Siga as instruções de instalação do [executar o VS Code no Linux](https://code.visualstudio.com/docs/setup/linux) página</span><span class="sxs-lookup"><span data-stu-id="1b1bf-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="1b1bf-116">**macOS**: Siga as instruções de instalação do [executar o VS Code no macOS](https://code.visualstudio.com/docs/setup/mac) página</span><span class="sxs-lookup"><span data-stu-id="1b1bf-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="1b1bf-117">No macOS, tem de instalar o OpenSSL para a extensão de PowerShell funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="1b1bf-118">A maneira mais fácil de realizar isso é instalar [Homebrew](https://brew.sh/) e, em seguida, execute `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="1b1bf-119">VS Code agora pode carregar a extensão de PowerShell com êxito.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="1b1bf-120">**Windows**: Siga as instruções de instalação do [executar o VS Code no Windows](https://code.visualstudio.com/docs/setup/windows) página</span><span class="sxs-lookup"><span data-stu-id="1b1bf-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="1b1bf-121">2. Instalar a extensão de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b1bf-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="1b1bf-122">Lançamento do Visual Studio Code aplicação por:</span><span class="sxs-lookup"><span data-stu-id="1b1bf-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="1b1bf-123">**Windows**: escrever `code` na sessão do PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b1bf-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="1b1bf-124">**Linux**: escrever `code` no seu terminal</span><span class="sxs-lookup"><span data-stu-id="1b1bf-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="1b1bf-125">**macOS**: escrever `code` no seu terminal</span><span class="sxs-lookup"><span data-stu-id="1b1bf-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="1b1bf-126">Inicie **Quick Open** pressionando **Ctrl + P** (**Cmd + P** no Mac).</span><span class="sxs-lookup"><span data-stu-id="1b1bf-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="1b1bf-127">Em Quick Open, escreva `ext install powershell` e prima **Enter**.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="1b1bf-128">O **extensões** é aberta uma vista na barra do lado.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="1b1bf-129">Selecione a extensão de PowerShell da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="1b1bf-130">Deverá ver algo, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="1b1bf-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="1b1bf-132">Clique nas **instalar** botão na extensão de PowerShell, da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="1b1bf-133">Depois da instalação, consulte a **instale** botão passa a **recarregar**.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="1b1bf-134">Clique em **recarregar**.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-134">Click on **Reload**.</span></span>
- <span data-ttu-id="1b1bf-135">Depois do Visual Studio Code tem recarregar, está pronto para edição.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="1b1bf-136">Por exemplo, para criar um novo ficheiro, clique em **arquivo -> novo**.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="1b1bf-137">Para guardar, clique em **ficheiro -> Save** e, em seguida, forneça um nome de ficheiro, vamos dizer `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="1b1bf-138">Para fechar o ficheiro, clique em "x" junto ao nome do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="1b1bf-139">Para sair do Visual Studio Code **ficheiro -> saída**.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-139">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="1b1bf-140">Utilizar uma versão específica instalada do PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b1bf-140">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="1b1bf-141">Se pretender utilizar uma instalação específica do PowerShell com o Visual Studio Code, terá de adicionar uma nova variável para o arquivo de configurações do usuário.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-141">If you wish to use a specific installation of PowerShell with Visual Studio Code, you need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="1b1bf-142">Clique em **ficheiro -> Preferências -> definições**</span><span class="sxs-lookup"><span data-stu-id="1b1bf-142">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="1b1bf-143">São apresentados dois painéis do editor.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-143">Two editor panes appear.</span></span>
   <span data-ttu-id="1b1bf-144">No painel mais à direita (`settings.json`), inserir a definição abaixo apropriado para seu sistema operacional em algum lugar entre as duas primeiras (`{` e `}`) e substitua **\<versão\>** com a versão instalada do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1b1bf-144">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace **\<version\>** with the installed PowerShell version:</span></span>

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. <span data-ttu-id="1b1bf-145">Substitua a definição com o caminho para o PowerShell pretendido executável</span><span class="sxs-lookup"><span data-stu-id="1b1bf-145">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="1b1bf-146">Guarde o ficheiro de definições e reinicie o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1b1bf-146">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="1b1bf-147">Definições de configuração para o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1b1bf-147">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="1b1bf-148">Utilize os passos no parágrafo anterior pode adicionar definições de configuração no `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-148">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="1b1bf-149">Recomendamos as seguintes definições de configuração para o Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="1b1bf-149">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="1b1bf-150">Depuração com o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1b1bf-150">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="1b1bf-151">Área de trabalho de não depuração</span><span class="sxs-lookup"><span data-stu-id="1b1bf-151">No-workspace debugging</span></span>

<span data-ttu-id="1b1bf-152">A partir da versão do Visual Studio Code 1.9 pode depurar scripts do PowerShell sem ter de abrir a pasta que contém o script do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-152">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="1b1bf-153">Basta abrir o ficheiro de script do PowerShell com **ficheiro -> Abrir ficheiro...** , defina um ponto de interrupção numa linha (pressionar o F9) e, em seguida, prima F5 para iniciar a depuração.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-153">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="1b1bf-154">Deverá ver o painel de ações de depuração aparecer que permite que invadir o depurador, passo, resume e stop depuração.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-154">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="1b1bf-155">Depuração de área de trabalho</span><span class="sxs-lookup"><span data-stu-id="1b1bf-155">Workspace debugging</span></span>

<span data-ttu-id="1b1bf-156">Depuração de área de trabalho refere-se a depuração no contexto de uma pasta que abriu o no Visual Studio Code com **Abrir pasta...**  partir de **ficheiro** menu.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-156">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="1b1bf-157">A pasta que abrir é, normalmente, a pasta do projeto do PowerShell e/ou a raiz do repositório de Git.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-157">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="1b1bf-158">Mesmo neste modo, pode começar a depurar o script do PowerShell atualmente selecionado, simplesmente pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-158">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="1b1bf-159">No entanto, a depuração de área de trabalho permite-lhe definir várias configurações de depuração que não seja de depuração apenas os ficheiros atualmente abertos.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-159">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="1b1bf-160">Por exemplo, pode adicionar um configurações para:</span><span class="sxs-lookup"><span data-stu-id="1b1bf-160">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="1b1bf-161">Inicie os testes de Pester no depurador</span><span class="sxs-lookup"><span data-stu-id="1b1bf-161">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="1b1bf-162">Iniciar um arquivo específico com argumentos no depurador</span><span class="sxs-lookup"><span data-stu-id="1b1bf-162">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="1b1bf-163">Iniciar uma sessão interativa no depurador</span><span class="sxs-lookup"><span data-stu-id="1b1bf-163">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="1b1bf-164">Anexar o depurador a um processo de anfitrião do PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b1bf-164">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="1b1bf-165">Siga estes passos para criar o arquivo de configuração de depuração:</span><span class="sxs-lookup"><span data-stu-id="1b1bf-165">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="1b1bf-166">Abra o **depurar** vista pressionando **Ctrl + Shift + D** (**Cmd + Shift + D** no Mac).</span><span class="sxs-lookup"><span data-stu-id="1b1bf-166">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="1b1bf-167">Prima a **configurar** ícone de engrenagem na barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-167">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="1b1bf-168">Pede-lhe para Visual Studio Code **selecionar ambiente**.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-168">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="1b1bf-169">Escolher **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-169">Choose **PowerShell**.</span></span>

  <span data-ttu-id="1b1bf-170">Ao fazê-lo, o código do Visual Studio cria um diretório e um arquivo de ".vscode\launch.json" na raiz da sua pasta de área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-170">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="1b1bf-171">Isso é onde está armazenada a sua configuração de depuração.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-171">This is where your debug configuration is stored.</span></span> <span data-ttu-id="1b1bf-172">Se os ficheiros estiverem num repositório de Git, normalmente pretende consolidar o ficheiro Launch JSON.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-172">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="1b1bf-173">O conteúdo do ficheiro Launch JSON é:</span><span class="sxs-lookup"><span data-stu-id="1b1bf-173">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="1b1bf-174">Isso representa os cenários comuns de depuração.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-174">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="1b1bf-175">No entanto, quando abrir esse arquivo no editor, verá um **configuração adicionar...**  botão.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-175">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="1b1bf-176">Pode pressionar este botão para adicionar mais configurações de depuração do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-176">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="1b1bf-177">É uma configuração útil para adicionar **PowerShell: iniciar o Script**.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-177">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="1b1bf-178">Com esta configuração, pode especificar um ficheiro específico com os argumentos opcionais que deve ser iniciado sempre que pressionar F5, independentemente da qual arquivo atualmente ativo no editor.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-178">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="1b1bf-179">Depois da configuração de depuração é estabelecida, pode selecionar que configuração que pretende utilizar durante uma sessão de depuração, selecionando uma na configuração de depuração menu pendente na **depurar** barra de ferramentas da exibição.</span><span class="sxs-lookup"><span data-stu-id="1b1bf-179">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="1b1bf-180">Existem alguns blogs que podem ser úteis para começar a utilizar a extensão de PowerShell para Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="1b1bf-180">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="1b1bf-181">[Extensão de PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="1b1bf-181">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="1b1bf-182">[Escreva e Depure os scripts do PowerShell no Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="1b1bf-182">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="1b1bf-183">[Depuração de diretrizes de código do Visual Studio][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="1b1bf-183">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="1b1bf-184">[Depuração do PowerShell no Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="1b1bf-184">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="1b1bf-185">[Introdução ao desenvolvimento do PowerShell no Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="1b1bf-185">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="1b1bf-186">[Visual Studio Code, edição de recursos para desenvolvimento do PowerShell – parte 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="1b1bf-186">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="1b1bf-187">[Visual Studio Code, edição de recursos para desenvolvimento do PowerShell – parte 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="1b1bf-187">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="1b1bf-188">[Script do PowerShell depuração no Visual Studio Code – parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="1b1bf-188">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="1b1bf-189">[Script do PowerShell depuração no Visual Studio Code – parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="1b1bf-189">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise-guide.md
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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="1b1bf-190">Extensão de PowerShell para Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1b1bf-190">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="1b1bf-191">Código-fonte a extensão de PowerShell pode ser encontrado no [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="1b1bf-191">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
