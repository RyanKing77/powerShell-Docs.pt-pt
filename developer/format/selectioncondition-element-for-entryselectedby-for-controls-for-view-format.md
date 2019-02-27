---
title: Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848224"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="0767d-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format) (Elemento SelectionCondition para EntrySelectedBy para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="0767d-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="0767d-103">Define uma condição que tem de existir durante a definição de controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="0767d-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="0767d-104">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="0767d-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="0767d-105">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para controles para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) EntrySelectedBy elemento para CustomEntry para controles para exibição (formato) SelectionCondition elemento para EntrySelectedBy para controles para exibição ( Formato)</span><span class="sxs-lookup"><span data-stu-id="0767d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0767d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0767d-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0767d-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="0767d-107">Attributes and Elements</span></span>

<span data-ttu-id="0767d-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="0767d-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0767d-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="0767d-109">Attributes</span></span>

<span data-ttu-id="0767d-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0767d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0767d-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="0767d-111">Child Elements</span></span>

|<span data-ttu-id="0767d-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="0767d-112">Element</span></span>|<span data-ttu-id="0767d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0767d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0767d-114">Elemento de PropertyName para SelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0767d-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="0767d-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0767d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0767d-116">Especifica uma propriedade de .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="0767d-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="0767d-117">Elemento de ScriptBlock para SelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0767d-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="0767d-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0767d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="0767d-119">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="0767d-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="0767d-120">Elemento de SelectionSetName para SelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0767d-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="0767d-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0767d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="0767d-122">Especifica o conjunto de tipos do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="0767d-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="0767d-123">Elemento de TypeName para SelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0767d-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="0767d-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0767d-124">Optional element.</span></span><br /><br /> <span data-ttu-id="0767d-125">Especifica um tipo .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="0767d-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0767d-126">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="0767d-126">Parent Elements</span></span>

|<span data-ttu-id="0767d-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="0767d-127">Element</span></span>|<span data-ttu-id="0767d-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="0767d-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0767d-129">Elemento de EntrySelectedBy para CustomEntry para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0767d-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="0767d-130">Define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="0767d-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0767d-131">Observações</span><span class="sxs-lookup"><span data-stu-id="0767d-131">Remarks</span></span>

<span data-ttu-id="0767d-132">Quando está a definir uma condição de seleção, aplicam-se os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="0767d-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="0767d-133">A condição de seleção tem de especificar um nome de uma propriedade, pelo menos, ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="0767d-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="0767d-134">A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="0767d-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="0767d-135">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0767d-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0767d-136">Veja Também</span><span class="sxs-lookup"><span data-stu-id="0767d-136">See Also</span></span>

[<span data-ttu-id="0767d-137">Elemento de PropertyName para SelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0767d-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="0767d-138">Elemento de ScriptBlock para SelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0767d-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="0767d-139">Elemento de SelectionSetName para SelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0767d-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="0767d-140">Elemento de TypeName para SelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0767d-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="0767d-141">Elemento de EntrySelectedBy para CustomEntry para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="0767d-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="0767d-142">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0767d-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
