---
title: Ver o elemento (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846915"
---
# <a name="view-element-format"></a><span data-ttu-id="a7237-102">View Element (Format) (Elemento View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="a7237-102">View Element (Format)</span></span>

<span data-ttu-id="a7237-103">Define uma vista que apresente um ou mais objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="a7237-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="a7237-104">Não existe nenhum limite para o número de visualizações que podem ser definidos num arquivo de formatação.</span><span class="sxs-lookup"><span data-stu-id="a7237-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="a7237-105">Elemento de configuração do modo de exibição elemento (formato) ViewDefinitions elemento (formato) (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a7237-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7237-106">Syntax</span></span>

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a7237-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="a7237-107">Attributes and Elements</span></span>

<span data-ttu-id="a7237-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `View` elemento.</span><span class="sxs-lookup"><span data-stu-id="a7237-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="a7237-109">Tem de especificar um e apenas um dos elementos subordinados controle e tem de especificar o nome de exibição e os objetos que utilizam a vista.</span><span class="sxs-lookup"><span data-stu-id="a7237-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="a7237-110">Definir controlos personalizados, como agrupar objetos e especificar se a vista está fora de banda são opcionais.</span><span class="sxs-lookup"><span data-stu-id="a7237-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="a7237-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="a7237-111">Attributes</span></span>

<span data-ttu-id="a7237-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a7237-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a7237-113">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="a7237-113">Child Elements</span></span>

|<span data-ttu-id="a7237-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="a7237-114">Element</span></span>|<span data-ttu-id="a7237-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7237-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a7237-116">Elemento de controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="a7237-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a7237-117">Optional element.</span></span><br /><br /> <span data-ttu-id="a7237-118">Define um conjunto de controlos que pode ser referenciado pelo nome, a partir do modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="a7237-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="a7237-119">Elemento de CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="a7237-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a7237-120">Optional element.</span></span><br /><br /> <span data-ttu-id="a7237-121">Define um formato de controle personalizado para a vista.</span><span class="sxs-lookup"><span data-stu-id="a7237-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="a7237-122">GroupBy elemento para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="a7237-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a7237-123">Optional element.</span></span><br /><br /> <span data-ttu-id="a7237-124">Define a forma como os membros dos objetos .NET são agrupados.</span><span class="sxs-lookup"><span data-stu-id="a7237-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="a7237-125">ListControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="a7237-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a7237-126">Optional element.</span></span><br /><br /> <span data-ttu-id="a7237-127">Define um formato de lista para a vista.</span><span class="sxs-lookup"><span data-stu-id="a7237-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="a7237-128">Elemento de nome para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="a7237-129">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="a7237-129">Required element.</span></span><br /><br /> <span data-ttu-id="a7237-130">Especifica o nome utilizado para referenciar o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="a7237-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="a7237-131">Elemento de TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="a7237-132">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a7237-132">Optional element.</span></span><br /><br /> <span data-ttu-id="a7237-133">Define um formato de tabela para a vista.</span><span class="sxs-lookup"><span data-stu-id="a7237-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="a7237-134">Elemento de ViewSelectedBy para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="a7237-135">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="a7237-135">Required element.</span></span><br /><br /> <span data-ttu-id="a7237-136">Define os objetos do .NET que esta vista apresenta.</span><span class="sxs-lookup"><span data-stu-id="a7237-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="a7237-137">Elemento de WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="a7237-138">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a7237-138">Optional element.</span></span><br /><br /> <span data-ttu-id="a7237-139">Define uma vasta (valor único) formato de lista para a vista.</span><span class="sxs-lookup"><span data-stu-id="a7237-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a7237-140">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="a7237-140">Parent Elements</span></span>

|<span data-ttu-id="a7237-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="a7237-141">Element</span></span>|<span data-ttu-id="a7237-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7237-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a7237-143">Elemento de ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="a7237-144">Define os modos de exibição utilizados para apresentar os objetos.</span><span class="sxs-lookup"><span data-stu-id="a7237-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a7237-145">Observações</span><span class="sxs-lookup"><span data-stu-id="a7237-145">Remarks</span></span>

<span data-ttu-id="a7237-146">Para obter mais informações sobre os componentes de diferentes modos de exibição e controles personalizados, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="a7237-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="a7237-147">Componentes de exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="a7237-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="a7237-148">Componentes de exibição de lista</span><span class="sxs-lookup"><span data-stu-id="a7237-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="a7237-149">Componentes de vista alargada</span><span class="sxs-lookup"><span data-stu-id="a7237-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="a7237-150">Controles personalizados</span><span class="sxs-lookup"><span data-stu-id="a7237-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="a7237-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7237-151">Example</span></span>

<span data-ttu-id="a7237-152">Este exemplo mostra uma `View` elemento que define uma vista de tabela para o [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="a7237-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="a7237-153">Veja Também</span><span class="sxs-lookup"><span data-stu-id="a7237-153">See Also</span></span>

[<span data-ttu-id="a7237-154">Elemento de ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="a7237-155">Elemento de nome para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="a7237-156">Elemento de ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="a7237-157">Elemento de controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="a7237-158">GroupBy elemento para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="a7237-159">Elemento de TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="a7237-160">ListControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="a7237-161">Elemento de WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="a7237-162">Elemento de CustomControl (formato)</span><span class="sxs-lookup"><span data-stu-id="a7237-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="a7237-163">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a7237-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
