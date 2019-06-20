---
title: Utilizar o Visual Studio Code para a edição e depuração remotas
description: Utilizar o Visual Studio Code para a edição e depuração remotas
ms.date: 06/13/2019
ms.openlocfilehash: ae3b7a3709498fcd547a48d0849b0dc880217225
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263991"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="5ef0c-103">Utilizar o Visual Studio Code para a edição e depuração remotas</span><span class="sxs-lookup"><span data-stu-id="5ef0c-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="5ef0c-104">Para aqueles que estão familiarizados com o ISE, deve se lembrar que pode executar `psedit file.ps1` a partir da consola integrada para abrir ficheiros - locais ou remotos - botão direito do rato no ISE.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-104">For those of you that are familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="5ef0c-105">Esse recurso também está disponível na extensão do PowerShell para VSCode.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-105">This feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="5ef0c-106">Este guia mostra-lhe como fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-106">This guide shows you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5ef0c-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5ef0c-107">Prerequisites</span></span>

<span data-ttu-id="5ef0c-108">Este guia assume que tem:</span><span class="sxs-lookup"><span data-stu-id="5ef0c-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="5ef0c-109">um recurso remoto (ex: uma VM, um contentor) que têm acesso a</span><span class="sxs-lookup"><span data-stu-id="5ef0c-109">A remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="5ef0c-110">PowerShell em execução no mesmo e a máquina de anfitrião</span><span class="sxs-lookup"><span data-stu-id="5ef0c-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="5ef0c-111">VSCode e a extensão de PowerShell para VSCode</span><span class="sxs-lookup"><span data-stu-id="5ef0c-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="5ef0c-112">Esta funcionalidade funciona no Windows PowerShell e no PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="5ef0c-113">Esta funcionalidade também funciona ao ligar a uma máquina remota através de WinRM, PowerShell Direct ou SSH.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="5ef0c-114">Se quiser utilizar o SSH, mas estiver a utilizar o Windows, consulte a [versão de Win32 do SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="5ef0c-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5ef0c-115">O `Open-EditorFile` e `psedit` comandos só funcionam **consola integrada de PowerShell** criado pela extensão do PowerShell para VSCode.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-115">The `Open-EditorFile` and `psedit` commands only work in the **PowerShell Integrated Console** created by the PowerShell extension for VSCode.</span></span>

## <a name="usage-examples"></a><span data-ttu-id="5ef0c-116">Exemplos de utilização</span><span class="sxs-lookup"><span data-stu-id="5ef0c-116">Usage examples</span></span>

<span data-ttu-id="5ef0c-117">Estes exemplos mostram remotos, edição e depuração de um MacBook Pro para uma VM do Ubuntu em execução no Azure.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-117">These examples show remote editing and debugging from a MacBook Pro to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="5ef0c-118">O processo é idêntico no Windows.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-118">The process is identical on Windows.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="5ef0c-119">Ficheiro local com Open EditorFile de edição</span><span class="sxs-lookup"><span data-stu-id="5ef0c-119">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="5ef0c-120">Com a extensão de PowerShell para utilizar o VSCode e abrir a consola integrada do PowerShell, também podemos digitar `Open-EditorFile foo.ps1` ou `psedit foo.ps1` para abrir o ficheiro de local foo.ps1 diretamente no editor.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-120">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Aberto EditorFile foo.ps1 funciona localmente](images/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> <span data-ttu-id="5ef0c-122">O ficheiro `foo.ps1` já devem existir.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-122">The file `foo.ps1` must already exist.</span></span>

<span data-ttu-id="5ef0c-123">A partir daí, podemos:</span><span class="sxs-lookup"><span data-stu-id="5ef0c-123">From there, we can:</span></span>

