---
title: Elemento de PropertyName para TableColumnItem para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849239"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="0429c-102">PropertyName Element for TableColumnItem for TableControl (Format) (Elemento PropertyName para TableColumnItem para TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="0429c-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="0429c-103">Especifica a propriedade cujo valor é apresentado na coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="0429c-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="0429c-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento (formato) TableRowEntry elemento (formato) TableColumnItems elemento (formato) TableColumnItem elemento de configuração (formato) Elemento de PropertyName para TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="0429c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0429c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0429c-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0429c-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="0429c-106">Attributes and Elements</span></span>

<span data-ttu-id="0429c-107">As secções seguintes descrevem os atributos e elemento pai de elementos filho do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="0429c-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0429c-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="0429c-108">Attributes</span></span>

<span data-ttu-id="0429c-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0429c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0429c-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="0429c-110">Child Elements</span></span>

<span data-ttu-id="0429c-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0429c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0429c-112">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="0429c-112">Parent Elements</span></span>

|<span data-ttu-id="0429c-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="0429c-113">Element</span></span>|<span data-ttu-id="0429c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="0429c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0429c-115">Elemento de TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="0429c-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="0429c-116">Define a propriedade ou um script cujo valor é apresentado na coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="0429c-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0429c-117">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="0429c-117">Text Value</span></span>

<span data-ttu-id="0429c-118">Especifique o nome da propriedade cujo valor é apresentado.</span><span class="sxs-lookup"><span data-stu-id="0429c-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="0429c-119">Observações</span><span class="sxs-lookup"><span data-stu-id="0429c-119">Remarks</span></span>

<span data-ttu-id="0429c-120">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="0429c-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0429c-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0429c-121">Example</span></span>

<span data-ttu-id="0429c-122">Este exemplo mostra uma `TableColumnItem` elemento que especifica o `Status` propriedade da [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="0429c-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="0429c-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="0429c-123">See Also</span></span>

[<span data-ttu-id="0429c-124">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="0429c-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0429c-125">Elemento de TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="0429c-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="0429c-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0429c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
