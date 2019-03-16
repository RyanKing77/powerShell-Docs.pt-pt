---
title: Elemento de EntrySelectedBy para ListEntry para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054948"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="48617-102">EntrySelectedBy Element for ListEntry for ListControl (Format) (Elemento EntrySelectedBy para ListEntry para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="48617-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="48617-103">Define os tipos do .NET que utilizam esta definição de vista de lista ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="48617-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="48617-104">Na maioria dos casos, apenas uma definição é necessária para uma vista de lista.</span><span class="sxs-lookup"><span data-stu-id="48617-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="48617-105">No entanto, pode fornecer várias definições para a vista de lista, se pretender utilizar a mesma vista de lista para apresentar dados diferentes para objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="48617-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="48617-106">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry ListControl (formato) para ListEntry para o elemento de EntrySelectedBy ListControl (formato) para ListEntry para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="48617-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="48617-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48617-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="48617-108">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="48617-108">Attributes and Elements</span></span>

<span data-ttu-id="48617-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="48617-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="48617-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="48617-110">Attributes</span></span>

<span data-ttu-id="48617-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="48617-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="48617-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="48617-112">Child Elements</span></span>

|<span data-ttu-id="48617-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="48617-113">Element</span></span>|<span data-ttu-id="48617-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="48617-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="48617-115">Elemento de SelectionCondition para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="48617-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="48617-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="48617-116">Optional element.</span></span><br /><br /> <span data-ttu-id="48617-117">Define a condição de que tem de existir para esta definição de vista de lista a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="48617-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="48617-118">Elemento de SelectionSetName para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="48617-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="48617-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="48617-119">Optional element.</span></span><br /><br /> <span data-ttu-id="48617-120">Especifica um conjunto de tipos do .NET que utilizam esta definição de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="48617-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="48617-121">Elemento de TypeName para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="48617-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="48617-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="48617-122">Optional element.</span></span><br /><br /> <span data-ttu-id="48617-123">Especifica um tipo .NET que utiliza esta definição de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="48617-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="48617-124">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="48617-124">Parent Elements</span></span>

|<span data-ttu-id="48617-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="48617-125">Element</span></span>|<span data-ttu-id="48617-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="48617-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="48617-127">Elemento de ListEntry para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="48617-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="48617-128">Define a forma como são apresentadas as linhas da lista.</span><span class="sxs-lookup"><span data-stu-id="48617-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="48617-129">Observações</span><span class="sxs-lookup"><span data-stu-id="48617-129">Remarks</span></span>

<span data-ttu-id="48617-130">Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para uma definição de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="48617-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="48617-131">Não existe nenhum limite máximo para o número de elementos filho que pode utilizar.</span><span class="sxs-lookup"><span data-stu-id="48617-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="48617-132">Condições de seleção são utilizadas para definir uma condição que tem de existir durante a definição a utilizar, por exemplo, quando um objeto tem uma propriedade específica ou um valor de propriedade específica ou um script é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="48617-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="48617-133">Para obter mais informações sobre as condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="48617-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="48617-134">Para obter mais informações sobre os componentes de uma vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="48617-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="48617-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48617-135">Example</span></span>

<span data-ttu-id="48617-136">O exemplo seguinte mostra como definir os objetos para uma vista de lista com o respetivo nome de tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="48617-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="48617-137">Veja Também</span><span class="sxs-lookup"><span data-stu-id="48617-137">See Also</span></span>

[<span data-ttu-id="48617-138">Elemento de ListEntry para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="48617-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="48617-139">Elemento de SelectionCondition para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="48617-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="48617-140">Elemento de SelectionSetName para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="48617-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="48617-141">Elemento de TypeName para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="48617-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="48617-142">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="48617-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="48617-143">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="48617-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="48617-144">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="48617-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
