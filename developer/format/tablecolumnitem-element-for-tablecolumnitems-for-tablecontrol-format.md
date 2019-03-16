---
title: Elemento de TableColumnItem para TableColumnItems para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 159f943f6bfb33c5403b5714380631351523789f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056996"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="d582f-102">TableColumnItem Element for TableColumnItems for TableControl (Format) (Elemento TableColumnItem para TableColumnItems para TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="d582f-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="d582f-103">Define a propriedade ou um script cujo valor é apresentado na coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="d582f-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="d582f-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento de configuração para o elemento de TableRowEntry TableControl (formato) para TableRowEntries para TableControl (formato) Elemento de TableColumnItems para TableControlEntry para o elemento de TableColumnItem TableControl (formato) para TableColumnItems para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d582f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d582f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d582f-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d582f-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="d582f-106">Attributes and Elements</span></span>

<span data-ttu-id="d582f-107">As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `TableColumnItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="d582f-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d582f-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="d582f-108">Attributes</span></span>

<span data-ttu-id="d582f-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d582f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d582f-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="d582f-110">Child Elements</span></span>

|<span data-ttu-id="d582f-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="d582f-111">Element</span></span>|<span data-ttu-id="d582f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d582f-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d582f-113">Elemento de alinhamento para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d582f-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="d582f-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d582f-114">Optional element.</span></span><br /><br /> <span data-ttu-id="d582f-115">Define como os dados numa coluna da linha são exibidos.</span><span class="sxs-lookup"><span data-stu-id="d582f-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="d582f-116">Elemento de FormatString para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d582f-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="d582f-117">Especifica um padrão de formato utilizada para formatar os dados na coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="d582f-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="d582f-118">Elemento de PropertyName para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d582f-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="d582f-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d582f-119">Optional element.</span></span><br /><br /> <span data-ttu-id="d582f-120">Especifica o nome da propriedade cujo valor é apresentado.</span><span class="sxs-lookup"><span data-stu-id="d582f-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="d582f-121">Elemento de ScriptBlock para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d582f-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="d582f-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="d582f-122">Optional element.</span></span><br /><br /> <span data-ttu-id="d582f-123">Especifica o script cujo valor é apresentado na coluna de uma linha.</span><span class="sxs-lookup"><span data-stu-id="d582f-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d582f-124">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="d582f-124">Parent Elements</span></span>

|<span data-ttu-id="d582f-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="d582f-125">Element</span></span>|<span data-ttu-id="d582f-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="d582f-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d582f-127">Elemento de TableColumnItems para TableControlEntry para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d582f-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="d582f-128">Define as propriedades ou scripts cujos valores são apresentados na linha.</span><span class="sxs-lookup"><span data-stu-id="d582f-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d582f-129">Observações</span><span class="sxs-lookup"><span data-stu-id="d582f-129">Remarks</span></span>

<span data-ttu-id="d582f-130">Pode especificar uma propriedade de um objeto ou um script em cada coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="d582f-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="d582f-131">Se nenhum elemento filho forem especificado, o item é um espaço reservado e não serem apresentados dados.</span><span class="sxs-lookup"><span data-stu-id="d582f-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="d582f-132">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d582f-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d582f-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d582f-133">Example</span></span>

<span data-ttu-id="d582f-134">Este exemplo mostra uma `TableColumnItem` elemento que exibe o valor da `Status` propriedade da [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="d582f-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="d582f-135">Veja Também</span><span class="sxs-lookup"><span data-stu-id="d582f-135">See Also</span></span>

[<span data-ttu-id="d582f-136">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="d582f-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d582f-137">Elemento de alinhamento para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d582f-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="d582f-138">Elemento de TableColumnItems (formato)</span><span class="sxs-lookup"><span data-stu-id="d582f-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="d582f-139">Elemento de FormatString para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d582f-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="d582f-140">Elemento de PropertyName para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d582f-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="d582f-141">Elemento de ScriptBlock para TableColumnItem para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="d582f-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="d582f-142">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d582f-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
