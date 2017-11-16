---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Como criar um separador de PowerShell no ISE do Windows PowerShell
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 3cfeb18babe6b63f0e02da8cf0fd460950f1afce
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="43ea4-103">Como criar um separador de PowerShell no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="43ea4-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>
<span data-ttu-id="43ea4-104">Separadores no Windows PowerShell Integrated Scripting Environment (ISE) permitem-lhe criar e utilizar vários ambientes de execução na mesma aplicação de em simultâneo.</span><span class="sxs-lookup"><span data-stu-id="43ea4-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="43ea4-105">Cada separador PowerShell corresponde a um ambiente de execução separados ou a sessão.</span><span class="sxs-lookup"><span data-stu-id="43ea4-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> <span data-ttu-id="43ea4-106">**TENHA EM ATENÇÃO**:</span><span class="sxs-lookup"><span data-stu-id="43ea4-106">**NOTE**:</span></span>
>
> <span data-ttu-id="43ea4-107">As variáveis, funções e aliases que criar no um separador não passa para outro.</span><span class="sxs-lookup"><span data-stu-id="43ea4-107">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="43ea4-108">Os valores são diferentes sessões do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="43ea4-108">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="43ea4-109">Utilize os seguintes passos para abrir ou fechar um separador no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="43ea4-109">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="43ea4-110">Para mudar o nome de um separador, defina o [DisplayName](The-PowerShellTab-Object.md#displayname) propriedade do objeto de scripting do Windows PowerShell separador.</span><span class="sxs-lookup"><span data-stu-id="43ea4-110">To rename a tab, set the [DisplayName](The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="43ea4-111">Criar e utilizar um novo separador do PowerShell</span><span class="sxs-lookup"><span data-stu-id="43ea4-111">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="43ea4-112">No **ficheiro** menu, clique em **novo separador do PowerShell**. O novo separador do PowerShell abre-se sempre como a janela ativa.</span><span class="sxs-lookup"><span data-stu-id="43ea4-112">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="43ea4-113">Separadores de PowerShell incrementalmente estão numeradas pela ordem que estão abertas.</span><span class="sxs-lookup"><span data-stu-id="43ea4-113">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="43ea4-114">Cada separador está associado a respetiva janela de consola do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="43ea4-114">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="43ea4-115">Pode ter até 32 PowerShell separadores com as suas próprias sessão aberta numa altura (trata limitada a 8 no Windows PowerShell ISE 2.0.)</span><span class="sxs-lookup"><span data-stu-id="43ea4-115">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="43ea4-116">Tenha em atenção que ao clicar no **novo** ou **abra** ícones na barra de ferramentas não criar um novo separador com uma sessão separada.</span><span class="sxs-lookup"><span data-stu-id="43ea4-116">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="43ea4-117">Em vez disso, os botões de abrir um ficheiro de script novo ou existente no separador atualmente ativo com uma sessão.</span><span class="sxs-lookup"><span data-stu-id="43ea4-117">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="43ea4-118">Pode ter vários script ficheiros são abertos com cada separador e a sessão.</span><span class="sxs-lookup"><span data-stu-id="43ea4-118">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="43ea4-119">Os separadores de script para uma sessão só serão apresentados abaixo os separadores de sessão quando a sessão associada está ativa.</span><span class="sxs-lookup"><span data-stu-id="43ea4-119">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="43ea4-120">Para tornar um separador de PowerShell ativa, clique no separador. Para selecionar todos os separadores de PowerShell que são abertos, no **vista** menu, clique no separador de PowerShell que pretende utilizar.</span><span class="sxs-lookup"><span data-stu-id="43ea4-120">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="43ea4-121">Criar e utilizar um novo separador do PowerShell remoto</span><span class="sxs-lookup"><span data-stu-id="43ea4-121">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="43ea4-122">No **ficheiro** menu, clique em **novo separador do PowerShell remoto** para estabelecer uma sessão num computador remoto.</span><span class="sxs-lookup"><span data-stu-id="43ea4-122">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="43ea4-123">Uma caixa de diálogo é apresentada e pede-lhe que introduza os detalhes necessários para estabelecer a ligação remota.</span><span class="sxs-lookup"><span data-stu-id="43ea4-123">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="43ea4-124">As funções do separador remoto tal como um separador de PowerShell local, mas os comandos e scripts são executados no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="43ea4-124">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="43ea4-125">Para fechar um separador de PowerShell</span><span class="sxs-lookup"><span data-stu-id="43ea4-125">To close a PowerShell Tab</span></span>

<span data-ttu-id="43ea4-126">Para fechar um separador, pode utilizar as seguintes técnicas:</span><span class="sxs-lookup"><span data-stu-id="43ea4-126">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="43ea4-127">Clique no separador que pretende fechar.</span><span class="sxs-lookup"><span data-stu-id="43ea4-127">Click the tab that you want to close.</span></span>

- <span data-ttu-id="43ea4-128">No **ficheiro** menu, clique em **separador de PowerShell fechar**, ou clique no botão Fechar (**X**) um separador de Active Directory para fechar o separador.</span><span class="sxs-lookup"><span data-stu-id="43ea4-128">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="43ea4-129">Se tem não foram guardadas ficheiros são abertos no separador de PowerShell que está a fechar, que lhe for pedido para guardar ou eliminá-las.</span><span class="sxs-lookup"><span data-stu-id="43ea4-129">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="43ea4-130">Para obter mais informações sobre como guardar um script, consulte [como guardar um Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="43ea4-130">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="43ea4-131">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="43ea4-131">See Also</span></span>

- [<span data-ttu-id="43ea4-132">Utilizar o ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="43ea4-132">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="43ea4-133">Como utilizar o painel de consola no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="43ea4-133">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)

