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
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056012"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="857a8-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format) (Elemento TypeName para SelectionCondition para EntrySelectedBy para WideControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="857a8-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="857a8-103">Especifica um tipo .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="857a8-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="857a8-104">Quando este tipo está presente, a definição é utilizada.</span><span class="sxs-lookup"><span data-stu-id="857a8-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="857a8-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition WideEntry (formato) para EntrySelectedBy para o elemento de TypeName WideEntry (formato) para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="857a8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="857a8-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="857a8-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="857a8-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="857a8-107">Attributes and Elements</span></span>

<span data-ttu-id="857a8-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="857a8-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="857a8-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="857a8-109">Attributes</span></span>

<span data-ttu-id="857a8-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="857a8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="857a8-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="857a8-111">Child Elements</span></span>

<span data-ttu-id="857a8-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="857a8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="857a8-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="857a8-113">Parent Elements</span></span>

|<span data-ttu-id="857a8-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="857a8-114">Element</span></span>|<span data-ttu-id="857a8-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="857a8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="857a8-116">Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="857a8-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="857a8-117">Define a condição de que tem de existir para esta entrada grande ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="857a8-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="857a8-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="857a8-118">Text Value</span></span>

<span data-ttu-id="857a8-119">Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="857a8-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="857a8-120">Observações</span><span class="sxs-lookup"><span data-stu-id="857a8-120">Remarks</span></span>

<span data-ttu-id="857a8-121">A condição de seleção, pode especificar um tipo .NET ou uma seleção definido, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="857a8-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="857a8-122">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="857a8-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="857a8-123">Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="857a8-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="857a8-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="857a8-124">See Also</span></span>

[<span data-ttu-id="857a8-125">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="857a8-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="857a8-126">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="857a8-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="857a8-127">Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="857a8-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="857a8-128">Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="857a8-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="857a8-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="857a8-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
