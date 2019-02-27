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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850310"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="9d889-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format) (Elemento SelectionSetName para EntrySelectedBy para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="9d889-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="9d889-103">Especifica um conjunto de tipos do .NET que utilizam esta definição do controle.</span><span class="sxs-lookup"><span data-stu-id="9d889-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="9d889-104">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="9d889-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="9d889-105">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para controles para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) EntrySelectedBy elemento para CustomEntry para controles para exibição (formato) SelectionSetName elemento para EntrySelectedBy para controles para exibição ( Formato)</span><span class="sxs-lookup"><span data-stu-id="9d889-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9d889-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d889-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9d889-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="9d889-107">Attributes and Elements</span></span>

<span data-ttu-id="9d889-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="9d889-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9d889-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="9d889-109">Attributes</span></span>

<span data-ttu-id="9d889-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9d889-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="9d889-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="9d889-111">Child Elements</span></span>

<span data-ttu-id="9d889-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9d889-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9d889-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="9d889-113">Parent Elements</span></span>

|<span data-ttu-id="9d889-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="9d889-114">Element</span></span>|<span data-ttu-id="9d889-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d889-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d889-116">Elemento de EntrySelectedBy para CustomEntry para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="9d889-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="9d889-117">Define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="9d889-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9d889-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="9d889-118">Text Value</span></span>

<span data-ttu-id="9d889-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="9d889-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d889-120">Observações</span><span class="sxs-lookup"><span data-stu-id="9d889-120">Remarks</span></span>

<span data-ttu-id="9d889-121">Cada definição de controlo tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.</span><span class="sxs-lookup"><span data-stu-id="9d889-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="9d889-122">Conjuntos de seleção são normalmente utilizados quando quiser definir um grupo de objetos que são utilizados em vários modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="9d889-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="9d889-123">Para obter mais informações sobre como definir conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="9d889-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d889-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="9d889-124">See Also</span></span>

[<span data-ttu-id="9d889-125">Elemento de EntrySelectedBy para CustomEntry para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="9d889-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="9d889-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d889-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
