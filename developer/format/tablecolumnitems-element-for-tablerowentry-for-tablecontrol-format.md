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
ms.openlocfilehash: faa9ba78397e713400f6072df9915f20d966bb37
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849225"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="a3c6d-102">TableColumnItems Element for TableRowEntry for TableControl (Format) (Elemento TableColumnItems para TableRowEntry para TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="a3c6d-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="a3c6d-103">Define as propriedades ou scripts cujos valores são exibidos numa linha.</span><span class="sxs-lookup"><span data-stu-id="a3c6d-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="a3c6d-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento de configuração para o elemento de TableRowEntry TableControl (formato) para TableRowEntries para TableControl (formato) Elemento de TableColumnItems para TableControlEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a3c6d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a3c6d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3c6d-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a3c6d-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="a3c6d-106">Attributes and Elements</span></span>

<span data-ttu-id="a3c6d-107">As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `TableColumnItems` elemento.</span><span class="sxs-lookup"><span data-stu-id="a3c6d-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a3c6d-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="a3c6d-108">Attributes</span></span>

<span data-ttu-id="a3c6d-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a3c6d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a3c6d-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="a3c6d-110">Child Elements</span></span>

|<span data-ttu-id="a3c6d-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="a3c6d-111">Element</span></span>|<span data-ttu-id="a3c6d-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3c6d-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a3c6d-113">Elemento de TableColumnItem para TableColumnItems para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a3c6d-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="a3c6d-114">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="a3c6d-114">Required element.</span></span><br /><br /> <span data-ttu-id="a3c6d-115">Define a propriedade ou um script cujo valor é apresentado numa coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="a3c6d-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a3c6d-116">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="a3c6d-116">Parent Elements</span></span>

|<span data-ttu-id="a3c6d-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="a3c6d-117">Element</span></span>|<span data-ttu-id="a3c6d-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3c6d-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a3c6d-119">Elemento de TableRowEntry para TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a3c6d-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|<span data-ttu-id="a3c6d-120">Define os dados que são apresentados numa linha da tabela.</span><span class="sxs-lookup"><span data-stu-id="a3c6d-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a3c6d-121">Observações</span><span class="sxs-lookup"><span data-stu-id="a3c6d-121">Remarks</span></span>

<span data-ttu-id="a3c6d-122">A `TableColumnItem` elemento é necessário para cada coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="a3c6d-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="a3c6d-123">A primeira entrada é apresentada na primeira coluna, a segunda entrada na segunda coluna e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="a3c6d-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="a3c6d-124">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="a3c6d-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a3c6d-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a3c6d-125">Example</span></span>

<span data-ttu-id="a3c6d-126">A exemplo a seguir mostra um `TableColumnItems` elemento que define três propriedades do [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="a3c6d-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a3c6d-127">Veja Também</span><span class="sxs-lookup"><span data-stu-id="a3c6d-127">See Also</span></span>

[<span data-ttu-id="a3c6d-128">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="a3c6d-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a3c6d-129">Elemento de TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="a3c6d-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="a3c6d-130">Elemento de TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="a3c6d-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="a3c6d-131">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a3c6d-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
