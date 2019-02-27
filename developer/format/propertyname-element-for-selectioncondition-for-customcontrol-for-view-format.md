---
title: Elemento de PropertyName para SelectionCondition para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850289"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="13b5b-102">PropertyName Element for SelectionCondition for CustomControl for View (Format) (Elemento PropertyName para SelectionCondition para CustomControl para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="13b5b-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="13b5b-103">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="13b5b-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="13b5b-104">Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e a definição é utilizada.</span><span class="sxs-lookup"><span data-stu-id="13b5b-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="13b5b-105">Este elemento é utilizado ao definir uma vista de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="13b5b-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="13b5b-106">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento de configuração para o modo de exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para CustomControl para exibição ( Elemento de CustomItem de formato) para CustomEntry para CustomControl para exibição (formato) EntrySelectedBy elemento para CustomEntry para CustomControl para exibição (formato) SelectionCondition elemento para EntrySelectedBy para CustomControl para exibição (formato) PropertyName Elemento para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="13b5b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="13b5b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13b5b-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="13b5b-108">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="13b5b-108">Attributes and Elements</span></span>

<span data-ttu-id="13b5b-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="13b5b-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="13b5b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="13b5b-110">Attributes</span></span>

<span data-ttu-id="13b5b-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="13b5b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="13b5b-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="13b5b-112">Child Elements</span></span>

<span data-ttu-id="13b5b-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="13b5b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="13b5b-114">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="13b5b-114">Parent Elements</span></span>

|<span data-ttu-id="13b5b-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="13b5b-115">Element</span></span>|<span data-ttu-id="13b5b-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="13b5b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13b5b-117">Elemento de SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="13b5b-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="13b5b-118">Define uma condição que tem de existir durante a definição de controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="13b5b-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="13b5b-119">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="13b5b-119">Text Value</span></span>

<span data-ttu-id="13b5b-120">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="13b5b-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="13b5b-121">Observações</span><span class="sxs-lookup"><span data-stu-id="13b5b-121">Remarks</span></span>

<span data-ttu-id="13b5b-122">A condição de seleção tem de especificar um nome de uma propriedade, pelo menos, ou um script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="13b5b-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="13b5b-123">Para obter mais informações sobre como as condições de seleção podem ser utilizadas, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="13b5b-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="13b5b-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="13b5b-124">See Also</span></span>

[<span data-ttu-id="13b5b-125">Elemento de SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="13b5b-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="13b5b-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="13b5b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
