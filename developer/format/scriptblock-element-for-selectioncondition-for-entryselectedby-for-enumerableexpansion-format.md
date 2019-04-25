---
title: Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064378"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="ac2b9-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format) (Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para EnumerableExpansion [Formatação])</span><span class="sxs-lookup"><span data-stu-id="ac2b9-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="ac2b9-103">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="ac2b9-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="ac2b9-104">O elemento (formato) DefaultSettings elemento (formato) EnumerableExpansions elemento (formato) EnumerableExpansion elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition EnumerableExpansion (formato) para EntrySelectedBy para Elemento de ScriptBlock EnumerableExpansion (formato) para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="ac2b9-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ac2b9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac2b9-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ac2b9-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ac2b9-106">Attributes and Elements</span></span>

<span data-ttu-id="ac2b9-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="ac2b9-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ac2b9-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="ac2b9-108">Attributes</span></span>

<span data-ttu-id="ac2b9-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ac2b9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ac2b9-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="ac2b9-110">Child Elements</span></span>

<span data-ttu-id="ac2b9-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ac2b9-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ac2b9-112">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="ac2b9-112">Parent Elements</span></span>

|<span data-ttu-id="ac2b9-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="ac2b9-113">Element</span></span>|<span data-ttu-id="ac2b9-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac2b9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ac2b9-115">Elemento de SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="ac2b9-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="ac2b9-116">Define a condição de que tem de existir para expandir os objetos da coleção desta definição.</span><span class="sxs-lookup"><span data-stu-id="ac2b9-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ac2b9-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="ac2b9-117">Text Value</span></span>

<span data-ttu-id="ac2b9-118">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="ac2b9-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="ac2b9-119">Observações</span><span class="sxs-lookup"><span data-stu-id="ac2b9-119">Remarks</span></span>

<span data-ttu-id="ac2b9-120">A condição de seleção tem de especificar, pelo menos, um nome de script ou de propriedade para avaliar, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="ac2b9-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="ac2b9-121">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ac2b9-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ac2b9-122">Veja Também</span><span class="sxs-lookup"><span data-stu-id="ac2b9-122">See Also</span></span>

[<span data-ttu-id="ac2b9-123">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="ac2b9-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ac2b9-124">Elemento de PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="ac2b9-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="ac2b9-125">Elemento de SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="ac2b9-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="ac2b9-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ac2b9-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
