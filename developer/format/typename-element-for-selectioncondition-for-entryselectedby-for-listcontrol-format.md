---
title: Elemento de TypeName para SelectionCondition para EntrySelectedBy para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851556"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="30c04-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format) (Elemento TypeName para SelectionCondition para EntrySelectedBy para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="30c04-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="30c04-103">Especifica um tipo .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="30c04-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="30c04-104">Quando este tipo está presente, é utilizada a entrada da lista.</span><span class="sxs-lookup"><span data-stu-id="30c04-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="30c04-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry ListControl (formato) para ListEntries para o elemento de EntrySelectedBy ListControl (formato) para ListEntry para o elemento de SelectionCondition ListControl (formato) para EntrySelectedBy para o elemento de TypeName ListControl (formato) para SelectionCondition para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="30c04-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="30c04-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30c04-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="30c04-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="30c04-107">Attributes and Elements</span></span>

<span data-ttu-id="30c04-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="30c04-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="30c04-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="30c04-109">Attributes</span></span>

<span data-ttu-id="30c04-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="30c04-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="30c04-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="30c04-111">Child Elements</span></span>

<span data-ttu-id="30c04-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="30c04-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="30c04-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="30c04-113">Parent Elements</span></span>

|<span data-ttu-id="30c04-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="30c04-114">Element</span></span>|<span data-ttu-id="30c04-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="30c04-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="30c04-116">Elemento de SelectionCondition para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="30c04-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="30c04-117">Define a condição de que tem de existir para esta entrada da lista a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="30c04-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="30c04-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="30c04-118">Text Value</span></span>

<span data-ttu-id="30c04-119">Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="30c04-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="30c04-120">Observações</span><span class="sxs-lookup"><span data-stu-id="30c04-120">Remarks</span></span>

<span data-ttu-id="30c04-121">A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="30c04-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="30c04-122">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="30c04-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="30c04-123">Para obter mais informações sobre outras os componentes de uma vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="30c04-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="30c04-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="30c04-124">See Also</span></span>

[<span data-ttu-id="30c04-125">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="30c04-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="30c04-126">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="30c04-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="30c04-127">Elemento de SelectionCondition para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="30c04-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="30c04-128">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="30c04-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
