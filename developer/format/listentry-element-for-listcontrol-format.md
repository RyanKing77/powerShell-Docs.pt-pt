---
title: Elemento de ListEntry para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851185"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="70a83-102">ListEntry Element for ListControl (Format) (Elemento ListEntry para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="70a83-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="70a83-103">Fornece uma definição de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="70a83-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="70a83-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento (formato) ListEntry o elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="70a83-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70a83-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70a83-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70a83-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="70a83-106">Attributes and Elements</span></span>

<span data-ttu-id="70a83-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ListEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="70a83-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="70a83-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="70a83-108">Attributes</span></span>

<span data-ttu-id="70a83-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="70a83-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70a83-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="70a83-110">Child Elements</span></span>

|<span data-ttu-id="70a83-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="70a83-111">Element</span></span>|<span data-ttu-id="70a83-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="70a83-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70a83-113">Elemento de EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="70a83-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="70a83-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="70a83-114">Optional element.</span></span><br /><br /> <span data-ttu-id="70a83-115">Define os objetos do .NET que utilizam esta definição de vista de lista ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="70a83-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="70a83-116">Elemento de ListItems (formato)</span><span class="sxs-lookup"><span data-stu-id="70a83-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="70a83-117">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="70a83-117">Required element.</span></span><br /><br /> <span data-ttu-id="70a83-118">Define as propriedades e os scripts cujos valores são apresentados pela vista de lista.</span><span class="sxs-lookup"><span data-stu-id="70a83-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="70a83-119">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="70a83-119">Parent Elements</span></span>

|<span data-ttu-id="70a83-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="70a83-120">Element</span></span>|<span data-ttu-id="70a83-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="70a83-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70a83-122">Elemento de ListEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="70a83-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="70a83-123">Fornece definições de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="70a83-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="70a83-124">Observações</span><span class="sxs-lookup"><span data-stu-id="70a83-124">Remarks</span></span>

<span data-ttu-id="70a83-125">Uma vista de lista é um formato de lista que mostra os valores de propriedade ou valores de script para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="70a83-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="70a83-126">Para obter mais informações sobre vistas de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="70a83-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="70a83-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="70a83-127">Example</span></span>

<span data-ttu-id="70a83-128">Este exemplo mostra os elementos XML que definem a vista de lista para o [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="70a83-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="70a83-129">Veja Também</span><span class="sxs-lookup"><span data-stu-id="70a83-129">See Also</span></span>

[<span data-ttu-id="70a83-130">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="70a83-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="70a83-131">Elemento de EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="70a83-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="70a83-132">Elemento de ListEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="70a83-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="70a83-133">Elemento de ListItems (formato)</span><span class="sxs-lookup"><span data-stu-id="70a83-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="70a83-134">Escrever do Windows PowerShell, formatação e os tipos de ficheiro</span><span class="sxs-lookup"><span data-stu-id="70a83-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
