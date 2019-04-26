---
title: Elemento de TableRowEntry para TableRowEntries para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075329"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a><span data-ttu-id="f7658-102">TableRowEntry Element for TableRowEntries for TableControl (Format) (Elemento TableRowEntry para TableRowEntries para TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="f7658-102">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

<span data-ttu-id="f7658-103">Define os dados que são apresentados numa linha da tabela.</span><span class="sxs-lookup"><span data-stu-id="f7658-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="f7658-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento de configuração para o elemento de TableRowEntry TableControl (formato) para TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f7658-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f7658-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7658-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f7658-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f7658-106">Attributes and Elements</span></span>

<span data-ttu-id="f7658-107">As secções seguintes descrevem os atributos e elemento pai de elementos filho do `TableRowEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="f7658-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f7658-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="f7658-108">Attributes</span></span>

<span data-ttu-id="f7658-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f7658-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f7658-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="f7658-110">Child Elements</span></span>

|<span data-ttu-id="f7658-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="f7658-111">Element</span></span>|<span data-ttu-id="f7658-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7658-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7658-113">Elemento de EntrySelectedBy para TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f7658-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="f7658-114">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="f7658-114">Required element.</span></span><br /><br /> <span data-ttu-id="f7658-115">Define os objetos cujos valores de propriedade são apresentados na linha.</span><span class="sxs-lookup"><span data-stu-id="f7658-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="f7658-116">Elemento de TableColumnItems para TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f7658-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="f7658-117">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="f7658-117">Required element.</span></span><br /><br /> <span data-ttu-id="f7658-118">Define as propriedades ou scripts cujos valores são apresentados.</span><span class="sxs-lookup"><span data-stu-id="f7658-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="f7658-119">Encapsular o elemento para TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f7658-119">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="f7658-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f7658-120">Optional element.</span></span><br /><br /> <span data-ttu-id="f7658-121">Especifica que o texto que excede a largura da coluna é apresentado na próxima linha.</span><span class="sxs-lookup"><span data-stu-id="f7658-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f7658-122">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="f7658-122">Parent Elements</span></span>

|<span data-ttu-id="f7658-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="f7658-123">Element</span></span>|<span data-ttu-id="f7658-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7658-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7658-125">Elemento de TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f7658-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="f7658-126">Define as linhas da tabela.</span><span class="sxs-lookup"><span data-stu-id="f7658-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f7658-127">Observações</span><span class="sxs-lookup"><span data-stu-id="f7658-127">Remarks</span></span>

<span data-ttu-id="f7658-128">Um `TableColumnItems` e um elemento `EntrySelectedBy` elemento tem de ser especificado.</span><span class="sxs-lookup"><span data-stu-id="f7658-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="f7658-129">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f7658-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f7658-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7658-130">Example</span></span>

<span data-ttu-id="f7658-131">A exemplo a seguir mostra um `TableRowEntry` elemento que define uma linha que apresenta os valores das duas propriedades do [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="f7658-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName> Property for first column</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName> Property for second column</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="f7658-132">Veja Também</span><span class="sxs-lookup"><span data-stu-id="f7658-132">See Also</span></span>

[<span data-ttu-id="f7658-133">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="f7658-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f7658-134">Elemento de EntrySelectedBy para TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f7658-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="f7658-135">Elemento de TableColumnItems para TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f7658-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="f7658-136">Elemento de TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f7658-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="f7658-137">Encapsular o elemento para TableRowEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f7658-137">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="f7658-138">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f7658-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
