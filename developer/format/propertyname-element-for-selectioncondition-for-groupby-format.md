---
title: Elemento de PropertyName para SelectionCondition para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844843"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="8f155-102">PropertyName Element for SelectionCondition for GroupBy (Format) (Elemento PropertyName para SelectionCondition para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="8f155-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="8f155-103">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="8f155-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="8f155-104">Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e a definição é utilizada.</span><span class="sxs-lookup"><span data-stu-id="8f155-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="8f155-105">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="8f155-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="8f155-106">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de EntrySelectedBy GroupBy (formato) para CustomEntry para o elemento de SelectionCondition GroupBy (formato) para EntrySelectedBy para o elemento de PropertyName GroupBy (formato) para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8f155-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8f155-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f155-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8f155-108">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="8f155-108">Attributes and Elements</span></span>

<span data-ttu-id="8f155-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="8f155-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8f155-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8f155-110">Attributes</span></span>

<span data-ttu-id="8f155-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8f155-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8f155-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="8f155-112">Child Elements</span></span>

<span data-ttu-id="8f155-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8f155-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8f155-114">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="8f155-114">Parent Elements</span></span>

|<span data-ttu-id="8f155-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="8f155-115">Element</span></span>|<span data-ttu-id="8f155-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f155-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f155-117">Elemento de SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8f155-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="8f155-118">Define uma condição que tem de existir durante a definição de controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="8f155-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8f155-119">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="8f155-119">Text Value</span></span>

<span data-ttu-id="8f155-120">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="8f155-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="8f155-121">Observações</span><span class="sxs-lookup"><span data-stu-id="8f155-121">Remarks</span></span>

<span data-ttu-id="8f155-122">A condição de seleção tem de especificar um nome de uma propriedade, pelo menos, ou um script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="8f155-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="8f155-123">Para obter mais informações sobre como as condições de seleção podem ser utilizadas, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8f155-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8f155-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="8f155-124">See Also</span></span>

[<span data-ttu-id="8f155-125">Elemento de SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8f155-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="8f155-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f155-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
