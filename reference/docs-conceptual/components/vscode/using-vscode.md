---
title: Utilizar o Visual Studio Code para o desenvolvimento de PowerShell
description: Utilizar o Visual Studio Code para o desenvolvimento de PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 1e9b9d811a39656327af2810bd6dc8aaf3fde3a4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086731"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="fe539-103">Utilizar o Visual Studio Code para o desenvolvimento de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe539-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="fe539-104">Para além da [ISE do PowerShell][ise], PowerShell também é bem suportada no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="fe539-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="fe539-105">Além disso, o ISE não é suportado com o PowerShell Core, embora o Visual Studio Code é suportada para o PowerShell Core em todas as plataformas (Windows, macOS e Linux)</span><span class="sxs-lookup"><span data-stu-id="fe539-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="fe539-106">Pode utilizar Visual Studio Code no Windows com o PowerShell versão 5 com o Windows 10 ou instalando [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) de nível inferior sistemas operacionais do Windows (por exemplo, Windows 8.1, etc.).</span><span class="sxs-lookup"><span data-stu-id="fe539-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="fe539-107">Antes de iniciá-lo, certifique-se de que PowerShell existe no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="fe539-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="fe539-108">Para cargas de trabalho modernas no Windows, macOS e Linux, consulte:</span><span class="sxs-lookup"><span data-stu-id="fe539-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="fe539-109">[Instalar o PowerShell Core no Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="fe539-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="fe539-110">[Instalar o PowerShell Core no macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="fe539-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="fe539-111">[Instalar o PowerShell Core no Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="fe539-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="fe539-112">Para as cargas de trabalho tradicionais do Windows PowerShell, consulte [instalar o Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="fe539-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="fe539-113">Edição com o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="fe539-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="fe539-114">1. Instalar o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="fe539-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="fe539-115">**Linux**: Siga as instruções de instalação do [executar o VS Code no Linux](https://code.visualstudio.com/docs/setup/linux) página</span><span class="sxs-lookup"><span data-stu-id="fe539-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="fe539-116">**macOS**: Siga as instruções de instalação do [executar o VS Code no macOS](https://code.visualstudio.com/docs/setup/mac) página</span><span class="sxs-lookup"><span data-stu-id="fe539-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="fe539-117">No macOS, tem de instalar o OpenSSL para a extensão de PowerShell funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="fe539-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="fe539-118">A maneira mais fácil de realizar isso é instalar [Homebrew](https://brew.sh/) e, em seguida, execute `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="fe539-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="fe539-119">VS Code agora pode carregar a extensão de PowerShell com êxito.</span><span class="sxs-lookup"><span data-stu-id="fe539-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="fe539-120">**Windows**: Siga as instruções de instalação do [executar o VS Code no Windows](https://code.visualstudio.com/docs/setup/windows) página</span><span class="sxs-lookup"><span data-stu-id="fe539-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="fe539-121">2. Instalar a extensão de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe539-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="fe539-122">Lançamento do Visual Studio Code aplicação por:</span><span class="sxs-lookup"><span data-stu-id="fe539-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="fe539-123">**Windows**: escrever `code` na sessão do PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe539-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="fe539-124">**Linux**: escrever `code` no seu terminal</span><span class="sxs-lookup"><span data-stu-id="fe539-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="fe539-125">**macOS**: escrever `code` no seu terminal</span><span class="sxs-lookup"><span data-stu-id="fe539-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="fe539-126">Inicie **Quick Open** pressionando **Ctrl + P** (**Cmd + P** no Mac).</span><span class="sxs-lookup"><span data-stu-id="fe539-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="fe539-127">Em Quick Open, escreva `ext install powershell` e prima **Enter**.</span><span class="sxs-lookup"><span data-stu-id="fe539-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="fe539-128">O **extensões** é aberta uma vista na barra do lado.</span><span class="sxs-lookup"><span data-stu-id="fe539-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="fe539-129">Selecione a extensão de PowerShell da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fe539-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="fe539-130">Deverá ver algo, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="fe539-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="fe539-132">Clique nas **instalar** botão na extensão de PowerShell, da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fe539-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="fe539-133">Depois da instalação, consulte a **instale** botão passa a **recarregar**.</span><span class="sxs-lookup"><span data-stu-id="fe539-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="fe539-134">Clique em **recarregar**.</span><span class="sxs-lookup"><span data-stu-id="fe539-134">Click on **Reload**.</span></span>
- <span data-ttu-id="fe539-135">Depois do Visual Studio Code tem recarregar, está pronto para edição.</span><span class="sxs-lookup"><span data-stu-id="fe539-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="fe539-136">Por exemplo, para criar um novo ficheiro, clique em **arquivo -> novo**.</span><span class="sxs-lookup"><span data-stu-id="fe539-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="fe539-137">Para guardar, clique em **ficheiro -> Save** e, em seguida, forneça um nome de ficheiro, vamos dizer `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="fe539-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="fe539-138">Para fechar o ficheiro, clique em "x" junto ao nome do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="fe539-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="fe539-139">Para sair do Visual Studio Code **ficheiro -> saída**.</span><span class="sxs-lookup"><span data-stu-id="fe539-139">To exit Visual Studio Code, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="fe539-140">Instalação da extensão de PowerShell em sistemas restritos</span><span class="sxs-lookup"><span data-stu-id="fe539-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="fe539-141">Alguns sistemas são configurados de forma que requer que todas as assinaturas de código a ser verificado e, portanto, requer os serviços de Editor do PowerShell ser aprovado manualmente para ser executado no sistema.</span><span class="sxs-lookup"><span data-stu-id="fe539-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span>
<span data-ttu-id="fe539-142">Uma atualização de política de grupo que altera a política de execução é das causas prováveis se tiver instalado a extensão de PowerShell, mas Contatando um erro, como:</span><span class="sxs-lookup"><span data-stu-id="fe539-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="fe539-143">Para aprovar manualmente os serviços de Editor do PowerShell e, portanto, a extensão de PowerShell para VSCode, abra o PowerShell linha de comandos e execute:</span><span class="sxs-lookup"><span data-stu-id="fe539-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="fe539-144">Lhe for pedido com "You want to executar software a partir deste publicador não fidedigno?"</span><span class="sxs-lookup"><span data-stu-id="fe539-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span>
<span data-ttu-id="fe539-145">Tipo de `R` para executar o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="fe539-145">Type `R` to run the file.</span></span> <span data-ttu-id="fe539-146">Em seguida, abra o Visual Studio Code e verifique se a extensão de PowerShell está a funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="fe539-146">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="fe539-147">Se ainda tiver problemas de introdução, fale na [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="fe539-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="fe539-148">Utilizar uma versão específica instalada do PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe539-148">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="fe539-149">Se pretender utilizar uma instalação específica do PowerShell com o Visual Studio Code, terá de adicionar uma nova variável para o arquivo de configurações do usuário.</span><span class="sxs-lookup"><span data-stu-id="fe539-149">If you wish to use a specific installation of PowerShell with Visual Studio Code, you need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="fe539-150">Clique em **ficheiro -> Preferências -> definições**</span><span class="sxs-lookup"><span data-stu-id="fe539-150">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="fe539-151">São apresentados dois painéis do editor.</span><span class="sxs-lookup"><span data-stu-id="fe539-151">Two editor panes appear.</span></span>
   <span data-ttu-id="fe539-152">No painel mais à direita (`settings.json`), inserir a definição abaixo apropriado para seu sistema operacional em algum lugar entre as duas primeiras (`{` e `}`) e substitua **\<versão\>** com a versão instalada do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fe539-152">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace **\<version\>** with the installed PowerShell version:</span></span>

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. <span data-ttu-id="fe539-153">Substitua a definição com o caminho para o PowerShell pretendido executável</span><span class="sxs-lookup"><span data-stu-id="fe539-153">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="fe539-154">Guarde o ficheiro de definições e reinicie o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="fe539-154">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="fe539-155">Definições de configuração para o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="fe539-155">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="fe539-156">Utilize os passos no parágrafo anterior pode adicionar definições de configuração no `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="fe539-156">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="fe539-157">Recomendamos as seguintes definições de configuração para o Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="fe539-157">We recommend the following configuration settings for Visual Studio Code:</span></span>

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

<span data-ttu-id="fe539-158">Se não pretender que estas definições afetam todos os tipos de ficheiros, VSCode também permite que configurações por idioma.</span><span class="sxs-lookup"><span data-stu-id="fe539-158">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="fe539-159">Criar uma configuração específica de idioma ao colocar configurações `[<language-name>]` campo.</span><span class="sxs-lookup"><span data-stu-id="fe539-159">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="fe539-160">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="fe539-160">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="fe539-161">Para obter mais informações sobre o ficheiro codificação no VS Code, consulte [compreender a codificação do ficheiro](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="fe539-161">For more information about file encoding in VS Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="fe539-162">Depuração com o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="fe539-162">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="fe539-163">Área de trabalho de não depuração</span><span class="sxs-lookup"><span data-stu-id="fe539-163">No-workspace debugging</span></span>

<span data-ttu-id="fe539-164">A partir da versão do Visual Studio Code 1.9 pode depurar scripts do PowerShell sem ter de abrir a pasta que contém o script do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe539-164">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="fe539-165">Abra o ficheiro de script do PowerShell com **ficheiro -> abrir o ficheiro...** , defina um ponto de interrupção numa linha (pressionar o F9) e, em seguida, prima F5 para iniciar a depuração.</span><span class="sxs-lookup"><span data-stu-id="fe539-165">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span> <span data-ttu-id="fe539-166">Deverá ver o painel de ações de depuração aparecer que permite que invadir o depurador, passo, resume e stop depuração.</span><span class="sxs-lookup"><span data-stu-id="fe539-166">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="fe539-167">Depuração de área de trabalho</span><span class="sxs-lookup"><span data-stu-id="fe539-167">Workspace debugging</span></span>

<span data-ttu-id="fe539-168">Depuração de área de trabalho refere-se a depuração no contexto de uma pasta que abriu o no Visual Studio Code com **Abrir pasta...**  partir de **ficheiro** menu.</span><span class="sxs-lookup"><span data-stu-id="fe539-168">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="fe539-169">A pasta que abrir é, normalmente, a pasta do projeto do PowerShell e/ou a raiz do repositório de Git.</span><span class="sxs-lookup"><span data-stu-id="fe539-169">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="fe539-170">Mesmo neste modo, pode começar a depurar o script do PowerShell atualmente selecionado, simplesmente pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="fe539-170">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="fe539-171">No entanto, a depuração de área de trabalho permite-lhe definir várias configurações de depuração que não seja de depuração apenas os ficheiros atualmente abertos.</span><span class="sxs-lookup"><span data-stu-id="fe539-171">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="fe539-172">Por exemplo, pode adicionar um configurações para:</span><span class="sxs-lookup"><span data-stu-id="fe539-172">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="fe539-173">Inicie os testes de Pester no depurador</span><span class="sxs-lookup"><span data-stu-id="fe539-173">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="fe539-174">Iniciar um arquivo específico com argumentos no depurador</span><span class="sxs-lookup"><span data-stu-id="fe539-174">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="fe539-175">Iniciar uma sessão interativa no depurador</span><span class="sxs-lookup"><span data-stu-id="fe539-175">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="fe539-176">Anexar o depurador a um processo de anfitrião do PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe539-176">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="fe539-177">Siga estes passos para criar o arquivo de configuração de depuração:</span><span class="sxs-lookup"><span data-stu-id="fe539-177">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="fe539-178">Abra o **depurar** vista pressionando **Ctrl + Shift + D** (**Cmd + Shift + D** no Mac).</span><span class="sxs-lookup"><span data-stu-id="fe539-178">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="fe539-179">Prima a **configurar** ícone de engrenagem na barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="fe539-179">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="fe539-180">Pede-lhe para Visual Studio Code **selecionar ambiente**.</span><span class="sxs-lookup"><span data-stu-id="fe539-180">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="fe539-181">Escolher **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="fe539-181">Choose **PowerShell**.</span></span>

  <span data-ttu-id="fe539-182">Ao fazê-lo, o código do Visual Studio cria um diretório e um arquivo de ".vscode\launch.json" na raiz da sua pasta de área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fe539-182">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="fe539-183">Isso é onde está armazenada a sua configuração de depuração.</span><span class="sxs-lookup"><span data-stu-id="fe539-183">This is where your debug configuration is stored.</span></span> <span data-ttu-id="fe539-184">Se os ficheiros estiverem num repositório de Git, normalmente pretende consolidar o ficheiro Launch JSON.</span><span class="sxs-lookup"><span data-stu-id="fe539-184">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="fe539-185">O conteúdo do ficheiro Launch JSON é:</span><span class="sxs-lookup"><span data-stu-id="fe539-185">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="fe539-186">Isso representa os cenários comuns de depuração.</span><span class="sxs-lookup"><span data-stu-id="fe539-186">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="fe539-187">No entanto, quando abrir esse arquivo no editor, verá um **configuração adicionar...**  botão.</span><span class="sxs-lookup"><span data-stu-id="fe539-187">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="fe539-188">Pode pressionar este botão para adicionar mais configurações de depuração do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe539-188">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="fe539-189">É uma configuração útil para adicionar **PowerShell: Inicie o Script**.</span><span class="sxs-lookup"><span data-stu-id="fe539-189">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="fe539-190">Com esta configuração, pode especificar um ficheiro específico com os argumentos opcionais que deve ser iniciado sempre que pressionar F5, independentemente da qual arquivo atualmente ativo no editor.</span><span class="sxs-lookup"><span data-stu-id="fe539-190">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="fe539-191">Depois da configuração de depuração é estabelecida, pode selecionar que configuração que pretende utilizar durante uma sessão de depuração, selecionando uma na configuração de depuração menu pendente na **depurar** barra de ferramentas da exibição.</span><span class="sxs-lookup"><span data-stu-id="fe539-191">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="fe539-192">Existem alguns blogs que podem ser úteis para começar a utilizar a extensão de PowerShell para Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="fe539-192">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="fe539-193">[Extensão de PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="fe539-193">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="fe539-194">[Escreva e Depure os scripts do PowerShell no Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="fe539-194">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="fe539-195">[Depuração de diretrizes de código do Visual Studio][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="fe539-195">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="fe539-196">[Depuração do PowerShell no Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="fe539-196">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="fe539-197">[Introdução ao desenvolvimento do PowerShell no Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="fe539-197">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="fe539-198">[Visual Studio Code, edição de recursos para desenvolvimento do PowerShell – parte 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="fe539-198">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="fe539-199">[Visual Studio Code, edição de recursos para desenvolvimento do PowerShell – parte 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="fe539-199">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="fe539-200">[Script do PowerShell depuração no Visual Studio Code – parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="fe539-200">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="fe539-201">[Script do PowerShell depuração no Visual Studio Code – parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="fe539-201">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="fe539-202">Extensão de PowerShell para Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="fe539-202">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="fe539-203">Código-fonte a extensão de PowerShell pode ser encontrado no [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="fe539-203">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
