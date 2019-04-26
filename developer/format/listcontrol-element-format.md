---
title: ListControl elemento (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065262"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="52469-102">ListControl Element (Format) (Elemento ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="52469-102">ListControl Element (Format)</span></span>

<span data-ttu-id="52469-103">Define um formato de lista para a vista.</span><span class="sxs-lookup"><span data-stu-id="52469-103">Defines a list format for the view.</span></span>

<span data-ttu-id="52469-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="52469-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="52469-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52469-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="52469-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="52469-106">Attributes and Elements</span></span>

<span data-ttu-id="52469-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ListControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="52469-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="52469-108">Este elemento tem de conter apenas um elemento único filho.</span><span class="sxs-lookup"><span data-stu-id="52469-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="52469-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="52469-109">Attributes</span></span>

<span data-ttu-id="52469-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="52469-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="52469-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="52469-111">Child Elements</span></span>

|<span data-ttu-id="52469-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="52469-112">Element</span></span>|<span data-ttu-id="52469-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="52469-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52469-114">Elemento de ListEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="52469-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="52469-115">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="52469-115">Required element.</span></span><br /><br /> <span data-ttu-id="52469-116">Fornece definições de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="52469-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="52469-117">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="52469-117">Parent Elements</span></span>

|<span data-ttu-id="52469-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="52469-118">Element</span></span>|<span data-ttu-id="52469-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="52469-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52469-120">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="52469-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="52469-121">Define uma vista que é utilizada para apresentar os membros de um ou mais objetos.</span><span class="sxs-lookup"><span data-stu-id="52469-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="52469-122">Observações</span><span class="sxs-lookup"><span data-stu-id="52469-122">Remarks</span></span>

<span data-ttu-id="52469-123">Para obter mais informações sobre como criar uma vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="52469-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="52469-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="52469-124">Example</span></span>

<span data-ttu-id="52469-125">Este exemplo mostra uma vista de lista para o [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="52469-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="52469-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="52469-126">See Also</span></span>

[<span data-ttu-id="52469-127">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="52469-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="52469-128">Elemento de ListEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="52469-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="52469-129">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="52469-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="52469-130">Escrever do Windows PowerShell, formatação e os tipos de ficheiro</span><span class="sxs-lookup"><span data-stu-id="52469-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
