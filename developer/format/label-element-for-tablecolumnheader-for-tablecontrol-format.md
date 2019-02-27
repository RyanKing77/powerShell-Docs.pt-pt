---
title: Elemento da etiqueta para TableColumnHeader para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 59dfd40b95d5088a711eb89cf101eb31a4b159f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846873"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="45b39-102">Label Element for TableColumnHeader for TableControl (Format) (Elemento Label para TableColumnHeader para TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="45b39-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="45b39-103">Define a etiqueta que é apresentada na parte superior de uma coluna.</span><span class="sxs-lookup"><span data-stu-id="45b39-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="45b39-104">Este elemento é utilizado ao definir uma vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="45b39-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="45b39-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableHeaders elemento de configuração para o elemento de TableColumnHeader TableControl (formato) para TableHeaders para o elemento de etiqueta TableControl (formato) para TableColumnHeader para TablControl (formato)</span><span class="sxs-lookup"><span data-stu-id="45b39-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TablControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="45b39-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45b39-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="45b39-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="45b39-107">Attributes and Elements</span></span>

<span data-ttu-id="45b39-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Label` elemento.</span><span class="sxs-lookup"><span data-stu-id="45b39-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="45b39-109">Apenas uma etiqueta é permitida para cada coluna.</span><span class="sxs-lookup"><span data-stu-id="45b39-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="45b39-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="45b39-110">Attributes</span></span>

<span data-ttu-id="45b39-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="45b39-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="45b39-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="45b39-112">Child Elements</span></span>

<span data-ttu-id="45b39-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="45b39-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="45b39-114">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="45b39-114">Parent Elements</span></span>

|<span data-ttu-id="45b39-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="45b39-115">Element</span></span>|<span data-ttu-id="45b39-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="45b39-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="45b39-117">Elemento de TableColumnHeader para TableHeaders para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="45b39-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="45b39-118">Define uma etiqueta, a largura e o alinhamento dos dados para uma coluna da tabela.</span><span class="sxs-lookup"><span data-stu-id="45b39-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="45b39-119">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="45b39-119">Text Value</span></span>

<span data-ttu-id="45b39-120">Especifique o texto que é apresentado na parte superior da coluna da tabela.</span><span class="sxs-lookup"><span data-stu-id="45b39-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="45b39-121">Não há nenhum caráter restrito para a etiqueta de coluna.</span><span class="sxs-lookup"><span data-stu-id="45b39-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="45b39-122">Observações</span><span class="sxs-lookup"><span data-stu-id="45b39-122">Remarks</span></span>

<span data-ttu-id="45b39-123">Se nenhuma etiqueta for especificada, é utilizado o nome da propriedade cujo valor é apresentado nas linhas.</span><span class="sxs-lookup"><span data-stu-id="45b39-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="45b39-124">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="45b39-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="45b39-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45b39-125">Example</span></span>

<span data-ttu-id="45b39-126">Este exemplo mostra um `TableColumnHeader` elemento cuja etiqueta é "Coluna 1".</span><span class="sxs-lookup"><span data-stu-id="45b39-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="45b39-127">Veja Também</span><span class="sxs-lookup"><span data-stu-id="45b39-127">See Also</span></span>

[<span data-ttu-id="45b39-128">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="45b39-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="45b39-129">Elemento de TableColumnHeader (formato)</span><span class="sxs-lookup"><span data-stu-id="45b39-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="45b39-130">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="45b39-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
