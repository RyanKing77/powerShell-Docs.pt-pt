---
title: Elemento de SelectionSetName para EntrySelectedBy para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075652"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="af623-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format) (Elemento SelectionSetName para EntrySelectedBy para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="af623-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="af623-103">Especifica um conjunto de tipos do .NET que utilizam esta definição do controle.</span><span class="sxs-lookup"><span data-stu-id="af623-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="af623-104">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="af623-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="af623-105">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para controles para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) EntrySelectedBy elemento para CustomEntry para controles para exibição (formato) SelectionSetName elemento para EntrySelectedBy para controles para exibição ( Formato)</span><span class="sxs-lookup"><span data-stu-id="af623-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="af623-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af623-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="af623-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="af623-107">Attributes and Elements</span></span>

<span data-ttu-id="af623-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="af623-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="af623-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="af623-109">Attributes</span></span>

<span data-ttu-id="af623-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="af623-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="af623-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="af623-111">Child Elements</span></span>

<span data-ttu-id="af623-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="af623-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="af623-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="af623-113">Parent Elements</span></span>

|<span data-ttu-id="af623-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="af623-114">Element</span></span>|<span data-ttu-id="af623-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="af623-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="af623-116">Elemento de EntrySelectedBy para CustomEntry para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="af623-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="af623-117">Define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="af623-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="af623-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="af623-118">Text Value</span></span>

<span data-ttu-id="af623-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="af623-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="af623-120">Observações</span><span class="sxs-lookup"><span data-stu-id="af623-120">Remarks</span></span>

<span data-ttu-id="af623-121">Cada definição de controlo tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.</span><span class="sxs-lookup"><span data-stu-id="af623-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="af623-122">Conjuntos de seleção são normalmente utilizados quando quiser definir um grupo de objetos que são utilizados em vários modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="af623-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="af623-123">Para obter mais informações sobre como definir conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="af623-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="af623-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="af623-124">See Also</span></span>

[<span data-ttu-id="af623-125">Elemento de EntrySelectedBy para CustomEntry para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="af623-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="af623-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="af623-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
