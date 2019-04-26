---
title: Elemento de PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064667"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="5adf7-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format) (Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry [Formatação])</span><span class="sxs-lookup"><span data-stu-id="5adf7-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="5adf7-103">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="5adf7-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="5adf7-104">Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e é utilizada a entrada da tabela.</span><span class="sxs-lookup"><span data-stu-id="5adf7-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="5adf7-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento (formato) TableRowEntry elemento (formato) EntrySelectedBy elemento de configuração para TableRowEntry (formato) Elemento de SelectionCondition para EntrySelectedBy para o elemento de PropertyName TableRowEntry (formato) para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="5adf7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5adf7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5adf7-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5adf7-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5adf7-107">Attributes and Elements</span></span>

<span data-ttu-id="5adf7-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="5adf7-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5adf7-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="5adf7-109">Attributes</span></span>

<span data-ttu-id="5adf7-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5adf7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5adf7-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="5adf7-111">Child Elements</span></span>

<span data-ttu-id="5adf7-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5adf7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5adf7-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="5adf7-113">Parent Elements</span></span>

|<span data-ttu-id="5adf7-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="5adf7-114">Element</span></span>|<span data-ttu-id="5adf7-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="5adf7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5adf7-116">Elemento de SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="5adf7-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="5adf7-117">Define a condição de que tem de existir para esta entrada de tabela a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="5adf7-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5adf7-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="5adf7-118">Text Value</span></span>

<span data-ttu-id="5adf7-119">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="5adf7-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="5adf7-120">Observações</span><span class="sxs-lookup"><span data-stu-id="5adf7-120">Remarks</span></span>

<span data-ttu-id="5adf7-121">A condição de seleção tem de especificar o nome de pelo menos uma propriedade ou um bloco de script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="5adf7-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="5adf7-122">Para obter mais informações sobre como as condições de seleção podem ser utilizadas, consulte [Defining condições para quando uma entrada de exibição ou Item serve](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5adf7-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="5adf7-123">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="5adf7-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5adf7-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="5adf7-124">See Also</span></span>

[<span data-ttu-id="5adf7-125">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="5adf7-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="5adf7-126">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="5adf7-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="5adf7-127">Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="5adf7-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="5adf7-128">Elemento de SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="5adf7-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="5adf7-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5adf7-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
