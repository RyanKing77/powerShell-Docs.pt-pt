---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "A iniciar a versão de 32 bits do Windows PowerShell"
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: d682ce45ebc92cda3a9008ab608bacf9ef8eba57
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="d4f40-103">A iniciar a versão de 32 bits do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d4f40-103">Starting the 32-Bit Version of Windows PowerShell</span></span>
<span data-ttu-id="d4f40-104">Quando instalar o Windows PowerShell no computador de 64 bits, **Windows PowerShell (x86)**, está instalada uma versão de 32 bits do Windows PowerShell para além da versão de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="d4f40-104">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="d4f40-105">Quando executar o Windows PowerShell, executa a versão de 64 bits por predefinição.</span><span class="sxs-lookup"><span data-stu-id="d4f40-105">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="d4f40-106">No entanto, ocasionalmente, poderá ter de executar **Windows PowerShell (x86)**, tal como quando estiver a utilizar um módulo que requer a versão de 32 bits ou quando estiverem a ligar remotamente a um computador de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="d4f40-106">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="d4f40-107">Para iniciar uma versão de 32 bits do Windows PowerShell, utilize qualquer um dos seguintes procedimentos.</span><span class="sxs-lookup"><span data-stu-id="d4f40-107">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="d4f40-108">No Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d4f40-108">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="d4f40-109">No **iniciar** ecrã, escreva **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4f40-109">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="d4f40-110">Clique em de **Windows PowerShell x86** mosaico.</span><span class="sxs-lookup"><span data-stu-id="d4f40-110">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="d4f40-111">No **Gestor de servidor**, do **ferramentas** menu, selecione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4f40-111">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4f40-112">No ambiente de trabalho, mova o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell x86** e, em seguida, clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4f40-112">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4f40-113">Linha de comandos, introduza:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="d4f40-113">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="d4f40-114">No Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="d4f40-114">In Windows Server® 2012</span></span>

- <span data-ttu-id="d4f40-115">No **iniciar** ecrã, escreva **PowerShell** e, em seguida, clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4f40-115">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4f40-116">No **Gestor de servidor**, do **ferramentas** menu, selecione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4f40-116">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4f40-117">No ambiente de trabalho, mova o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell** e, em seguida, clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4f40-117">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4f40-118">Linha de comandos, introduza:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="d4f40-118">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="d4f40-119">No Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="d4f40-119">In Windows® 8.1</span></span>

- <span data-ttu-id="d4f40-120">No **iniciar** ecrã, escreva **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4f40-120">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="d4f40-121">Clique em de **Windows PowerShell x86** mosaico.</span><span class="sxs-lookup"><span data-stu-id="d4f40-121">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="d4f40-122">Se estiver a executar [ferramentas de administração remota do servidor](http://go.microsoft.com/fwlink/?LinkID=304145) para Windows 8.1, pode também abrir o Windows PowerShell x86 a partir de **ManagerTools servidor** menu.</span><span class="sxs-lookup"><span data-stu-id="d4f40-122">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="d4f40-123">Selecione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4f40-123">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4f40-124">No ambiente de trabalho, mova o cursor para o canto superior direito, clique em **pesquisa**, tipo **PowerShell x86** e, em seguida, clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4f40-124">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
   
- <span data-ttu-id="d4f40-125">Linha de comandos, introduza:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="d4f40-125">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="d4f40-126">No Windows® 8</span><span class="sxs-lookup"><span data-stu-id="d4f40-126">In Windows® 8</span></span>

- <span data-ttu-id="d4f40-127">No **iniciar** ecrã, mova o cursor para o canto superior direito, clique em **definições**, clique em **mosaicos**e, em seguida, mova o **Mostrar Ferramentas administrativas** controlo de deslize para Sim.</span><span class="sxs-lookup"><span data-stu-id="d4f40-127">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="d4f40-128">Em seguida, escreva **PowerShell** e clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4f40-128">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4f40-129">Se estiver a executar [ferramentas de administração remota do servidor](http://www.microsoft.com/download/details.aspx?id=28972) para o Windows 8, pode também abrir o Windows PowerShell x86 do **servidor ManagerTools** menu.</span><span class="sxs-lookup"><span data-stu-id="d4f40-129">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="d4f40-130">Selecione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4f40-130">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4f40-131">No **iniciar** ecrã ou ambiente de trabalho, escreva **PowerShell (x86)** e, em seguida, clique em **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4f40-131">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4f40-132">Linha de comandos, introduza:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="d4f40-132">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

