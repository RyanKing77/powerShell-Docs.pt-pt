---
title: Elemento de SelectionSetName para SelectionCondition para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075584"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="a29f8-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format) (Elemento SelectionSetName para SelectionCondition para CustomControl para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="a29f8-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="a29f8-103">Especifica o conjunto de tipos do .NET que acionam a condição.</span><span class="sxs-lookup"><span data-stu-id="a29f8-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="a29f8-104">Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado com esse controle.</span><span class="sxs-lookup"><span data-stu-id="a29f8-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="a29f8-105">Este elemento é utilizado ao definir uma vista de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="a29f8-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="a29f8-106">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para EntrySelectedBy de exibição (formato) Elemento para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="a29f8-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a29f8-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a29f8-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a29f8-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a29f8-108">Attributes and Elements</span></span>

<span data-ttu-id="a29f8-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="a29f8-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a29f8-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="a29f8-110">Attributes</span></span>

<span data-ttu-id="a29f8-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a29f8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a29f8-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="a29f8-112">Child Elements</span></span>

<span data-ttu-id="a29f8-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a29f8-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a29f8-114">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="a29f8-114">Parent Elements</span></span>

|<span data-ttu-id="a29f8-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="a29f8-115">Element</span></span>|<span data-ttu-id="a29f8-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="a29f8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a29f8-117">Elemento de SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="a29f8-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="a29f8-118">Define uma condição que tem de existir durante a definição de controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="a29f8-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a29f8-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="a29f8-119">Text Value</span></span>

<span data-ttu-id="a29f8-120">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="a29f8-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="a29f8-121">Observações</span><span class="sxs-lookup"><span data-stu-id="a29f8-121">Remarks</span></span>

<span data-ttu-id="a29f8-122">Conjuntos de seleção são comuns grupos de objetos .NET que podem ser utilizados por qualquer vista que define o ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="a29f8-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="a29f8-123">Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a29f8-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="a29f8-124">A condição de seleção pode especificar um conjunto de seleção ou o tipo .NET, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="a29f8-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="a29f8-125">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a29f8-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a29f8-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="a29f8-126">See Also</span></span>

[<span data-ttu-id="a29f8-127">Elemento de SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="a29f8-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="a29f8-128">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="a29f8-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a29f8-129">Definir conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="a29f8-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a29f8-130">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a29f8-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
