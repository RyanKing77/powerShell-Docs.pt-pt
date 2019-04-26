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
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064896"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="f5741-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format) (Elemento PropertyName para SelectionCondition para EntrySelectedBy para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="f5741-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="f5741-103">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="f5741-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="f5741-104">Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e é utilizada a entrada da lista.</span><span class="sxs-lookup"><span data-stu-id="f5741-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="f5741-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento (formato) ListEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition ListEntry (formato) para EntrySelectedBy para o elemento de PropertyName ListEntry (formato) para SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f5741-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f5741-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5741-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f5741-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f5741-107">Attributes and Elements</span></span>

<span data-ttu-id="f5741-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="f5741-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5741-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f5741-109">Attributes</span></span>

<span data-ttu-id="f5741-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f5741-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f5741-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="f5741-111">Child Elements</span></span>

<span data-ttu-id="f5741-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f5741-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f5741-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="f5741-113">Parent Elements</span></span>

|<span data-ttu-id="f5741-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="f5741-114">Element</span></span>|<span data-ttu-id="f5741-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5741-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5741-116">Elemento de SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f5741-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="f5741-117">Define a condição de que tem de existir para esta entrada da lista a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="f5741-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f5741-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="f5741-118">Text Value</span></span>

<span data-ttu-id="f5741-119">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="f5741-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5741-120">Observações</span><span class="sxs-lookup"><span data-stu-id="f5741-120">Remarks</span></span>

<span data-ttu-id="f5741-121">A condição de seleção tem de especificar o nome de pelo menos uma propriedade ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="f5741-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="f5741-122">Para obter mais informações sobre como utilizar condições de seleção, consulte [Defining condições para quando uma entrada de exibição ou Item serve](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f5741-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f5741-123">Para obter mais informações sobre os outros componentes de uma vista de lista, consulte [Criar vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="f5741-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5741-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="f5741-124">See Also</span></span>

[<span data-ttu-id="f5741-125">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="f5741-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f5741-126">Definir condições para os dados quando é apresentada</span><span class="sxs-lookup"><span data-stu-id="f5741-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f5741-127">Elemento de ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f5741-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="f5741-128">Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f5741-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="f5741-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f5741-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
