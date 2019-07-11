---
title: Elemento de SelectionCondition para EntrySelectedBy para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: f04a07c241268566eaedfe2b299c33d5be4dc19d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735078"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="3ba51-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format) (Elemento SelectionCondition para EntrySelectedBy para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="3ba51-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="3ba51-103">Define a condição de que tem de existir para utilizar esta definição de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="3ba51-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="3ba51-104">Não existe nenhum limite para o número de condições de seleção que podem ser especificados para uma definição de lista.</span><span class="sxs-lookup"><span data-stu-id="3ba51-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="3ba51-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento (formato) ListEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition ListEntry (formato) para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3ba51-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3ba51-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ba51-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3ba51-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="3ba51-107">Attributes and Elements</span></span>

<span data-ttu-id="3ba51-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="3ba51-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3ba51-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="3ba51-109">Attributes</span></span>

<span data-ttu-id="3ba51-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3ba51-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3ba51-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="3ba51-111">Child Elements</span></span>

|<span data-ttu-id="3ba51-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="3ba51-112">Element</span></span>|<span data-ttu-id="3ba51-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ba51-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ba51-114">Elemento de PropertyName para SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3ba51-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="3ba51-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3ba51-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3ba51-116">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="3ba51-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="3ba51-117">Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3ba51-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="3ba51-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3ba51-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3ba51-119">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="3ba51-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="3ba51-120">Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3ba51-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="3ba51-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3ba51-121">Optional element.</span></span><br /><br /> <span data-ttu-id="3ba51-122">Especifica o conjunto de tipos do .NET que acionam a condição.</span><span class="sxs-lookup"><span data-stu-id="3ba51-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="3ba51-123">Elemento de TypeName para SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3ba51-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="3ba51-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3ba51-124">Optional element.</span></span><br /><br /> <span data-ttu-id="3ba51-125">Especifica um tipo .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="3ba51-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3ba51-126">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="3ba51-126">Parent Elements</span></span>

|<span data-ttu-id="3ba51-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="3ba51-127">Element</span></span>|<span data-ttu-id="3ba51-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ba51-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ba51-129">Elemento de EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3ba51-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="3ba51-130">Define os tipos do .NET que utilizam esta entrada de tabela ou a condição que tem de existir para esta entrada a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="3ba51-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3ba51-131">Observações</span><span class="sxs-lookup"><span data-stu-id="3ba51-131">Remarks</span></span>

<span data-ttu-id="3ba51-132">lWhen está a definir uma condição de seleção, são aplicáveis os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="3ba51-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="3ba51-133">A condição de seleção tem de especificar um nome de uma propriedade, pelo menos, ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="3ba51-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="3ba51-134">A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="3ba51-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="3ba51-135">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3ba51-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="3ba51-136">Para obter mais informações sobre os outros componentes de uma vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="3ba51-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3ba51-137">Veja Também</span><span class="sxs-lookup"><span data-stu-id="3ba51-137">See Also</span></span>

[<span data-ttu-id="3ba51-138">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="3ba51-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="3ba51-139">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="3ba51-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3ba51-140">Elemento de ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3ba51-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="3ba51-141">Elemento de SelectionSetName para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3ba51-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="3ba51-142">Elemento de TypeName para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="3ba51-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="3ba51-143">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ba51-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
