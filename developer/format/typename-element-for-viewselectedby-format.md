---
title: Elemento de TypeName para ViewSelectedBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083761"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="d3c38-102">TypeName Element for ViewSelectedBy (Format) (Elemento TypeName para ViewSelectedBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="d3c38-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="d3c38-103">Especifica um objeto .NET que é apresentado pela vista.</span><span class="sxs-lookup"><span data-stu-id="d3c38-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="d3c38-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ViewSelectedBy elemento (formato) TypeName elemento de configuração para ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d3c38-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d3c38-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3c38-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d3c38-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d3c38-106">Attributes and Elements</span></span>

<span data-ttu-id="d3c38-107">As secções seguintes descrevem os atributos e elementos filho e os elementos pai do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="d3c38-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d3c38-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="d3c38-108">Attributes</span></span>

<span data-ttu-id="d3c38-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d3c38-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d3c38-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="d3c38-110">Child Elements</span></span>

<span data-ttu-id="d3c38-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d3c38-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d3c38-112">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="d3c38-112">Parent Elements</span></span>

|<span data-ttu-id="d3c38-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="d3c38-113">Element</span></span>|<span data-ttu-id="d3c38-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3c38-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d3c38-115">Elemento de ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d3c38-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="d3c38-116">Define os objetos do .NET que são apresentados pela exibição.</span><span class="sxs-lookup"><span data-stu-id="d3c38-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d3c38-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="d3c38-117">Text Value</span></span>

<span data-ttu-id="d3c38-118">Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="d3c38-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d3c38-119">Observações</span><span class="sxs-lookup"><span data-stu-id="d3c38-119">Remarks</span></span>

<span data-ttu-id="d3c38-120">Para obter mais informações sobre como este elemento é usado em exibições diferentes, consulte [criar uma vista de tabela](./creating-a-table-view.md), [criar uma vista de lista](./creating-a-list-view.md), [criação de uma vista alargada](./creating-a-wide-view.md), e [ Componentes de exibição personalizada](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d3c38-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="d3c38-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3c38-121">Example</span></span>

<span data-ttu-id="d3c38-122">O exemplo seguinte mostra como especificar a [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto para uma vista de lista.</span><span class="sxs-lookup"><span data-stu-id="d3c38-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="d3c38-123">O mesmo esquema é usado para exibições de tabela, ampla e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="d3c38-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="d3c38-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="d3c38-124">See Also</span></span>

[<span data-ttu-id="d3c38-125">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="d3c38-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d3c38-126">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="d3c38-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d3c38-127">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="d3c38-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d3c38-128">Criação de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="d3c38-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="d3c38-129">Elemento de ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d3c38-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="d3c38-130">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3c38-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
