---
title: O elemento de TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054582"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="550da-102">TableControl Element (Format) (Elemento TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="550da-102">TableControl Element (Format)</span></span>

<span data-ttu-id="550da-103">Define um formato de tabela para obter uma exibição.</span><span class="sxs-lookup"><span data-stu-id="550da-103">Defines a table format for a view.</span></span>

<span data-ttu-id="550da-104">O elemento de ViewDefinitions (formato) vista elemento (formato) TableControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="550da-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="550da-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="550da-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="550da-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="550da-106">Attributes and Elements</span></span>

<span data-ttu-id="550da-107">As secções seguintes descrevem os atributos e elemento pai de elementos filho do `TableControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="550da-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="550da-108">Tem de especificar as linhas da tabela.</span><span class="sxs-lookup"><span data-stu-id="550da-108">You must specify the rows of the table.</span></span> <span data-ttu-id="550da-109">Todos os outros elementos filho são opcionais.</span><span class="sxs-lookup"><span data-stu-id="550da-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="550da-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="550da-110">Attributes</span></span>

<span data-ttu-id="550da-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="550da-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="550da-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="550da-112">Child Elements</span></span>

|<span data-ttu-id="550da-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="550da-113">Element</span></span>|<span data-ttu-id="550da-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="550da-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="550da-115">Elemento de dimensionamento automático para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="550da-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="550da-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="550da-116">Optional element.</span></span><br /><br /> <span data-ttu-id="550da-117">Especifica se o tamanho da coluna e o número de colunas são ajustados com base no tamanho dos dados.</span><span class="sxs-lookup"><span data-stu-id="550da-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="550da-118">Elemento de HideTableHeaders para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="550da-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="550da-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="550da-119">Optional element.</span></span><br /><br /> <span data-ttu-id="550da-120">Indica se o cabeçalho da tabela não é apresentado.</span><span class="sxs-lookup"><span data-stu-id="550da-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="550da-121">Elemento de TableHeaders para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="550da-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="550da-122">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="550da-122">Required element.</span></span><br /><br /> <span data-ttu-id="550da-123">Define as etiquetas, as larguras e o alinhamento dos dados para as colunas de vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="550da-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="550da-124">Elemento de TableRowEntries para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="550da-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="550da-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="550da-125">Optional element.</span></span><br /><br /> <span data-ttu-id="550da-126">Fornece definições de vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="550da-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="550da-127">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="550da-127">Parent Elements</span></span>

|<span data-ttu-id="550da-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="550da-128">Element</span></span>|<span data-ttu-id="550da-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="550da-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="550da-130">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="550da-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="550da-131">Define uma vista que é utilizada para apresentar os membros de um ou mais objetos.</span><span class="sxs-lookup"><span data-stu-id="550da-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="550da-132">Observações</span><span class="sxs-lookup"><span data-stu-id="550da-132">Remarks</span></span>

<span data-ttu-id="550da-133">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="550da-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="550da-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="550da-134">Example</span></span>

<span data-ttu-id="550da-135">Este exemplo mostra uma `TableControl` elemento que é utilizado para apresentar as propriedades do [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="550da-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="550da-136">Veja Também</span><span class="sxs-lookup"><span data-stu-id="550da-136">See Also</span></span>

[<span data-ttu-id="550da-137">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="550da-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="550da-138">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="550da-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="550da-139">Elemento de dimensionamento automático para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="550da-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="550da-140">Elemento de HideTableHeaders (formato)</span><span class="sxs-lookup"><span data-stu-id="550da-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="550da-141">Elemento de TableHeaders (formato)</span><span class="sxs-lookup"><span data-stu-id="550da-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="550da-142">Elemento de TableRowEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="550da-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="550da-143">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="550da-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
