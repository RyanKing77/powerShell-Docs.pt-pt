---
title: Elemento de SelectionSetName para SelectionCondition para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063892"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="c755a-102">SelectionSetName Element for SelectionCondition for Controls for View (Format) (Elemento SelectionSetName para SelectionCondition para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="c755a-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="c755a-103">Especifica o conjunto de tipos do .NET que acionam a condição.</span><span class="sxs-lookup"><span data-stu-id="c755a-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="c755a-104">Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado com esse controle.</span><span class="sxs-lookup"><span data-stu-id="c755a-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="c755a-105">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="c755a-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c755a-106">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para controles para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) EntrySelectedBy elemento para CustomEntry para controles para exibição (formato) SelectionCondition elemento para EntrySelectedBy para controles para exibição ( Elemento de SelectionSetName de formato) para SelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="c755a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c755a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c755a-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c755a-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c755a-108">Attributes and Elements</span></span>

<span data-ttu-id="c755a-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="c755a-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c755a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c755a-110">Attributes</span></span>

<span data-ttu-id="c755a-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c755a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c755a-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="c755a-112">Child Elements</span></span>

<span data-ttu-id="c755a-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c755a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c755a-114">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="c755a-114">Parent Elements</span></span>

|<span data-ttu-id="c755a-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="c755a-115">Element</span></span>|<span data-ttu-id="c755a-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="c755a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c755a-117">Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="c755a-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="c755a-118">Define uma condição que tem de existir durante a definição de controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="c755a-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c755a-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="c755a-119">Text Value</span></span>

<span data-ttu-id="c755a-120">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="c755a-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c755a-121">Observações</span><span class="sxs-lookup"><span data-stu-id="c755a-121">Remarks</span></span>

<span data-ttu-id="c755a-122">Conjuntos de seleção são comuns grupos de objetos .NET que podem ser utilizados por qualquer vista que define o ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="c755a-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="c755a-123">Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c755a-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="c755a-124">A condição de seleção pode especificar um conjunto de seleção ou o tipo .NET, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="c755a-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="c755a-125">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c755a-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c755a-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="c755a-126">See Also</span></span>

[<span data-ttu-id="c755a-127">Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="c755a-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="c755a-128">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="c755a-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c755a-129">Definir conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="c755a-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c755a-130">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c755a-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
