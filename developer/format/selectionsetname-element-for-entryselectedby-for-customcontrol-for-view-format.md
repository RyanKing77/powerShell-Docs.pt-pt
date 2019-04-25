---
title: Elemento de SelectionSetName para EntrySelectedBy para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063982"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="879f6-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format) (Elemento SelectionSetName para EntrySelectedBy para CustomControl para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="879f6-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="879f6-103">Especifica um conjunto de objetos .NET para a entrada da lista.</span><span class="sxs-lookup"><span data-stu-id="879f6-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="879f6-104">Não existe nenhum limite para o número de conjuntos de seleção que podem ser especificados para uma entrada.</span><span class="sxs-lookup"><span data-stu-id="879f6-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="879f6-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para EntrySelectedBy de exibição (formato) Elemento para CustomEntry para exibição (formato) SelectionSetName elemento para EntrySelectedBy para CustomEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="879f6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="879f6-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="879f6-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="879f6-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="879f6-107">Attributes and Elements</span></span>

<span data-ttu-id="879f6-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="879f6-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="879f6-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="879f6-109">Attributes</span></span>

<span data-ttu-id="879f6-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="879f6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="879f6-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="879f6-111">Child Elements</span></span>

<span data-ttu-id="879f6-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="879f6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="879f6-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="879f6-113">Parent Elements</span></span>

|<span data-ttu-id="879f6-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="879f6-114">Element</span></span>|<span data-ttu-id="879f6-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="879f6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="879f6-116">Elemento de EntrySelectedBy para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="879f6-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="879f6-117">Define os tipos do .NET que utilizam esta entrada personalizada ou a condição que tem de existir para esta entrada a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="879f6-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="879f6-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="879f6-118">Text Value</span></span>

<span data-ttu-id="879f6-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="879f6-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="879f6-120">Observações</span><span class="sxs-lookup"><span data-stu-id="879f6-120">Remarks</span></span>

<span data-ttu-id="879f6-121">Cada entrada de controle personalizado tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.</span><span class="sxs-lookup"><span data-stu-id="879f6-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="879f6-122">Conjuntos de seleção são normalmente utilizados quando quiser definir um grupo de objetos que são utilizados em vários modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="879f6-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="879f6-123">Por exemplo, pode querer criar uma vista de tabela e uma vista de lista para o mesmo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="879f6-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="879f6-124">Para obter mais informações sobre como definir conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="879f6-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="879f6-125">Para obter mais informações sobre os componentes de uma vista de controle personalizado, consulte [criar controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="879f6-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="879f6-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="879f6-126">See Also</span></span>

[<span data-ttu-id="879f6-127">Elemento de EntrySelectedBy para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="879f6-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="879f6-128">Modo de exibição do controle personalizado</span><span class="sxs-lookup"><span data-stu-id="879f6-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="879f6-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="879f6-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
