---
title: Elemento de EntrySelectedBy para EnumerableExpansion (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846523"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="5ac14-102">EntrySelectedBy Element for EnumerableExpansion (Format) (Elemento EntrySelectedBy para EnumerableExpansion [Formatação])</span><span class="sxs-lookup"><span data-stu-id="5ac14-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="5ac14-103">Define os tipos do .NET que utilizam esta definição ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="5ac14-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="5ac14-104">O elemento (formato) DefaultSettings elemento (formato) EnumerableExpansions elemento (formato) EnumerableExpansion elemento (formato) EntrySelectedBy elemento de configuração para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="5ac14-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5ac14-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ac14-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ac14-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="5ac14-106">Attributes and Elements</span></span>

<span data-ttu-id="5ac14-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="5ac14-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ac14-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="5ac14-108">Attributes</span></span>

<span data-ttu-id="5ac14-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5ac14-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ac14-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="5ac14-110">Child Elements</span></span>

|<span data-ttu-id="5ac14-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ac14-111">Element</span></span>|<span data-ttu-id="5ac14-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ac14-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ac14-113">Elemento de SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="5ac14-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="5ac14-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5ac14-114">Optional element.</span></span><br /><br /> <span data-ttu-id="5ac14-115">Define a condição de que tem de existir para expandir os objetos da coleção desta definição.</span><span class="sxs-lookup"><span data-stu-id="5ac14-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="5ac14-116">Elemento de SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="5ac14-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="5ac14-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5ac14-117">Optional element.</span></span><br /><br /> <span data-ttu-id="5ac14-118">Especifica um conjunto de tipos do .NET que utilizam esta definição de como os objetos da coleção são expandidos.</span><span class="sxs-lookup"><span data-stu-id="5ac14-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="5ac14-119">Elemento de TypeName para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="5ac14-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="5ac14-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5ac14-120">Optional element.</span></span><br /><br /> <span data-ttu-id="5ac14-121">Especifica um tipo .NET que utiliza esta definição de como os objetos da coleção são expandidos.</span><span class="sxs-lookup"><span data-stu-id="5ac14-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5ac14-122">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="5ac14-122">Parent Elements</span></span>

|<span data-ttu-id="5ac14-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ac14-123">Element</span></span>|<span data-ttu-id="5ac14-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ac14-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ac14-125">Elemento de EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="5ac14-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="5ac14-126">Define a coleção de .NET como específica objetos são expandidos quando são apresentados numa vista.</span><span class="sxs-lookup"><span data-stu-id="5ac14-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5ac14-127">Observações</span><span class="sxs-lookup"><span data-stu-id="5ac14-127">Remarks</span></span>

<span data-ttu-id="5ac14-128">Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para uma entrada de definição.</span><span class="sxs-lookup"><span data-stu-id="5ac14-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="5ac14-129">Não existe nenhum limite máximo para o número de elementos filho que pode utilizar.</span><span class="sxs-lookup"><span data-stu-id="5ac14-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="5ac14-130">Condições de seleção são utilizadas para definir uma condição que tem de existir durante a definição a utilizar, por exemplo, quando um objeto tem uma propriedade específica ou um valor de propriedade específica ou um script é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="5ac14-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="5ac14-131">Para obter mais informações sobre as condições de seleção, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5ac14-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5ac14-132">Veja Também</span><span class="sxs-lookup"><span data-stu-id="5ac14-132">See Also</span></span>

[<span data-ttu-id="5ac14-133">Definir condições para apresentar os dados</span><span class="sxs-lookup"><span data-stu-id="5ac14-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="5ac14-134">Elemento de EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="5ac14-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="5ac14-135">Elemento de SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="5ac14-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="5ac14-136">Elemento de SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="5ac14-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="5ac14-137">Elemento de TypeName para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="5ac14-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="5ac14-138">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5ac14-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
