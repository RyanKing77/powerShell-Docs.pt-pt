---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9ead27fd5d4f146e9062488c1c8cc22a073b922e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187107"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="25812-102">Melhorias na Depuração de Scripts do PowerShell</span><span class="sxs-lookup"><span data-stu-id="25812-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="25812-103">Um número de melhorias efetuado no PowerShell 5.0 para melhorar a experiência de depuração:</span><span class="sxs-lookup"><span data-stu-id="25812-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="25812-104">Quebrar a todos os</span><span class="sxs-lookup"><span data-stu-id="25812-104">Break All</span></span>

<span data-ttu-id="25812-105">A consola do PowerShell e o ISE do Windows PowerShell agora permitem-lhe aceder ao depurador para executar scripts.</span><span class="sxs-lookup"><span data-stu-id="25812-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="25812-106">Este procedimento funciona em sessões locais e remotas.</span><span class="sxs-lookup"><span data-stu-id="25812-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="25812-107">Na consola, prima **Ctrl + Break**.</span><span class="sxs-lookup"><span data-stu-id="25812-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="25812-108">No ISE, prima **Ctrl + B**, ou utilize o **depuração -> interromper todos os** comandos de menu.</span><span class="sxs-lookup"><span data-stu-id="25812-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="25812-109">Depuração remota e edição de ficheiros remotos no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="25812-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="25812-110">Agora o ISE do Windows PowerShell permite-lhe abrir e editar ficheiros numa sessão remota, executando o comando PSEdit.</span><span class="sxs-lookup"><span data-stu-id="25812-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="25812-111">Por exemplo, pode abrir um ficheiro para a edição na linha de comandos numa sessão remota da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="25812-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="25812-112">Além disso, agora pode editar e guardar as alterações num ficheiro remoto que é aberto automaticamente no ISE do Windows PowerShell quando atingiu um ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="25812-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="25812-113">Agora, pode depurar um ficheiro de script está em execução num computador remoto, edite o ficheiro para corrigir um erro e, em seguida, volte a executar o script modificado.</span><span class="sxs-lookup"><span data-stu-id="25812-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="25812-114">A depuração de scripts avançados</span><span class="sxs-lookup"><span data-stu-id="25812-114">Advanced Script Debugging</span></span>

<span data-ttu-id="25812-115">Não existem funcionalidades de depuração novo, avançadas que lhe permitem ligar a nenhum processo de computador local que foi carregadas do Windows PowerShell e depurar arbitrários espaços de execução no processo.</span><span class="sxs-lookup"><span data-stu-id="25812-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="25812-116">A depuração de espaço de execução</span><span class="sxs-lookup"><span data-stu-id="25812-116">Runspace Debugging</span></span>

<span data-ttu-id="25812-117">Foram adicionados novos cmdlets que lhe permitem a lista de espaços de execução atuais num processo e anexar a consola do Windows PowerShell ou o depurador ISE para esse espaço de execução para a depuração de scripts:</span><span class="sxs-lookup"><span data-stu-id="25812-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="25812-118">Get-espaço de execução</span><span class="sxs-lookup"><span data-stu-id="25812-118">Get-Runspace</span></span>
-   <span data-ttu-id="25812-119">Espaço de execução de depuração</span><span class="sxs-lookup"><span data-stu-id="25812-119">Debug-Runspace</span></span>
-   <span data-ttu-id="25812-120">Ativar RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="25812-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="25812-121">Desativar RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="25812-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="25812-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="25812-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="25812-123">Ligar ao processo de alojamento do PowerShell</span><span class="sxs-lookup"><span data-stu-id="25812-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="25812-124">Agora pode anexar à qualquer processo computador carregado com o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="25812-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="25812-125">Fazê-lo ao introduzir para uma sessão interativa com o processo, de forma semelhante ao como introduziu para uma sessão remota interativa executando o cmdlet Enter-PSSession:</span><span class="sxs-lookup"><span data-stu-id="25812-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="25812-126">PSHostProcess introduza</span><span class="sxs-lookup"><span data-stu-id="25812-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="25812-127">Saída PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="25812-127">Exit-PSHostProcess</span></span>
