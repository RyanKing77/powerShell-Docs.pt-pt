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
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="7e834-103">Utilizar o Visual Studio Code para o desenvolvimento de PowerShell</span><span class="sxs-lookup"><span data-stu-id="7e834-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="7e834-104">Para além da [ISE do PowerShell][ise], PowerShell também é bem suportada no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="7e834-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="7e834-105">Além disso, o ISE não é suportado com o PowerShell Core, embora o Visual Studio Code é suportada para o PowerShell Core em todas as plataformas (Windows, macOS e Linux)</span><span class="sxs-lookup"><span data-stu-id="7e834-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="7e834-106">Pode utilizar Visual Studio Code no Windows com o PowerShell versão 5 com o Windows 10 ou instalando [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) de nível inferior sistemas operacionais do Windows (por exemplo, Windows 8.1, etc.).</span><span class="sxs-lookup"><span data-stu-id="7e834-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="7e834-107">Antes de iniciá-lo, certifique-se de que PowerShell existe no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="7e834-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="7e834-108">Para cargas de trabalho modernas no Windows, macOS e Linux, consulte:</span><span class="sxs-lookup"><span data-stu-id="7e834-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="7e834-109">[Instalar o PowerShell Core no Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="7e834-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="7e834-110">[Instalar o PowerShell Core no macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="7e834-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="7e834-111">[Instalar o PowerShell Core no Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="7e834-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="7e834-112">Para as cargas de trabalho tradicionais do Windows PowerShell, consulte [instalar o Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="7e834-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="7e834-113">Edição com o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7e834-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="7e834-114">1. Instalar o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7e834-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="7e834-115">**Linux**: Siga as instruções de instalação do [executar o VS Code no Linux](https://code.visualstudio.com/docs/setup/linux) página</span><span class="sxs-lookup"><span data-stu-id="7e834-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="7e834-116">**macOS**: Siga as instruções de instalação do [executar o VS Code no macOS](https://code.visualstudio.com/docs/setup/mac) página</span><span class="sxs-lookup"><span data-stu-id="7e834-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="7e834-117">No macOS, tem de instalar o OpenSSL para a extensão de PowerShell funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="7e834-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="7e834-118">A maneira mais fácil de realizar isso é instalar [Homebrew](https://brew.sh/) e, em seguida, execute `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="7e834-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="7e834-119">VS Code agora pode carregar a extensão de PowerShell com êxito.</span><span class="sxs-lookup"><span data-stu-id="7e834-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="7e834-120">**Windows**: Siga as instruções de instalação do [executar o VS Code no Windows](https://code.visualstudio.com/docs/setup/windows) página</span><span class="sxs-lookup"><span data-stu-id="7e834-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="7e834-121">2. Instalar a extensão de PowerShell</span><span class="sxs-lookup"><span data-stu-id="7e834-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="7e834-122">Lançamento do Visual Studio Code aplicação por:</span><span class="sxs-lookup"><span data-stu-id="7e834-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="7e834-123">**Windows**: escrever `code` na sessão do PowerShell</span><span class="sxs-lookup"><span data-stu-id="7e834-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="7e834-124">**Linux**: escrever `code` no seu terminal</span><span class="sxs-lookup"><span data-stu-id="7e834-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="7e834-125">**macOS**: escrever `code` no seu terminal</span><span class="sxs-lookup"><span data-stu-id="7e834-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="7e834-126">Inicie **Quick Open** pressionando **Ctrl + P** (**Cmd + P** no Mac).</span><span class="sxs-lookup"><span data-stu-id="7e834-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="7e834-127">Em Quick Open, escreva `ext install powershell` e prima **Enter**.</span><span class="sxs-lookup"><span data-stu-id="7e834-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="7e834-128">O **extensões** é aberta uma vista na barra do lado.</span><span class="sxs-lookup"><span data-stu-id="7e834-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="7e834-129">Selecione a extensão de PowerShell da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7e834-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="7e834-130">Deverá ver algo, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="7e834-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="7e834-132">Clique nas **instalar** botão na extensão de PowerShell, da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7e834-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="7e834-133">Depois da instalação, consulte a **instale** botão passa a **recarregar**.</span><span class="sxs-lookup"><span data-stu-id="7e834-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="7e834-134">Clique em **recarregar**.</span><span class="sxs-lookup"><span data-stu-id="7e834-134">Click on **Reload**.</span></span>
- <span data-ttu-id="7e834-135">Depois do Visual Studio Code tem recarregar, está pronto para edição.</span><span class="sxs-lookup"><span data-stu-id="7e834-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="7e834-136">Por exemplo, para criar um novo ficheiro, clique em **arquivo -> novo**.</span><span class="sxs-lookup"><span data-stu-id="7e834-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="7e834-137">Para guardar, clique em **ficheiro -> Save** e, em seguida, forneça um nome de ficheiro, vamos dizer `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="7e834-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="7e834-138">Para fechar o ficheiro, clique em "x" junto ao nome do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="7e834-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="7e834-139">Para sair do Visual Studio Code **ficheiro -> saída**.</span><span class="sxs-lookup"><span data-stu-id="7e834-139">To exit Visual Studio Code, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="7e834-140">Instalação da extensão de PowerShell em sistemas restritos</span><span class="sxs-lookup"><span data-stu-id="7e834-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="7e834-141">Alguns sistemas são configurados de forma que requer que todas as assinaturas de código a ser verificado e, portanto, requer os serviços de Editor do PowerShell ser aprovado manualmente para ser executado no sistema.</span><span class="sxs-lookup"><span data-stu-id="7e834-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span>
<span data-ttu-id="7e834-142">Uma atualização de política de grupo que altera a política de execução é das causas prováveis se tiver instalado a extensão de PowerShell, mas Contatando um erro, como:</span><span class="sxs-lookup"><span data-stu-id="7e834-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="7e834-143">Para aprovar manualmente os serviços de Editor do PowerShell e, portanto, a extensão de PowerShell para VSCode, abra o PowerShell linha de comandos e execute:</span><span class="sxs-lookup"><span data-stu-id="7e834-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="7e834-144">Lhe for pedido com "You want to executar software a partir deste publicador não fidedigno?"</span><span class="sxs-lookup"><span data-stu-id="7e834-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span>
<span data-ttu-id="7e834-145">Tipo de `R` para executar o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="7e834-145">Type `R` to run the file.</span></span> <span data-ttu-id="7e834-146">Em seguida, abra o Visual Studio Code e verifique se a extensão de PowerShell está a funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="7e834-146">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="7e834-147">Se ainda tiver problemas de introdução, fale na [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="7e834-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="7e834-148">Escolher uma versão do PowerShell para utilizar com a extensão</span><span class="sxs-lookup"><span data-stu-id="7e834-148">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="7e834-149">Com o PowerShell Core, a instalação lado a lado com o Windows PowerShell, é agora possível para uma versão específica do PowerShell com a extensão de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7e834-149">With PowerShell Core installing side-by-side with Windows PowerShell, is it now possible to a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="7e834-150">Utilize o seguinte estes passos para escolher a versão:</span><span class="sxs-lookup"><span data-stu-id="7e834-150">Use the following these steps to choose the version:</span></span>

1. <span data-ttu-id="7e834-151">Abra o palete de comando (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> no Windows e Linux, <kbd>Cmd</kbd> + <kbd>Shift</kbd>+<kbd>P</kbd> no macOS).</span><span class="sxs-lookup"><span data-stu-id="7e834-151">Open the command pallet (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on Windows & Linux, <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS).</span></span>
1. <span data-ttu-id="7e834-152">Procure "Session".</span><span class="sxs-lookup"><span data-stu-id="7e834-152">Search for "Session".</span></span>
1. <span data-ttu-id="7e834-153">Clique em "PowerShell: Mostre Menu de sessão".</span><span class="sxs-lookup"><span data-stu-id="7e834-153">Click on "PowerShell: Show Session Menu".</span></span>
1. <span data-ttu-id="7e834-154">Escolha a versão do PowerShell que pretende utilizar na lista - por exemplo, "PowerShell"principal".</span><span class="sxs-lookup"><span data-stu-id="7e834-154">Choose the version of PowerShell you want to use from the list - for example, "PowerShell Core".</span></span>

>[!IMPORTANT]
> <span data-ttu-id="7e834-155">Esta funcionalidade analisa alguns caminhos bem conhecidos em diferentes sistemas operativos para detetar localizações de instalação do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7e834-155">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="7e834-156">Se tiver instalado o PowerShell para uma localização não típico, ela poderá não aparecem inicialmente no Menu de sessão.</span><span class="sxs-lookup"><span data-stu-id="7e834-156">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="7e834-157">Pode estender o menu de sessão por [adicionar seus próprios caminhos personalizados](#adding-your-own-powershell-paths-to-the-session-menu) conforme descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="7e834-157">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="7e834-158">Existe outra forma de obter ao menu de sessão.</span><span class="sxs-lookup"><span data-stu-id="7e834-158">There is another way to get to the session menu.</span></span> <span data-ttu-id="7e834-159">Quando um ficheiro do PowerShell está aberto no seu editor, verá um número de versão verde na inferior direito.</span><span class="sxs-lookup"><span data-stu-id="7e834-159">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="7e834-160">Clicar neste número de versão irão direcioná-lo para o menu de sessão.</span><span class="sxs-lookup"><span data-stu-id="7e834-160">Clicking this version number will bring you to the session menu.</span></span>

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="7e834-161">Adicionar seus próprios caminhos de PowerShell para o menu de sessão</span><span class="sxs-lookup"><span data-stu-id="7e834-161">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="7e834-162">Pode adicionar outros caminhos de executáveis do PowerShell para o menu de sessão através de uma definição do VS Code.</span><span class="sxs-lookup"><span data-stu-id="7e834-162">You can add other PowerShell executable paths to the session menu through a VS Code setting.</span></span>

<span data-ttu-id="7e834-163">Adicionar um item à lista `powershell.powerShellAdditionalExePaths` ou criar a lista, se não existir na sua `settings.json`:</span><span class="sxs-lookup"><span data-stu-id="7e834-163">Add an item to the list  `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="7e834-164">Cada item tem de ter:</span><span class="sxs-lookup"><span data-stu-id="7e834-164">Each item must have:</span></span>

* <span data-ttu-id="7e834-165">`exePath`: O caminho para o `pwsh` ou `powershell` executável.</span><span class="sxs-lookup"><span data-stu-id="7e834-165">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="7e834-166">`versionName`: O texto que aparecerá no menu de sessão.</span><span class="sxs-lookup"><span data-stu-id="7e834-166">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="7e834-167">Pode definir a versão do PowerShell de predefinida para utilizar com o `powershell.powerShellDefaultVersion` definição por definição esta opção para o texto apresentado no menu de sessão (também conhecido como o `versionName` na definição de último):</span><span class="sxs-lookup"><span data-stu-id="7e834-167">You can set the default PowerShell version to use using the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (aka the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="7e834-168">Assim que tiver configurado esta definição, reinicie o Visual Studio Code ou utilizar o o "desenvolvedor: Recarregue a janela"comando palete ação para recarregar a janela de vscode atual.</span><span class="sxs-lookup"><span data-stu-id="7e834-168">Once you've set this setting, restart Visual Studio Code or use the the "Developer: Reload Window" command pallet action to reload the current vscode window.</span></span>

<span data-ttu-id="7e834-169">Se abrir o menu de sessão, verá agora sua versões adicionais do PowerShell!</span><span class="sxs-lookup"><span data-stu-id="7e834-169">If you open the session menu, you will now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="7e834-170">Se criar PowerShell da origem, esta é uma excelente forma de testar sua compilação local do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7e834-170">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="7e834-171">Definições de configuração para o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7e834-171">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="7e834-172">Utilize os passos no parágrafo anterior pode adicionar definições de configuração no `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="7e834-172">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="7e834-173">Recomendamos as seguintes definições de configuração para o Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="7e834-173">We recommend the following configuration settings for Visual Studio Code:</span></span>

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

<span data-ttu-id="7e834-174">Se não pretender que estas definições afetam todos os tipos de ficheiros, VSCode também permite que configurações por idioma.</span><span class="sxs-lookup"><span data-stu-id="7e834-174">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="7e834-175">Criar uma configuração específica de idioma ao colocar configurações `[<language-name>]` campo.</span><span class="sxs-lookup"><span data-stu-id="7e834-175">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="7e834-176">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7e834-176">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="7e834-177">Para obter mais informações sobre o ficheiro codificação no VS Code, consulte [compreender a codificação do ficheiro](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="7e834-177">For more information about file encoding in VS Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="7e834-178">Depuração com o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7e834-178">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="7e834-179">Área de trabalho de não depuração</span><span class="sxs-lookup"><span data-stu-id="7e834-179">No-workspace debugging</span></span>

<span data-ttu-id="7e834-180">A partir da versão do Visual Studio Code 1.9 pode depurar scripts do PowerShell sem ter de abrir a pasta que contém o script do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7e834-180">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="7e834-181">Abra o ficheiro de script do PowerShell com **ficheiro -> abrir o ficheiro...** , defina um ponto de interrupção numa linha (pressionar o F9) e, em seguida, prima F5 para iniciar a depuração.</span><span class="sxs-lookup"><span data-stu-id="7e834-181">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span> <span data-ttu-id="7e834-182">Deverá ver o painel de ações de depuração aparecer que permite que invadir o depurador, passo, resume e stop depuração.</span><span class="sxs-lookup"><span data-stu-id="7e834-182">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="7e834-183">Depuração de área de trabalho</span><span class="sxs-lookup"><span data-stu-id="7e834-183">Workspace debugging</span></span>

<span data-ttu-id="7e834-184">Depuração de área de trabalho refere-se a depuração no contexto de uma pasta que abriu o no Visual Studio Code com **Abrir pasta...**  partir de **ficheiro** menu.</span><span class="sxs-lookup"><span data-stu-id="7e834-184">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="7e834-185">A pasta que abrir é, normalmente, a pasta do projeto do PowerShell e/ou a raiz do repositório de Git.</span><span class="sxs-lookup"><span data-stu-id="7e834-185">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="7e834-186">Mesmo neste modo, pode começar a depurar o script do PowerShell atualmente selecionado, simplesmente pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="7e834-186">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="7e834-187">No entanto, a depuração de área de trabalho permite-lhe definir várias configurações de depuração que não seja de depuração apenas os ficheiros atualmente abertos.</span><span class="sxs-lookup"><span data-stu-id="7e834-187">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="7e834-188">Por exemplo, pode adicionar um configurações para:</span><span class="sxs-lookup"><span data-stu-id="7e834-188">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="7e834-189">Inicie os testes de Pester no depurador</span><span class="sxs-lookup"><span data-stu-id="7e834-189">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="7e834-190">Iniciar um arquivo específico com argumentos no depurador</span><span class="sxs-lookup"><span data-stu-id="7e834-190">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="7e834-191">Iniciar uma sessão interativa no depurador</span><span class="sxs-lookup"><span data-stu-id="7e834-191">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="7e834-192">Anexar o depurador a um processo de anfitrião do PowerShell</span><span class="sxs-lookup"><span data-stu-id="7e834-192">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="7e834-193">Siga estes passos para criar o arquivo de configuração de depuração:</span><span class="sxs-lookup"><span data-stu-id="7e834-193">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="7e834-194">Abra o **depurar** vista pressionando **Ctrl + Shift + D** (**Cmd + Shift + D** no Mac).</span><span class="sxs-lookup"><span data-stu-id="7e834-194">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="7e834-195">Prima a **configurar** ícone de engrenagem na barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="7e834-195">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="7e834-196">Pede-lhe para Visual Studio Code **selecionar ambiente**.</span><span class="sxs-lookup"><span data-stu-id="7e834-196">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="7e834-197">Escolher **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="7e834-197">Choose **PowerShell**.</span></span>

  <span data-ttu-id="7e834-198">Ao fazê-lo, o código do Visual Studio cria um diretório e um arquivo de ".vscode\launch.json" na raiz da sua pasta de área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7e834-198">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="7e834-199">Isso é onde está armazenada a sua configuração de depuração.</span><span class="sxs-lookup"><span data-stu-id="7e834-199">This is where your debug configuration is stored.</span></span> <span data-ttu-id="7e834-200">Se os ficheiros estiverem num repositório de Git, normalmente pretende consolidar o ficheiro Launch JSON.</span><span class="sxs-lookup"><span data-stu-id="7e834-200">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="7e834-201">O conteúdo do ficheiro Launch JSON é:</span><span class="sxs-lookup"><span data-stu-id="7e834-201">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="7e834-202">Isso representa os cenários comuns de depuração.</span><span class="sxs-lookup"><span data-stu-id="7e834-202">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="7e834-203">No entanto, quando abrir esse arquivo no editor, verá um **configuração adicionar...**  botão.</span><span class="sxs-lookup"><span data-stu-id="7e834-203">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="7e834-204">Pode pressionar este botão para adicionar mais configurações de depuração do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7e834-204">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="7e834-205">É uma configuração útil para adicionar **PowerShell: Inicie o Script**.</span><span class="sxs-lookup"><span data-stu-id="7e834-205">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="7e834-206">Com esta configuração, pode especificar um ficheiro específico com os argumentos opcionais que deve ser iniciado sempre que pressionar F5, independentemente da qual arquivo atualmente ativo no editor.</span><span class="sxs-lookup"><span data-stu-id="7e834-206">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="7e834-207">Depois da configuração de depuração é estabelecida, pode selecionar que configuração que pretende utilizar durante uma sessão de depuração, selecionando uma na configuração de depuração menu pendente na **depurar** barra de ferramentas da exibição.</span><span class="sxs-lookup"><span data-stu-id="7e834-207">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="7e834-208">Existem alguns blogs que podem ser úteis para começar a utilizar a extensão de PowerShell para Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="7e834-208">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="7e834-209">[Extensão de PowerShell][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="7e834-209">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="7e834-210">[Escreva e Depure os scripts do PowerShell no Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="7e834-210">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="7e834-211">[Depuração de diretrizes de código do Visual Studio][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="7e834-211">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="7e834-212">[Depuração do PowerShell no Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="7e834-212">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="7e834-213">[Introdução ao desenvolvimento do PowerShell no Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="7e834-213">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="7e834-214">[Visual Studio Code, edição de recursos para desenvolvimento do PowerShell – parte 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="7e834-214">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="7e834-215">[Visual Studio Code, edição de recursos para desenvolvimento do PowerShell – parte 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="7e834-215">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="7e834-216">[Script do PowerShell depuração no Visual Studio Code – parte 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="7e834-216">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="7e834-217">[Script do PowerShell depuração no Visual Studio Code – parte 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="7e834-217">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="7e834-218">Extensão de PowerShell para Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7e834-218">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="7e834-219">Código-fonte a extensão de PowerShell pode ser encontrado no [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="7e834-219">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
