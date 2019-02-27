---
title: Elemento de SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848413"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="1defb-102">Elemento SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format) (Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion [Formatação])</span><span class="sxs-lookup"><span data-stu-id="1defb-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="1defb-103">Define a condição de que tem de existir para expandir os objetos da coleção desta definição.</span><span class="sxs-lookup"><span data-stu-id="1defb-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="1defb-104">O elemento (formato) DefaultSettings elemento (formato) EnumerableExpansions elemento (formato) EnumerableExpansion elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition EnumerableExpansion (formato) para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="1defb-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1defb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1defb-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1defb-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="1defb-106">Attributes and Elements</span></span>

<span data-ttu-id="1defb-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="1defb-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="1defb-108">Tem de especificar um único `PropertyName` ou `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="1defb-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="1defb-109">O `SelectionSetName` e `TypeName` elementos são opcionais.</span><span class="sxs-lookup"><span data-stu-id="1defb-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="1defb-110">Pode especificar um de qualquer elemento.</span><span class="sxs-lookup"><span data-stu-id="1defb-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1defb-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="1defb-111">Attributes</span></span>

<span data-ttu-id="1defb-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1defb-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1defb-113">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="1defb-113">Child Elements</span></span>

|<span data-ttu-id="1defb-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="1defb-114">Element</span></span>|<span data-ttu-id="1defb-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="1defb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1defb-116">Elemento de PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="1defb-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="1defb-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1defb-117">Optional element.</span></span><br /><br /> <span data-ttu-id="1defb-118">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="1defb-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="1defb-119">Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="1defb-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="1defb-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1defb-120">Optional element.</span></span><br /><br /> <span data-ttu-id="1defb-121">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="1defb-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="1defb-122">Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="1defb-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="1defb-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1defb-123">Optional element.</span></span><br /><br /> <span data-ttu-id="1defb-124">Especifica o conjunto de tipos do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="1defb-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="1defb-125">Elemento de TypeName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="1defb-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="1defb-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="1defb-126">Optional element.</span></span><br /><br /> <span data-ttu-id="1defb-127">Especifica um tipo .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="1defb-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1defb-128">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="1defb-128">Parent Elements</span></span>

|<span data-ttu-id="1defb-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="1defb-129">Element</span></span>|<span data-ttu-id="1defb-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="1defb-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1defb-131">Elemento de EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="1defb-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="1defb-132">Define os objetos da coleção de .NET são expandidos por esta definição.</span><span class="sxs-lookup"><span data-stu-id="1defb-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1defb-133">Observações</span><span class="sxs-lookup"><span data-stu-id="1defb-133">Remarks</span></span>

<span data-ttu-id="1defb-134">Cada definição tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.</span><span class="sxs-lookup"><span data-stu-id="1defb-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="1defb-135">Quando está a definir uma condição de seleção, aplicam-se os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="1defb-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="1defb-136">A condição de seleção tem de especificar um nome de uma propriedade, pelo menos, ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="1defb-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="1defb-137">A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="1defb-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="1defb-138">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para os dados de Diplaying](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1defb-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1defb-139">Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="1defb-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1defb-140">Veja Também</span><span class="sxs-lookup"><span data-stu-id="1defb-140">See Also</span></span>

[<span data-ttu-id="1defb-141">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="1defb-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1defb-142">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1defb-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
