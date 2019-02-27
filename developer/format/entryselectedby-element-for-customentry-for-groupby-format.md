---
title: Elemento de EntrySelectedBy para CustomEntry para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851584"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="03ca1-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format) (Elemento EntrySelectedBy para CustomEntry para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="03ca1-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="03ca1-103">Define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="03ca1-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="03ca1-104">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="03ca1-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="03ca1-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de EntrySelectedBy GroupBy (formato) para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="03ca1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="03ca1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03ca1-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="03ca1-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="03ca1-107">Attributes and Elements</span></span>

<span data-ttu-id="03ca1-108">As secções seguintes descrevem os atributos e elemento pai de elementos filho do `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="03ca1-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="03ca1-109">Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção de uma definição.</span><span class="sxs-lookup"><span data-stu-id="03ca1-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="03ca1-110">Não existe nenhum limite máximo para o número de elementos filho que pode utilizar.</span><span class="sxs-lookup"><span data-stu-id="03ca1-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="03ca1-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="03ca1-111">Attributes</span></span>

<span data-ttu-id="03ca1-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="03ca1-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="03ca1-113">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="03ca1-113">Child Elements</span></span>

|<span data-ttu-id="03ca1-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="03ca1-114">Element</span></span>|<span data-ttu-id="03ca1-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="03ca1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="03ca1-116">Elemento de SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="03ca1-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="03ca1-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="03ca1-117">Optional element.</span></span><br /><br /> <span data-ttu-id="03ca1-118">Define a condição de que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="03ca1-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="03ca1-119">Elemento de SelectionSetName para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="03ca1-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="03ca1-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="03ca1-120">Optional element.</span></span><br /><br /> <span data-ttu-id="03ca1-121">Especifica um conjunto de tipos do .NET que utilizam esta definição do controle.</span><span class="sxs-lookup"><span data-stu-id="03ca1-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="03ca1-122">Elemento de TypeName para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="03ca1-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="03ca1-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="03ca1-123">Optional element.</span></span><br /><br /> <span data-ttu-id="03ca1-124">Especifica um tipo .NET que utiliza esta definição do controle.</span><span class="sxs-lookup"><span data-stu-id="03ca1-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="03ca1-125">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="03ca1-125">Parent Elements</span></span>

|<span data-ttu-id="03ca1-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="03ca1-126">Element</span></span>|<span data-ttu-id="03ca1-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="03ca1-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="03ca1-128">Elemento de CustomEntry para CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="03ca1-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="03ca1-129">Fornece uma definição do controle.</span><span class="sxs-lookup"><span data-stu-id="03ca1-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="03ca1-130">Observações</span><span class="sxs-lookup"><span data-stu-id="03ca1-130">Remarks</span></span>

<span data-ttu-id="03ca1-131">Condições de seleção são utilizadas para definir uma condição que tem de existir para a definição a utilizar, como quando um objeto tem uma propriedade específica ou quando um valor de propriedade específica ou script que é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="03ca1-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="03ca1-132">Para obter mais informações sobre as condições de seleção, consulte [Defining condições para quando uma entrada de exibição ou Item serve](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="03ca1-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="03ca1-133">Veja Também</span><span class="sxs-lookup"><span data-stu-id="03ca1-133">See Also</span></span>

[<span data-ttu-id="03ca1-134">Elemento de SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="03ca1-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="03ca1-135">Elemento de SelectionSetName para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="03ca1-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="03ca1-136">Elemento de TypeName para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="03ca1-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="03ca1-137">Elemento de CustomEntry para CustomEntries para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="03ca1-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="03ca1-138">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="03ca1-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
