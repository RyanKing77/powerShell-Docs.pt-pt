---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Iniciar o Windows PowerShell
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: 9184e8b0e508610e7f4775f1032f3a69c93bb8c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688323"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="e094d-103">Iniciar o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e094d-103">Starting Windows PowerShell</span></span>
<span data-ttu-id="e094d-104">O PowerShell é uma dll de mecanismo de script que é incorporada em vários anfitriões.</span><span class="sxs-lookup"><span data-stu-id="e094d-104">PowerShell is a scripting engine dll which is embedded into multiple hosts.</span></span>  <span data-ttu-id="e094d-105">O anfitrião mais comuns que começa são a linha de comandos interativa PowerShell.exe e ambiente PowerShell_ISE.exe interativa de scripts.</span><span class="sxs-lookup"><span data-stu-id="e094d-105">The most common host you will start are the interactive command line PowerShell.exe and the Interactive Scripting Environment PowerShell_ISE.exe.</span></span>

<span data-ttu-id="e094d-106">Para iniciar Windows PowerShell® no Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 e Windows 8, consulte [tarefas de gestão comuns e navegação](https://technet.microsoft.com/library/hh831491.aspx).</span><span class="sxs-lookup"><span data-stu-id="e094d-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation](https://technet.microsoft.com/library/hh831491.aspx).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="e094d-107">Como iniciar o Windows PowerShell em versões anteriores do Windows</span><span class="sxs-lookup"><span data-stu-id="e094d-107">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="e094d-108">Esta secção explica como iniciar o Windows PowerShell e o Windows PowerShell Integrated Scripting Environment (ISE) no Windows® 7, Windows Server® 2008 R2 e Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="e094d-108">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="e094d-109">Também explica como ativar a funcionalidade opcional para o Windows PowerShell ISE do Windows PowerShell 2.0 no Windows Server® 2008 R2 e Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="e094d-109">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="e094d-110">Utilize qualquer um dos seguintes métodos para iniciar a versão instalada do Windows PowerShell 3.0 ou o Windows PowerShell 4.0, quando aplicável.</span><span class="sxs-lookup"><span data-stu-id="e094d-110">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="e094d-111">No Menu Iniciar</span><span class="sxs-lookup"><span data-stu-id="e094d-111">From the Start Menu</span></span>

- <span data-ttu-id="e094d-112">Clique em **começar**, tipo **PowerShell**e, em seguida, clique em **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e094d-112">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="e094d-113">Do **começar** menu, clique em **iniciar**, clique em **todos os programas**, clique em **acessórios**, clique no **Windows PowerShell**  e, em seguida, clique **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e094d-113">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="e094d-114">No Prompt de comando</span><span class="sxs-lookup"><span data-stu-id="e094d-114">At the Command Prompt</span></span>

<span data-ttu-id="e094d-115">Na Cmd.exe, o Windows PowerShell ou o ISE do Windows PowerShell, para iniciar o Windows PowerShell, escreva:</span><span class="sxs-lookup"><span data-stu-id="e094d-115">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="e094d-116">Também pode utilizar os parâmetros do programa PowerShell.exe para personalizar a sessão.</span><span class="sxs-lookup"><span data-stu-id="e094d-116">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="e094d-117">Para obter mais informações, consulte [a ajuda de linha de comandos PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="e094d-117">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="e094d-118">Com a administração de privilégios ("Executar como administrador")</span><span class="sxs-lookup"><span data-stu-id="e094d-118">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="e094d-119">Clique em **começar**, tipo **PowerShell**, clique com botão direito **Windows PowerShell**e, em seguida, clique em **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="e094d-119">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="e094d-120">Como iniciar o ISE do Windows PowerShell em versões anteriores do Windows</span><span class="sxs-lookup"><span data-stu-id="e094d-120">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="e094d-121">Utilize qualquer um dos seguintes métodos para iniciar o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e094d-121">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="e094d-122">No Menu Iniciar</span><span class="sxs-lookup"><span data-stu-id="e094d-122">From the Start Menu</span></span>

- <span data-ttu-id="e094d-123">Clique em **começar**, tipo **ISE**e, em seguida, clique em **ISE do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e094d-123">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="e094d-124">Do **começar** menu, clique em **iniciar**, clique em **todos os programas**, clique em **acessórios**, clique no **Windows PowerShell**  e, em seguida, clique **ISE do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e094d-124">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="e094d-125">No Prompt de comando</span><span class="sxs-lookup"><span data-stu-id="e094d-125">At the Command Prompt</span></span>

<span data-ttu-id="e094d-126">Na Cmd.exe, o Windows PowerShell ou o ISE do Windows PowerShell, para iniciar o Windows PowerShell, escreva:</span><span class="sxs-lookup"><span data-stu-id="e094d-126">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="e094d-127">ou</span><span class="sxs-lookup"><span data-stu-id="e094d-127">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="e094d-128">Com a administração de privilégios ("Executar como administrador")</span><span class="sxs-lookup"><span data-stu-id="e094d-128">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="e094d-129">Clique em **começar**, tipo **ISE**, clique com botão direito **ISE do Windows PowerShell**e, em seguida, clique em **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="e094d-129">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="e094d-130">Como ativar o ISE do Windows PowerShell em versões anteriores do Windows</span><span class="sxs-lookup"><span data-stu-id="e094d-130">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="e094d-131">No Windows PowerShell 4.0 e no Windows PowerShell 3.0, o ISE do Windows PowerShell está ativado por predefinição em todas as versões do Windows.</span><span class="sxs-lookup"><span data-stu-id="e094d-131">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="e094d-132">Se não estiver já ativada, Windows Management Framework 4.0 ou Windows Management Framework 3.0 permite que ela.</span><span class="sxs-lookup"><span data-stu-id="e094d-132">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="e094d-133">No Windows PowerShell 2.0, o ISE do Windows PowerShell está ativado por predefinição no Windows 7.</span><span class="sxs-lookup"><span data-stu-id="e094d-133">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="e094d-134">No entanto, no Windows Server 2008 R2 e Windows Server 2008, é uma funcionalidade opcional.</span><span class="sxs-lookup"><span data-stu-id="e094d-134">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="e094d-135">Para ativar o Windows PowerShell ISE do Windows PowerShell 2.0 no Windows Server 2008 R2 ou Windows Server 2008, utilize o procedimento seguinte.</span><span class="sxs-lookup"><span data-stu-id="e094d-135">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="e094d-136">Para ativar o Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="e094d-136">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="e094d-137">Inicie o Gestor de Servidores.</span><span class="sxs-lookup"><span data-stu-id="e094d-137">Start Server Manager.</span></span>
2. <span data-ttu-id="e094d-138">Clique em **funcionalidades** e, em seguida, clique em **adicionar funcionalidades**.</span><span class="sxs-lookup"><span data-stu-id="e094d-138">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="e094d-139">Em Selecionar funcionalidades, clique em Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="e094d-139">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="e094d-140">Iniciar a versão de 32 bits do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e094d-140">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="e094d-141">Quando instala o Windows PowerShell num computador de 64 bits **Windows PowerShell (x86)**, está instalada uma versão de 32 bits do Windows PowerShell, além da versão de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="e094d-141">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="e094d-142">Quando executa o Windows PowerShell, a versão de 64 bits é executada por predefinição.</span><span class="sxs-lookup"><span data-stu-id="e094d-142">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="e094d-143">No entanto, ocasionalmente, poderá ter de ser executado **Windows PowerShell (x86)**, como quando estiver a utilizar um módulo que requer a versão de 32 bits ou quando estiver a ligar remotamente a um computador de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="e094d-143">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="e094d-144">Para iniciar uma versão de 32 bits do Windows PowerShell, utilize qualquer um dos seguintes procedimentos.</span><span class="sxs-lookup"><span data-stu-id="e094d-144">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="e094d-145">No Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="e094d-145">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="e094d-146">Sobre o **começar** ecrã, escreva **(x86) do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e094d-146">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="e094d-147">Clique nas **x86 do Windows PowerShell** mosaico.</span><span class="sxs-lookup"><span data-stu-id="e094d-147">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="e094d-148">Na **Gestor de servidores**, da **ferramentas** menu, selecione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e094d-148">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e094d-149">Na área de trabalho, mover o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell x86** e, em seguida, clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e094d-149">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e094d-150">Por meio da linha de comandos, introduza: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="e094d-150">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="e094d-151">In Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="e094d-151">In Windows Server® 2012</span></span>

- <span data-ttu-id="e094d-152">Sobre o **começar** ecrã, escreva **PowerShell** e, em seguida, clique em **(x86) do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e094d-152">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e094d-153">Na **Gestor de servidores**, da **ferramentas** menu, selecione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e094d-153">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e094d-154">Na área de trabalho, mover o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell** e, em seguida, clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e094d-154">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e094d-155">Por meio da linha de comandos, introduza: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="e094d-155">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="e094d-156">No Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="e094d-156">In Windows® 8.1</span></span>

- <span data-ttu-id="e094d-157">Sobre o **começar** ecrã, escreva **(x86) do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e094d-157">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="e094d-158">Clique nas **x86 do Windows PowerShell** mosaico.</span><span class="sxs-lookup"><span data-stu-id="e094d-158">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="e094d-159">Se estiver a executar [ferramentas de administração remota do servidor](https://go.microsoft.com/fwlink/?LinkID=304145) para Windows 8.1, também pode abrir o Windows PowerShell x86 a partir do **servidor ManagerTools** menu.</span><span class="sxs-lookup"><span data-stu-id="e094d-159">If you are running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span>
  <span data-ttu-id="e094d-160">Selecione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e094d-160">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e094d-161">Na área de trabalho, mover o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell x86** e, em seguida, clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e094d-161">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e094d-162">Por meio da linha de comandos, introduza: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="e094d-162">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="e094d-163">No Windows® 8</span><span class="sxs-lookup"><span data-stu-id="e094d-163">In Windows® 8</span></span>

- <span data-ttu-id="e094d-164">Na **começar** ecrã, mova o cursor para o canto superior direito, clique em **definições**, clique em **mosaicos**e, em seguida, mova o **Mostrar Ferramentas administrativas** controlo de deslize como Yes.</span><span class="sxs-lookup"><span data-stu-id="e094d-164">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="e094d-165">Em seguida, escreva **PowerShell** e clique em **(x86) do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e094d-165">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e094d-166">Se estiver a executar [ferramentas de administração remota do servidor](https://www.microsoft.com/download/details.aspx?id=28972) para Windows 8, também pode abrir o Windows PowerShell x86 a partir do **servidor ManagerTools** menu.</span><span class="sxs-lookup"><span data-stu-id="e094d-166">If you are running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="e094d-167">Selecione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="e094d-167">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e094d-168">Sobre o **começar** ecrã ou ambiente de trabalho, escreva **PowerShell (x86)** e, em seguida, clique em **(x86) do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e094d-168">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="e094d-169">Por meio da linha de comandos, introduza: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="e094d-169">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>