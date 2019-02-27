---
title: Elemento de SelectionSetName para EntrySelectedBy para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846880"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="0f4cf-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format) (Elemento SelectionSetName para EntrySelectedBy para TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="0f4cf-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="0f4cf-103">Especifica que a utilização de tipos de um conjunto de .NET, esta entrada da vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="0f4cf-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="0f4cf-104">Não existe nenhum limite para o número de conjuntos de seleção que podem ser especificados para uma entrada.</span><span class="sxs-lookup"><span data-stu-id="0f4cf-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="0f4cf-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento (formato) TableRowEntry elemento (formato) EntrySelectedBy elemento (formato) SelectionSetName elemento de configuração para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="0f4cf-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0f4cf-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f4cf-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0f4cf-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="0f4cf-107">Attributes and Elements</span></span>

<span data-ttu-id="0f4cf-108">As secções seguintes descrevem os atributos e elementos principais elementos filho.</span><span class="sxs-lookup"><span data-stu-id="0f4cf-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0f4cf-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="0f4cf-109">Attributes</span></span>

<span data-ttu-id="0f4cf-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0f4cf-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0f4cf-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="0f4cf-111">Child Elements</span></span>

<span data-ttu-id="0f4cf-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0f4cf-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0f4cf-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="0f4cf-113">Parent Elements</span></span>

|<span data-ttu-id="0f4cf-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="0f4cf-114">Element</span></span>|<span data-ttu-id="0f4cf-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f4cf-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0f4cf-116">Elemento de EntrySelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="0f4cf-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="0f4cf-117">Define os tipos do .NET que utilizam esta entrada ou a condição que tem de existir para esta entrada a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="0f4cf-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0f4cf-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="0f4cf-118">Text Value</span></span>

<span data-ttu-id="0f4cf-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="0f4cf-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f4cf-120">Observações</span><span class="sxs-lookup"><span data-stu-id="0f4cf-120">Remarks</span></span>

<span data-ttu-id="0f4cf-121">Conjuntos de seleção são normalmente utilizados quando quiser definir um grupo de objetos que são utilizados em vários modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="0f4cf-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="0f4cf-122">Por exemplo, pode querer criar uma vista de tabela e uma vista de lista para o mesmo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="0f4cf-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="0f4cf-123">Para obter mais informações sobre como definir conjuntos de seleção, consulte [definir conjuntos de objetos para uma visão](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="0f4cf-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="0f4cf-124">Se especificar uma seleção definido para uma entrada, não é possível especificar um nome de tipo.</span><span class="sxs-lookup"><span data-stu-id="0f4cf-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="0f4cf-125">Para obter mais informações sobre como especificar um tipo .NET, consulte [elemento TypeName para EntrySelectedBy para TableRowEntry (formato)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="0f4cf-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="0f4cf-126">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="0f4cf-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f4cf-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="0f4cf-127">See Also</span></span>

[<span data-ttu-id="0f4cf-128">Elemento de EntrySelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="0f4cf-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="0f4cf-129">Definir conjuntos de objetos para uma visão</span><span class="sxs-lookup"><span data-stu-id="0f4cf-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="0f4cf-130">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="0f4cf-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0f4cf-131">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f4cf-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
