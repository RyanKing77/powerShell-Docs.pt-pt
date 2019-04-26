---
title: Elemento de SelectionSetName para EntrySelectedBy para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064035"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="fc6d5-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format) (Elemento SelectionSetName para EntrySelectedBy para WideControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="fc6d5-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="fc6d5-103">Especifica um conjunto de objetos .NET para a definição.</span><span class="sxs-lookup"><span data-stu-id="fc6d5-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="fc6d5-104">A definição é utilizada sempre que um desses objetos é apresentado.</span><span class="sxs-lookup"><span data-stu-id="fc6d5-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="fc6d5-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionSetName WideEntry (formato) para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="fc6d5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fc6d5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc6d5-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="fc6d5-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fc6d5-107">Attributes and Elements</span></span>

<span data-ttu-id="fc6d5-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="fc6d5-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fc6d5-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="fc6d5-109">Attributes</span></span>

<span data-ttu-id="fc6d5-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fc6d5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fc6d5-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="fc6d5-111">Child Elements</span></span>

<span data-ttu-id="fc6d5-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fc6d5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fc6d5-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="fc6d5-113">Parent Elements</span></span>

|<span data-ttu-id="fc6d5-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="fc6d5-114">Element</span></span>|<span data-ttu-id="fc6d5-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc6d5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fc6d5-116">Elemento de EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="fc6d5-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="fc6d5-117">Define os tipos do .NET que utilizam esta entrada ampla ou a condição que tem de existir para esta entrada a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="fc6d5-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fc6d5-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="fc6d5-118">Text Value</span></span>

<span data-ttu-id="fc6d5-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="fc6d5-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc6d5-120">Observações</span><span class="sxs-lookup"><span data-stu-id="fc6d5-120">Remarks</span></span>

<span data-ttu-id="fc6d5-121">Cada definição tem de especificar um nome de tipo, o conjunto de seleção ou condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="fc6d5-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="fc6d5-122">Conjuntos de seleção são normalmente utilizados quando quiser definir um grupo de objetos que são utilizados em vários modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="fc6d5-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="fc6d5-123">Por exemplo, pode querer criar uma vista de tabela e uma vista de lista para o mesmo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="fc6d5-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="fc6d5-124">Para obter mais informações sobre como definir conjuntos de seleção, consulte [definir conjuntos de objetos para uma visão](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="fc6d5-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="fc6d5-125">Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="fc6d5-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fc6d5-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="fc6d5-126">See Also</span></span>

[<span data-ttu-id="fc6d5-127">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="fc6d5-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="fc6d5-128">Definir conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="fc6d5-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="fc6d5-129">Elemento de EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="fc6d5-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="fc6d5-130">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc6d5-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
