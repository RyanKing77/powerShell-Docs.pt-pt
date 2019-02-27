---
title: Elemento de SelectionCondition para EntrySelectedBy para CustomControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848791"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="2bdf6-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format) (Elemento SelectionCondition para EntrySelectedBy para CustomControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="2bdf6-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="2bdf6-103">Define uma condição que tem de existir para obter uma definição de controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="2bdf6-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="2bdf6-104">Este elemento é utilizado ao definir uma vista de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="2bdf6-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="2bdf6-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento de configuração para o modo de exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para CustomControl para exibição ( Elemento de CustomItem de formato) para CustomEntry para CustomControl para exibição (formato) EntrySelectedBy elemento para CustomEntry para CustomControl para exibição (formato) SelectionCondition elemento para EntrySelectedBy para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="2bdf6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2bdf6-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2bdf6-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2bdf6-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="2bdf6-107">Attributes and Elements</span></span>

<span data-ttu-id="2bdf6-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="2bdf6-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2bdf6-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="2bdf6-109">Attributes</span></span>

<span data-ttu-id="2bdf6-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2bdf6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2bdf6-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="2bdf6-111">Child Elements</span></span>

|<span data-ttu-id="2bdf6-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="2bdf6-112">Element</span></span>|<span data-ttu-id="2bdf6-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="2bdf6-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2bdf6-114">Elemento de PropertyName para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="2bdf6-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="2bdf6-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2bdf6-115">Optional element.</span></span><br /><br /> <span data-ttu-id="2bdf6-116">Especifica uma propriedade de .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="2bdf6-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="2bdf6-117">Elemento de ScriptBlock para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="2bdf6-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="2bdf6-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2bdf6-118">Optional element.</span></span><br /><br /> <span data-ttu-id="2bdf6-119">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="2bdf6-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="2bdf6-120">Elemento de SelectionSetName para SelectionCondition para controle personalizado para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="2bdf6-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="2bdf6-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2bdf6-121">Optional element.</span></span><br /><br /> <span data-ttu-id="2bdf6-122">Especifica o conjunto de tipos do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="2bdf6-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="2bdf6-123">Elemento de TypeName para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="2bdf6-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="2bdf6-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="2bdf6-124">Optional element.</span></span><br /><br /> <span data-ttu-id="2bdf6-125">Especifica um tipo .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="2bdf6-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2bdf6-126">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="2bdf6-126">Parent Elements</span></span>

|<span data-ttu-id="2bdf6-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="2bdf6-127">Element</span></span>|<span data-ttu-id="2bdf6-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="2bdf6-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2bdf6-129">Elemento de EntrySelectedBy para CustomEntry para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="2bdf6-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="2bdf6-130">Define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="2bdf6-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2bdf6-131">Observações</span><span class="sxs-lookup"><span data-stu-id="2bdf6-131">Remarks</span></span>

<span data-ttu-id="2bdf6-132">Quando está a definir uma condição de seleção, aplicam-se os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="2bdf6-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="2bdf6-133">A condição de seleção tem de especificar um nome de uma propriedade, pelo menos, ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="2bdf6-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="2bdf6-134">A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="2bdf6-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="2bdf6-135">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2bdf6-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2bdf6-136">Veja Também</span><span class="sxs-lookup"><span data-stu-id="2bdf6-136">See Also</span></span>

[<span data-ttu-id="2bdf6-137">Elemento de PropertyName para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="2bdf6-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2bdf6-138">Elemento de ScriptBlock para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="2bdf6-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2bdf6-139">Elemento de SelectionSetName para SelectionCondition para controle personalizado para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="2bdf6-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2bdf6-140">Elemento de TypeName para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="2bdf6-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2bdf6-141">Elemento de EntrySelectedBy para CustomEntry para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="2bdf6-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2bdf6-142">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2bdf6-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
