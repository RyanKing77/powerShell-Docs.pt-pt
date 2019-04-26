---
title: O elemento de ViewSelectedBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083829"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="4f4cb-102">ViewSelectedBy Element (Format) (Elemento ViewSelectedBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="4f4cb-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="4f4cb-103">Define os objetos do .NET que são apresentados pela exibição.</span><span class="sxs-lookup"><span data-stu-id="4f4cb-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="4f4cb-104">Cada vista tem de especificar pelo menos um objeto .NET.</span><span class="sxs-lookup"><span data-stu-id="4f4cb-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="4f4cb-105">O elemento de ViewDefinitions (formato) vista elemento (formato) ViewSelectedBy elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="4f4cb-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4f4cb-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f4cb-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4f4cb-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4f4cb-107">Attributes and Elements</span></span>

<span data-ttu-id="4f4cb-108">As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `ViewSelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="4f4cb-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="4f4cb-109">Este elemento tem de conter, pelo menos, um `TypeName` ou `SelectionSetName` elemento subordinado.</span><span class="sxs-lookup"><span data-stu-id="4f4cb-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="4f4cb-110">Não há limite para o número de elementos filho que podem ser especificados nem é sua ordem significativo.</span><span class="sxs-lookup"><span data-stu-id="4f4cb-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="4f4cb-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="4f4cb-111">Attributes</span></span>

<span data-ttu-id="4f4cb-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="4f4cb-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4f4cb-113">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="4f4cb-113">Child Elements</span></span>

|<span data-ttu-id="4f4cb-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f4cb-114">Element</span></span>|<span data-ttu-id="4f4cb-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f4cb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f4cb-116">Elemento de TypeName para ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="4f4cb-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="4f4cb-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4f4cb-117">Optional element.</span></span><br /><br /> <span data-ttu-id="4f4cb-118">Especifica um objeto .NET que é apresentado pela vista.</span><span class="sxs-lookup"><span data-stu-id="4f4cb-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="4f4cb-119">Elemento de SelectionSetName para ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="4f4cb-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="4f4cb-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="4f4cb-120">Optional element.</span></span><br /><br /> <span data-ttu-id="4f4cb-121">Especifica um conjunto de objetos do .NET que são apresentados pela exibição.</span><span class="sxs-lookup"><span data-stu-id="4f4cb-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4f4cb-122">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="4f4cb-122">Parent Elements</span></span>

|<span data-ttu-id="4f4cb-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="4f4cb-123">Element</span></span>|<span data-ttu-id="4f4cb-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f4cb-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f4cb-125">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="4f4cb-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="4f4cb-126">Define uma vista que apresente um ou mais objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="4f4cb-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4f4cb-127">Observações</span><span class="sxs-lookup"><span data-stu-id="4f4cb-127">Remarks</span></span>

<span data-ttu-id="4f4cb-128">Para obter mais informações sobre como este elemento é usado em exibições diferentes, consulte [componentes de exibição de tabela](./creating-a-table-view.md), [componentes de exibição de lista](./creating-a-list-view.md), [ampla componentes de exibição](./creating-a-wide-view.md)e [Componentes de controle personalizado](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="4f4cb-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="4f4cb-129">O `SelectionSetName` elemento é usado quando o arquivo de formatação define um conjunto de objetos que são apresentadas por várias exibições.</span><span class="sxs-lookup"><span data-stu-id="4f4cb-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="4f4cb-130">Para obter mais informações sobre como os conjuntos de seleção são definidos e referenciados, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="4f4cb-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="4f4cb-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f4cb-131">Example</span></span>

<span data-ttu-id="4f4cb-132">O exemplo seguinte mostra como especificar a [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto para uma vista de lista.</span><span class="sxs-lookup"><span data-stu-id="4f4cb-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="4f4cb-133">O mesmo esquema é usado para exibições de tabela, ampla e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="4f4cb-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="4f4cb-134">Veja Também</span><span class="sxs-lookup"><span data-stu-id="4f4cb-134">See Also</span></span>

[<span data-ttu-id="4f4cb-135">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="4f4cb-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="4f4cb-136">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="4f4cb-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="4f4cb-137">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="4f4cb-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4f4cb-138">Criação de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="4f4cb-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="4f4cb-139">Definir conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="4f4cb-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="4f4cb-140">Elemento de SelectionSetName para ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="4f4cb-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="4f4cb-141">Elemento de TypeName (formato)</span><span class="sxs-lookup"><span data-stu-id="4f4cb-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="4f4cb-142">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f4cb-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
