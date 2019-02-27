---
title: Elemento de PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849904"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="74a59-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format) (Elemento PropertyName para SelectionCondition para EntrySelectedBy para WideEntry [Formatação])</span><span class="sxs-lookup"><span data-stu-id="74a59-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="74a59-103">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="74a59-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="74a59-104">Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e a definição é utilizada.</span><span class="sxs-lookup"><span data-stu-id="74a59-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="74a59-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition WideEntry (formato) para EntrySelectedBy para o elemento de PropertyName WideEntry (formato) para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="74a59-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="74a59-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74a59-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="74a59-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="74a59-107">Attributes and Elements</span></span>

<span data-ttu-id="74a59-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="74a59-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="74a59-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="74a59-109">Attributes</span></span>

<span data-ttu-id="74a59-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="74a59-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="74a59-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="74a59-111">Child Elements</span></span>

<span data-ttu-id="74a59-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="74a59-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="74a59-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="74a59-113">Parent Elements</span></span>

|<span data-ttu-id="74a59-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="74a59-114">Element</span></span>|<span data-ttu-id="74a59-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="74a59-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="74a59-116">Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="74a59-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="74a59-117">Define a condição de que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="74a59-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="74a59-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="74a59-118">Text Value</span></span>

<span data-ttu-id="74a59-119">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="74a59-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="74a59-120">Observações</span><span class="sxs-lookup"><span data-stu-id="74a59-120">Remarks</span></span>

<span data-ttu-id="74a59-121">A condição de seleção tem de especificar o nome de pelo menos uma propriedade ou um script para avaliar, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="74a59-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="74a59-122">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="74a59-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="74a59-123">Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="74a59-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="74a59-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="74a59-124">See Also</span></span>

[<span data-ttu-id="74a59-125">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="74a59-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="74a59-126">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="74a59-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="74a59-127">Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="74a59-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="74a59-128">Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="74a59-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="74a59-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="74a59-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
