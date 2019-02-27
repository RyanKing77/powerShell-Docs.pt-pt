---
title: Elemento de PropertyName para SelectionCondition para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845081"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="c6874-102">PropertyName Element for SelectionCondition for Controls for View (Format) (Elemento PropertyName para SelectionCondition para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="c6874-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="c6874-103">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="c6874-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="c6874-104">Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e a entrada é utilizada.</span><span class="sxs-lookup"><span data-stu-id="c6874-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="c6874-105">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="c6874-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c6874-106">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para controles para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) EntrySelectedBy elemento para CustomEntry para controles para exibição (formato) SelectionCondition elemento para EntrySelectedBy para controles para exibição ( Elemento de PropertyName de formato) para SelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="c6874-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c6874-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6874-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c6874-108">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="c6874-108">Attributes and Elements</span></span>

<span data-ttu-id="c6874-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="c6874-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c6874-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c6874-110">Attributes</span></span>

<span data-ttu-id="c6874-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c6874-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c6874-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="c6874-112">Child Elements</span></span>

<span data-ttu-id="c6874-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c6874-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c6874-114">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="c6874-114">Parent Elements</span></span>

|<span data-ttu-id="c6874-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="c6874-115">Element</span></span>|<span data-ttu-id="c6874-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6874-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c6874-117">Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="c6874-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="c6874-118">Define uma condição que tem de existir durante a definição de controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="c6874-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c6874-119">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="c6874-119">Text Value</span></span>

<span data-ttu-id="c6874-120">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="c6874-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="c6874-121">Observações</span><span class="sxs-lookup"><span data-stu-id="c6874-121">Remarks</span></span>

<span data-ttu-id="c6874-122">A condição de seleção tem de especificar um nome de uma propriedade, pelo menos, ou um script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="c6874-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="c6874-123">Para obter mais informações sobre como as condições de seleção podem ser utilizadas, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c6874-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6874-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c6874-124">See Also</span></span>

[<span data-ttu-id="c6874-125">Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="c6874-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="c6874-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6874-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
