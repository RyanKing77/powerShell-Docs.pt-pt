---
title: Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844766"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="78754-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format) (Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="78754-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="78754-103">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="78754-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="78754-104">Quando esse script é avaliado para `true`, a condição é cumprida e a definição é utilizada.</span><span class="sxs-lookup"><span data-stu-id="78754-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="78754-105">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="78754-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="78754-106">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de EntrySelectedBy GroupBy (formato) para CustomEntry para o elemento de SelectionCondition GroupBy (formato) para EntrySelectedBy para o elemento de ScriptBlock GroupBy (formato) para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="78754-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="78754-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78754-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="78754-108">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="78754-108">Attributes and Elements</span></span>

<span data-ttu-id="78754-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="78754-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="78754-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="78754-110">Attributes</span></span>

<span data-ttu-id="78754-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="78754-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="78754-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="78754-112">Child Elements</span></span>

<span data-ttu-id="78754-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="78754-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="78754-114">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="78754-114">Parent Elements</span></span>

|<span data-ttu-id="78754-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="78754-115">Element</span></span>|<span data-ttu-id="78754-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="78754-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="78754-117">Elemento de SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="78754-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="78754-118">Define uma condição que tem de existir durante a definição de controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="78754-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="78754-119">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="78754-119">Text Value</span></span>

<span data-ttu-id="78754-120">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="78754-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="78754-121">Observações</span><span class="sxs-lookup"><span data-stu-id="78754-121">Remarks</span></span>

<span data-ttu-id="78754-122">A condição de seleção tem de especificar um, pelo menos, um script ou a propriedade nome para avaliar, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="78754-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="78754-123">Para obter mais informações sobre como as condições de seleção podem ser utilizadas, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="78754-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="78754-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="78754-124">See Also</span></span>

[<span data-ttu-id="78754-125">Elemento de SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="78754-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="78754-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="78754-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
