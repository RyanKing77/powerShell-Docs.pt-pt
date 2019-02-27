---
title: Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845501"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="131bf-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format) (Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry [Formatação])</span><span class="sxs-lookup"><span data-stu-id="131bf-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="131bf-103">Especifica o conjunto de tipos do .NET que acionam a condição.</span><span class="sxs-lookup"><span data-stu-id="131bf-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="131bf-104">Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado ao utilizar esta definição da vista ampla.</span><span class="sxs-lookup"><span data-stu-id="131bf-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="131bf-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition WideEntry (formato) para EntrySelectedBy para o elemento de SelectionSetName WideEntry (formato) para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="131bf-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="131bf-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="131bf-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="131bf-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="131bf-107">Attributes and Elements</span></span>

<span data-ttu-id="131bf-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="131bf-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="131bf-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="131bf-109">Attributes</span></span>

<span data-ttu-id="131bf-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="131bf-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="131bf-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="131bf-111">Child Elements</span></span>

<span data-ttu-id="131bf-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="131bf-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="131bf-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="131bf-113">Parent Elements</span></span>

|<span data-ttu-id="131bf-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="131bf-114">Element</span></span>|<span data-ttu-id="131bf-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="131bf-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="131bf-116">Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="131bf-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="131bf-117">Define a condição de que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="131bf-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="131bf-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="131bf-118">Text Value</span></span>

<span data-ttu-id="131bf-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="131bf-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="131bf-120">Observações</span><span class="sxs-lookup"><span data-stu-id="131bf-120">Remarks</span></span>

<span data-ttu-id="131bf-121">A condição de seleção pode especificar um conjunto de seleção ou o tipo .NET, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="131bf-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="131bf-122">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="131bf-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="131bf-123">Conjuntos de seleção são comuns grupos de objetos .NET que podem ser utilizados por qualquer vista que define o ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="131bf-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="131bf-124">Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="131bf-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="131bf-125">Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="131bf-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="131bf-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="131bf-126">See Also</span></span>

[<span data-ttu-id="131bf-127">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="131bf-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="131bf-128">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="131bf-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="131bf-129">Definir conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="131bf-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="131bf-130">Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="131bf-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="131bf-131">Elemento de TypeName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="131bf-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="131bf-132">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="131bf-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
