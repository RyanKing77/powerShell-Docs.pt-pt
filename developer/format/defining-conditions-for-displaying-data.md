---
title: Definir condições para a exibição de dados | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066333"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="21958-102">Defining Conditions for Displaying Data (Definir Condições para Apresentar Dados)</span><span class="sxs-lookup"><span data-stu-id="21958-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="21958-103">Ao definir os dados que são apresentados por um modo de exibição ou um controle, pode especificar uma condição que tem de existir para os dados a serem exibidos.</span><span class="sxs-lookup"><span data-stu-id="21958-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="21958-104">A condição pode ser acionada por uma propriedade específica ou quando um script ou valor da propriedade é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="21958-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="21958-105">Quando a condição de seleção for cumprida, é utilizada a definição da vista ou do controle.</span><span class="sxs-lookup"><span data-stu-id="21958-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="21958-106">Especificar uma condição de seleção de uma definição</span><span class="sxs-lookup"><span data-stu-id="21958-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="21958-107">Ao criar uma definição para uma vista ou o controle, o `EntrySelectedBy` elemento é utilizado para especificar quais os objetos que irão utilizar a definição ou que condição tem de existir durante a definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="21958-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="21958-108">A condição é especificada pelo `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="21958-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="21958-109">No exemplo a seguir, uma condição de seleção está especificada para uma definição de uma vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="21958-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="21958-110">Neste exemplo, a definição é utilizada apenas quando o script especificado é avaliado para `true`.</span><span class="sxs-lookup"><span data-stu-id="21958-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

<span data-ttu-id="21958-111">Não existe nenhum limite para o número de condições de seleção que pode especificar uma definição de uma vista ou o controle.</span><span class="sxs-lookup"><span data-stu-id="21958-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="21958-112">Os únicos requisitos são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="21958-112">The only requirements are the following:</span></span>

- <span data-ttu-id="21958-113">A condição de seleção tem de especificar um nome de propriedade ou script para acionar a condição, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="21958-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="21958-114">A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="21958-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="21958-115">Especificar uma condição de seleção de um Item</span><span class="sxs-lookup"><span data-stu-id="21958-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="21958-116">Também pode especificar quando um item de uma vista de lista ou um controlo é utilizado, incluindo o `ItemSelectionCondition` elemento na definição do item.</span><span class="sxs-lookup"><span data-stu-id="21958-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="21958-117">No exemplo a seguir, uma condição de seleção está especificada para um item de uma vista de lista.</span><span class="sxs-lookup"><span data-stu-id="21958-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="21958-118">Neste exemplo, o item é utilizado apenas quando o script é avaliado para `true`.</span><span class="sxs-lookup"><span data-stu-id="21958-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="21958-119">Pode especificar a condição de apenas uma seleção de um item.</span><span class="sxs-lookup"><span data-stu-id="21958-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="21958-120">E a condição tem de especificar um nome de propriedade ou script para acionar a condição, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="21958-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="21958-121">Elementos XML</span><span class="sxs-lookup"><span data-stu-id="21958-121">XML Elements</span></span>

 <span data-ttu-id="21958-122">Os seguintes elementos XML são utilizados para criar uma condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="21958-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="21958-123">Condições de seleção para definições de exibição de especificar os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="21958-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="21958-124">Elemento de SelectionCondition para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="21958-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="21958-125">Elemento de SelectionCondition para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="21958-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="21958-126">Elemento de SelectionCondition para EntrySelectedBy para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="21958-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="21958-127">Elemento de SelectionCondition para EntrySelectedBy para CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="21958-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="21958-128">Seleção de especificar os elementos seguintes condições para comum e vista de controlam definições:</span><span class="sxs-lookup"><span data-stu-id="21958-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="21958-129">Elemento de SelectionCondition para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="21958-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="21958-130">Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="21958-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="21958-131">O elemento seguinte especifica as condições de seleção para expandir os objetos da coleção:</span><span class="sxs-lookup"><span data-stu-id="21958-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="21958-132">Elemento de SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="21958-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="21958-133">O elemento seguinte especifica as condições de seleção para exibir um novo grupo de dados:</span><span class="sxs-lookup"><span data-stu-id="21958-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="21958-134">Elemento de SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="21958-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="21958-135">O elemento seguinte especifica uma condição de seleção de item para uma vista de lista:</span><span class="sxs-lookup"><span data-stu-id="21958-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="21958-136">Elemento de ItemSelectionCondition para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="21958-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="21958-137">Os seguintes elementos especificar uma condição de seleção de item para controles:</span><span class="sxs-lookup"><span data-stu-id="21958-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="21958-138">Elemento de ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="21958-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="21958-139">Elemento de ItemSelectionCondition para ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="21958-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="21958-140">Elemento de ItemSelectionCondition para ExpressionBinding para CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="21958-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="21958-141">Veja Também</span><span class="sxs-lookup"><span data-stu-id="21958-141">See Also</span></span>

[<span data-ttu-id="21958-142">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="21958-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
