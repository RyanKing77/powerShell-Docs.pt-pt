---
title: Elemento de alinhamento para TableColumnItem para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066945"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="e802f-102">Alignment Element for TableColumnItem for TableControl (Format) (Elemento Alignment para TableColumnItem para TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="e802f-102">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="e802f-103">Define como os dados numa coluna da linha são exibidos.</span><span class="sxs-lookup"><span data-stu-id="e802f-103">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="e802f-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento (formato) TableRowEntry elemento (formato) TableColumnItems elemento (formato) TableColumnItem elemento de configuração (formato) Elemento de alinhamento para TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="e802f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e802f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e802f-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e802f-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e802f-106">Attributes and Elements</span></span>

<span data-ttu-id="e802f-107">As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `Alignment` elemento.</span><span class="sxs-lookup"><span data-stu-id="e802f-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e802f-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="e802f-108">Attributes</span></span>

<span data-ttu-id="e802f-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e802f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e802f-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="e802f-110">Child Elements</span></span>

<span data-ttu-id="e802f-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e802f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e802f-112">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="e802f-112">Parent Elements</span></span>

|<span data-ttu-id="e802f-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="e802f-113">Element</span></span>|<span data-ttu-id="e802f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e802f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e802f-115">Elemento de TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="e802f-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="e802f-116">Define uma etiqueta, a largura e o alinhamento dos dados para uma coluna da tabela.</span><span class="sxs-lookup"><span data-stu-id="e802f-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e802f-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="e802f-117">Text Value</span></span>

<span data-ttu-id="e802f-118">Especifique um dos seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="e802f-118">Specify one of the following values.</span></span> <span data-ttu-id="e802f-119">(Esses valores não diferenciam maiúsculas de minúsculas.)</span><span class="sxs-lookup"><span data-stu-id="e802f-119">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="e802f-120">Os dados apresentados na coluna à esquerda de turnos à esquerda.</span><span class="sxs-lookup"><span data-stu-id="e802f-120">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="e802f-121">(Esta é a predefinição se este elemento não for especificado.)</span><span class="sxs-lookup"><span data-stu-id="e802f-121">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="e802f-122">Os dados apresentados na coluna à direita de turnos certos.</span><span class="sxs-lookup"><span data-stu-id="e802f-122">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="e802f-123">Centros de centro de dados na coluna.</span><span class="sxs-lookup"><span data-stu-id="e802f-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="e802f-124">Observações</span><span class="sxs-lookup"><span data-stu-id="e802f-124">Remarks</span></span>

<span data-ttu-id="e802f-125">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="e802f-125">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e802f-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="e802f-126">See Also</span></span>

[<span data-ttu-id="e802f-127">Vista de tabela</span><span class="sxs-lookup"><span data-stu-id="e802f-127">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e802f-128">Elemento de TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="e802f-128">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