- <span data-ttu-id="5ef0c-124">Adicionar pontos de interrupção para o medianiz</span><span class="sxs-lookup"><span data-stu-id="5ef0c-124">Add breakpoints to the gutter</span></span>

  ![adicionar o ponto de interrupção para medianiz](images/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- <span data-ttu-id="5ef0c-126">Pressione F5 para depurar o script do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-126">Hit F5 to debug the PowerShell script.</span></span>

  ![depurar o script do PowerShell local](images/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

<span data-ttu-id="5ef0c-128">Durante a depuração, pode interagir com a consola de depuração, confira as variáveis no âmbito à esquerda, e todos os outro padrão ferramentas de depuração.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-128">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="5ef0c-129">Ficheiro remoto edição com EditorFile aberto</span><span class="sxs-lookup"><span data-stu-id="5ef0c-129">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="5ef0c-130">Agora vamos entrar em ficheiro remoto, edição e depuração.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-130">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="5ef0c-131">Os passos são praticamente os mesmos, existe apenas uma coisa que precisamos fazer primeiro - introduzir nossa sessão de PowerShell para o servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-131">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="5ef0c-132">Existe um cmdlet para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-132">There's a cmdlet for to do so.</span></span> <span data-ttu-id="5ef0c-133">Ele é chamado `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-133">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="5ef0c-134">A explicação menos potente para baixo do cmdlet é:</span><span class="sxs-lookup"><span data-stu-id="5ef0c-134">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="5ef0c-135">`Enter-PSSession -ComputerName foo` inicia uma sessão através do WinRM</span><span class="sxs-lookup"><span data-stu-id="5ef0c-135">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="5ef0c-136">`Enter-PSSession -ContainerId foo` e `Enter-PSSession -VmId foo` iniciar uma sessão através do PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="5ef0c-136">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="5ef0c-137">`Enter-PSSession -HostName foo` inicia uma sessão através de SSH</span><span class="sxs-lookup"><span data-stu-id="5ef0c-137">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="5ef0c-138">Para obter mais informações, consulte a documentação para [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="5ef0c-138">For more information, see the documentation for [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span></span>

<span data-ttu-id="5ef0c-139">Uma vez que vamos partir de macOS para uma VM do Ubuntu no Azure, estamos a utilizar SSH para a gestão remota.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-139">Since we are going from macOS to an Ubuntu VM in Azure, we are using SSH for remoting.</span></span>

<span data-ttu-id="5ef0c-140">Em primeiro lugar, na consola do integrada, execute `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-140">First, in the Integrated Console, run `Enter-PSSession`.</span></span> <span data-ttu-id="5ef0c-141">Está conectado à sessão remota quando `[<hostname>]` mostra até à esquerda da sua linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-141">You're connected to the remote session when `[<hostname>]` shows up to the left of your prompt.</span></span>

![A chamada para Enter-PSSession](images/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

<span data-ttu-id="5ef0c-143">Agora, podemos fazer as mesmas etapas que estejamos editando um script local.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-143">Now, we can do the same steps as if we are editing a local script.</span></span>

1. <span data-ttu-id="5ef0c-144">Execute `Open-EditorFile test.ps1` ou `psedit test.ps1` para abrir a ligação remota `test.ps1` ficheiro</span><span class="sxs-lookup"><span data-stu-id="5ef0c-144">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file</span></span>

  ![O ficheiro de test.ps1 de EditorFile aberto](images/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. <span data-ttu-id="5ef0c-146">Editar os pontos de interrupção do ficheiro/conjunto</span><span class="sxs-lookup"><span data-stu-id="5ef0c-146">Edit the file/set breakpoints</span></span>

   ![editar e configurar pontos de interrupção](images/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. <span data-ttu-id="5ef0c-148">Iniciar a depuração (F5) o ficheiro remoto</span><span class="sxs-lookup"><span data-stu-id="5ef0c-148">Start debugging (F5) the remote file</span></span>

   ![depuração do ficheiro remoto](images/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

<span data-ttu-id="5ef0c-150">Se tiver quaisquer problemas, pode abrir problemas a [repositório do GitHub](https://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="5ef0c-150">If you have any problems, you can open issues in the [GitHub repo](https://github.com/powershell/vscode-powershell).</span></span>
