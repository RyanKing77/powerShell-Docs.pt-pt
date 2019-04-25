---
title: Elemento de SelectionSetName para EntrySelectedBy para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075567"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="aa125-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format) (Elemento SelectionSetName para EntrySelectedBy para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="aa125-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="aa125-103">Especifica um conjunto de objetos .NET para a entrada da lista.</span><span class="sxs-lookup"><span data-stu-id="aa125-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="aa125-104">Não existe nenhum limite para o número de conjuntos de seleção que podem ser especificados para uma entrada.</span><span class="sxs-lookup"><span data-stu-id="aa125-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="aa125-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento (formato) ListEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionSetName ListEntry (formato) para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="aa125-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aa125-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa125-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aa125-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="aa125-107">Attributes and Elements</span></span>

<span data-ttu-id="aa125-108">As secções seguintes descrevem os atributos e elemento pai de elementos filho do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="aa125-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aa125-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="aa125-109">Attributes</span></span>

<span data-ttu-id="aa125-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="aa125-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aa125-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="aa125-111">Child Elements</span></span>

<span data-ttu-id="aa125-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="aa125-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aa125-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="aa125-113">Parent Elements</span></span>

|<span data-ttu-id="aa125-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="aa125-114">Element</span></span>|<span data-ttu-id="aa125-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa125-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aa125-116">Elemento de EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="aa125-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="aa125-117">Define os tipos do .NET que utilizam esta entrada da lista ou a condição que tem de existir para esta entrada a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="aa125-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="aa125-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="aa125-118">Text Value</span></span>

<span data-ttu-id="aa125-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="aa125-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="aa125-120">Observações</span><span class="sxs-lookup"><span data-stu-id="aa125-120">Remarks</span></span>

<span data-ttu-id="aa125-121">Cada entrada da lista tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.</span><span class="sxs-lookup"><span data-stu-id="aa125-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="aa125-122">Conjuntos de seleção são normalmente utilizados quando quiser definir um grupo de objetos que são utilizados em vários modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="aa125-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="aa125-123">Por exemplo, pode querer criar uma vista de tabela e uma vista de lista para o mesmo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="aa125-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="aa125-124">Para obter mais informações sobre como definir conjuntos de seleção, consulte [definir conjuntos de objetos para uma visão](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="aa125-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="aa125-125">Para obter mais informações sobre os componentes de uma vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="aa125-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="aa125-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa125-126">Example</span></span>

<span data-ttu-id="aa125-127">O exemplo seguinte mostra como especificar uma seleção definido para uma entrada de uma vista de lista.</span><span class="sxs-lookup"><span data-stu-id="aa125-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="aa125-128">Veja Também</span><span class="sxs-lookup"><span data-stu-id="aa125-128">See Also</span></span>

[<span data-ttu-id="aa125-129">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="aa125-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="aa125-130">Elemento de EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="aa125-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="aa125-131">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa125-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
