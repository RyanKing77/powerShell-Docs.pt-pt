---
title: Elemento de CustomItem para CustomEntry para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066403"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="c1047-102">CustomItem Element for CustomEntry for GroupBy (Format) (Elemento CustomItem para CustomEntry para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="c1047-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="c1047-103">Define os dados que são apresentados pela vista do controle personalizado e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="c1047-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="c1047-104">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="c1047-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="c1047-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomItem GroupBy (formato) para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c1047-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c1047-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1047-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1047-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c1047-107">Attributes and Elements</span></span>

<span data-ttu-id="c1047-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="c1047-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1047-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="c1047-109">Attributes</span></span>

<span data-ttu-id="c1047-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c1047-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c1047-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="c1047-111">Child Elements</span></span>

|<span data-ttu-id="c1047-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="c1047-112">Element</span></span>|<span data-ttu-id="c1047-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1047-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1047-114">Elemento de ExpressionBinding para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c1047-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="c1047-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="c1047-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c1047-116">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="c1047-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="c1047-117">Elemento de quadro para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c1047-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="c1047-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="c1047-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c1047-119">Define os dados que são apresentados pela vista do controle personalizado e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="c1047-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="c1047-120">Elemento de nova linha para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c1047-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="c1047-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="c1047-121">Optional element.</span></span><br /><br /> <span data-ttu-id="c1047-122">Adiciona uma linha em branco para a exibição do controle.</span><span class="sxs-lookup"><span data-stu-id="c1047-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="c1047-123">Elemento de texto para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c1047-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="c1047-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="c1047-124">Optional element.</span></span><br /><br /> <span data-ttu-id="c1047-125">Especifica o texto adicional para os dados apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="c1047-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c1047-126">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="c1047-126">Parent Elements</span></span>

|<span data-ttu-id="c1047-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="c1047-127">Element</span></span>|<span data-ttu-id="c1047-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1047-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1047-129">Elemento de CustomEntry para CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c1047-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="c1047-130">Fornece uma definição de vista do controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="c1047-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c1047-131">Observações</span><span class="sxs-lookup"><span data-stu-id="c1047-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="c1047-132">Veja Também</span><span class="sxs-lookup"><span data-stu-id="c1047-132">See Also</span></span>

[<span data-ttu-id="c1047-133">Elemento de CustomEntry para CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c1047-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="c1047-134">Elemento de ExpressionBinding para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c1047-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="c1047-135">Elemento de quadro para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c1047-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="c1047-136">Elemento de nova linha para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c1047-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="c1047-137">Elemento de texto para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="c1047-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="c1047-138">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c1047-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
