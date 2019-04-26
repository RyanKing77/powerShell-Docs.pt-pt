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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075482"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="75ba1-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format) (Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry [Formatação])</span><span class="sxs-lookup"><span data-stu-id="75ba1-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="75ba1-103">Especifica o conjunto de tipos do .NET que acionam a condição.</span><span class="sxs-lookup"><span data-stu-id="75ba1-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="75ba1-104">Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado ao utilizar esta definição da vista ampla.</span><span class="sxs-lookup"><span data-stu-id="75ba1-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="75ba1-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition WideEntry (formato) para EntrySelectedBy para o elemento de SelectionSetName WideEntry (formato) para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="75ba1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="75ba1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75ba1-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75ba1-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="75ba1-107">Attributes and Elements</span></span>

<span data-ttu-id="75ba1-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="75ba1-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="75ba1-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="75ba1-109">Attributes</span></span>

<span data-ttu-id="75ba1-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="75ba1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="75ba1-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="75ba1-111">Child Elements</span></span>

<span data-ttu-id="75ba1-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="75ba1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="75ba1-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="75ba1-113">Parent Elements</span></span>

|<span data-ttu-id="75ba1-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="75ba1-114">Element</span></span>|<span data-ttu-id="75ba1-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="75ba1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75ba1-116">Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="75ba1-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="75ba1-117">Define a condição de que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="75ba1-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="75ba1-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="75ba1-118">Text Value</span></span>

<span data-ttu-id="75ba1-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="75ba1-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="75ba1-120">Observações</span><span class="sxs-lookup"><span data-stu-id="75ba1-120">Remarks</span></span>

<span data-ttu-id="75ba1-121">A condição de seleção pode especificar um conjunto de seleção ou o tipo .NET, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="75ba1-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="75ba1-122">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="75ba1-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="75ba1-123">Conjuntos de seleção são comuns grupos de objetos .NET que podem ser utilizados por qualquer vista que define o ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="75ba1-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="75ba1-124">Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="75ba1-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="75ba1-125">Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="75ba1-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="75ba1-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="75ba1-126">See Also</span></span>

[<span data-ttu-id="75ba1-127">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="75ba1-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="75ba1-128">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="75ba1-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="75ba1-129">Definir conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="75ba1-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="75ba1-130">Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="75ba1-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="75ba1-131">Elemento de TypeName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="75ba1-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="75ba1-132">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="75ba1-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
