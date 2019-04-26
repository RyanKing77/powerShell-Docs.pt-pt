---
title: Elemento de EntrySelectedBy para WideEntry (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066180"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="ba18f-102">EntrySelectedBy Element for WideEntry (Format) (Elemento EntrySelectedBy para WideEntry [Formatação])</span><span class="sxs-lookup"><span data-stu-id="ba18f-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="ba18f-103">Define os tipos do .NET que utilizam esta definição da vista alargada ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="ba18f-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="ba18f-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) EntrySelectedBy elemento de configuração para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ba18f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ba18f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba18f-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ba18f-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ba18f-106">Attributes and Elements</span></span>

<span data-ttu-id="ba18f-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="ba18f-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ba18f-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="ba18f-108">Attributes</span></span>

<span data-ttu-id="ba18f-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ba18f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ba18f-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="ba18f-110">Child Elements</span></span>

|<span data-ttu-id="ba18f-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="ba18f-111">Element</span></span>|<span data-ttu-id="ba18f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba18f-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ba18f-113">Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ba18f-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="ba18f-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ba18f-114">Optional element.</span></span><br /><br /> <span data-ttu-id="ba18f-115">Define a condição de que tem de existir para esta definição de vista alargada ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="ba18f-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="ba18f-116">Elemento de SelectionSetName para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ba18f-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="ba18f-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ba18f-117">Optional element.</span></span><br /><br /> <span data-ttu-id="ba18f-118">Especifica um conjunto de tipos do .NET que utilizam esta definição de vista alargada.</span><span class="sxs-lookup"><span data-stu-id="ba18f-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="ba18f-119">Elemento de TypeName para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ba18f-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="ba18f-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="ba18f-120">Optional element.</span></span><br /><br /> <span data-ttu-id="ba18f-121">Especifica um tipo .NET que utiliza esta definição de vista alargada.</span><span class="sxs-lookup"><span data-stu-id="ba18f-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ba18f-122">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="ba18f-122">Parent Elements</span></span>

|<span data-ttu-id="ba18f-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="ba18f-123">Element</span></span>|<span data-ttu-id="ba18f-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba18f-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ba18f-125">Elemento de WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ba18f-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="ba18f-126">Fornece uma definição da vista ampla.</span><span class="sxs-lookup"><span data-stu-id="ba18f-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ba18f-127">Observações</span><span class="sxs-lookup"><span data-stu-id="ba18f-127">Remarks</span></span>

<span data-ttu-id="ba18f-128">Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção de uma definição de vista alargada.</span><span class="sxs-lookup"><span data-stu-id="ba18f-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="ba18f-129">Não existe nenhum limite máximo para o número de elementos filho que pode utilizar.</span><span class="sxs-lookup"><span data-stu-id="ba18f-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="ba18f-130">Condições de seleção são utilizadas para definir uma condição que tem de existir durante a definição a utilizar, por exemplo, quando um objeto tem uma propriedade específica ou um valor de propriedade específica ou um valor de script, que é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="ba18f-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="ba18f-131">Para obter mais informações sobre as condições de seleção, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ba18f-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ba18f-132">Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="ba18f-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ba18f-133">Veja Também</span><span class="sxs-lookup"><span data-stu-id="ba18f-133">See Also</span></span>

[<span data-ttu-id="ba18f-134">Elemento de WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ba18f-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="ba18f-135">Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ba18f-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="ba18f-136">Elemento de SelectionSetName para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ba18f-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="ba18f-137">Elemento de TypeName para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="ba18f-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="ba18f-138">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="ba18f-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ba18f-139">Definir condições para apresentar os dados</span><span class="sxs-lookup"><span data-stu-id="ba18f-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ba18f-140">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba18f-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
