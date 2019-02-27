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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849267"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="ab7b0-102">Name Element for View (Format) (Elemento Name para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="ab7b0-102">Name Element for View (Format)</span></span>

<span data-ttu-id="ab7b0-103">Especifica o nome que é utilizado para identificar o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="ab7b0-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="ab7b0-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) nome elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="ab7b0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ab7b0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab7b0-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ab7b0-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="ab7b0-106">Attributes and Elements</span></span>

<span data-ttu-id="ab7b0-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Name` elemento.</span><span class="sxs-lookup"><span data-stu-id="ab7b0-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="ab7b0-108">Apenas um `Name` elemento é permitido para cada exibição.</span><span class="sxs-lookup"><span data-stu-id="ab7b0-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab7b0-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="ab7b0-109">Attributes</span></span>

<span data-ttu-id="ab7b0-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ab7b0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ab7b0-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="ab7b0-111">Child Elements</span></span>

<span data-ttu-id="ab7b0-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ab7b0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ab7b0-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="ab7b0-113">Parent Elements</span></span>

|<span data-ttu-id="ab7b0-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="ab7b0-114">Element</span></span>|<span data-ttu-id="ab7b0-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab7b0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab7b0-116">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="ab7b0-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="ab7b0-117">Define uma vista que é utilizada para apresentar os membros de um ou mais objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="ab7b0-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ab7b0-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="ab7b0-118">Text Value</span></span>

<span data-ttu-id="ab7b0-119">Especifique um nome amigável exclusivo para a vista.</span><span class="sxs-lookup"><span data-stu-id="ab7b0-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="ab7b0-120">Este nome pode incluir uma referência para o tipo da exibição (como uma vista de tabela ou vista de lista), qual objeto ou conjunto de objetos, utilize a vista, o comando devolve os objetos ou uma combinação das mesmas.</span><span class="sxs-lookup"><span data-stu-id="ab7b0-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="ab7b0-121">Observações</span><span class="sxs-lookup"><span data-stu-id="ab7b0-121">Remarks</span></span>

<span data-ttu-id="ab7b0-122">Para obter mais informações sobre os diferentes tipos de vistas, consulte os seguintes tópicos: [Exibição de tabela](./creating-a-table-view.md), [vista de lista](./creating-a-list-view.md), [vista alargada](./creating-a-wide-view.md), e [vista personalizada](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ab7b0-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="ab7b0-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ab7b0-123">Example</span></span>

<span data-ttu-id="ab7b0-124">A exemplo a seguir mostra um `View` elemento que define uma vista de tabela para o [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="ab7b0-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="ab7b0-125">O nome da vista é o "serviço".</span><span class="sxs-lookup"><span data-stu-id="ab7b0-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="ab7b0-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="ab7b0-126">See Also</span></span>

[<span data-ttu-id="ab7b0-127">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="ab7b0-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="ab7b0-128">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="ab7b0-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ab7b0-129">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="ab7b0-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ab7b0-130">Criação de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="ab7b0-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="ab7b0-131">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="ab7b0-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="ab7b0-132">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab7b0-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
