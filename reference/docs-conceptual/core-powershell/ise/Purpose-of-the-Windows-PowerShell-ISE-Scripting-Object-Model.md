---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: 3256d8bff3885d266f0db6f52932e40c4beaf8b1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a><span data-ttu-id="e9498-103">Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do</span><span class="sxs-lookup"><span data-stu-id="e9498-103">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>
  <span data-ttu-id="e9498-104">Objetos associados a formulário e a função do Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="e9498-104">Objects are associated with the form and function of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="e9498-105">A referência de modelo de objeto fornece detalhes sobre o membro, propriedades e métodos que estes objetos expõem.</span><span class="sxs-lookup"><span data-stu-id="e9498-105">The object model reference provides details about the member properties and methods that these objects expose.</span></span> <span data-ttu-id="e9498-106">Os exemplos são fornecidos para mostrar a forma como pode utilizar scripts aceda diretamente a estes métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="e9498-106">Examples are provided to show how you can use scripts to directly access these methods and properties.</span></span> <span data-ttu-id="e9498-107">O modelo de objeto de scripting facilita seguinte intervalo de tarefas.</span><span class="sxs-lookup"><span data-stu-id="e9498-107">The scripting object model makes the following range of tasks easier.</span></span>

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a><span data-ttu-id="e9498-108">Personalizar o aspeto do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e9498-108">Customizing the appearance of Windows PowerShell ISE</span></span>
 <span data-ttu-id="e9498-109">Pode utilizar o modelo de objeto para modificar as definições da aplicação e as opções.</span><span class="sxs-lookup"><span data-stu-id="e9498-109">You can use the object model to modify the application settings and options.</span></span> <span data-ttu-id="e9498-110">Por exemplo, pode modificá-los da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="e9498-110">For example, you can modify them as follows:</span></span>

- <span data-ttu-id="e9498-111">Pode alterar a cor de erros, avisos, verbosas saídas e produz de depuração.</span><span class="sxs-lookup"><span data-stu-id="e9498-111">You can change the color of errors, warnings, verbose outputs, and debug outputs.</span></span>

- <span data-ttu-id="e9498-112">Pode obter ou definir as cores de fundo para o painel de comando, o painel de resultados e o painel de Script.</span><span class="sxs-lookup"><span data-stu-id="e9498-112">You can get or set the background colors for the Command pane, the Output pane, and the Script pane.</span></span>

- <span data-ttu-id="e9498-113">Pode definir a cor de primeiro plano para o painel de resultados.</span><span class="sxs-lookup"><span data-stu-id="e9498-113">You can set the foreground color for the Output pane.</span></span>

- <span data-ttu-id="e9498-114">Pode definir o nome de tipo de letra e o tamanho de tipo de letra para o ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9498-114">You can set the font name and font size for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="e9498-115">Pode configurar avisos.</span><span class="sxs-lookup"><span data-stu-id="e9498-115">You can configure warnings.</span></span> <span data-ttu-id="e9498-116">Esta definição inclui avisos que são emitidos quando um ficheiro está aberto em vários separadores do PowerShell ou ao executar um script no ficheiro antes do ficheiro foi guardado.</span><span class="sxs-lookup"><span data-stu-id="e9498-116">This setting includes warnings that are issued when a file is opened in multiple PowerShell tabs or when a script in the file is run before the file has been saved.</span></span>

- <span data-ttu-id="e9498-117">Pode alternar entre uma vista onde o painel de Script e o painel de resultados estão lado a lado e uma vista onde o painel de Script é na parte superior do painel de resultados.</span><span class="sxs-lookup"><span data-stu-id="e9498-117">You can switch between a view where the Script pane and the Output pane are side-by-side and a view where the Script pane is on top of the Output pane.</span></span> <span data-ttu-id="e9498-118">Pode ancoragem do painel de comando na parte inferior ou na parte superior do painel de resultados do.</span><span class="sxs-lookup"><span data-stu-id="e9498-118">You can dock the Command pane to the bottom or the top of the Output pane.</span></span>

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a><span data-ttu-id="e9498-119">Otimização da funcionalidade do ISE do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e9498-119">Enhancing the functionality of Windows PowerShell ISE</span></span>
 <span data-ttu-id="e9498-120">Pode utilizar o modelo de objeto para melhorar a funcionalidade do ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9498-120">You can use the object model to enhance the functionality of Windows PowerShell ISE.</span></span> <span data-ttu-id="e9498-121">Por exemplo, pode:</span><span class="sxs-lookup"><span data-stu-id="e9498-121">For example, you can:</span></span>

- <span data-ttu-id="e9498-122">Adicionar e modificar a instância do ISE do Windows PowerShell em si.</span><span class="sxs-lookup"><span data-stu-id="e9498-122">Add and modify the instance of Windows PowerShell ISE itself.</span></span> <span data-ttu-id="e9498-123">Por exemplo, para alterar os menus, pode adicionar novos itens de menu e mapear os itens de menu novo scripts.</span><span class="sxs-lookup"><span data-stu-id="e9498-123">For example, to change the menus, you can add new menu items and map the new menu items to scripts.</span></span>

