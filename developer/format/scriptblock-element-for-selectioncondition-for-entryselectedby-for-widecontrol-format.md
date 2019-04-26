---
title: Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064327"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="1f225-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format) (Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para WideControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="1f225-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="1f225-103">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="1f225-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="1f225-104">Quando esse script é avaliado para `true`, a condição é cumprida e é utilizada a definição de entrada ampla.</span><span class="sxs-lookup"><span data-stu-id="1f225-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="1f225-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition WideEntry (formato) para EntrySelectedBy para o elemento de ScriptBlock WideEntry (formato) para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1f225-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f225-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1f225-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f225-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1f225-107">Attributes and Elements</span></span>

<span data-ttu-id="1f225-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="1f225-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f225-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="1f225-109">Attributes</span></span>

<span data-ttu-id="1f225-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1f225-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f225-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="1f225-111">Child Elements</span></span>

<span data-ttu-id="1f225-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1f225-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1f225-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="1f225-113">Parent Elements</span></span>

|<span data-ttu-id="1f225-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="1f225-114">Element</span></span>|<span data-ttu-id="1f225-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="1f225-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f225-116">Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1f225-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="1f225-117">Define a condição de que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="1f225-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1f225-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="1f225-118">Text Value</span></span>

<span data-ttu-id="1f225-119">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="1f225-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f225-120">Observações</span><span class="sxs-lookup"><span data-stu-id="1f225-120">Remarks</span></span>

<span data-ttu-id="1f225-121">A condição de seleção tem de especificar, pelo menos, um nome de script ou de propriedade para avaliar, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="1f225-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="1f225-122">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1f225-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1f225-123">Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="1f225-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f225-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="1f225-124">See Also</span></span>

[<span data-ttu-id="1f225-125">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="1f225-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1f225-126">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="1f225-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1f225-127">Elemento de PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1f225-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="1f225-128">Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1f225-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="1f225-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1f225-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
