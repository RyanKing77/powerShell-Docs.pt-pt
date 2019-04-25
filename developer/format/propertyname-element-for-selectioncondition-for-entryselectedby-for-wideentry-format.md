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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064684"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="662a2-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format) (Elemento PropertyName para SelectionCondition para EntrySelectedBy para WideEntry [Formatação])</span><span class="sxs-lookup"><span data-stu-id="662a2-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="662a2-103">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="662a2-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="662a2-104">Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e a definição é utilizada.</span><span class="sxs-lookup"><span data-stu-id="662a2-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="662a2-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition WideEntry (formato) para EntrySelectedBy para o elemento de PropertyName WideEntry (formato) para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="662a2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="662a2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="662a2-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="662a2-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="662a2-107">Attributes and Elements</span></span>

<span data-ttu-id="662a2-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="662a2-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="662a2-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="662a2-109">Attributes</span></span>

<span data-ttu-id="662a2-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="662a2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="662a2-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="662a2-111">Child Elements</span></span>

<span data-ttu-id="662a2-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="662a2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="662a2-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="662a2-113">Parent Elements</span></span>

|<span data-ttu-id="662a2-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="662a2-114">Element</span></span>|<span data-ttu-id="662a2-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="662a2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="662a2-116">Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="662a2-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="662a2-117">Define a condição de que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="662a2-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="662a2-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="662a2-118">Text Value</span></span>

<span data-ttu-id="662a2-119">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="662a2-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="662a2-120">Observações</span><span class="sxs-lookup"><span data-stu-id="662a2-120">Remarks</span></span>

<span data-ttu-id="662a2-121">A condição de seleção tem de especificar o nome de pelo menos uma propriedade ou um script para avaliar, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="662a2-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="662a2-122">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="662a2-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="662a2-123">Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="662a2-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="662a2-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="662a2-124">See Also</span></span>

[<span data-ttu-id="662a2-125">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="662a2-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="662a2-126">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="662a2-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="662a2-127">Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="662a2-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="662a2-128">Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="662a2-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="662a2-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="662a2-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
