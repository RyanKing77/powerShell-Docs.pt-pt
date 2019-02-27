---
title: Elemento de PropertyName para SelectionCondition para EntrySelectedBy para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: f857f5944b9e971215a06d6f5c39f7c22c6cf99f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844920"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="f6244-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format) (Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="f6244-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="f6244-103">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="f6244-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="f6244-104">Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e é utilizada a entrada da lista.</span><span class="sxs-lookup"><span data-stu-id="f6244-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="f6244-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento (formato) ListEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition ListEntry (formato) para EntrySelectedBy para o elemento de PropertyName ListEntry (formato) para SelectionCondition para EmtrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f6244-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f6244-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6244-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f6244-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="f6244-107">Attributes and Elements</span></span>

<span data-ttu-id="f6244-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="f6244-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f6244-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f6244-109">Attributes</span></span>

<span data-ttu-id="f6244-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f6244-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f6244-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="f6244-111">Child Elements</span></span>

<span data-ttu-id="f6244-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f6244-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f6244-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="f6244-113">Parent Elements</span></span>

|<span data-ttu-id="f6244-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="f6244-114">Element</span></span>|<span data-ttu-id="f6244-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6244-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6244-116">Elemento de SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f6244-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="f6244-117">Define a condição de que tem de existir para esta entrada da lista a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="f6244-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f6244-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="f6244-118">Text Value</span></span>

<span data-ttu-id="f6244-119">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="f6244-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="f6244-120">Observações</span><span class="sxs-lookup"><span data-stu-id="f6244-120">Remarks</span></span>

<span data-ttu-id="f6244-121">A condição de seleção tem de especificar o nome de pelo menos uma propriedade ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="f6244-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="f6244-122">Para obter mais informações sobre como utilizar condições de seleção, consulte [Defining condições para quando uma entrada de exibição ou Item serve](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f6244-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f6244-123">Para obter mais informações sobre os outros componentes de uma vista de lista, consulte [Criar vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="f6244-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f6244-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="f6244-124">See Also</span></span>

[<span data-ttu-id="f6244-125">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="f6244-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f6244-126">Definir condições para os dados quando é apresentada</span><span class="sxs-lookup"><span data-stu-id="f6244-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f6244-127">Elemento de ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f6244-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="f6244-128">Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f6244-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="f6244-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6244-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
