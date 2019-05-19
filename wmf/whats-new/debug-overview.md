---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Melhorias na Depuração de Scripts do PowerShell
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856176"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="7632c-103">Melhorias na Depuração de Scripts do PowerShell</span><span class="sxs-lookup"><span data-stu-id="7632c-103">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="7632c-104">PowerShell 5.0 inclui vários melhoramentos que melhoram a experiência de depuração.</span><span class="sxs-lookup"><span data-stu-id="7632c-104">PowerShell 5.0 includes several improvements that enhance the debugging experience.</span></span>

## <a name="break-all"></a><span data-ttu-id="7632c-105">Interromper todos os</span><span class="sxs-lookup"><span data-stu-id="7632c-105">Break All</span></span>

<span data-ttu-id="7632c-106">A consola do PowerShell e o ISE do PowerShell agora permitem-lhe aceder ao depurador para a execução de scripts.</span><span class="sxs-lookup"><span data-stu-id="7632c-106">The PowerShell console and PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="7632c-107">Isso funciona em sessões locais e remotos.</span><span class="sxs-lookup"><span data-stu-id="7632c-107">This works in both local and remote sessions.</span></span>

<span data-ttu-id="7632c-108">Na consola, prima <kbd>Ctrl</kbd>+<kbd>quebrar</kbd>.</span><span class="sxs-lookup"><span data-stu-id="7632c-108">In the console, press <kbd>Ctrl</kbd>+<kbd>Break</kbd>.</span></span>

<span data-ttu-id="7632c-109">No ISE, pressione <kbd>Ctrl</kbd>+<kbd>B</kbd>, ou utilizar o **depuração -> interromper todos os** comando de menu.</span><span class="sxs-lookup"><span data-stu-id="7632c-109">In ISE, press <kbd>Ctrl</kbd>+<kbd>B</kbd>, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a><span data-ttu-id="7632c-110">Depuração remota e a edição de arquivos remoto no ISE do PowerShell</span><span class="sxs-lookup"><span data-stu-id="7632c-110">Remote debugging and remote file editing in PowerShell ISE</span></span>

<span data-ttu-id="7632c-111">ISE do PowerShell agora permite-lhe abrir e editar arquivos numa sessão remota ao executar o comando PSEdit.</span><span class="sxs-lookup"><span data-stu-id="7632c-111">PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="7632c-112">Por exemplo, pode abrir um arquivo para edição da linha de comando numa sessão remota da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="7632c-112">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="7632c-113">Além disso, agora pode editar e guardar as alterações num arquivo remoto que é aberto automaticamente no ISE do PowerShell quando atingir um ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="7632c-113">In addition, you can now edit and save changes in a remote file that is automatically opened in PowerShell ISE when you hit a breakpoint.</span></span> <span data-ttu-id="7632c-114">Agora, pode depurar um ficheiro de script que está em execução num computador remoto, edite o ficheiro para corrigir um erro e, em seguida, volte a executar o script modificado.</span><span class="sxs-lookup"><span data-stu-id="7632c-114">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="7632c-115">Depuração de scripts avançados</span><span class="sxs-lookup"><span data-stu-id="7632c-115">Advanced Script Debugging</span></span>

<span data-ttu-id="7632c-116">Existem novos e avançados recursos de depuração que permitem anexar a qualquer processo de computador local que carregou o PowerShell e depurar os espaços de execução arbitrários nesse processo.</span><span class="sxs-lookup"><span data-stu-id="7632c-116">There are new, advanced debugging features that let you attach to any local computer process that has loaded PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="7632c-117">Depuração do espaço de execução</span><span class="sxs-lookup"><span data-stu-id="7632c-117">Runspace Debugging</span></span>

<span data-ttu-id="7632c-118">Foram adicionados novos cmdlets que permitem-lhe a lista de espaços de execução atuais num processo e anexar a consola do PowerShell ou o depurador do ISE do PowerShell para esse espaço de execução para a depuração de scripts:</span><span class="sxs-lookup"><span data-stu-id="7632c-118">New cmdlets have been added that let you list current runspaces in a process, and attach the PowerShell console or PowerShell ISE debugger to that runspace for script debugging:</span></span>

- <span data-ttu-id="7632c-119">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="7632c-119">Get-Runspace</span></span>
- <span data-ttu-id="7632c-120">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="7632c-120">Debug-Runspace</span></span>
- <span data-ttu-id="7632c-121">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="7632c-121">Enable-RunspaceDebug</span></span>
- <span data-ttu-id="7632c-122">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="7632c-122">Disable-RunspaceDebug</span></span>
- <span data-ttu-id="7632c-123">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="7632c-123">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="7632c-124">Anexar a processo que hospeda o PowerShell</span><span class="sxs-lookup"><span data-stu-id="7632c-124">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="7632c-125">Agora pode anexar a qualquer processo de computador que tenha carregado do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7632c-125">You can now attach to any computer process that has PowerShell loaded.</span></span> <span data-ttu-id="7632c-126">Pode fazê-lo ao introduzir para uma sessão interativa com o processo de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="7632c-126">You do this by entering into an interactive session with the host process.</span></span> <span data-ttu-id="7632c-127">Para mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="7632c-127">For more information, see:</span></span>

- [<span data-ttu-id="7632c-128">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="7632c-128">Enter-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [<span data-ttu-id="7632c-129">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="7632c-129">Exit-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
