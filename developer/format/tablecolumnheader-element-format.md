---
title: O elemento de TableColumnHeader (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063814"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="f089d-102">TableColumnHeader Element (Format) (Elemento TableColumnHeader [Formatação])</span><span class="sxs-lookup"><span data-stu-id="f089d-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="f089d-103">Define a etiqueta, a largura da coluna e o alinhamento da etiqueta para uma coluna da tabela.</span><span class="sxs-lookup"><span data-stu-id="f089d-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="f089d-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableHeaders elemento de configuração para o elemento de TableColumnHeader TableControl (formato) para TableHeaders para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f089d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f089d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f089d-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f089d-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f089d-106">Attributes and Elements</span></span>

<span data-ttu-id="f089d-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TableColumnHeader` elemento.</span><span class="sxs-lookup"><span data-stu-id="f089d-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f089d-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="f089d-108">Attributes</span></span>

<span data-ttu-id="f089d-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f089d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f089d-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="f089d-110">Child Elements</span></span>

|<span data-ttu-id="f089d-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="f089d-111">Element</span></span>|<span data-ttu-id="f089d-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f089d-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f089d-113">Elemento da etiqueta para TableColumnHeader para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f089d-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="f089d-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f089d-114">Optional element.</span></span><br /><br /> <span data-ttu-id="f089d-115">Define a etiqueta que é apresentada na parte superior da coluna.</span><span class="sxs-lookup"><span data-stu-id="f089d-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="f089d-116">Se nenhuma etiqueta for especificada, é utilizado o nome da propriedade cujo valor é apresentado nas linhas.</span><span class="sxs-lookup"><span data-stu-id="f089d-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="f089d-117">Elemento de largura para TableColumnHeader para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f089d-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="f089d-118">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="f089d-118">Required element.</span></span><br /><br /> <span data-ttu-id="f089d-119">Especifica a largura (em carateres) da coluna.</span><span class="sxs-lookup"><span data-stu-id="f089d-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="f089d-120">Elemento de alinhamento para TableColumnHeader para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f089d-120">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="f089d-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f089d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f089d-122">Especifica como a etiqueta da coluna é exibida.</span><span class="sxs-lookup"><span data-stu-id="f089d-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="f089d-123">Se não for especificado nenhum alinhamento, a etiqueta é alinhada à esquerda.</span><span class="sxs-lookup"><span data-stu-id="f089d-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f089d-124">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="f089d-124">Parent Elements</span></span>

|<span data-ttu-id="f089d-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="f089d-125">Element</span></span>|<span data-ttu-id="f089d-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="f089d-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f089d-127">Elemento de TableHeaders (formato)</span><span class="sxs-lookup"><span data-stu-id="f089d-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="f089d-128">Define as colunas de uma vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="f089d-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f089d-129">Observações</span><span class="sxs-lookup"><span data-stu-id="f089d-129">Remarks</span></span>

<span data-ttu-id="f089d-130">Especifique um cabeçalho de cada coluna da tabela.</span><span class="sxs-lookup"><span data-stu-id="f089d-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="f089d-131">As colunas são apresentadas na ordem em que o `TableColumnHeader` elementos são definidos.</span><span class="sxs-lookup"><span data-stu-id="f089d-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="f089d-132">Uma tabela tem de ter o mesmo número de `TableColumnHeader` elementos como `TableRowEntry` elementos.</span><span class="sxs-lookup"><span data-stu-id="f089d-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="f089d-133">No cabeçalho da coluna define como o texto na parte superior da tabela é exibido.</span><span class="sxs-lookup"><span data-stu-id="f089d-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="f089d-134">As entradas de linha definem que dados são apresentados nas linhas da tabela.</span><span class="sxs-lookup"><span data-stu-id="f089d-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="f089d-135">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f089d-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f089d-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f089d-136">Example</span></span>

<span data-ttu-id="f089d-137">O exemplo seguinte mostra dois `TableColumnHeader` elementos.</span><span class="sxs-lookup"><span data-stu-id="f089d-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="f089d-138">O primeiro elemento define uma coluna cuja etiqueta é "Coluna 1", tem uma largura de 16 carateres e cuja etiqueta está alinhada à esquerda.</span><span class="sxs-lookup"><span data-stu-id="f089d-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="f089d-139">O segundo elemento define uma coluna cuja etiqueta é "Coluna 2", tem uma largura de 10 caracteres, e cuja etiqueta centra-se na coluna.</span><span class="sxs-lookup"><span data-stu-id="f089d-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
    <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="f089d-140">Veja Também</span><span class="sxs-lookup"><span data-stu-id="f089d-140">See Also</span></span>

[<span data-ttu-id="f089d-141">Elemento de alinhamento para TableColumnHeader para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f089d-141">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="f089d-142">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="f089d-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f089d-143">Elemento da etiqueta para TableColumnHeader para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f089d-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="f089d-144">Elemento de TableHeaders para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f089d-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="f089d-145">Largura para TableColumnHeader TableControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="f089d-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="f089d-146">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f089d-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
