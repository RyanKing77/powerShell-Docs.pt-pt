---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Iniciar o Windows PowerShell
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: b56ddc2f577225646729b99f3a2abcb8cc60d307
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953128"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="3f0e1-103">Iniciar o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f0e1-103">Starting Windows PowerShell</span></span>
<span data-ttu-id="3f0e1-104">PowerShell é uma dll de motor de script que está incorporada em vários anfitriões.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-104">PowerShell is a scripting engine dll which is embedded into multiple hosts.</span></span>  <span data-ttu-id="3f0e1-105">O anfitrião mais comuns que iniciará são a linha de comandos interativa PowerShell.exe e ambiente PowerShell_ISE.exe interativa Scripting.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-105">The most common host you will start are the interactive command line PowerShell.exe and the Interactive Scripting Environment PowerShell_ISE.exe.</span></span>

<span data-ttu-id="3f0e1-106">Para iniciar Windows PowerShell® no Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 e Windows 8, consulte [tarefas de gestão comuns e navegação](http://technet.microsoft.com/library/hh831491.aspx).</span><span class="sxs-lookup"><span data-stu-id="3f0e1-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation](http://technet.microsoft.com/library/hh831491.aspx).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="3f0e1-107">Como iniciar o Windows PowerShell em versões anteriores do Windows</span><span class="sxs-lookup"><span data-stu-id="3f0e1-107">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="3f0e1-108">Esta secção explica como iniciar o Windows PowerShell e Windows PowerShell Integrated Scripting Environment (ISE) no Windows® 7, Windows Server® 2008 R2 e Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-108">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="3f0e1-109">Também explica como ativar a funcionalidade opcional para o ISE do Windows PowerShell no Windows PowerShell 2.0 no Windows Server® 2008 R2 e no Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-109">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="3f0e1-110">Utilize qualquer um dos seguintes métodos para iniciar a versão instalada do Windows PowerShell 3.0 ou Windows PowerShell 4.0, onde for aplicável.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-110">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="3f0e1-111">No Menu Iniciar</span><span class="sxs-lookup"><span data-stu-id="3f0e1-111">From the Start Menu</span></span>

- <span data-ttu-id="3f0e1-112">Clique em **iniciar**, tipo **PowerShell**e, em seguida, clique em **do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-112">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="3f0e1-113">Do **iniciar** menu, clique em **iniciar**, clique em **todos os programas**, clique em **acessórios**, clique em de **do Windows PowerShell**  pasta e, em seguida, clique em **do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-113">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="3f0e1-114">Na linha de comandos</span><span class="sxs-lookup"><span data-stu-id="3f0e1-114">At the Command Prompt</span></span>

<span data-ttu-id="3f0e1-115">No Cmd.exe, o Windows PowerShell ou o ISE do Windows PowerShell, para iniciar o Windows PowerShell, escreva:</span><span class="sxs-lookup"><span data-stu-id="3f0e1-115">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="3f0e1-116">Também pode utilizar os parâmetros do programa PowerShell.exe para personalizar a sessão.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-116">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="3f0e1-117">Para obter mais informações, consulte [ajudar a linha de comandos PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="3f0e1-117">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="3f0e1-118">Com administração privilégios ("Executar como administrador")</span><span class="sxs-lookup"><span data-stu-id="3f0e1-118">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="3f0e1-119">Clique em **iniciar**, tipo **PowerShell**, faça duplo clique **do Windows PowerShell**e, em seguida, clique em **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-119">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="3f0e1-120">Como iniciar o ISE do Windows PowerShell em versões anteriores do Windows</span><span class="sxs-lookup"><span data-stu-id="3f0e1-120">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="3f0e1-121">Utilize qualquer um dos seguintes métodos para iniciar o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-121">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="3f0e1-122">No Menu Iniciar</span><span class="sxs-lookup"><span data-stu-id="3f0e1-122">From the Start Menu</span></span>

- <span data-ttu-id="3f0e1-123">Clique em **iniciar**, tipo **ISE**e, em seguida, clique em **ISE do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-123">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="3f0e1-124">Do **iniciar** menu, clique em **iniciar**, clique em **todos os programas**, clique em **acessórios**, clique em de **do Windows PowerShell**  pasta e, em seguida, clique em **ISE do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-124">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="3f0e1-125">Na linha de comandos</span><span class="sxs-lookup"><span data-stu-id="3f0e1-125">At the Command Prompt</span></span>

<span data-ttu-id="3f0e1-126">No Cmd.exe, o Windows PowerShell ou o ISE do Windows PowerShell, para iniciar o Windows PowerShell, escreva:</span><span class="sxs-lookup"><span data-stu-id="3f0e1-126">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="3f0e1-127">ou</span><span class="sxs-lookup"><span data-stu-id="3f0e1-127">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="3f0e1-128">Com administração privilégios ("Executar como administrador")</span><span class="sxs-lookup"><span data-stu-id="3f0e1-128">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="3f0e1-129">Clique em **iniciar**, tipo **ISE**, faça duplo clique **ISE do Windows PowerShell**e, em seguida, clique em **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-129">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="3f0e1-130">Como ativar o ISE do Windows PowerShell em versões anteriores do Windows</span><span class="sxs-lookup"><span data-stu-id="3f0e1-130">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="3f0e1-131">No Windows PowerShell 4.0 e o Windows PowerShell 3.0, o ISE do Windows PowerShell está ativada por predefinição em todas as versões do Windows.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-131">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="3f0e1-132">Caso não ainda esteja ativado, Windows Management Framework 4.0 ou o Windows Management Framework 3.0 ativa o mesmo.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-132">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="3f0e1-133">No Windows PowerShell 2.0, o ISE do Windows PowerShell está ativada por predefinição no Windows 7.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-133">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="3f0e1-134">No entanto, no Windows Server 2008 R2 e Windows Server 2008, é uma funcionalidade opcional.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-134">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="3f0e1-135">Para ativar o ISE do Windows PowerShell no Windows PowerShell 2.0 no Windows Server 2008 R2 ou Windows Server 2008, utilize o procedimento seguinte.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-135">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="3f0e1-136">Para ativar o Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="3f0e1-136">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="3f0e1-137">Inicie o Gestor de Servidor.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-137">Start Server Manager.</span></span>
2. <span data-ttu-id="3f0e1-138">Clique em **funcionalidades** e, em seguida, clique em **adicionar funcionalidades**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-138">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="3f0e1-139">Em Selecionar funcionalidades, clique em Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="3f0e1-139">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="3f0e1-140">A iniciar a versão de 32 bits do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f0e1-140">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="3f0e1-141">Quando instalar o Windows PowerShell no computador de 64 bits, **Windows PowerShell (x86)**, está instalada uma versão de 32 bits do Windows PowerShell para além da versão de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-141">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="3f0e1-142">Quando executar o Windows PowerShell, executa a versão de 64 bits por predefinição.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-142">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="3f0e1-143">No entanto, ocasionalmente, poderá ter de executar **Windows PowerShell (x86)**, tal como quando estiver a utilizar um módulo que requer a versão de 32 bits ou quando estiverem a ligar remotamente a um computador de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-143">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="3f0e1-144">Para iniciar uma versão de 32 bits do Windows PowerShell, utilize qualquer um dos seguintes procedimentos.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-144">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="3f0e1-145">In Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="3f0e1-145">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="3f0e1-146">No **iniciar** ecrã, escreva **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-146">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="3f0e1-147">Clique em de **Windows PowerShell x86** mosaico.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-147">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="3f0e1-148">No **Gestor de servidor**, do **ferramentas** menu, selecione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-148">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3f0e1-149">No ambiente de trabalho, mova o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell x86** e, em seguida, clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-149">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3f0e1-150">Linha de comandos, introduza: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="3f0e1-150">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="3f0e1-151">In Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="3f0e1-151">In Windows Server® 2012</span></span>

- <span data-ttu-id="3f0e1-152">No **iniciar** ecrã, escreva **PowerShell** e, em seguida, clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-152">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3f0e1-153">No **Gestor de servidor**, do **ferramentas** menu, selecione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-153">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3f0e1-154">No ambiente de trabalho, mova o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell** e, em seguida, clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-154">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3f0e1-155">Linha de comandos, introduza: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="3f0e1-155">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="3f0e1-156">No Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="3f0e1-156">In Windows® 8.1</span></span>

- <span data-ttu-id="3f0e1-157">No **iniciar** ecrã, escreva **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-157">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="3f0e1-158">Clique em de **Windows PowerShell x86** mosaico.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-158">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="3f0e1-159">Se estiver a executar [ferramentas de administração remota do servidor](http://go.microsoft.com/fwlink/?LinkID=304145) para Windows 8.1, pode também abrir o Windows PowerShell x86 a partir de **ManagerTools servidor** menu.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-159">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span>
  <span data-ttu-id="3f0e1-160">Selecione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-160">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3f0e1-161">No ambiente de trabalho, mova o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell x86** e, em seguida, clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-161">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3f0e1-162">Linha de comandos, introduza: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="3f0e1-162">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="3f0e1-163">No Windows® 8</span><span class="sxs-lookup"><span data-stu-id="3f0e1-163">In Windows® 8</span></span>

- <span data-ttu-id="3f0e1-164">No **iniciar** ecrã, mova o cursor para o canto superior direito, clique em **definições**, clique em **mosaicos**e, em seguida, mova o **Mostrar Ferramentas administrativas** controlo de deslize para Sim.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-164">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="3f0e1-165">Em seguida, escreva **PowerShell** e clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-165">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3f0e1-166">Se estiver a executar [ferramentas de administração remota do servidor](http://www.microsoft.com/download/details.aspx?id=28972) para o Windows 8, pode também abrir o Windows PowerShell x86 do **servidor ManagerTools** menu.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-166">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="3f0e1-167">Selecione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-167">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3f0e1-168">No **iniciar** ecrã ou ambiente de trabalho, escreva **PowerShell (x86)** e, em seguida, clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="3f0e1-168">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="3f0e1-169">Linha de comandos, introduza: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="3f0e1-169">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>