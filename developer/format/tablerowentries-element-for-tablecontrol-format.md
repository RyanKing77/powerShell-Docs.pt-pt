---
title: Elemento de TableRowEntries para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075499"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="0ec43-102">TableRowEntries Element for TableControl (Format) (Elemento TableRowEntries para TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="0ec43-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="0ec43-103">Define as linhas da tabela.</span><span class="sxs-lookup"><span data-stu-id="0ec43-103">Defines the rows of the table.</span></span>

<span data-ttu-id="0ec43-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento de configuração para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="0ec43-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0ec43-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0ec43-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0ec43-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0ec43-106">Attributes and Elements</span></span>

<span data-ttu-id="0ec43-107">As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `TableRowEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="0ec43-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0ec43-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="0ec43-108">Attributes</span></span>

<span data-ttu-id="0ec43-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0ec43-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0ec43-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="0ec43-110">Child Elements</span></span>

|<span data-ttu-id="0ec43-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="0ec43-111">Element</span></span>|<span data-ttu-id="0ec43-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ec43-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ec43-113">Elemento de TableRowEntry para TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="0ec43-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="0ec43-114">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="0ec43-114">Required element.</span></span><br /><br /> <span data-ttu-id="0ec43-115">Define os dados que são apresentados numa linha da tabela.</span><span class="sxs-lookup"><span data-stu-id="0ec43-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0ec43-116">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="0ec43-116">Parent Elements</span></span>

|<span data-ttu-id="0ec43-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="0ec43-117">Element</span></span>|<span data-ttu-id="0ec43-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ec43-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ec43-119">Elemento de TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="0ec43-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="0ec43-120">Define um formato de tabela para obter uma exibição.</span><span class="sxs-lookup"><span data-stu-id="0ec43-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0ec43-121">Observações</span><span class="sxs-lookup"><span data-stu-id="0ec43-121">Remarks</span></span>

<span data-ttu-id="0ec43-122">Tem de especificar um ou mais `TableRowEntry` elementos para a vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="0ec43-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="0ec43-123">Não existe nenhum limite máximo para o número de `TableRowEntry` elementos que podem ser adicionados nem é sua ordem significativo.</span><span class="sxs-lookup"><span data-stu-id="0ec43-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="0ec43-124">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="0ec43-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0ec43-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ec43-125">Example</span></span>

<span data-ttu-id="0ec43-126">A exemplo a seguir mostra um `TableRowEntries` elemento que define uma linha que apresenta os valores das duas propriedades do [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="0ec43-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntries>
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
</TableRowEntries>

```

## <a name="see-also"></a><span data-ttu-id="0ec43-127">Veja Também</span><span class="sxs-lookup"><span data-stu-id="0ec43-127">See Also</span></span>

[<span data-ttu-id="0ec43-128">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="0ec43-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0ec43-129">Elemento de TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="0ec43-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="0ec43-130">Elemento de TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="0ec43-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="0ec43-131">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0ec43-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
