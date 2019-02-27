---
title: Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846516"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="a1b48-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format) (Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="a1b48-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="a1b48-103">Especifica o bloco de script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="a1b48-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="a1b48-104">Quando esse script é avaliado para `true`, a condição é cumprida e é utilizada a entrada da tabela.</span><span class="sxs-lookup"><span data-stu-id="a1b48-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="a1b48-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento (formato) TableRowEntry elemento (formato) EntrySelectedBy elemento de configuração para TableRowEntry (formato) Elemento de SelectionCondition para EntrySelectedBy para o elemento de ScriptBlock TableRowEntry (formato) para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="a1b48-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a1b48-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1b48-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a1b48-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="a1b48-107">Attributes and Elements</span></span>

<span data-ttu-id="a1b48-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="a1b48-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a1b48-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="a1b48-109">Attributes</span></span>

<span data-ttu-id="a1b48-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a1b48-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a1b48-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="a1b48-111">Child Elements</span></span>

<span data-ttu-id="a1b48-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a1b48-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a1b48-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="a1b48-113">Parent Elements</span></span>

|<span data-ttu-id="a1b48-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1b48-114">Element</span></span>|<span data-ttu-id="a1b48-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1b48-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1b48-116">Elemento de SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="a1b48-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a1b48-117">Define a condição de que tem de existir para esta entrada de tabela a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="a1b48-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a1b48-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="a1b48-118">Text Value</span></span>

<span data-ttu-id="a1b48-119">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="a1b48-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="a1b48-120">Observações</span><span class="sxs-lookup"><span data-stu-id="a1b48-120">Remarks</span></span>

<span data-ttu-id="a1b48-121">A condição de seleção tem de especificar pelo menos um bloco ou a propriedade nome do script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="a1b48-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="a1b48-122">Para obter mais informações sobre como utilizar condições de seleção, consulte [Defining condições para quando uma entrada de exibição ou Item serve](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a1b48-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a1b48-123">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="a1b48-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a1b48-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="a1b48-124">See Also</span></span>

[<span data-ttu-id="a1b48-125">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="a1b48-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a1b48-126">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="a1b48-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a1b48-127">Elemento de PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="a1b48-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="a1b48-128">Elemento de SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="a1b48-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a1b48-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1b48-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
