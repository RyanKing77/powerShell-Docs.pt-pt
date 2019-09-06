---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Alterar o Estado do Computador
ms.openlocfilehash: de3e31e358548943a015b7bba275c4461202b20f
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386289"
---
# <a name="changing-computer-state"></a><span data-ttu-id="62fae-103">Alterar o Estado do Computador</span><span class="sxs-lookup"><span data-stu-id="62fae-103">Changing Computer State</span></span>

<span data-ttu-id="62fae-104">Para redefinir um computador no Windows PowerShell, use uma ferramenta de linha de comando padrão, a classe WMI ou CIM.</span><span class="sxs-lookup"><span data-stu-id="62fae-104">To reset a computer in Windows PowerShell, use either a standard command-line tool, WMI or CIM class.</span></span> <span data-ttu-id="62fae-105">Embora você esteja usando o Windows PowerShell somente para executar a ferramenta, aprender a alterar o estado de energia de um computador no Windows PowerShell ilustra alguns dos detalhes importantes sobre como trabalhar com ferramentas externas no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="62fae-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="62fae-106">Bloqueando um computador</span><span class="sxs-lookup"><span data-stu-id="62fae-106">Locking a Computer</span></span>

<span data-ttu-id="62fae-107">A única maneira de bloquear um computador diretamente com as ferramentas padrão disponíveis é chamar a função **LockWorkstation ()** no **user32. dll**:</span><span class="sxs-lookup"><span data-stu-id="62fae-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="62fae-108">Esse comando bloqueia imediatamente a estação de trabalho.</span><span class="sxs-lookup"><span data-stu-id="62fae-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="62fae-109">Ele usa o *rundll32. exe*, que executa as DLLs do Windows (e salva suas bibliotecas para uso repetido) para executar user32. dll, uma biblioteca de funções de gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="62fae-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="62fae-110">Quando você bloqueia uma estação de trabalho enquanto a troca rápida de usuário está habilitada, como no Windows XP, o computador exibe a tela de logon do usuário em vez de iniciar a proteção do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="62fae-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="62fae-111">Para desligar sessões específicas em um Terminal Server, use a ferramenta de linha de comando **tsshutdn. exe** .</span><span class="sxs-lookup"><span data-stu-id="62fae-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="62fae-112">Fazendo logoff da sessão atual</span><span class="sxs-lookup"><span data-stu-id="62fae-112">Logging Off the Current Session</span></span>

<span data-ttu-id="62fae-113">Você pode usar várias técnicas diferentes para fazer logoff de uma sessão no sistema local.</span><span class="sxs-lookup"><span data-stu-id="62fae-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="62fae-114">A maneira mais simples é usar a ferramenta de linha de comando Área de Trabalho Remota/serviços de terminal, **logoff. exe** (para obter detalhes, no prompt do Windows PowerShell, digite **logoff/?** ).</span><span class="sxs-lookup"><span data-stu-id="62fae-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="62fae-115">Para fazer logoff da sessão ativa atual, digite **logoff** sem argumentos.</span><span class="sxs-lookup"><span data-stu-id="62fae-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="62fae-116">Você também pode usar a ferramenta **Shutdown. exe** com sua opção de logoff:</span><span class="sxs-lookup"><span data-stu-id="62fae-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="62fae-117">Outra opção é usar o WMI.</span><span class="sxs-lookup"><span data-stu-id="62fae-117">Another option is to use WMI.</span></span> <span data-ttu-id="62fae-118">A classe Win32_OperatingSystem tem um método Win32Shutdown.</span><span class="sxs-lookup"><span data-stu-id="62fae-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="62fae-119">Invocar o método com o sinalizador 0 inicia o logoff:</span><span class="sxs-lookup"><span data-stu-id="62fae-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="62fae-120">Para obter mais informações e para encontrar outros recursos do método Win32Shutdown, consulte "método Win32Shutdown da classe Win32_OperatingSystem" no MSDN.</span><span class="sxs-lookup"><span data-stu-id="62fae-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

<span data-ttu-id="62fae-121">Por fim, você pode usar o CIM com a mesma classe Win32_OperatingSystem, conforme descrito acima no método WMI.</span><span class="sxs-lookup"><span data-stu-id="62fae-121">Finally you can use CIM with the same Win32_OperatingSystem class as described above in the WMI method.</span></span>

```powershell
Get-CIMInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="62fae-122">Desligando ou reiniciando um computador</span><span class="sxs-lookup"><span data-stu-id="62fae-122">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="62fae-123">O desligamento e a reinicialização de computadores geralmente são os mesmos tipos de tarefa.</span><span class="sxs-lookup"><span data-stu-id="62fae-123">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="62fae-124">As ferramentas que desligam um computador geralmente também o reiniciam, e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="62fae-124">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="62fae-125">Há duas opções simples para reiniciar um computador do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="62fae-125">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="62fae-126">Use tsshutdn. exe ou Shutdown. exe com argumentos apropriados.</span><span class="sxs-lookup"><span data-stu-id="62fae-126">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="62fae-127">Você pode obter informações de uso detalhadas de **tsshutdn. exe/?**</span><span class="sxs-lookup"><span data-stu-id="62fae-127">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="62fae-128">ou **Shutdown. exe/?** .</span><span class="sxs-lookup"><span data-stu-id="62fae-128">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="62fae-129">Também é possível executar operações de desligamento e reinicialização diretamente do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="62fae-129">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="62fae-130">Para desligar o computador, use o comando Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="62fae-130">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="62fae-131">Para reiniciar o sistema operacional, use o comando Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="62fae-131">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="62fae-132">Para forçar uma reinicialização imediata do computador, use o parâmetro-Force.</span><span class="sxs-lookup"><span data-stu-id="62fae-132">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
