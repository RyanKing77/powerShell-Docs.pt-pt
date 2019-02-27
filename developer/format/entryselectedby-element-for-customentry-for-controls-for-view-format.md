---
title: Elemento de EntrySelectedBy para CustomEntry para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849288"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="5ec14-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format) (Elemento EntrySelectedBy para CustomEntry para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="5ec14-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="5ec14-103">Define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="5ec14-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="5ec14-104">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="5ec14-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="5ec14-105">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para controles para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) EntrySelectedBy elemento para CustomEntry para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5ec14-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5ec14-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ec14-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ec14-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="5ec14-107">Attributes and Elements</span></span>

<span data-ttu-id="5ec14-108">As secções seguintes descrevem os atributos e elemento pai de elementos filho do `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="5ec14-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="5ec14-109">Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção de uma definição.</span><span class="sxs-lookup"><span data-stu-id="5ec14-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="5ec14-110">Não existe nenhum limite máximo para o número de elementos filho que pode utilizar.</span><span class="sxs-lookup"><span data-stu-id="5ec14-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ec14-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="5ec14-111">Attributes</span></span>

<span data-ttu-id="5ec14-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5ec14-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ec14-113">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="5ec14-113">Child Elements</span></span>

|<span data-ttu-id="5ec14-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ec14-114">Element</span></span>|<span data-ttu-id="5ec14-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ec14-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ec14-116">Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5ec14-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="5ec14-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5ec14-117">Optional element.</span></span><br /><br /> <span data-ttu-id="5ec14-118">Define a condição de que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="5ec14-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="5ec14-119">Elemento de SelectionSetName para EntrySelectedBy para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5ec14-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="5ec14-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5ec14-120">Optional element.</span></span><br /><br /> <span data-ttu-id="5ec14-121">Especifica um conjunto de tipos do .NET que utilizam esta definição do controle.</span><span class="sxs-lookup"><span data-stu-id="5ec14-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="5ec14-122">Elemento de TypeName para EntrySelectedBy para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5ec14-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="5ec14-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5ec14-123">Optional element.</span></span><br /><br /> <span data-ttu-id="5ec14-124">Especifica um tipo .NET que utiliza esta definição do controle.</span><span class="sxs-lookup"><span data-stu-id="5ec14-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5ec14-125">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="5ec14-125">Parent Elements</span></span>

|<span data-ttu-id="5ec14-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ec14-126">Element</span></span>|<span data-ttu-id="5ec14-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ec14-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ec14-128">Elemento de CustomEntry para CustomEntries para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5ec14-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="5ec14-129">Fornece uma definição do controle.</span><span class="sxs-lookup"><span data-stu-id="5ec14-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5ec14-130">Observações</span><span class="sxs-lookup"><span data-stu-id="5ec14-130">Remarks</span></span>

<span data-ttu-id="5ec14-131">Condições de seleção são utilizadas para definir uma condição que tem de existir para a definição a utilizar, como quando um objeto tem uma propriedade específica ou quando um valor de propriedade específica ou script que é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="5ec14-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="5ec14-132">Para obter mais informações sobre as condições de seleção, consulte [Defining condições para quando uma entrada de exibição ou Item serve](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5ec14-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5ec14-133">Veja Também</span><span class="sxs-lookup"><span data-stu-id="5ec14-133">See Also</span></span>

[<span data-ttu-id="5ec14-134">Elemento de CustomEntry para CustomEntries para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5ec14-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="5ec14-135">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5ec14-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
