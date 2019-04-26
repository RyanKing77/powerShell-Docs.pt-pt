---
title: Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075516"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="84c41-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format) (Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry [Formatação])</span><span class="sxs-lookup"><span data-stu-id="84c41-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="84c41-103">Especifica o conjunto de tipos do .NET que acionam a condição.</span><span class="sxs-lookup"><span data-stu-id="84c41-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="84c41-104">Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado ao utilizar esta definição de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="84c41-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="84c41-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento (formato) ListEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition ListEntry (formato) para EntrySelectedBy para o elemento de SelectionSetName ListEntry (formato) para SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="84c41-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="84c41-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84c41-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="84c41-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="84c41-107">Attributes and Elements</span></span>

<span data-ttu-id="84c41-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="84c41-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="84c41-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="84c41-109">Attributes</span></span>

<span data-ttu-id="84c41-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="84c41-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="84c41-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="84c41-111">Child Elements</span></span>

<span data-ttu-id="84c41-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="84c41-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="84c41-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="84c41-113">Parent Elements</span></span>

|<span data-ttu-id="84c41-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="84c41-114">Element</span></span>|<span data-ttu-id="84c41-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="84c41-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="84c41-116">Elemento de SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="84c41-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="84c41-117">Define a condição de que tem de existir para utilizar esta definição de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="84c41-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="84c41-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="84c41-118">Text Value</span></span>

<span data-ttu-id="84c41-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="84c41-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="84c41-120">Observações</span><span class="sxs-lookup"><span data-stu-id="84c41-120">Remarks</span></span>

<span data-ttu-id="84c41-121">A condição de seleção pode especificar um conjunto de seleção ou o tipo .NET, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="84c41-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="84c41-122">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="84c41-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="84c41-123">Conjuntos de seleção são comuns grupos de objetos .NET que podem ser utilizados por qualquer vista que define o ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="84c41-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="84c41-124">Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="84c41-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="84c41-125">Para obter mais informações sobre os outros componentes de uma vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="84c41-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="84c41-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="84c41-126">See Also</span></span>

[<span data-ttu-id="84c41-127">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="84c41-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="84c41-128">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="84c41-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="84c41-129">Elemento de SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="84c41-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="84c41-130">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="84c41-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
