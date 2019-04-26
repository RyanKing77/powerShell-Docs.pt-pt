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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064140"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="89686-102">Elemento SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format) (Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion [Formatação])</span><span class="sxs-lookup"><span data-stu-id="89686-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="89686-103">Define a condição de que tem de existir para expandir os objetos da coleção desta definição.</span><span class="sxs-lookup"><span data-stu-id="89686-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="89686-104">O elemento (formato) DefaultSettings elemento (formato) EnumerableExpansions elemento (formato) EnumerableExpansion elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition EnumerableExpansion (formato) para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="89686-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="89686-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89686-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="89686-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="89686-106">Attributes and Elements</span></span>

<span data-ttu-id="89686-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="89686-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="89686-108">Tem de especificar um único `PropertyName` ou `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="89686-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="89686-109">O `SelectionSetName` e `TypeName` elementos são opcionais.</span><span class="sxs-lookup"><span data-stu-id="89686-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="89686-110">Pode especificar um de qualquer elemento.</span><span class="sxs-lookup"><span data-stu-id="89686-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="89686-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="89686-111">Attributes</span></span>

<span data-ttu-id="89686-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="89686-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="89686-113">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="89686-113">Child Elements</span></span>

|<span data-ttu-id="89686-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="89686-114">Element</span></span>|<span data-ttu-id="89686-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="89686-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89686-116">Elemento de PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="89686-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="89686-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="89686-117">Optional element.</span></span><br /><br /> <span data-ttu-id="89686-118">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="89686-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="89686-119">Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="89686-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="89686-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="89686-120">Optional element.</span></span><br /><br /> <span data-ttu-id="89686-121">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="89686-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="89686-122">Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="89686-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="89686-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="89686-123">Optional element.</span></span><br /><br /> <span data-ttu-id="89686-124">Especifica o conjunto de tipos do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="89686-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="89686-125">Elemento de TypeName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="89686-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="89686-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="89686-126">Optional element.</span></span><br /><br /> <span data-ttu-id="89686-127">Especifica um tipo .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="89686-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="89686-128">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="89686-128">Parent Elements</span></span>

|<span data-ttu-id="89686-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="89686-129">Element</span></span>|<span data-ttu-id="89686-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="89686-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89686-131">Elemento de EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="89686-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="89686-132">Define os objetos da coleção de .NET são expandidos por esta definição.</span><span class="sxs-lookup"><span data-stu-id="89686-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="89686-133">Observações</span><span class="sxs-lookup"><span data-stu-id="89686-133">Remarks</span></span>

<span data-ttu-id="89686-134">Cada definição tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.</span><span class="sxs-lookup"><span data-stu-id="89686-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="89686-135">Quando está a definir uma condição de seleção, aplicam-se os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="89686-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="89686-136">A condição de seleção tem de especificar um nome de uma propriedade, pelo menos, ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="89686-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="89686-137">A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="89686-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="89686-138">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para os dados de Diplaying](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="89686-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="89686-139">Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="89686-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="89686-140">Veja Também</span><span class="sxs-lookup"><span data-stu-id="89686-140">See Also</span></span>

[<span data-ttu-id="89686-141">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="89686-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="89686-142">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="89686-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
