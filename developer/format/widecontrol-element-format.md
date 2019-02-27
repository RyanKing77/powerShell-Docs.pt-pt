---
title: O elemento de WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849491"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="b263b-102">WideControl Element (Format) (Elemento WideControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="b263b-102">WideControl Element (Format)</span></span>

<span data-ttu-id="b263b-103">Define uma vasta (valor único) formato de lista para a vista.</span><span class="sxs-lookup"><span data-stu-id="b263b-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="b263b-104">Esta vista apresenta um valor de propriedade de único ou um valor de script para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="b263b-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="b263b-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="b263b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b263b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b263b-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b263b-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="b263b-107">Attributes and Elements</span></span>

<span data-ttu-id="b263b-108">As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `WideControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="b263b-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="b263b-109">Não é possível especificar a `AutoSize` e `ColumnNumber` elementos ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="b263b-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="b263b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b263b-110">Attributes</span></span>

<span data-ttu-id="b263b-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b263b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b263b-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="b263b-112">Child Elements</span></span>

|<span data-ttu-id="b263b-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="b263b-113">Element</span></span>|<span data-ttu-id="b263b-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b263b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b263b-115">Elemento de dimensionamento automático para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b263b-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="b263b-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b263b-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b263b-117">Especifica se o tamanho da coluna e o número de colunas são ajustados com base no tamanho dos dados.</span><span class="sxs-lookup"><span data-stu-id="b263b-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="b263b-118">Elemento de ColumnNumber para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b263b-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="b263b-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b263b-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b263b-120">Especifica o número de colunas apresentadas na vista alargada.</span><span class="sxs-lookup"><span data-stu-id="b263b-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="b263b-121">Elemento de WideEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="b263b-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="b263b-122">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="b263b-122">Required element.</span></span><br /><br /> <span data-ttu-id="b263b-123">Fornece as definições da vista ampla.</span><span class="sxs-lookup"><span data-stu-id="b263b-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b263b-124">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="b263b-124">Parent Elements</span></span>

|<span data-ttu-id="b263b-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="b263b-125">Element</span></span>|<span data-ttu-id="b263b-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="b263b-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b263b-127">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="b263b-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="b263b-128">Define uma vista que é utilizada para apresentar um ou mais objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="b263b-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b263b-129">Observações</span><span class="sxs-lookup"><span data-stu-id="b263b-129">Remarks</span></span>

<span data-ttu-id="b263b-130">Ao definir uma vista alargada, pode adicionar os `AutoSize` elemento ou o `ColumnNumber` , mas não é possível adicionar ambos.</span><span class="sxs-lookup"><span data-stu-id="b263b-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="b263b-131">Na maioria dos casos, apenas uma definição é necessária para cada vista alargada, mas é possível ter várias definições, se pretender utilizar a mesma vista para apresentar diferentes objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="b263b-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="b263b-132">Nesses casos, pode fornecer uma definição de separado para cada objeto ou conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="b263b-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="b263b-133">Para obter mais informações sobre os componentes de uma vista alargada, consulte [ampla componentes de exibição](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="b263b-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b263b-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b263b-134">Example</span></span>

<span data-ttu-id="b263b-135">A exemplo a seguir mostra um `WideControl` elemento que é utilizado para apresentar uma propriedade do [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="b263b-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

<span data-ttu-id="b263b-136">Para obter um exemplo completo de uma vista alargada, consulte [vista alargada (básico)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="b263b-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b263b-137">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="b263b-137">See Also</span></span>

[<span data-ttu-id="b263b-138">Elemento de dimensionamento automático para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b263b-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="b263b-139">Elemento de ColumnNumber para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="b263b-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="b263b-140">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="b263b-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="b263b-141">Elemento de WideEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="b263b-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="b263b-142">Vista alargada (básico)</span><span class="sxs-lookup"><span data-stu-id="b263b-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="b263b-143">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="b263b-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b263b-144">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b263b-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
