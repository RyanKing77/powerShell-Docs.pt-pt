---
title: Elemento de nome para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065075"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="cfefc-102">Name Element for View (Format) (Elemento Name para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="cfefc-102">Name Element for View (Format)</span></span>

<span data-ttu-id="cfefc-103">Especifica o nome que é utilizado para identificar o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="cfefc-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="cfefc-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) nome elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="cfefc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cfefc-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cfefc-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cfefc-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cfefc-106">Attributes and Elements</span></span>

<span data-ttu-id="cfefc-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Name` elemento.</span><span class="sxs-lookup"><span data-stu-id="cfefc-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="cfefc-108">Apenas um `Name` elemento é permitido para cada exibição.</span><span class="sxs-lookup"><span data-stu-id="cfefc-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="cfefc-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="cfefc-109">Attributes</span></span>

<span data-ttu-id="cfefc-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cfefc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cfefc-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="cfefc-111">Child Elements</span></span>

<span data-ttu-id="cfefc-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cfefc-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cfefc-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="cfefc-113">Parent Elements</span></span>

|<span data-ttu-id="cfefc-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="cfefc-114">Element</span></span>|<span data-ttu-id="cfefc-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="cfefc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cfefc-116">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="cfefc-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="cfefc-117">Define uma vista que é utilizada para apresentar os membros de um ou mais objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="cfefc-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cfefc-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="cfefc-118">Text Value</span></span>

<span data-ttu-id="cfefc-119">Especifique um nome amigável exclusivo para a vista.</span><span class="sxs-lookup"><span data-stu-id="cfefc-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="cfefc-120">Este nome pode incluir uma referência para o tipo da exibição (como uma vista de tabela ou vista de lista), qual objeto ou conjunto de objetos, utilize a vista, o comando devolve os objetos ou uma combinação das mesmas.</span><span class="sxs-lookup"><span data-stu-id="cfefc-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="cfefc-121">Observações</span><span class="sxs-lookup"><span data-stu-id="cfefc-121">Remarks</span></span>

<span data-ttu-id="cfefc-122">Para obter mais informações sobre os diferentes tipos de vistas, consulte os seguintes tópicos: [Exibição de tabela](./creating-a-table-view.md), [vista de lista](./creating-a-list-view.md), [vista alargada](./creating-a-wide-view.md), e [vista personalizada](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="cfefc-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="cfefc-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cfefc-123">Example</span></span>

<span data-ttu-id="cfefc-124">A exemplo a seguir mostra um `View` elemento que define uma vista de tabela para o [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="cfefc-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="cfefc-125">O nome da vista é o "serviço".</span><span class="sxs-lookup"><span data-stu-id="cfefc-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="cfefc-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="cfefc-126">See Also</span></span>

[<span data-ttu-id="cfefc-127">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="cfefc-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="cfefc-128">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="cfefc-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="cfefc-129">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="cfefc-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="cfefc-130">Criação de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="cfefc-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="cfefc-131">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="cfefc-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="cfefc-132">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cfefc-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
