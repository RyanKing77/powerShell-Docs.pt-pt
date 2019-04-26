---
title: O elemento de ViewDefinitions (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083710"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="d0ace-102">ViewDefinitions Element (Format) (Elemento ViewDefinitions [Formatação])</span><span class="sxs-lookup"><span data-stu-id="d0ace-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="d0ace-103">Define os modos de exibição utilizados para apresentar os objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="d0ace-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="d0ace-104">Estas vistas podem apresentar as propriedades e valores de script de um objeto num formato de tabela, o formato de lista, a amplo formato e o formato de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="d0ace-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="d0ace-105">Elemento de configuração do elemento (formato) ViewDefinitions (formato XML)</span><span class="sxs-lookup"><span data-stu-id="d0ace-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="d0ace-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0ace-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d0ace-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d0ace-107">Attributes and Elements</span></span>

<span data-ttu-id="d0ace-108">As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `ViewDefinitions` elemento.</span><span class="sxs-lookup"><span data-stu-id="d0ace-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="d0ace-109">Não há limite para o número de visualizações que podem ser definidos num arquivo de formatação e podem ser adicionados por qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="d0ace-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="d0ace-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d0ace-110">Attributes</span></span>

<span data-ttu-id="d0ace-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d0ace-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d0ace-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="d0ace-112">Child Elements</span></span>

|<span data-ttu-id="d0ace-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="d0ace-113">Element</span></span>|<span data-ttu-id="d0ace-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0ace-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0ace-115">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d0ace-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="d0ace-116">Define uma vista que é utilizada para apresentar um ou mais objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="d0ace-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d0ace-117">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="d0ace-117">Parent Elements</span></span>

|<span data-ttu-id="d0ace-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="d0ace-118">Element</span></span>|<span data-ttu-id="d0ace-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0ace-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0ace-120">Elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="d0ace-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="d0ace-121">Representa o elemento de nível superior de um ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="d0ace-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d0ace-122">Observações</span><span class="sxs-lookup"><span data-stu-id="d0ace-122">Remarks</span></span>

<span data-ttu-id="d0ace-123">Para obter mais informações sobre os componentes dos diferentes tipos de vistas, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="d0ace-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="d0ace-124">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="d0ace-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="d0ace-125">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="d0ace-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="d0ace-126">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="d0ace-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="d0ace-127">Controles personalizados</span><span class="sxs-lookup"><span data-stu-id="d0ace-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="d0ace-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0ace-128">Example</span></span>

<span data-ttu-id="d0ace-129">Este exemplo mostra um `ViewDefinitions` elemento que contém os elementos de principal para uma vista de tabela e uma vista de lista.</span><span class="sxs-lookup"><span data-stu-id="d0ace-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="d0ace-130">Veja Também</span><span class="sxs-lookup"><span data-stu-id="d0ace-130">See Also</span></span>

[<span data-ttu-id="d0ace-131">Elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="d0ace-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="d0ace-132">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d0ace-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="d0ace-133">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="d0ace-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d0ace-134">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="d0ace-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d0ace-135">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="d0ace-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d0ace-136">Controles personalizados</span><span class="sxs-lookup"><span data-stu-id="d0ace-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="d0ace-137">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0ace-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
