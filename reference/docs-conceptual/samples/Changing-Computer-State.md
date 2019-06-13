---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Alterar o Estado do Computador
ms.openlocfilehash: 80692ad7c56aa13e55d4997cfec289ffb3605458
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030275"
---
# <a name="changing-computer-state"></a><span data-ttu-id="fd0a0-103">Alterar o Estado do Computador</span><span class="sxs-lookup"><span data-stu-id="fd0a0-103">Changing Computer State</span></span>

<span data-ttu-id="fd0a0-104">Para repor um computador no Windows PowerShell, utilize uma ferramenta de linha de comando padrão ou uma classe WMI.</span><span class="sxs-lookup"><span data-stu-id="fd0a0-104">To reset a computer in Windows PowerShell, use either a standard command-line tool or a WMI class.</span></span> <span data-ttu-id="fd0a0-105">Embora o estiver a utilizar o Windows PowerShell apenas para executar a ferramenta, aprendendo a alterar o estado de energia de um computador no Windows PowerShell ilustra alguns dos detalhes importantes sobre como trabalhar com as ferramentas externas no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fd0a0-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="fd0a0-106">Bloqueio de um computador</span><span class="sxs-lookup"><span data-stu-id="fd0a0-106">Locking a Computer</span></span>

<span data-ttu-id="fd0a0-107">A única forma de bloquear um computador diretamente com as ferramentas disponíveis padrão é chamar o **LockWorkstation()** funcionar **user32.dll**:</span><span class="sxs-lookup"><span data-stu-id="fd0a0-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="fd0a0-108">Este comando bloqueia imediatamente a estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fd0a0-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="fd0a0-109">Ele usa *rundll32.exe*, que executa o Windows DLLs (e salva suas bibliotecas para uso repetido) para executar user32.dll, uma biblioteca de funções de gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="fd0a0-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="fd0a0-110">Quando bloquear uma estação de trabalho enquanto estiver ativada a troca rápida de usuário, como no Windows XP, o computador apresenta o ecrã de início de sessão do utilizador, em vez de iniciar a proteção de tela do utilizador atual.</span><span class="sxs-lookup"><span data-stu-id="fd0a0-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="fd0a0-111">Para desligar sessões particulares num Terminal Server, utilize o **tsshutdn.exe** ferramenta da linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="fd0a0-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="fd0a0-112">Terminar a sessão atual</span><span class="sxs-lookup"><span data-stu-id="fd0a0-112">Logging Off the Current Session</span></span>

<span data-ttu-id="fd0a0-113">Pode usar várias técnicas diferentes para terminar sessão numa sessão no sistema local.</span><span class="sxs-lookup"><span data-stu-id="fd0a0-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="fd0a0-114">A forma mais simples é usar a ferramenta de linha de comandos de serviços de Terminal/ambiente de trabalho remoto, **logoff.exe** (para obter detalhes, na linha de comandos da Windows PowerShell, escreva **logoff /?** ).</span><span class="sxs-lookup"><span data-stu-id="fd0a0-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="fd0a0-115">Para terminar a sessão atual do Active Directory, escreva **logoff** sem argumentos.</span><span class="sxs-lookup"><span data-stu-id="fd0a0-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="fd0a0-116">Também pode utilizar o **shutdown.exe** ferramenta com a opção de terminar sessão:</span><span class="sxs-lookup"><span data-stu-id="fd0a0-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="fd0a0-117">Uma terceira opção é usar o WMI.</span><span class="sxs-lookup"><span data-stu-id="fd0a0-117">A third option is to use WMI.</span></span> <span data-ttu-id="fd0a0-118">A classe Win32_OperatingSystem tem um método de Win32Shutdown.</span><span class="sxs-lookup"><span data-stu-id="fd0a0-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="fd0a0-119">Invocando o método com o sinalizador 0 inicia a fim de sessão:</span><span class="sxs-lookup"><span data-stu-id="fd0a0-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="fd0a0-120">Para obter mais informações e para localizar outros recursos do método Win32Shutdown, consulte "Win32Shutdown método da classe Win32_OperatingSystem" no MSDN.</span><span class="sxs-lookup"><span data-stu-id="fd0a0-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="fd0a0-121">Encerrar ou reiniciar um computador</span><span class="sxs-lookup"><span data-stu-id="fd0a0-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="fd0a0-122">Encerrar e reiniciar os computadores em geral são os mesmos tipos de tarefas.</span><span class="sxs-lookup"><span data-stu-id="fd0a0-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="fd0a0-123">Ferramentas que encerrar um computador em geral serão reiniciá-lo também — e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="fd0a0-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="fd0a0-124">Existem duas opções simples para reiniciar um computador a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fd0a0-124">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="fd0a0-125">Utilize Tsshutdn.exe ou Shutdown.exe com argumentos adequados.</span><span class="sxs-lookup"><span data-stu-id="fd0a0-125">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="fd0a0-126">Pode obter informações de utilização detalhadas de **tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="fd0a0-126">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="fd0a0-127">ou **shutdown.exe /?** .</span><span class="sxs-lookup"><span data-stu-id="fd0a0-127">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="fd0a0-128">Também pode efetuar encerrar e reiniciar operações diretamente a partir do Windows PowerShell também.</span><span class="sxs-lookup"><span data-stu-id="fd0a0-128">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="fd0a0-129">Para encerrar o computador, utilize o comando Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="fd0a0-129">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="fd0a0-130">Para reiniciar o sistema operativo, utilize o comando de reiniciar o computador</span><span class="sxs-lookup"><span data-stu-id="fd0a0-130">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="fd0a0-131">Para forçar um reinício imediato do computador, utilize o parâmetro - Force.</span><span class="sxs-lookup"><span data-stu-id="fd0a0-131">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
