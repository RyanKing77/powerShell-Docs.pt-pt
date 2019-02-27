---
title: Elemento de SelectionCondition para EntrySelectedBy para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846229"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="867b0-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format) (Elemento SelectionCondition para EntrySelectedBy para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="867b0-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="867b0-103">Define uma condição que tem de existir para obter uma definição de controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="867b0-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="867b0-104">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="867b0-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="867b0-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de EntrySelectedBy GroupBy (formato) para CustomEntry para o elemento de SelectionCondition GroupBy (formato) para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="867b0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="867b0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="867b0-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="867b0-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="867b0-107">Attributes and Elements</span></span>

<span data-ttu-id="867b0-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="867b0-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="867b0-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="867b0-109">Attributes</span></span>

<span data-ttu-id="867b0-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="867b0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="867b0-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="867b0-111">Child Elements</span></span>

|<span data-ttu-id="867b0-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="867b0-112">Element</span></span>|<span data-ttu-id="867b0-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="867b0-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="867b0-114">Elemento de PropertyName para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="867b0-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="867b0-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="867b0-115">Optional element.</span></span><br /><br /> <span data-ttu-id="867b0-116">Especifica uma propriedade de .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="867b0-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="867b0-117">Elemento de ScriptBlock para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="867b0-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="867b0-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="867b0-118">Optional element.</span></span><br /><br /> <span data-ttu-id="867b0-119">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="867b0-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="867b0-120">Elemento de SelectionSetName para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="867b0-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="867b0-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="867b0-121">Optional element.</span></span><br /><br /> <span data-ttu-id="867b0-122">Especifica o conjunto de tipos do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="867b0-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="867b0-123">Elemento de TypeName para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="867b0-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="867b0-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="867b0-124">Optional element.</span></span><br /><br /> <span data-ttu-id="867b0-125">Especifica um tipo .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="867b0-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="867b0-126">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="867b0-126">Parent Elements</span></span>

|<span data-ttu-id="867b0-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="867b0-127">Element</span></span>|<span data-ttu-id="867b0-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="867b0-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="867b0-129">Elemento de EntrySelectedBy para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="867b0-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="867b0-130">Define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="867b0-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="867b0-131">Observações</span><span class="sxs-lookup"><span data-stu-id="867b0-131">Remarks</span></span>

<span data-ttu-id="867b0-132">Quando está a definir uma condição de seleção, aplicam-se os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="867b0-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="867b0-133">A condição de seleção tem de especificar um nome de uma propriedade, pelo menos, ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="867b0-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="867b0-134">A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="867b0-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="867b0-135">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="867b0-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="867b0-136">Veja Também</span><span class="sxs-lookup"><span data-stu-id="867b0-136">See Also</span></span>

[<span data-ttu-id="867b0-137">Elemento de PropertyName para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="867b0-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="867b0-138">Elemento de ScriptBlock para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="867b0-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="867b0-139">Elemento de SelectionSetName para SelectionCondition para controle personalizado para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="867b0-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="867b0-140">Elemento de TypeName para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="867b0-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="867b0-141">Elemento de EntrySelectedBy para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="867b0-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="867b0-142">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="867b0-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
