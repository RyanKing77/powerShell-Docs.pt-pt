---
title: Usando o Visual Studio Code para edição e a depuração remota
description: Usando o Visual Studio Code para edição e a depuração remota
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655542"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="26ce6-103">Usando o Visual Studio Code para edição e a depuração remota</span><span class="sxs-lookup"><span data-stu-id="26ce6-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="26ce6-104">Para aqueles que estão familiarizados com o ISE, deve se lembrar que pode executar `psedit file.ps1` a partir da consola integrada para abrir ficheiros - locais ou remotos - botão direito do rato no ISE.</span><span class="sxs-lookup"><span data-stu-id="26ce6-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="26ce6-105">Na verdade, esse recurso também está disponível na extensão do PowerShell para VSCode.</span><span class="sxs-lookup"><span data-stu-id="26ce6-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="26ce6-106">Este guia irá mostrar como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="26ce6-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="26ce6-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="26ce6-107">Prerequisites</span></span>

<span data-ttu-id="26ce6-108">Este guia assume que tem:</span><span class="sxs-lookup"><span data-stu-id="26ce6-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="26ce6-109">um recurso remoto (ex: uma VM, um contentor) que têm acesso a</span><span class="sxs-lookup"><span data-stu-id="26ce6-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="26ce6-110">PowerShell em execução no mesmo e a máquina de anfitrião</span><span class="sxs-lookup"><span data-stu-id="26ce6-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="26ce6-111">VSCode e a extensão de PowerShell para VSCode</span><span class="sxs-lookup"><span data-stu-id="26ce6-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="26ce6-112">Esta funcionalidade funciona no Windows PowerShell e no PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="26ce6-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="26ce6-113">Esta funcionalidade também funciona ao ligar a uma máquina remota através de WinRM, PowerShell Direct ou SSH.</span><span class="sxs-lookup"><span data-stu-id="26ce6-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="26ce6-114">Se quiser utilizar o SSH, mas estiver a utilizar o Windows, consulte a [versão de Win32 do SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="26ce6-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="26ce6-115">Vamos</span><span class="sxs-lookup"><span data-stu-id="26ce6-115">Let's go</span></span>

<span data-ttu-id="26ce6-116">Nesta seção, vou percorrer remoto de edição e depuração de meu MacBook Pro, para uma VM do Ubuntu em execução no Azure.</span><span class="sxs-lookup"><span data-stu-id="26ce6-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="26ce6-117">Eu poderá não estar a utilizar o Windows, mas **o processo é idêntico**.</span><span class="sxs-lookup"><span data-stu-id="26ce6-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="26ce6-118">Ficheiro local com Open EditorFile de edição</span><span class="sxs-lookup"><span data-stu-id="26ce6-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="26ce6-119">Com a extensão de PowerShell para utilizar o VSCode e abrir a consola integrada do PowerShell, também podemos digitar `Open-EditorFile foo.ps1` ou `psedit foo.ps1` para abrir o ficheiro de local foo.ps1 diretamente no editor.</span><span class="sxs-lookup"><span data-stu-id="26ce6-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Aberto EditorFile foo.ps1 funciona localmente](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="26ce6-121">foo.ps1 já devem existir.</span><span class="sxs-lookup"><span data-stu-id="26ce6-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="26ce6-122">A partir daí, podemos:</span><span class="sxs-lookup"><span data-stu-id="26ce6-122">From there, we can:</span></span>

<span data-ttu-id="26ce6-123">adicionar pontos de interrupção para o medianiz ![adicionar o ponto de interrupção para medianiz](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="26ce6-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="26ce6-124">e pressionar F5 para depurar o script do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26ce6-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="26ce6-125">![depurar o script do PowerShell local](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="26ce6-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="26ce6-126">Durante a depuração, pode interagir com a consola de depuração, confira as variáveis no âmbito à esquerda, e todos os outro padrão ferramentas de depuração.</span><span class="sxs-lookup"><span data-stu-id="26ce6-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="26ce6-127">Ficheiro remoto edição com EditorFile aberto</span><span class="sxs-lookup"><span data-stu-id="26ce6-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="26ce6-128">Agora vamos entrar em ficheiro remoto, edição e depuração.</span><span class="sxs-lookup"><span data-stu-id="26ce6-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="26ce6-129">Os passos são praticamente os mesmos, existe apenas uma coisa que precisamos fazer primeiro - introduzir nossa sessão de PowerShell para o servidor remoto.</span><span class="sxs-lookup"><span data-stu-id="26ce6-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="26ce6-130">Existe um cmdlet para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="26ce6-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="26ce6-131">Ele é chamado `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="26ce6-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="26ce6-132">A explicação menos potente para baixo do cmdlet é:</span><span class="sxs-lookup"><span data-stu-id="26ce6-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="26ce6-133">`Enter-PSSession -ComputerName foo` inicia uma sessão através do WinRM</span><span class="sxs-lookup"><span data-stu-id="26ce6-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="26ce6-134">`Enter-PSSession -ContainerId foo` e `Enter-PSSession -VmId foo` iniciar uma sessão através do PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="26ce6-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="26ce6-135">`Enter-PSSession -HostName foo` inicia uma sessão através de SSH</span><span class="sxs-lookup"><span data-stu-id="26ce6-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="26ce6-136">Para obter mais informações sobre `Enter-PSSession`, verifique os docs [aqui](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="26ce6-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="26ce6-137">Posso utilizar SSH para a gestão remota, uma vez que vou partir de macOS para uma VM do Ubuntu no Azure.</span><span class="sxs-lookup"><span data-stu-id="26ce6-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="26ce6-138">Em primeiro lugar, na consola do integrada, vamos executar nosso Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="26ce6-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="26ce6-139">Saberá que está na sessão porque `[something]` aparecerá para a esquerda da sua linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="26ce6-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![A chamada para Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="26ce6-141">A partir daí, podemos fazer os passos exatos como se podemos estava editando um script local.</span><span class="sxs-lookup"><span data-stu-id="26ce6-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="26ce6-142">Execute `Open-EditorFile test.ps1` ou `psedit test.ps1` para abrir a ligação remota `test.ps1` ficheiro ![EditorFile de abrir o ficheiro de test.ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="26ce6-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="26ce6-143">Editar os pontos de interrupção do ficheiro/conjunto</span><span class="sxs-lookup"><span data-stu-id="26ce6-143">Edit the file/set breakpoints</span></span> ![editar e configurar pontos de interrupção](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="26ce6-145">Iniciar a depuração (F5) o ficheiro remoto</span><span class="sxs-lookup"><span data-stu-id="26ce6-145">Start debugging (F5) the remote file</span></span>

![depuração do ficheiro remoto](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="26ce6-147">É tudo o que é preciso!</span><span class="sxs-lookup"><span data-stu-id="26ce6-147">That's all there's to it!</span></span> <span data-ttu-id="26ce6-148">Esperamos que este guia ajudou a limpar a quaisquer perguntas sobre a depuração remota e o PowerShell no VSCode de edição.</span><span class="sxs-lookup"><span data-stu-id="26ce6-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="26ce6-149">Se tiver quaisquer problemas, pode abrir problemas [no repositório GitHub](http://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="26ce6-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>
