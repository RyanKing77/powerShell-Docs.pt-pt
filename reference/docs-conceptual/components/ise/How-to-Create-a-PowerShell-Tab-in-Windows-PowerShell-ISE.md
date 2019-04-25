---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Como Criar um Separador do PowerShell no ISE do Windows PowerShell
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 080fe89bf1443f51460589b445431913fa20b4b8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057745"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="8bd16-103">Como Criar um Separador do PowerShell no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8bd16-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>

<span data-ttu-id="8bd16-104">Separadores no Windows PowerShell Integrated Scripting Environment (ISE) permitem-lhe criar e utilizar vários ambientes de execução dentro do mesmo aplicativo simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="8bd16-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="8bd16-105">Cada separador do PowerShell corresponde a um ambiente de execução separado ou uma sessão.</span><span class="sxs-lookup"><span data-stu-id="8bd16-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> [!NOTE]
> <span data-ttu-id="8bd16-106">Variáveis, funções e aliases que vai criar uma guia não vão ser transferidos para outro.</span><span class="sxs-lookup"><span data-stu-id="8bd16-106">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="8bd16-107">Eles são diferentes sessões do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8bd16-107">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="8bd16-108">Utilize os seguintes passos para abrir ou fechar uma guia no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8bd16-108">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="8bd16-109">Para mudar o nome de uma guia, defina o [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) propriedade no objeto de scripting de separador do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8bd16-109">To rename a tab, set the [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="8bd16-110">Criar e utilizar um novo separador do PowerShell</span><span class="sxs-lookup"><span data-stu-id="8bd16-110">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="8bd16-111">Sobre o **arquivo** menu, clique em **novo separador do PowerShell**. O novo separador do PowerShell abre-se sempre como a janela ativa.</span><span class="sxs-lookup"><span data-stu-id="8bd16-111">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="8bd16-112">Guias do PowerShell são numerados incrementalmente na ordem que estão abertas.</span><span class="sxs-lookup"><span data-stu-id="8bd16-112">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="8bd16-113">Cada separador está associado a sua própria janela de consola do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8bd16-113">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="8bd16-114">Pode ter até 32 guias do PowerShell com a sua própria sessão aberta por vez (isto é limitado a 8 no Windows PowerShell ISE 2.0.)</span><span class="sxs-lookup"><span data-stu-id="8bd16-114">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="8bd16-115">Tenha em atenção que ao clicar o **New** ou **aberto** ícones na barra de ferramentas não cria um novo separador com uma sessão separada.</span><span class="sxs-lookup"><span data-stu-id="8bd16-115">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="8bd16-116">Em vez disso, esses botões abrir um ficheiro de script novo ou existente no separador ativo no momento com uma sessão.</span><span class="sxs-lookup"><span data-stu-id="8bd16-116">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="8bd16-117">Pode ter vários script ficheiros abrir com cada separador e a sessão.</span><span class="sxs-lookup"><span data-stu-id="8bd16-117">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="8bd16-118">Os separadores de script para uma sessão de apenas serão apresentados abaixo os separadores de sessão quando a sessão associada está ativa.</span><span class="sxs-lookup"><span data-stu-id="8bd16-118">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="8bd16-119">Para tornar um separador do PowerShell ativa, clique no separador. Para selecionar a partir de todos os guias do PowerShell que estão abertas, no **vista** menu, clique no separador do PowerShell que pretende utilizar.</span><span class="sxs-lookup"><span data-stu-id="8bd16-119">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="8bd16-120">Criar e utilizar um novo separador do PowerShell remoto</span><span class="sxs-lookup"><span data-stu-id="8bd16-120">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="8bd16-121">Sobre o **arquivo** menu, clique em **novo separador do PowerShell remoto** para estabelecer uma sessão num computador remoto.</span><span class="sxs-lookup"><span data-stu-id="8bd16-121">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="8bd16-122">Uma caixa de diálogo é apresentada e pede-lhe para introduzir os detalhes necessários para estabelecer a ligação remota.</span><span class="sxs-lookup"><span data-stu-id="8bd16-122">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="8bd16-123">As funções de separador remoto, tal como um separador do PowerShell local, mas os comandos e scripts são executados no computador remoto.</span><span class="sxs-lookup"><span data-stu-id="8bd16-123">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="8bd16-124">Para fechar um separador do PowerShell</span><span class="sxs-lookup"><span data-stu-id="8bd16-124">To close a PowerShell Tab</span></span>

<span data-ttu-id="8bd16-125">Para fechar uma guia, pode usar qualquer uma das seguintes técnicas:</span><span class="sxs-lookup"><span data-stu-id="8bd16-125">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="8bd16-126">Clique no separador que pretende fechar.</span><span class="sxs-lookup"><span data-stu-id="8bd16-126">Click the tab that you want to close.</span></span>

- <span data-ttu-id="8bd16-127">Sobre o **ficheiro** menu, clique em **fechar separador do PowerShell**, ou clique no botão Fechar (**X**) numa guia Active Directory para fechar o separador.</span><span class="sxs-lookup"><span data-stu-id="8bd16-127">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="8bd16-128">Se tem não foram guardadas ficheiros abrir no separador do PowerShell que está a fechar, que lhe for pedido para guardar ou rejeitá-los.</span><span class="sxs-lookup"><span data-stu-id="8bd16-128">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="8bd16-129">Para obter mais informações sobre como guardar um script, consulte [como guardar um Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="8bd16-129">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="8bd16-130">Veja Também</span><span class="sxs-lookup"><span data-stu-id="8bd16-130">See Also</span></span>

- [<span data-ttu-id="8bd16-131">Introdução ao ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8bd16-131">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="8bd16-132">Como utilizar o painel de consola no ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8bd16-132">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)