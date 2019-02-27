---
title: Elemento de SelectionSetName para SelectionCondition para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847342"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="ccd13-102">SelectionSetName Element for SelectionCondition for GroupBy (Format) (Elemento SelectionSetName para SelectionCondition para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="ccd13-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="ccd13-103">Especifica o conjunto de tipos do .NET que acionam a condição.</span><span class="sxs-lookup"><span data-stu-id="ccd13-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="ccd13-104">Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado ao utilizar este controlo.</span><span class="sxs-lookup"><span data-stu-id="ccd13-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="ccd13-105">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="ccd13-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="ccd13-106">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de EntrySelectedBy GroupBy (formato) para CustomEntry para o elemento de SelectionCondition GroupBy (formato) para EntrySelectedBy para o elemento de SelectionSetName GroupBy (formato) para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ccd13-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ccd13-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ccd13-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ccd13-108">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="ccd13-108">Attributes and Elements</span></span>

<span data-ttu-id="ccd13-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="ccd13-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ccd13-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ccd13-110">Attributes</span></span>

<span data-ttu-id="ccd13-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ccd13-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ccd13-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="ccd13-112">Child Elements</span></span>

<span data-ttu-id="ccd13-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ccd13-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ccd13-114">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="ccd13-114">Parent Elements</span></span>

|<span data-ttu-id="ccd13-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="ccd13-115">Element</span></span>|<span data-ttu-id="ccd13-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccd13-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ccd13-117">Elemento de SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ccd13-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="ccd13-118">Define uma condição que tem de existir durante a definição de controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="ccd13-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ccd13-119">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="ccd13-119">Text Value</span></span>

<span data-ttu-id="ccd13-120">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="ccd13-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ccd13-121">Observações</span><span class="sxs-lookup"><span data-stu-id="ccd13-121">Remarks</span></span>

<span data-ttu-id="ccd13-122">Conjuntos de seleção são comuns grupos de objetos .NET que podem ser utilizados por qualquer vista que define o ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="ccd13-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="ccd13-123">Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ccd13-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="ccd13-124">Quando este elemento é especificado, não é possível especificar a [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="ccd13-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="ccd13-125">Para obter mais informações sobre como definir condições de seleção, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ccd13-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ccd13-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="ccd13-126">See Also</span></span>

[<span data-ttu-id="ccd13-127">Elemento de TypeName para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ccd13-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="ccd13-128">Elemento de SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ccd13-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="ccd13-129">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="ccd13-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ccd13-130">Definir conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="ccd13-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="ccd13-131">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ccd13-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
