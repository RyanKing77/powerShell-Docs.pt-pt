---
title: Elemento de SelectionCondition para EntrySelectedBy para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064002"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="8df0a-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format) (Elemento SelectionCondition para EntrySelectedBy para WideControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="8df0a-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="8df0a-103">Define a condição de que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="8df0a-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="8df0a-104">Não existe nenhum limite para o número de condições de seleção que podem ser especificados para uma definição de entrada ampla.</span><span class="sxs-lookup"><span data-stu-id="8df0a-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="8df0a-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition WideEntry (formato) para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8df0a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8df0a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8df0a-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8df0a-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8df0a-107">Attributes and Elements</span></span>

<span data-ttu-id="8df0a-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="8df0a-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="8df0a-109">Tem de especificar um único `PropertyName` ou `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="8df0a-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="8df0a-110">O `SelectionSetName` e `TypeName` elementos são opcionais.</span><span class="sxs-lookup"><span data-stu-id="8df0a-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="8df0a-111">Pode especificar um de qualquer elemento.</span><span class="sxs-lookup"><span data-stu-id="8df0a-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8df0a-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8df0a-112">Attributes</span></span>

<span data-ttu-id="8df0a-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8df0a-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8df0a-114">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="8df0a-114">Child Elements</span></span>

|<span data-ttu-id="8df0a-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="8df0a-115">Element</span></span>|<span data-ttu-id="8df0a-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="8df0a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8df0a-117">Elemento de PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8df0a-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="8df0a-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8df0a-118">Optional element.</span></span><br /><br /> <span data-ttu-id="8df0a-119">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="8df0a-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="8df0a-120">Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8df0a-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="8df0a-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8df0a-121">Optional element.</span></span><br /><br /> <span data-ttu-id="8df0a-122">Especifica o bloco de script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="8df0a-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="8df0a-123">Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8df0a-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="8df0a-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8df0a-124">Optional element.</span></span><br /><br /> <span data-ttu-id="8df0a-125">Especifica o conjunto de tipos do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="8df0a-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="8df0a-126">Elemento de TypeName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8df0a-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="8df0a-127">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8df0a-127">Optional element.</span></span><br /><br /> <span data-ttu-id="8df0a-128">Especifica um tipo .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="8df0a-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8df0a-129">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="8df0a-129">Parent Elements</span></span>

|<span data-ttu-id="8df0a-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="8df0a-130">Element</span></span>|<span data-ttu-id="8df0a-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="8df0a-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8df0a-132">Elemento de EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8df0a-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="8df0a-133">Define os tipos do .NET que utilizam esta entrada ampla ou a condição que tem de existir para esta entrada a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="8df0a-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8df0a-134">Observações</span><span class="sxs-lookup"><span data-stu-id="8df0a-134">Remarks</span></span>

<span data-ttu-id="8df0a-135">Cada entrada ampla tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.</span><span class="sxs-lookup"><span data-stu-id="8df0a-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="8df0a-136">Quando está a definir uma condição de seleção, aplicam-se os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="8df0a-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="8df0a-137">A condição de seleção tem de especificar um nome de uma propriedade, pelo menos, ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="8df0a-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="8df0a-138">A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="8df0a-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="8df0a-139">Para obter mais informações sobre como utilizar condições de seleção, consulte [Defining condições para quando uma entrada de exibição ou Item serve](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8df0a-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8df0a-140">Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="8df0a-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8df0a-141">Veja Também</span><span class="sxs-lookup"><span data-stu-id="8df0a-141">See Also</span></span>

[<span data-ttu-id="8df0a-142">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="8df0a-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="8df0a-143">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="8df0a-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="8df0a-144">Elemento de EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8df0a-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="8df0a-145">Elemento de PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8df0a-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="8df0a-146">Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8df0a-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="8df0a-147">Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8df0a-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="8df0a-148">Elemento de TypeName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="8df0a-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="8df0a-149">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8df0a-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
