---
title: Elemento de largura para TableColumnHeader para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: a38fcbef457e69e3ea08d25ba3a9843621036f1e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844787"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="c50cb-102">Width Element for TableColumnHeader for TableControl (Format) (Elemento Width para TableColumnHeader para TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="c50cb-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="c50cb-103">Define a largura (em carateres) de uma coluna.</span><span class="sxs-lookup"><span data-stu-id="c50cb-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="c50cb-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableHeaders elemento de configuração para TableHeaders de elemento de TableColumnHeader TableControl (formato) para o elemento de largura de TableControl (formato) para TableColumnHeader para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c50cb-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c50cb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c50cb-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c50cb-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="c50cb-106">Attributes and Elements</span></span>

<span data-ttu-id="c50cb-107">As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `Width` elemento usado ao definir cabeçalhos de coluna.</span><span class="sxs-lookup"><span data-stu-id="c50cb-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="c50cb-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="c50cb-108">Attributes</span></span>

<span data-ttu-id="c50cb-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c50cb-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c50cb-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="c50cb-110">Child Elements</span></span>

<span data-ttu-id="c50cb-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c50cb-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c50cb-112">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="c50cb-112">Parent Elements</span></span>

|<span data-ttu-id="c50cb-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="c50cb-113">Element</span></span>|<span data-ttu-id="c50cb-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c50cb-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c50cb-115">Elemento de TableColumnHeader para TableHeaders para TbleControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c50cb-115">TableColumnHeader Element for TableHeaders for TbleControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="c50cb-116">Define uma etiqueta, largura e alinhamento de dados para uma coluna da tabela.</span><span class="sxs-lookup"><span data-stu-id="c50cb-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c50cb-117">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="c50cb-117">Text Value</span></span>

<span data-ttu-id="c50cb-118">Quando em todos os possíveis, especifique uma largura (em carateres), que é superior ao comprimento dos valores de propriedade apresentado.</span><span class="sxs-lookup"><span data-stu-id="c50cb-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="c50cb-119">Observações</span><span class="sxs-lookup"><span data-stu-id="c50cb-119">Remarks</span></span>

<span data-ttu-id="c50cb-120">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="c50cb-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c50cb-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c50cb-121">Example</span></span>

<span data-ttu-id="c50cb-122">A exemplo a seguir mostra um `TableColumnHeader` elemento cuja largura é de 16 carateres.</span><span class="sxs-lookup"><span data-stu-id="c50cb-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="c50cb-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="c50cb-123">See Also</span></span>

[<span data-ttu-id="c50cb-124">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="c50cb-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c50cb-125">Elemento de TableColumnHeader para TableHeader para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c50cb-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="c50cb-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c50cb-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
