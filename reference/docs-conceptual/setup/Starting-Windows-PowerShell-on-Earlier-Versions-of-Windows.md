---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Iniciar o Windows PowerShell em Versões Anteriores do Windows"
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: 52e3acc1fd3009ecad3b7134008e38d4edfb5ca7
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/08/2018
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="98e53-103">Iniciar o Windows PowerShell em Versões Anteriores do Windows</span><span class="sxs-lookup"><span data-stu-id="98e53-103">Starting Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="98e53-104">Esta secção explica como iniciar o Windows PowerShell e Windows PowerShell Integrated Scripting Environment (ISE) no Windows® 7, Windows Server® 2008 R2 e Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="98e53-104">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="98e53-105">Também explica como ativar a funcionalidade opcional para o ISE do Windows PowerShell no Windows PowerShell 2.0 no Windows Server® 2008 R2 e no Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="98e53-105">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="98e53-106">Para instalar o Windows PowerShell 4.0 em sistemas suportados, transfira e instale [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span><span class="sxs-lookup"><span data-stu-id="98e53-106">To install Windows PowerShell 4.0 on supported systems, download and install [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span></span> <span data-ttu-id="98e53-107">Para obter mais informações, consulte [instalar o Windows PowerShell](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="98e53-107">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

<span data-ttu-id="98e53-108">Para instalar o Windows PowerShell 3.0 em sistemas suportados, transfira e instale [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span><span class="sxs-lookup"><span data-stu-id="98e53-108">To install Windows PowerShell 3.0 on supported systems, download and install [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span> <span data-ttu-id="98e53-109">Para obter mais informações, consulte [instalar o Windows PowerShell](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="98e53-109">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="98e53-110">Como iniciar o Windows PowerShell em versões anteriores do Windows</span><span class="sxs-lookup"><span data-stu-id="98e53-110">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="98e53-111">Utilize qualquer um dos seguintes métodos para iniciar a versão instalada do Windows PowerShell 3.0 ou Windows PowerShell 4.0, onde for aplicável.</span><span class="sxs-lookup"><span data-stu-id="98e53-111">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="98e53-112">No Menu Iniciar</span><span class="sxs-lookup"><span data-stu-id="98e53-112">From the Start Menu</span></span>

- <span data-ttu-id="98e53-113">Clique em **iniciar**, tipo **PowerShell**e, em seguida, clique em **do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="98e53-113">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>

- <span data-ttu-id="98e53-114">Do **iniciar** menu, clique em **iniciar**, clique em **todos os programas**, clique em **acessórios**, clique em de **do Windows PowerShell**  pasta e, em seguida, clique em **do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="98e53-114">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="98e53-115">Na linha de comandos</span><span class="sxs-lookup"><span data-stu-id="98e53-115">At the Command Prompt</span></span>

- <span data-ttu-id="98e53-116">No Cmd.exe, o Windows PowerShell ou o ISE do Windows PowerShell, para iniciar o Windows PowerShell, escreva:</span><span class="sxs-lookup"><span data-stu-id="98e53-116">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell
    ```

    <span data-ttu-id="98e53-117">Também pode utilizar os parâmetros do programa PowerShell.exe para personalizar a sessão.</span><span class="sxs-lookup"><span data-stu-id="98e53-117">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="98e53-118">Para obter mais informações, consulte [ajudar a linha de comandos PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="98e53-118">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="98e53-119">Com administração privilégios ("Executar como administrador")</span><span class="sxs-lookup"><span data-stu-id="98e53-119">With Administrative privileges ("Run as administrator")</span></span>

1. <span data-ttu-id="98e53-120">Clique em **iniciar**, tipo **PowerShell**, faça duplo clique **do Windows PowerShell**e, em seguida, clique em **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="98e53-120">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="98e53-121">Como iniciar o ISE do Windows PowerShell em versões anteriores do Windows</span><span class="sxs-lookup"><span data-stu-id="98e53-121">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="98e53-122">Utilize qualquer um dos seguintes métodos para iniciar o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="98e53-122">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="98e53-123">No Menu Iniciar</span><span class="sxs-lookup"><span data-stu-id="98e53-123">From the Start Menu</span></span>

- <span data-ttu-id="98e53-124">Clique em **iniciar**, tipo **ISE**e, em seguida, clique em **ISE do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="98e53-124">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>

- <span data-ttu-id="98e53-125">Do **iniciar** menu, clique em **iniciar**, clique em **todos os programas**, clique em **acessórios**, clique em de **do Windows PowerShell**  pasta e, em seguida, clique em **ISE do Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="98e53-125">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="98e53-126">Na linha de comandos</span><span class="sxs-lookup"><span data-stu-id="98e53-126">At the Command Prompt</span></span>

- <span data-ttu-id="98e53-127">No Cmd.exe, o Windows PowerShell ou o ISE do Windows PowerShell, para iniciar o Windows PowerShell, escreva:</span><span class="sxs-lookup"><span data-stu-id="98e53-127">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell_ISE
    ```

    <span data-ttu-id="98e53-128">ou</span><span class="sxs-lookup"><span data-stu-id="98e53-128">or</span></span>

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="98e53-129">Com administração privilégios ("Executar como administrador")</span><span class="sxs-lookup"><span data-stu-id="98e53-129">With Administrative privileges ("Run as administrator")</span></span>

1. <span data-ttu-id="98e53-130">Clique em **iniciar**, tipo **ISE**, faça duplo clique **ISE do Windows PowerShell**e, em seguida, clique em **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="98e53-130">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="98e53-131">Como ativar o ISE do Windows PowerShell em versões anteriores do Windows</span><span class="sxs-lookup"><span data-stu-id="98e53-131">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="98e53-132">No Windows PowerShell 4.0 e o Windows PowerShell 3.0, o ISE do Windows PowerShell está ativada por predefinição em todas as versões do Windows.</span><span class="sxs-lookup"><span data-stu-id="98e53-132">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="98e53-133">Caso não ainda esteja ativado, Windows Management Framework 4.0 ou o Windows Management Framework 3.0 ativa o mesmo.</span><span class="sxs-lookup"><span data-stu-id="98e53-133">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="98e53-134">No Windows PowerShell 2.0, o ISE do Windows PowerShell está ativada por predefinição no Windows 7.</span><span class="sxs-lookup"><span data-stu-id="98e53-134">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="98e53-135">No entanto, no Windows Server 2008 R2 e Windows Server 2008, é uma funcionalidade opcional.</span><span class="sxs-lookup"><span data-stu-id="98e53-135">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="98e53-136">Para ativar o ISE do Windows PowerShell no Windows PowerShell 2.0 no Windows Server 2008 R2 ou Windows Server 2008, utilize o procedimento seguinte.</span><span class="sxs-lookup"><span data-stu-id="98e53-136">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="98e53-137">Para ativar o Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="98e53-137">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="98e53-138">Inicie o Gestor de Servidor.</span><span class="sxs-lookup"><span data-stu-id="98e53-138">Start Server Manager.</span></span>

2. <span data-ttu-id="98e53-139">Clique em **funcionalidades** e, em seguida, clique em **adicionar funcionalidades**.</span><span class="sxs-lookup"><span data-stu-id="98e53-139">Click **Features** and then click **Add Features**.</span></span>

3. <span data-ttu-id="98e53-140">Em Selecionar funcionalidades, clique em Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="98e53-140">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

