---
title: Elemento de PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849351"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="44a47-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format) (Elemento PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion [Formatação])</span><span class="sxs-lookup"><span data-stu-id="44a47-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="44a47-103">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="44a47-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="44a47-104">Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e a definição é utilizada.</span><span class="sxs-lookup"><span data-stu-id="44a47-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="44a47-105">O elemento (formato) DefaultSettings elemento (formato) EnumerableExpansions elemento (formato) EnumerableExpansion elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition EnumerableExpansion (formato) para EntrySelectedBy para Elemento de PropertyName EnumerableExpansion (formato) para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="44a47-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="44a47-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44a47-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="44a47-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="44a47-107">Attributes and Elements</span></span>

<span data-ttu-id="44a47-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="44a47-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="44a47-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="44a47-109">Attributes</span></span>

<span data-ttu-id="44a47-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="44a47-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="44a47-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="44a47-111">Child Elements</span></span>

<span data-ttu-id="44a47-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="44a47-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="44a47-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="44a47-113">Parent Elements</span></span>

|<span data-ttu-id="44a47-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="44a47-114">Element</span></span>|<span data-ttu-id="44a47-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="44a47-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="44a47-116">Elemento de SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="44a47-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="44a47-117">Define a condição de que tem de existir para expandir os objetos da coleção desta definição.</span><span class="sxs-lookup"><span data-stu-id="44a47-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="44a47-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="44a47-118">Text Value</span></span>

<span data-ttu-id="44a47-119">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="44a47-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="44a47-120">Observações</span><span class="sxs-lookup"><span data-stu-id="44a47-120">Remarks</span></span>

<span data-ttu-id="44a47-121">A condição de seleção tem de especificar o nome de pelo menos uma propriedade ou um script para avaliar, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="44a47-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="44a47-122">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="44a47-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="44a47-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="44a47-123">See Also</span></span>

[<span data-ttu-id="44a47-124">Definir condições para os dados quando é apresentada</span><span class="sxs-lookup"><span data-stu-id="44a47-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="44a47-125">Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="44a47-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="44a47-126">Elemento de SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="44a47-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="44a47-127">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="44a47-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
