---
title: Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064055"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="764c3-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format) (Elemento SelectionSetName para SelectionCondition para EntrySelectedBy para TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="764c3-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="764c3-103">Especifica o conjunto de tipos do .NET que acionam a condição.</span><span class="sxs-lookup"><span data-stu-id="764c3-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="764c3-104">Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado ao utilizar esta definição de vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="764c3-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="764c3-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento (formato) TableRowEntry elemento (formato) EntrySelectedBy elemento de configuração para TableRowEntry (formato) Elemento de SelectionCondition para EntrySelectedBy para o elemento de SelectionSetName TableRowEntry (formato) para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="764c3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="764c3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="764c3-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="764c3-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="764c3-107">Attributes and Elements</span></span>

<span data-ttu-id="764c3-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="764c3-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="764c3-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="764c3-109">Attributes</span></span>

<span data-ttu-id="764c3-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="764c3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="764c3-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="764c3-111">Child Elements</span></span>

<span data-ttu-id="764c3-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="764c3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="764c3-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="764c3-113">Parent Elements</span></span>

|<span data-ttu-id="764c3-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="764c3-114">Element</span></span>|<span data-ttu-id="764c3-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="764c3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="764c3-116">Elemento de SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="764c3-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="764c3-117">Define a condição de que tem de existir para utilizar para esta definição de vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="764c3-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="764c3-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="764c3-118">Text Value</span></span>

<span data-ttu-id="764c3-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="764c3-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="764c3-120">Observações</span><span class="sxs-lookup"><span data-stu-id="764c3-120">Remarks</span></span>

<span data-ttu-id="764c3-121">A condição de seleção pode especificar um conjunto de seleção ou o tipo .NET, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="764c3-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="764c3-122">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="764c3-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="764c3-123">Conjuntos de seleção são comuns grupos de objetos .NET que podem ser utilizados por qualquer vista que define o ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="764c3-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="764c3-124">Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="764c3-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="764c3-125">Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="764c3-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="764c3-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="764c3-126">See Also</span></span>

[<span data-ttu-id="764c3-127">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="764c3-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="764c3-128">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="764c3-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="764c3-129">Elemento de TypeName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="764c3-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="764c3-130">Elemento de SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="764c3-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="764c3-131">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="764c3-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
