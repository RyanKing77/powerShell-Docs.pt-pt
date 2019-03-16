---
title: Elemento de EntrySelectedBy para TableRowEntry para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058764"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="a51cd-102">EntrySelectedBy Element for TableRowEntry for TableControl (Format) (Elemento EntrySelectedBy para TableRowEntry para TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="a51cd-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="a51cd-103">Define os tipos do .NET que utilizam esta definição de vista de tabela ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="a51cd-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="a51cd-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento (formato) TableRowEntry elemento (formato) EntrySelectedBy elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a51cd-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a51cd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a51cd-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a51cd-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="a51cd-106">Attributes and Elements</span></span>

<span data-ttu-id="a51cd-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="a51cd-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a51cd-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="a51cd-108">Attributes</span></span>

<span data-ttu-id="a51cd-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a51cd-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a51cd-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="a51cd-110">Child Elements</span></span>

|<span data-ttu-id="a51cd-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="a51cd-111">Element</span></span>|<span data-ttu-id="a51cd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a51cd-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a51cd-113">Elemento de SelectionCondition para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a51cd-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a51cd-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a51cd-114">Optional element.</span></span><br /><br /> <span data-ttu-id="a51cd-115">Define a condição de que tem de existir para esta definição de vista de tabela a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="a51cd-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="a51cd-116">Elemento de SelectionSetName para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a51cd-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a51cd-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a51cd-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a51cd-118">Especifica um conjunto de tipos do .NET que utilizam esta definição de vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="a51cd-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="a51cd-119">Elemento de TypeName para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a51cd-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a51cd-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a51cd-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a51cd-121">Especifica um tipo .NET que utiliza esta definição de vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="a51cd-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a51cd-122">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="a51cd-122">Parent Elements</span></span>

|<span data-ttu-id="a51cd-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="a51cd-123">Element</span></span>|<span data-ttu-id="a51cd-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="a51cd-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a51cd-125">Elemento de TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a51cd-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="a51cd-126">Define os dados que são apresentados numa linha da tabela.</span><span class="sxs-lookup"><span data-stu-id="a51cd-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a51cd-127">Observações</span><span class="sxs-lookup"><span data-stu-id="a51cd-127">Remarks</span></span>

<span data-ttu-id="a51cd-128">Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para uma definição de vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="a51cd-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="a51cd-129">Não existe nenhum limite máximo para o número de elementos filho que pode utilizar.</span><span class="sxs-lookup"><span data-stu-id="a51cd-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="a51cd-130">Condições de seleção são utilizadas para definir uma condição que tem de existir durante a definição a utilizar, por exemplo, quando um objeto tem uma propriedade específica ou um valor de propriedade específica ou um script é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="a51cd-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="a51cd-131">Para obter mais informações sobre as condições de seleção, consulte [Defining condições para quando uma entrada de exibição ou Item serve](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a51cd-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a51cd-132">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="a51cd-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a51cd-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a51cd-133">Example</span></span>

<span data-ttu-id="a51cd-134">A exemplo a seguir mostra um `TableRowEntry` elemento que é utilizado para apresentar as propriedades do [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="a51cd-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="a51cd-135">Veja Também</span><span class="sxs-lookup"><span data-stu-id="a51cd-135">See Also</span></span>

[<span data-ttu-id="a51cd-136">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="a51cd-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a51cd-137">Elemento de SelectionCondition para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a51cd-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a51cd-138">Elemento de SelectionSetName para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a51cd-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a51cd-139">Elemento de TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a51cd-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="a51cd-140">Elemento de TypeName para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a51cd-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a51cd-141">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a51cd-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
