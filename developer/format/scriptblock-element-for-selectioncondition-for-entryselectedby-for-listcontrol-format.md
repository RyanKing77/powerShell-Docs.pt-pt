---
title: Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: fd708473d04a76bcf6cf3a8f8278e1d15fb9addf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848672"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="c3e10-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format) (Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="c3e10-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="c3e10-103">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="c3e10-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="c3e10-104">Quando esse script é avaliado para `true`, a condição é cumprida e é utilizada a entrada da lista.</span><span class="sxs-lookup"><span data-stu-id="c3e10-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="c3e10-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento (formato) ListEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition ListEntry (formato) para EntrySelectedBy para o elemento de ScriptBlock ListEntry (formato) para SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="c3e10-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c3e10-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3e10-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c3e10-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="c3e10-107">Attributes and Elements</span></span>

<span data-ttu-id="c3e10-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="c3e10-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c3e10-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="c3e10-109">Attributes</span></span>

<span data-ttu-id="c3e10-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c3e10-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c3e10-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="c3e10-111">Child Elements</span></span>

<span data-ttu-id="c3e10-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c3e10-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c3e10-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="c3e10-113">Parent Elements</span></span>

|<span data-ttu-id="c3e10-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="c3e10-114">Element</span></span>|<span data-ttu-id="c3e10-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3e10-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c3e10-116">Elemento de SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="c3e10-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="c3e10-117">Define a condição de que tem de existir para esta entrada da lista a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="c3e10-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c3e10-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="c3e10-118">Text Value</span></span>

<span data-ttu-id="c3e10-119">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="c3e10-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3e10-120">Observações</span><span class="sxs-lookup"><span data-stu-id="c3e10-120">Remarks</span></span>

<span data-ttu-id="c3e10-121">A condição de seleção tem de especificar um, pelo menos, um script ou a propriedade nome para avaliar, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="c3e10-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="c3e10-122">(Para obter mais informações sobre como as condições de seleção podem ser utilizadas, consulte [Defining condições para quando uma entrada de exibição ou Item serve](./defining-conditions-for-displaying-data.md).)</span><span class="sxs-lookup"><span data-stu-id="c3e10-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="c3e10-123">Para obter mais informações sobre os outros componentes de uma vista de lista, consulte [vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="c3e10-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c3e10-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="c3e10-124">See Also</span></span>

[<span data-ttu-id="c3e10-125">Elemento de ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="c3e10-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="c3e10-126">Elemento de PropertyName para SelectionCondition para EmtrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="c3e10-126">PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="c3e10-127">Elemento de SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="c3e10-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="c3e10-128">Vista de lista</span><span class="sxs-lookup"><span data-stu-id="c3e10-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c3e10-129">Definir condições para quando é utilizada uma entrada de exibição ou Item</span><span class="sxs-lookup"><span data-stu-id="c3e10-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c3e10-130">Escrever do Windows PowerShell, formatação e os tipos de ficheiro</span><span class="sxs-lookup"><span data-stu-id="c3e10-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
