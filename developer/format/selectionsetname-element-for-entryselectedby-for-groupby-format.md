---
title: Elemento de SelectionSetName para EntrySelectedBy para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064072"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="b02f8-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format) (Elemento SelectionSetName para EntrySelectedBy para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="b02f8-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="b02f8-103">Especifica um conjunto de objetos .NET para a entrada da lista.</span><span class="sxs-lookup"><span data-stu-id="b02f8-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="b02f8-104">Não existe nenhum limite para o número de conjuntos de seleção que podem ser especificados para uma entrada.</span><span class="sxs-lookup"><span data-stu-id="b02f8-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="b02f8-105">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="b02f8-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b02f8-106">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de EntrySelectedBy GroupBy (formato) para CustomEntry para o elemento de SelectionSetName GroupBy (formato) para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b02f8-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b02f8-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b02f8-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b02f8-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b02f8-108">Attributes and Elements</span></span>

<span data-ttu-id="b02f8-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="b02f8-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b02f8-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b02f8-110">Attributes</span></span>

<span data-ttu-id="b02f8-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b02f8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b02f8-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="b02f8-112">Child Elements</span></span>

<span data-ttu-id="b02f8-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b02f8-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b02f8-114">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="b02f8-114">Parent Elements</span></span>

|<span data-ttu-id="b02f8-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="b02f8-115">Element</span></span>|<span data-ttu-id="b02f8-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="b02f8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b02f8-117">Elemento de EntrySelectedBy para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b02f8-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="b02f8-118">Define os tipos do .NET que utilizam esta entrada personalizada ou a condição que tem de existir para esta entrada a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="b02f8-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b02f8-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="b02f8-119">Text Value</span></span>

<span data-ttu-id="b02f8-120">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="b02f8-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b02f8-121">Observações</span><span class="sxs-lookup"><span data-stu-id="b02f8-121">Remarks</span></span>

<span data-ttu-id="b02f8-122">Cada definição de controle personalizado tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.</span><span class="sxs-lookup"><span data-stu-id="b02f8-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="b02f8-123">Conjuntos de seleção são normalmente utilizados quando quiser definir um grupo de objetos que são utilizados em vários modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="b02f8-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="b02f8-124">Por exemplo, pode querer criar uma vista de tabela e uma vista de lista para o mesmo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="b02f8-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="b02f8-125">Para obter mais informações sobre como definir conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b02f8-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b02f8-126">Para obter mais informações sobre os componentes de uma vista de controle personalizado, consulte [criar controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b02f8-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b02f8-127">Veja Também</span><span class="sxs-lookup"><span data-stu-id="b02f8-127">See Also</span></span>

[<span data-ttu-id="b02f8-128">Elemento de EntrySelectedBy para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b02f8-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="b02f8-129">Criação de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="b02f8-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="b02f8-130">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b02f8-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
