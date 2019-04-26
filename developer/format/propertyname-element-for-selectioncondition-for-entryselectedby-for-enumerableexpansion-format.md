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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064956"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="55764-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format) (Elemento PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion [Formatação])</span><span class="sxs-lookup"><span data-stu-id="55764-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="55764-103">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="55764-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="55764-104">Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e a definição é utilizada.</span><span class="sxs-lookup"><span data-stu-id="55764-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="55764-105">O elemento (formato) DefaultSettings elemento (formato) EnumerableExpansions elemento (formato) EnumerableExpansion elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition EnumerableExpansion (formato) para EntrySelectedBy para Elemento de PropertyName EnumerableExpansion (formato) para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="55764-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="55764-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55764-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="55764-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="55764-107">Attributes and Elements</span></span>

<span data-ttu-id="55764-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="55764-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="55764-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="55764-109">Attributes</span></span>

<span data-ttu-id="55764-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="55764-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="55764-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="55764-111">Child Elements</span></span>

<span data-ttu-id="55764-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="55764-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="55764-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="55764-113">Parent Elements</span></span>

|<span data-ttu-id="55764-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="55764-114">Element</span></span>|<span data-ttu-id="55764-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="55764-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55764-116">Elemento de SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="55764-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="55764-117">Define a condição de que tem de existir para expandir os objetos da coleção desta definição.</span><span class="sxs-lookup"><span data-stu-id="55764-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="55764-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="55764-118">Text Value</span></span>

<span data-ttu-id="55764-119">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="55764-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="55764-120">Observações</span><span class="sxs-lookup"><span data-stu-id="55764-120">Remarks</span></span>

<span data-ttu-id="55764-121">A condição de seleção tem de especificar o nome de pelo menos uma propriedade ou um script para avaliar, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="55764-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="55764-122">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="55764-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="55764-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="55764-123">See Also</span></span>

[<span data-ttu-id="55764-124">Definir condições para os dados quando é apresentada</span><span class="sxs-lookup"><span data-stu-id="55764-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="55764-125">Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="55764-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="55764-126">Elemento de SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="55764-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="55764-127">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="55764-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
