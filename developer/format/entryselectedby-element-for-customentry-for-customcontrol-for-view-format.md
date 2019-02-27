---
title: Elemento de EntrySelectedBy para CustomEntry para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849323"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="acb5d-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) (Elemento EntrySelectedBy para CustomEntry para CustomControl para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="acb5d-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="acb5d-103">Define os tipos do .NET que utilizam esta entrada personalizada ou a condição que tem de existir para esta entrada a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="acb5d-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="acb5d-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para EntrySelectedBy de exibição (formato) Elemento para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="acb5d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="acb5d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="acb5d-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="acb5d-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="acb5d-106">Attributes and Elements</span></span>

<span data-ttu-id="acb5d-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="acb5d-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="acb5d-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="acb5d-108">Attributes</span></span>

<span data-ttu-id="acb5d-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="acb5d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="acb5d-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="acb5d-110">Child Elements</span></span>

|<span data-ttu-id="acb5d-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="acb5d-111">Element</span></span>|<span data-ttu-id="acb5d-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="acb5d-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="acb5d-113">Elemento de SelectionCondition para EntrySelectedBy para CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="acb5d-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="acb5d-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="acb5d-114">Optional element.</span></span><br /><br /> <span data-ttu-id="acb5d-115">Define a condição de que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="acb5d-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="acb5d-116">Elemento de SelectionSetName para EntrySelectedBy para CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="acb5d-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="acb5d-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="acb5d-117">Optional element.</span></span><br /><br /> <span data-ttu-id="acb5d-118">Especifica um conjunto de tipos do .NET que utilizam esta definição do modo de exibição control.</span><span class="sxs-lookup"><span data-stu-id="acb5d-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="acb5d-119">Elemento de TypeName para EntrySelectedBy para CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="acb5d-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="acb5d-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="acb5d-120">Optional element.</span></span><br /><br /> <span data-ttu-id="acb5d-121">Especifica um tipo .NET que utiliza esta definição do modo de exibição control.</span><span class="sxs-lookup"><span data-stu-id="acb5d-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="acb5d-122">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="acb5d-122">Parent Elements</span></span>

|<span data-ttu-id="acb5d-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="acb5d-123">Element</span></span>|<span data-ttu-id="acb5d-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="acb5d-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="acb5d-125">Elemento de CustomEntry para CustomEntries para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="acb5d-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="acb5d-126">Define os controlos utilizados por objetos específicos do .NET.</span><span class="sxs-lookup"><span data-stu-id="acb5d-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="acb5d-127">Observações</span><span class="sxs-lookup"><span data-stu-id="acb5d-127">Remarks</span></span>

<span data-ttu-id="acb5d-128">Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para uma entrada.</span><span class="sxs-lookup"><span data-stu-id="acb5d-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="acb5d-129">Não existe nenhum limite máximo para o número de elementos filho que pode utilizar.</span><span class="sxs-lookup"><span data-stu-id="acb5d-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="acb5d-130">Condições de seleção são utilizadas para definir uma condição que tem de existir para a entrada a ser utilizado, como quando um objeto tem uma propriedade específica ou quando um valor de propriedade específica ou script que é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="acb5d-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="acb5d-131">Para obter mais informações sobre as condições de seleção, consulte [Defining condições para quando uma entrada de exibição ou Item serve](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="acb5d-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="acb5d-132">Para obter mais informações sobre os componentes de uma vista de controle personalizado, consulte [modo de exibição de controle personalizado](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="acb5d-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="acb5d-133">Veja Também</span><span class="sxs-lookup"><span data-stu-id="acb5d-133">See Also</span></span>

[<span data-ttu-id="acb5d-134">Elemento de SelectionCondition para EntrySelectedBy para CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="acb5d-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="acb5d-135">Elemento de SelectionSetName para EntrySelectedBy para CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="acb5d-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="acb5d-136">Elemento de TypeName para EntrySelectedBy para CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="acb5d-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="acb5d-137">Elemento de CustomEntry para CustomEntries para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="acb5d-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="acb5d-138">Modo de exibição do controle personalizado</span><span class="sxs-lookup"><span data-stu-id="acb5d-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="acb5d-139">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="acb5d-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
