---
title: GroupBy elemento para a exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849281"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="dc2e8-102">GroupBy Element for View (Format) (Elemento GroupBy para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="dc2e8-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="dc2e8-103">Define a forma como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="dc2e8-104">Este elemento é utilizado ao definir uma tabela, a lista, o modo de exibição control ampla ou personalizada.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="dc2e8-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="dc2e8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dc2e8-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc2e8-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dc2e8-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="dc2e8-107">Attributes and Elements</span></span>

<span data-ttu-id="dc2e8-108">As secções seguintes descrevem os atributos e elementos principais elementos filho.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="dc2e8-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="dc2e8-109">Attributes</span></span>

<span data-ttu-id="dc2e8-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dc2e8-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="dc2e8-111">Child Elements</span></span>

|<span data-ttu-id="dc2e8-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="dc2e8-112">Element</span></span>|<span data-ttu-id="dc2e8-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc2e8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dc2e8-114">Elemento de CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="dc2e8-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="dc2e8-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-115">Optional element.</span></span><br /><br /> <span data-ttu-id="dc2e8-116">Define o controlo personalizado que apresentar novos grupos.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="dc2e8-117">Elemento de CustomControlName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="dc2e8-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="dc2e8-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-118">Optional element.</span></span><br /><br /> <span data-ttu-id="dc2e8-119">Especifica o nome de um controlo que é utilizado para apresentar o novo grupo.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="dc2e8-120">Elemento da etiqueta para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="dc2e8-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="dc2e8-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-121">Optional element.</span></span><br /><br /> <span data-ttu-id="dc2e8-122">Especifica uma etiqueta que é apresentada quando for detetado um novo grupo.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="dc2e8-123">Elemento de PropertyName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="dc2e8-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="dc2e8-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-124">Optional element.</span></span><br /><br /> <span data-ttu-id="dc2e8-125">Especifica a propriedade .NET iniciada a um novo grupo sempre que seu valor é alterado.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="dc2e8-126">Elemento de ScriptBlock para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="dc2e8-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="dc2e8-127">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-127">Optional element.</span></span><br /><br /> <span data-ttu-id="dc2e8-128">Especifica o script que inicia um novo grupo sempre que seu valor é alterado.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dc2e8-129">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="dc2e8-129">Parent Elements</span></span>

|<span data-ttu-id="dc2e8-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="dc2e8-130">Element</span></span>|<span data-ttu-id="dc2e8-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc2e8-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dc2e8-132">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="dc2e8-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="dc2e8-133">Define uma vista que apresente um ou mais objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dc2e8-134">Observações</span><span class="sxs-lookup"><span data-stu-id="dc2e8-134">Remarks</span></span>

<span data-ttu-id="dc2e8-135">Ao definir como é apresentado um novo grupo de objetos, tem de especificar a propriedade ou um script que iniciará o novo grupo; No entanto, não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="dc2e8-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc2e8-136">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="dc2e8-136">See Also</span></span>

[<span data-ttu-id="dc2e8-137">Elemento de CustomControlName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="dc2e8-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="dc2e8-138">Elemento da etiqueta para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="dc2e8-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="dc2e8-139">Elemento de PropertyName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="dc2e8-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="dc2e8-140">Elemento de ScriptBlock para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="dc2e8-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="dc2e8-141">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="dc2e8-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="dc2e8-142">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="dc2e8-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
