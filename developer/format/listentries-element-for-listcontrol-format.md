---
title: Elemento de ListEntries para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847363"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="268e6-102">ListEntries Element for ListControl (Format) (Elemento ListEntries para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="268e6-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="268e6-103">Fornece definições de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="268e6-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="268e6-104">A vista de lista tem de especificar uma ou mais definições.</span><span class="sxs-lookup"><span data-stu-id="268e6-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="268e6-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries o elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="268e6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="268e6-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="268e6-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="268e6-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="268e6-107">Attributes and Elements</span></span>

<span data-ttu-id="268e6-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ListEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="268e6-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="268e6-109">Elemento, pelo menos, um subordinado tem de ser especificado.</span><span class="sxs-lookup"><span data-stu-id="268e6-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="268e6-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="268e6-110">Attributes</span></span>

<span data-ttu-id="268e6-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="268e6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="268e6-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="268e6-112">Child Elements</span></span>

|<span data-ttu-id="268e6-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="268e6-113">Element</span></span>|<span data-ttu-id="268e6-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="268e6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="268e6-115">Elemento de ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="268e6-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="268e6-116">Fornece uma definição de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="268e6-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="268e6-117">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="268e6-117">Parent Elements</span></span>

|<span data-ttu-id="268e6-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="268e6-118">Element</span></span>|<span data-ttu-id="268e6-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="268e6-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="268e6-120">ListControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="268e6-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="268e6-121">Define um formato de lista para a vista.</span><span class="sxs-lookup"><span data-stu-id="268e6-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="268e6-122">Observações</span><span class="sxs-lookup"><span data-stu-id="268e6-122">Remarks</span></span>

<span data-ttu-id="268e6-123">Para obter mais informações sobre vistas de lista, consulte [vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="268e6-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="268e6-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="268e6-124">Example</span></span>

<span data-ttu-id="268e6-125">Este exemplo mostra os elementos XML que definem a vista de lista para o [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="268e6-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="268e6-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="268e6-126">See Also</span></span>

[<span data-ttu-id="268e6-127">ListControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="268e6-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="268e6-128">Elemento de ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="268e6-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="268e6-129">Vista de lista</span><span class="sxs-lookup"><span data-stu-id="268e6-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="268e6-130">Escrever do Windows PowerShell, formatação e os tipos de ficheiro</span><span class="sxs-lookup"><span data-stu-id="268e6-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
