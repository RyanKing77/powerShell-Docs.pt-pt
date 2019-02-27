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
ms.openlocfilehash: dd48e82452e83f93e2e005c9db53bbc51d8b2eb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848854"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="71280-102">TableControl Element (Format) (Elemento TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="71280-102">TableControl Element (Format)</span></span>

<span data-ttu-id="71280-103">Define um formato de tabela para obter uma exibição.</span><span class="sxs-lookup"><span data-stu-id="71280-103">Defines a table format for a view.</span></span>

<span data-ttu-id="71280-104">O elemento de ViewDefinitions (formato) vista elemento (formato) TableControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="71280-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="71280-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71280-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="71280-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="71280-106">Attributes and Elements</span></span>

<span data-ttu-id="71280-107">As secções seguintes descrevem os atributos e elemento pai de elementos filho do `TableControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="71280-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="71280-108">Tem de especificar as linhas da tabela.</span><span class="sxs-lookup"><span data-stu-id="71280-108">You must specify the rows of the table.</span></span> <span data-ttu-id="71280-109">Todos os outros elementos filho são opcionais.</span><span class="sxs-lookup"><span data-stu-id="71280-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="71280-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="71280-110">Attributes</span></span>

<span data-ttu-id="71280-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="71280-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="71280-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="71280-112">Child Elements</span></span>

|<span data-ttu-id="71280-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="71280-113">Element</span></span>|<span data-ttu-id="71280-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="71280-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="71280-115">Elemento de dimensionamento automático para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="71280-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="71280-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="71280-116">Optional element.</span></span><br /><br /> <span data-ttu-id="71280-117">Especifica se o tamanho da coluna e o número de colunas são ajustados com base no tamanho dos dados.</span><span class="sxs-lookup"><span data-stu-id="71280-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="71280-118">Elemento de HideTableHeaders para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="71280-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="71280-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="71280-119">Optional element.</span></span><br /><br /> <span data-ttu-id="71280-120">Indica se o cabeçalho da tabela não é apresentado.</span><span class="sxs-lookup"><span data-stu-id="71280-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="71280-121">Elemento de TableHeaders para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="71280-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="71280-122">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="71280-122">Required element.</span></span><br /><br /> <span data-ttu-id="71280-123">Define as etiquetas, as larguras e o alinhamento dos dados para as colunas de vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="71280-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="71280-124">Elemento de TableRowEntries para TableCotrol (formato)</span><span class="sxs-lookup"><span data-stu-id="71280-124">TableRowEntries Element for TableCotrol (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="71280-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="71280-125">Optional element.</span></span><br /><br /> <span data-ttu-id="71280-126">Fornece definições de vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="71280-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="71280-127">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="71280-127">Parent Elements</span></span>

|<span data-ttu-id="71280-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="71280-128">Element</span></span>|<span data-ttu-id="71280-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="71280-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="71280-130">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="71280-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="71280-131">Define uma vista que é utilizada para apresentar os membros de um ou mais objetos.</span><span class="sxs-lookup"><span data-stu-id="71280-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="71280-132">Observações</span><span class="sxs-lookup"><span data-stu-id="71280-132">Remarks</span></span>

<span data-ttu-id="71280-133">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="71280-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="71280-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71280-134">Example</span></span>

<span data-ttu-id="71280-135">Este exemplo mostra uma `TableControl` elemento que é utilizado para apresentar as propriedades do [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="71280-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="71280-136">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="71280-136">See Also</span></span>

[<span data-ttu-id="71280-137">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="71280-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="71280-138">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="71280-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="71280-139">Elemento de dimensionamento automático para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="71280-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="71280-140">Elemento de HideTableHeaders (formato)</span><span class="sxs-lookup"><span data-stu-id="71280-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="71280-141">Elemento de TableHeaders (formato)</span><span class="sxs-lookup"><span data-stu-id="71280-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="71280-142">Elemento de TableRowEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="71280-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="71280-143">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="71280-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
