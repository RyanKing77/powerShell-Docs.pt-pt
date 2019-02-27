---
title: Elemento de SelectionCondition para EntrySelectedBy para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850478"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="2f792-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format) (Elemento SelectionCondition para EntrySelectedBy para TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="2f792-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="2f792-103">Define a condição de que tem de existir para utilizar para esta definição de vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="2f792-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="2f792-104">Não existe nenhum limite para o número de condições de seleção que podem ser especificados para uma definição de tabela.</span><span class="sxs-lookup"><span data-stu-id="2f792-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="2f792-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento (formato) TableRowEntry elemento (formato) EntrySelectedBy elemento de configuração para TableRowEntry (formato) Elemento de SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="2f792-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2f792-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2f792-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2f792-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="2f792-107">Attributes and Elements</span></span>

<span data-ttu-id="2f792-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do elemento SelectionCondition.</span><span class="sxs-lookup"><span data-stu-id="2f792-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2f792-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="2f792-109">Attributes</span></span>

<span data-ttu-id="2f792-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2f792-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2f792-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="2f792-111">Child Elements</span></span>

|<span data-ttu-id="2f792-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="2f792-112">Element</span></span>|<span data-ttu-id="2f792-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f792-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f792-114">Elemento de PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="2f792-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="2f792-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2f792-115">Optional element.</span></span><br /><br /> <span data-ttu-id="2f792-116">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="2f792-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="2f792-117">Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="2f792-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="2f792-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2f792-118">Optional element.</span></span><br /><br /> <span data-ttu-id="2f792-119">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="2f792-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="2f792-120">Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="2f792-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="2f792-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2f792-121">Optional element.</span></span><br /><br /> <span data-ttu-id="2f792-122">Especifica o conjunto de tipos do .NET que acionam a condição.</span><span class="sxs-lookup"><span data-stu-id="2f792-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="2f792-123">Elemento de TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="2f792-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="2f792-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2f792-124">Optional element.</span></span><br /><br /> <span data-ttu-id="2f792-125">Especifica um tipo .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="2f792-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2f792-126">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="2f792-126">Parent Elements</span></span>

|<span data-ttu-id="2f792-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="2f792-127">Element</span></span>|<span data-ttu-id="2f792-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f792-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f792-129">Elemento de EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="2f792-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="2f792-130">Define os tipos do .NET que utilizam esta entrada de tabela ou a condição que tem de existir para esta entrada a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="2f792-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2f792-131">Observações</span><span class="sxs-lookup"><span data-stu-id="2f792-131">Remarks</span></span>

<span data-ttu-id="2f792-132">Cada entrada da lista tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.</span><span class="sxs-lookup"><span data-stu-id="2f792-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="2f792-133">Quando está a definir uma condição de seleção, aplicam-se os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="2f792-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="2f792-134">A condição de seleção tem de especificar um nome de uma propriedade, pelo menos, ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="2f792-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="2f792-135">A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="2f792-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="2f792-136">Para obter mais informações sobre como utilizar condições de seleção, consulte [Defining condições para quando uma entrada de exibição ou Item serve](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2f792-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2f792-137">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="2f792-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2f792-138">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="2f792-138">See Also</span></span>

[<span data-ttu-id="2f792-139">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="2f792-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2f792-140">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="2f792-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2f792-141">Elemento de EntrySelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="2f792-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="2f792-142">Elemento de PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="2f792-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="2f792-143">Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="2f792-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="2f792-144">Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="2f792-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="2f792-145">Elemento de TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="2f792-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="2f792-146">Escrever do Windows PowerShell, formatação e os tipos de ficheiro</span><span class="sxs-lookup"><span data-stu-id="2f792-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