- <span data-ttu-id="e9498-124">Crie scripts que executar algumas das tarefas que pode realizar utilizando os comandos de menu e botões no ISE do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9498-124">Create scripts that perform some of the tasks that you can perform by using the menu commands and buttons in Windows PowerShell ISE.</span></span> <span data-ttu-id="e9498-125">Por exemplo, pode adicionar, remover ou selecione um separador de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9498-125">For example, you can add, remove, or select a PowerShell tab.</span></span>

- <span data-ttu-id="e9498-126">Tarefas de complemento que podem ser efetuadas utilizando os botões e comandos de menu.</span><span class="sxs-lookup"><span data-stu-id="e9498-126">Complement tasks that can be performed by using menu commands and buttons.</span></span> <span data-ttu-id="e9498-127">Por exemplo, pode mudar o nome de um separador de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9498-127">For example, you can rename a PowerShell tab.</span></span>

- <span data-ttu-id="e9498-128">Manipular memórias intermédias texto para o painel de comando, o painel de resultados e o painel de Script que estão associadas um ficheiro.</span><span class="sxs-lookup"><span data-stu-id="e9498-128">Manipulate text buffers for the Command pane, the Output pane, and the Script pane that are associated with a file.</span></span> <span data-ttu-id="e9498-129">Por exemplo, pode:</span><span class="sxs-lookup"><span data-stu-id="e9498-129">For example, you can:</span></span>

    -   <span data-ttu-id="e9498-130">Obter ou definir todo o texto.</span><span class="sxs-lookup"><span data-stu-id="e9498-130">Get or set all text.</span></span>

    -   <span data-ttu-id="e9498-131">Obter ou definir uma selecção de texto.</span><span class="sxs-lookup"><span data-stu-id="e9498-131">Get or set a text selection.</span></span>

    -   <span data-ttu-id="e9498-132">Executar um script ou executar uma parte de um script selecionada.</span><span class="sxs-lookup"><span data-stu-id="e9498-132">Run a script or run a selected portion of a script.</span></span>

    -   <span data-ttu-id="e9498-133">Desloque-se de uma linha na vista.</span><span class="sxs-lookup"><span data-stu-id="e9498-133">Scroll a line into view.</span></span>

    -   <span data-ttu-id="e9498-134">Inserir texto na posição acento circunflexo.</span><span class="sxs-lookup"><span data-stu-id="e9498-134">Insert text at a caret position.</span></span>

    -   <span data-ttu-id="e9498-135">Selecione um bloco de texto.</span><span class="sxs-lookup"><span data-stu-id="e9498-135">Select a block of text.</span></span>

    -   <span data-ttu-id="e9498-136">Obter o último número de linha.</span><span class="sxs-lookup"><span data-stu-id="e9498-136">Get the last line number.</span></span>

- <span data-ttu-id="e9498-137">Realizar operações de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="e9498-137">Perform file operations.</span></span> <span data-ttu-id="e9498-138">Por exemplo, pode:</span><span class="sxs-lookup"><span data-stu-id="e9498-138">For example, you can:</span></span>

    -   <span data-ttu-id="e9498-139">Abrir um ficheiro, guarde um ficheiro ou guardar um ficheiro ao utilizar um nome diferente.</span><span class="sxs-lookup"><span data-stu-id="e9498-139">Open a file, save a file, or save a file by using a different name.</span></span>

    -   <span data-ttu-id="e9498-140">Determine se um ficheiro foi alterado após a última foi guardada.</span><span class="sxs-lookup"><span data-stu-id="e9498-140">Determine whether a file has been changed after it was last saved.</span></span>

    -   <span data-ttu-id="e9498-141">Obter o nome de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="e9498-141">Get the file name.</span></span>

    -   <span data-ttu-id="e9498-142">Selecione um ficheiro.</span><span class="sxs-lookup"><span data-stu-id="e9498-142">Select a file.</span></span>

## <a name="automating-tasks"></a><span data-ttu-id="e9498-143">Automatizar tarefas</span><span class="sxs-lookup"><span data-stu-id="e9498-143">Automating tasks</span></span>
 <span data-ttu-id="e9498-144">Pode utilizar o modelo de objeto de scripting para criar atalhos de teclado para operações frequentes.</span><span class="sxs-lookup"><span data-stu-id="e9498-144">You can use the scripting object model to create keyboard shortcuts for frequent operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9498-145">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="e9498-145">See Also</span></span>
- [<span data-ttu-id="e9498-146">A hierarquia de modelo de objeto ISE</span><span class="sxs-lookup"><span data-stu-id="e9498-146">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md) 
- [<span data-ttu-id="e9498-147">Referência de modelo de objeto do Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="e9498-147">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="e9498-148">O ISE do Windows PowerShell modelo de objeto de Scripting</span><span class="sxs-lookup"><span data-stu-id="e9498-148">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
