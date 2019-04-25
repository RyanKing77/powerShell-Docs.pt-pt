---
title: Elemento de PropertyName para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075873"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="11ed9-102">PropertyName Element for GroupBy (Format) (Elemento PropertyName para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="11ed9-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="11ed9-103">Especifica a propriedade do .NET que inicia um novo grupo sempre que seu valor é alterado.</span><span class="sxs-lookup"><span data-stu-id="11ed9-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="11ed9-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o modo de exibição (formato) PropertyName elemento para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="11ed9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="11ed9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11ed9-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11ed9-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="11ed9-106">Attributes and Elements</span></span>

<span data-ttu-id="11ed9-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="11ed9-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="11ed9-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="11ed9-108">Attributes</span></span>

<span data-ttu-id="11ed9-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="11ed9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="11ed9-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="11ed9-110">Child Elements</span></span>

<span data-ttu-id="11ed9-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="11ed9-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="11ed9-112">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="11ed9-112">Parent Elements</span></span>

|<span data-ttu-id="11ed9-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="11ed9-113">Element</span></span>|<span data-ttu-id="11ed9-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="11ed9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11ed9-115">GroupBy elemento para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="11ed9-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="11ed9-116">Define como um grupo de objetos do .NET é exibido.</span><span class="sxs-lookup"><span data-stu-id="11ed9-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="11ed9-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="11ed9-117">Text Value</span></span>

<span data-ttu-id="11ed9-118">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="11ed9-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="11ed9-119">Observações</span><span class="sxs-lookup"><span data-stu-id="11ed9-119">Remarks</span></span>

<span data-ttu-id="11ed9-120">É iniciado um novo grupo do Windows PowerShell sempre que o valor desta propriedade é alterado.</span><span class="sxs-lookup"><span data-stu-id="11ed9-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="11ed9-121">Quando este elemento é especificado, não é possível especificar a [ScriptBlock](./scriptblock-element-for-groupby-format.md) elemento para iniciar um novo grupo.</span><span class="sxs-lookup"><span data-stu-id="11ed9-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="11ed9-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="11ed9-122">Example</span></span>

<span data-ttu-id="11ed9-123">O exemplo seguinte mostra como iniciar um novo grupo, quando o valor de uma propriedade é alterado.</span><span class="sxs-lookup"><span data-stu-id="11ed9-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="11ed9-124">Para obter um exemplo de um ficheiro de formatação completado que inclui esse elemento, consulte [vista alargada (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="11ed9-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="11ed9-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="11ed9-125">See Also</span></span>

[<span data-ttu-id="11ed9-126">GroupBy elemento para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="11ed9-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="11ed9-127">Elemento de ScriptBlock para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="11ed9-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="11ed9-128">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="11ed9-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
