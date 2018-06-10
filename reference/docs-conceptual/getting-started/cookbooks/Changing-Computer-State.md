---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Alterar o Estado do Computador
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: c659ad54325b0f7305f882e1cb9607062abad6a4
ms.sourcegitcommit: 2ffb9fa92129c2001379ca2c17646466721f7165
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251522"
---
# <a name="changing-computer-state"></a><span data-ttu-id="37df1-103">Alterar o Estado do Computador</span><span class="sxs-lookup"><span data-stu-id="37df1-103">Changing Computer State</span></span>

<span data-ttu-id="37df1-104">Para repor um computador no Windows PowerShell, utilize uma ferramenta de linha de comandos padrão ou uma classe WMI.</span><span class="sxs-lookup"><span data-stu-id="37df1-104">To reset a computer in Windows PowerShell, use either a standard command-line tool or a WMI class.</span></span> <span data-ttu-id="37df1-105">Embora estiver a utilizar o Windows PowerShell apenas para executar a ferramenta, aprender a alterar o estado de energia de um computador no Windows PowerShell ilustra alguns dos detalhes importantes sobre como trabalhar com ferramentas externas no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="37df1-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

### <a name="locking-a-computer"></a><span data-ttu-id="37df1-106">Bloqueio de um computador</span><span class="sxs-lookup"><span data-stu-id="37df1-106">Locking a Computer</span></span>

<span data-ttu-id="37df1-107">É a única forma de bloquear um computador diretamente com as ferramentas disponíveis padrão para chamar o **LockWorkstation()** funcionar **user32.dll**:</span><span class="sxs-lookup"><span data-stu-id="37df1-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="37df1-108">Este comando bloqueia imediatamente a estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="37df1-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="37df1-109">Utiliza *rundll32.exe*, que é executado DLLs do Windows (e guarda os respetivos bibliotecas para utilização repetida) para executar user32.dll, uma biblioteca de funções de gestão do Windows.</span><span class="sxs-lookup"><span data-stu-id="37df1-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="37df1-110">Quando bloqueia uma estação de trabalho enquanto a mudança rápida de utilizador estiver ativada, tal como no Windows XP, o computador apresenta o ecrã de início de sessão do utilizador em vez de iniciar a proteção de ecrã ser o utilizador atual.</span><span class="sxs-lookup"><span data-stu-id="37df1-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="37df1-111">Para encerrar sessões específicas num servidor de Terminal, utilize o **tsshutdn.exe** ferramenta da linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="37df1-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

### <a name="logging-off-the-current-session"></a><span data-ttu-id="37df1-112">Terminar a sessão atual</span><span class="sxs-lookup"><span data-stu-id="37df1-112">Logging Off the Current Session</span></span>

<span data-ttu-id="37df1-113">Pode utilizar várias técnicas diferentes para terminar uma sessão no sistema local.</span><span class="sxs-lookup"><span data-stu-id="37df1-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="37df1-114">A forma mais simples consiste em utilizar a ferramenta de linha de comandos de serviços de Terminal/ambiente de trabalho remoto, **logoff.exe** (para obter mais detalhes, na linha de comandos do Windows PowerShell, escreva **fim de sessão /?**).</span><span class="sxs-lookup"><span data-stu-id="37df1-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="37df1-115">Para terminar a sessão atual do Active Directory, escreva **terminar sessão** sem argumentos.</span><span class="sxs-lookup"><span data-stu-id="37df1-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="37df1-116">Também pode utilizar o **shutdown.exe** ferramenta com a sua opção de terminar sessão:</span><span class="sxs-lookup"><span data-stu-id="37df1-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="37df1-117">Uma terceira opção consiste em utilizar o WMI.</span><span class="sxs-lookup"><span data-stu-id="37df1-117">A third option is to use WMI.</span></span> <span data-ttu-id="37df1-118">A classe Win32_OperatingSystem tem um método de Win32Shutdown.</span><span class="sxs-lookup"><span data-stu-id="37df1-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="37df1-119">Invocar o método com o sinalizador 0 inicia a fim de sessão:</span><span class="sxs-lookup"><span data-stu-id="37df1-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="37df1-120">Para obter mais informações e para localizar outras funcionalidades do método Win32Shutdown, consulte "Win32Shutdown método da classe Win32_OperatingSystem" no MSDN.</span><span class="sxs-lookup"><span data-stu-id="37df1-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

### <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="37df1-121">Encerrar ou reiniciar um computador</span><span class="sxs-lookup"><span data-stu-id="37df1-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="37df1-122">Encerrar e reiniciar os computadores são, geralmente, os mesmos tipos de tarefas.</span><span class="sxs-lookup"><span data-stu-id="37df1-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="37df1-123">As ferramentas que encerrar um computador, geralmente, serão reiniciá-lo, bem como — e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="37df1-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="37df1-124">Existem duas opções simples para reiniciar um computador a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="37df1-124">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="37df1-125">Utilize Tsshutdn.exe ou Shutdown.exe com argumentos adequados.</span><span class="sxs-lookup"><span data-stu-id="37df1-125">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="37df1-126">Pode obter informações de utilização detalhada do **tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="37df1-126">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="37df1-127">ou **shutdown.exe /?**.</span><span class="sxs-lookup"><span data-stu-id="37df1-127">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="37df1-128">Também pode efetuar encerrar e reiniciar operações diretamente a partir do Windows PowerShell, bem como.</span><span class="sxs-lookup"><span data-stu-id="37df1-128">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="37df1-129">Para encerrar o computador, utilize o comando de reiniciar o computador</span><span class="sxs-lookup"><span data-stu-id="37df1-129">To shut down the computer, use the restart-computer command</span></span>

```powershell
stop-computer
```

<span data-ttu-id="37df1-130">Para reiniciar o sistema operativo, utilize o comando de reiniciar o computador</span><span class="sxs-lookup"><span data-stu-id="37df1-130">To restart the operating system, use the restart-computer command</span></span>

```powershell
restart-computer
```
