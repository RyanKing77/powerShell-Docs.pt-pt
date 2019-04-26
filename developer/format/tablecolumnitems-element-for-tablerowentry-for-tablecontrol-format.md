---
title: Elemento de TableColumnItems para TableRowEntry para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075397"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="c9cf4-102">TableColumnItems Element for TableRowEntry for TableControl (Format) (Elemento TableColumnItems para TableRowEntry para TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="c9cf4-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="c9cf4-103">Define as propriedades ou scripts cujos valores são exibidos numa linha.</span><span class="sxs-lookup"><span data-stu-id="c9cf4-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="c9cf4-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento de configuração para o elemento de TableRowEntry TableControl (formato) para TableRowEntries para TableControl (formato) Elemento de TableColumnItems para TableControlEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c9cf4-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c9cf4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9cf4-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9cf4-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c9cf4-106">Attributes and Elements</span></span>

<span data-ttu-id="c9cf4-107">As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `TableColumnItems` elemento.</span><span class="sxs-lookup"><span data-stu-id="c9cf4-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9cf4-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="c9cf4-108">Attributes</span></span>

<span data-ttu-id="c9cf4-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c9cf4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c9cf4-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="c9cf4-110">Child Elements</span></span>

|<span data-ttu-id="c9cf4-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="c9cf4-111">Element</span></span>|<span data-ttu-id="c9cf4-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9cf4-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9cf4-113">Elemento de TableColumnItem para TableColumnItems para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c9cf4-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="c9cf4-114">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="c9cf4-114">Required element.</span></span><br /><br /> <span data-ttu-id="c9cf4-115">Define a propriedade ou um script cujo valor é apresentado numa coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="c9cf4-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c9cf4-116">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="c9cf4-116">Parent Elements</span></span>

|<span data-ttu-id="c9cf4-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="c9cf4-117">Element</span></span>|<span data-ttu-id="c9cf4-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9cf4-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9cf4-119">Elemento de TableRowEntry para TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c9cf4-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="c9cf4-120">Define os dados que são apresentados numa linha da tabela.</span><span class="sxs-lookup"><span data-stu-id="c9cf4-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c9cf4-121">Observações</span><span class="sxs-lookup"><span data-stu-id="c9cf4-121">Remarks</span></span>

<span data-ttu-id="c9cf4-122">A `TableColumnItem` elemento é necessário para cada coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="c9cf4-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="c9cf4-123">A primeira entrada é apresentada na primeira coluna, a segunda entrada na segunda coluna e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="c9cf4-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="c9cf4-124">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="c9cf4-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c9cf4-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9cf4-125">Example</span></span>

<span data-ttu-id="c9cf4-126">A exemplo a seguir mostra um `TableColumnItems` elemento que define três propriedades do [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="c9cf4-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a><span data-ttu-id="c9cf4-127">Veja Também</span><span class="sxs-lookup"><span data-stu-id="c9cf4-127">See Also</span></span>

[<span data-ttu-id="c9cf4-128">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="c9cf4-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c9cf4-129">Elemento de TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="c9cf4-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="c9cf4-130">Elemento de TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="c9cf4-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="c9cf4-131">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9cf4-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
