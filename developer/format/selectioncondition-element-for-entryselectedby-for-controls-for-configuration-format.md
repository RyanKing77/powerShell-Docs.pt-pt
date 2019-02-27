---
title: Elemento de SelectionCondition para EntrySelectedBy para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845515"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="67298-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) (Elemento SelectionCondition para EntrySelectedBy para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="67298-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="67298-103">Define uma condição que tem de existir uma definição de controle comum a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="67298-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="67298-104">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="67298-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="67298-105">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para controles para Elemento de CustomEntry de configuração (formato) para CustomControl para controles para o elemento de EntrySelectedBy de configuração (formato) para CustomEntry para controles para o elemento de SelectionCondition de configuração (formato) para EntrySelectedBy para CustomEntry para Configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="67298-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67298-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67298-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="67298-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="67298-107">Attributes and Elements</span></span>

<span data-ttu-id="67298-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="67298-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="67298-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="67298-109">Attributes</span></span>

<span data-ttu-id="67298-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="67298-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="67298-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="67298-111">Child Elements</span></span>

|<span data-ttu-id="67298-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="67298-112">Element</span></span>|<span data-ttu-id="67298-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="67298-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67298-114">Elemento de PropertyName para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="67298-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="67298-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="67298-115">Optional element.</span></span><br /><br /> <span data-ttu-id="67298-116">Especifica uma propriedade de .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="67298-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="67298-117">Elemento de ScriptBlock para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="67298-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="67298-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="67298-118">Optional element.</span></span><br /><br /> <span data-ttu-id="67298-119">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="67298-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="67298-120">Elemento de SelectionSetName para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="67298-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="67298-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="67298-121">Optional element.</span></span><br /><br /> <span data-ttu-id="67298-122">Especifica o conjunto de tipos do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="67298-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="67298-123">Elemento de TypeName para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="67298-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="67298-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="67298-124">Optional element.</span></span><br /><br /> <span data-ttu-id="67298-125">Especifica um tipo .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="67298-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="67298-126">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="67298-126">Parent Elements</span></span>

|<span data-ttu-id="67298-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="67298-127">Element</span></span>|<span data-ttu-id="67298-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="67298-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67298-129">Elemento de EntrySelectedBy para CustomEntry para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="67298-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="67298-130">Define os tipos do .NET que utilizam esta entrada da definição de controlo comuns.</span><span class="sxs-lookup"><span data-stu-id="67298-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="67298-131">Observações</span><span class="sxs-lookup"><span data-stu-id="67298-131">Remarks</span></span>

<span data-ttu-id="67298-132">Devem ser seguidas as seguintes diretrizes ao definir uma condição de seleção:</span><span class="sxs-lookup"><span data-stu-id="67298-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="67298-133">A condição de seleção tem de especificar um nome de uma propriedade, pelo menos, ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="67298-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="67298-134">A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="67298-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="67298-135">Para obter mais informações sobre como as condições de seleção podem ser utilizadas, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="67298-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="67298-136">Veja Também</span><span class="sxs-lookup"><span data-stu-id="67298-136">See Also</span></span>

[<span data-ttu-id="67298-137">Elemento de PropertyName para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="67298-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="67298-138">Elemento de ScriptBlock para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="67298-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="67298-139">Elemento de SelectionSetName para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="67298-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="67298-140">Elemento de TypeName para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="67298-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="67298-141">Elemento de EntrySelectedBy para CustomEntry para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="67298-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="67298-142">Escrever do Windows PowerShell, formatação e os tipos de ficheiro</span><span class="sxs-lookup"><span data-stu-id="67298-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
