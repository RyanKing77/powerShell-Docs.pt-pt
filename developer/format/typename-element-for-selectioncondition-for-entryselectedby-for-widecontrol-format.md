---
title: Elemento de TypeName para SelectionCondition para EntrySelectedBy para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 0d7bbfd8be3bf2bd1af75a45ca4db016dfb6bff6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848182"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="af3f4-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format) (Elemento TypeName para SelectionCondition para EntrySelectedBy para WideControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="af3f4-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="af3f4-103">Especifica um tipo .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="af3f4-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="af3f4-104">Quando este tipo está presente, a definição é utilizada.</span><span class="sxs-lookup"><span data-stu-id="af3f4-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="af3f4-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition WideEntry (formato) para EntrySelectedBy para o elemento de TypeName WideEntry (formato) para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="af3f4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="af3f4-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af3f4-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="af3f4-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="af3f4-107">Attributes and Elements</span></span>

<span data-ttu-id="af3f4-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="af3f4-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="af3f4-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="af3f4-109">Attributes</span></span>

<span data-ttu-id="af3f4-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="af3f4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="af3f4-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="af3f4-111">Child Elements</span></span>

<span data-ttu-id="af3f4-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="af3f4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="af3f4-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="af3f4-113">Parent Elements</span></span>

|<span data-ttu-id="af3f4-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="af3f4-114">Element</span></span>|<span data-ttu-id="af3f4-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="af3f4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="af3f4-116">Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="af3f4-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="af3f4-117">Define a condição de que tem de existir para esta entrada grande ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="af3f4-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="af3f4-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="af3f4-118">Text Value</span></span>

<span data-ttu-id="af3f4-119">Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="af3f4-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="af3f4-120">Observações</span><span class="sxs-lookup"><span data-stu-id="af3f4-120">Remarks</span></span>

<span data-ttu-id="af3f4-121">A condição de seleção, pode especificar um tipo .NET ou uma seleção definido, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="af3f4-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="af3f4-122">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="af3f4-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="af3f4-123">Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="af3f4-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="af3f4-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="af3f4-124">See Also</span></span>

[<span data-ttu-id="af3f4-125">É criada uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="af3f4-125">Creatng a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="af3f4-126">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="af3f4-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="af3f4-127">Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="af3f4-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="af3f4-128">Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="af3f4-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="af3f4-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="af3f4-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
