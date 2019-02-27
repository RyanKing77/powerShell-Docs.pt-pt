---
title: O elemento de TableHeaders (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847426"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="dafbe-102">TableHeaders Element (Format) (Elemento TableHeaders [Formatação])</span><span class="sxs-lookup"><span data-stu-id="dafbe-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="dafbe-103">Define os cabeçalhos das colunas de uma tabela.</span><span class="sxs-lookup"><span data-stu-id="dafbe-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="dafbe-104">O elemento de ViewDefinitions (formato) vista elemento (formato) TableControl elemento (formato) TableHeaders elemento para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="dafbe-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dafbe-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dafbe-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="dafbe-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="dafbe-106">Attributes and Elements</span></span>

<span data-ttu-id="dafbe-107">As secções seguintes descrevem os atributos, elementos filho e elementos pai do `TableHeaders` elemento.</span><span class="sxs-lookup"><span data-stu-id="dafbe-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="dafbe-108">Tem de existir um elemento filho para cada propriedade do objeto que está a ser exibido.</span><span class="sxs-lookup"><span data-stu-id="dafbe-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="dafbe-109">As informações de cabeçalho de coluna são apresentadas na ordem em que os elementos filho são especificados.</span><span class="sxs-lookup"><span data-stu-id="dafbe-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="dafbe-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="dafbe-110">Attributes</span></span>

<span data-ttu-id="dafbe-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="dafbe-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dafbe-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="dafbe-112">Child Elements</span></span>

|<span data-ttu-id="dafbe-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="dafbe-113">Element</span></span>|<span data-ttu-id="dafbe-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="dafbe-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dafbe-115">Elemento de TableColumnHeader (formato)</span><span class="sxs-lookup"><span data-stu-id="dafbe-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="dafbe-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="dafbe-116">Optional element.</span></span><br /><br /> <span data-ttu-id="dafbe-117">Define o alinhamento dos dados para uma coluna de uma vista de tabela, a largura e a etiqueta.</span><span class="sxs-lookup"><span data-stu-id="dafbe-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dafbe-118">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="dafbe-118">Parent Elements</span></span>

|<span data-ttu-id="dafbe-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="dafbe-119">Element</span></span>|<span data-ttu-id="dafbe-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="dafbe-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dafbe-121">Elemento de TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="dafbe-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="dafbe-122">Define um formato de tabela para obter uma exibição.</span><span class="sxs-lookup"><span data-stu-id="dafbe-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dafbe-123">Observações</span><span class="sxs-lookup"><span data-stu-id="dafbe-123">Remarks</span></span>

<span data-ttu-id="dafbe-124">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="dafbe-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="dafbe-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dafbe-125">Example</span></span>

<span data-ttu-id="dafbe-126">Este exemplo mostra um `TableHeaders` elemento que define dois cabeçalhos de coluna.</span><span class="sxs-lookup"><span data-stu-id="dafbe-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dafbe-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="dafbe-127">See Also</span></span>

[<span data-ttu-id="dafbe-128">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="dafbe-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="dafbe-129">Elemento de TableColumnHeader (formato)</span><span class="sxs-lookup"><span data-stu-id="dafbe-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="dafbe-130">Elemento de TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="dafbe-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="dafbe-131">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="dafbe-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
