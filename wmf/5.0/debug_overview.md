---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 22a027ebc97e15075980bc77ce272d8ecdae0b5f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058669"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="84409-102">Melhorias na Depuração de Scripts do PowerShell</span><span class="sxs-lookup"><span data-stu-id="84409-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="84409-103">Uma série de melhorias foram feita no PowerShell 5.0 para melhorar a experiência de depuração:</span><span class="sxs-lookup"><span data-stu-id="84409-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="84409-104">Interromper todos os</span><span class="sxs-lookup"><span data-stu-id="84409-104">Break All</span></span>

<span data-ttu-id="84409-105">A consola do PowerShell e o Windows PowerShell ISE agora o permitem-lhe aceder ao depurador para a execução de scripts.</span><span class="sxs-lookup"><span data-stu-id="84409-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="84409-106">Isso funciona em sessões locais e remotos.</span><span class="sxs-lookup"><span data-stu-id="84409-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="84409-107">Na consola, prima **Ctrl + Break**.</span><span class="sxs-lookup"><span data-stu-id="84409-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="84409-108">No ISE, pressione **Ctrl + B**, ou utilize o **depuração -> interromper todos os** comando de menu.</span><span class="sxs-lookup"><span data-stu-id="84409-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="84409-109">Depuração remota e a edição de arquivos remoto no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="84409-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="84409-110">Agora o ISE do Windows PowerShell permite-lhe abrir e editar arquivos numa sessão remota ao executar o comando PSEdit.</span><span class="sxs-lookup"><span data-stu-id="84409-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="84409-111">Por exemplo, pode abrir um arquivo para edição da linha de comando numa sessão remota da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="84409-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="84409-112">Além disso, agora pode editar e guardar as alterações num arquivo remoto que é aberto automaticamente no ISE do Windows PowerShell quando atingir um ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="84409-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="84409-113">Agora, pode depurar um ficheiro de script que está em execução num computador remoto, edite o ficheiro para corrigir um erro e, em seguida, volte a executar o script modificado.</span><span class="sxs-lookup"><span data-stu-id="84409-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="84409-114">Depuração de scripts avançados</span><span class="sxs-lookup"><span data-stu-id="84409-114">Advanced Script Debugging</span></span>

<span data-ttu-id="84409-115">Existem novos e avançados recursos de depuração que permitem anexar a qualquer processo de computador local que foi carregado o Windows PowerShell e depurar os espaços de execução arbitrários nesse processo.</span><span class="sxs-lookup"><span data-stu-id="84409-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="84409-116">Depuração do espaço de execução</span><span class="sxs-lookup"><span data-stu-id="84409-116">Runspace Debugging</span></span>

<span data-ttu-id="84409-117">Foram adicionados novos cmdlets que permitem-lhe a lista de espaços de execução atuais num processo e anexar a consola do Windows PowerShell ou o depurador ISE para esse espaço de execução para a depuração de scripts:</span><span class="sxs-lookup"><span data-stu-id="84409-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="84409-118">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="84409-118">Get-Runspace</span></span>
-   <span data-ttu-id="84409-119">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="84409-119">Debug-Runspace</span></span>
-   <span data-ttu-id="84409-120">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="84409-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="84409-121">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="84409-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="84409-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="84409-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="84409-123">Anexar a processo que hospeda o PowerShell</span><span class="sxs-lookup"><span data-stu-id="84409-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="84409-124">Agora pode anexar a qualquer processo de computador com o PowerShell do Windows carregados.</span><span class="sxs-lookup"><span data-stu-id="84409-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="84409-125">Fazê-lo ao introduzir para uma sessão interativa com o processo, da mesma forma para como de celebrar uma sessão remota interativa ao executar o cmdlet Enter-PSSession:</span><span class="sxs-lookup"><span data-stu-id="84409-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="84409-126">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="84409-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="84409-127">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="84409-127">Exit-PSHostProcess</span></span>
