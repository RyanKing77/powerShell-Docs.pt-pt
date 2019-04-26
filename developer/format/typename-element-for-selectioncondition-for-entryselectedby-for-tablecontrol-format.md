---
title: Elemento de TypeName para SelectionCondition para EntrySelectedBy para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083846"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="1b634-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format) (Elemento TypeName para SelectionCondition para EntrySelectedBy para TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="1b634-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="1b634-103">Especifica um tipo .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="1b634-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="1b634-104">Quando este tipo está presente, a condição é cumprida e a linha da tabela é utilizada.</span><span class="sxs-lookup"><span data-stu-id="1b634-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="1b634-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento (formato) TableRowEntry elemento (formato) EntrySelectedBy elemento de configuração para TableRowEntry (formato) Elemento de SelectionCondition para EntrySelectedBy para o elemento de TypeName TableRowEntry (formato) para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1b634-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1b634-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b634-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1b634-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1b634-107">Attributes and Elements</span></span>

<span data-ttu-id="1b634-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="1b634-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1b634-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="1b634-109">Attributes</span></span>

<span data-ttu-id="1b634-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1b634-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1b634-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="1b634-111">Child Elements</span></span>

<span data-ttu-id="1b634-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1b634-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1b634-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="1b634-113">Parent Elements</span></span>

|<span data-ttu-id="1b634-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="1b634-114">Element</span></span>|<span data-ttu-id="1b634-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b634-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1b634-116">Elemento de SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1b634-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="1b634-117">Define a condição de que tem de existir para esta linha de tabela a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="1b634-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1b634-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="1b634-118">Text Value</span></span>

<span data-ttu-id="1b634-119">Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="1b634-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b634-120">Observações</span><span class="sxs-lookup"><span data-stu-id="1b634-120">Remarks</span></span>

<span data-ttu-id="1b634-121">A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="1b634-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="1b634-122">Para obter mais informações sobre como utilizar condições de seleção, consulte [Defining condições para quando uma entrada de exibição ou Item serve](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1b634-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1b634-123">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="1b634-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1b634-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="1b634-124">See Also</span></span>

[<span data-ttu-id="1b634-125">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="1b634-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1b634-126">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="1b634-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1b634-127">Elemento de SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1b634-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="1b634-128">Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1b634-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="1b634-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b634-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
