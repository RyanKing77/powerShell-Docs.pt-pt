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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846194"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="b93b2-102">SelectionSetName Element for SelectionCondition for Controls for View (Format) (Elemento SelectionSetName para SelectionCondition para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="b93b2-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="b93b2-103">Especifica o conjunto de tipos do .NET que acionam a condição.</span><span class="sxs-lookup"><span data-stu-id="b93b2-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="b93b2-104">Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado com esse controle.</span><span class="sxs-lookup"><span data-stu-id="b93b2-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="b93b2-105">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="b93b2-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b93b2-106">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para controles para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) EntrySelectedBy elemento para CustomEntry para controles para exibição (formato) SelectionCondition elemento para EntrySelectedBy para controles para exibição ( Elemento de SelectionSetName de formato) para SelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="b93b2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b93b2-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b93b2-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b93b2-108">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="b93b2-108">Attributes and Elements</span></span>

<span data-ttu-id="b93b2-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="b93b2-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b93b2-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b93b2-110">Attributes</span></span>

<span data-ttu-id="b93b2-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b93b2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b93b2-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="b93b2-112">Child Elements</span></span>

<span data-ttu-id="b93b2-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b93b2-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b93b2-114">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="b93b2-114">Parent Elements</span></span>

|<span data-ttu-id="b93b2-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="b93b2-115">Element</span></span>|<span data-ttu-id="b93b2-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="b93b2-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b93b2-117">Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="b93b2-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="b93b2-118">Define uma condição que tem de existir durante a definição de controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="b93b2-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b93b2-119">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="b93b2-119">Text Value</span></span>

<span data-ttu-id="b93b2-120">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="b93b2-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b93b2-121">Observações</span><span class="sxs-lookup"><span data-stu-id="b93b2-121">Remarks</span></span>

<span data-ttu-id="b93b2-122">Conjuntos de seleção são comuns grupos de objetos .NET que podem ser utilizados por qualquer vista que define o ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="b93b2-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="b93b2-123">Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b93b2-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b93b2-124">A condição de seleção pode especificar um conjunto de seleção ou o tipo .NET, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="b93b2-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="b93b2-125">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b93b2-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b93b2-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="b93b2-126">See Also</span></span>

[<span data-ttu-id="b93b2-127">Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="b93b2-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="b93b2-128">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="b93b2-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b93b2-129">Definir conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="b93b2-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="b93b2-130">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b93b2-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
