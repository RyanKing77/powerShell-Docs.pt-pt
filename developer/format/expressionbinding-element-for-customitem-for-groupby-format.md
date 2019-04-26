---
title: Elemento de ExpressionBinding para CustomItem para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065908"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="b88d3-102">ExpressionBinding Element for CustomItem for GroupBy (Format) (Elemento ExpressionBinding para CustomItem para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="b88d3-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="b88d3-103">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="b88d3-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="b88d3-104">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="b88d3-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b88d3-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de CustomItem GroupBy (formato) para CustomEntry para o elemento de ExpressionBinding GroupBy (formato) para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b88d3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b88d3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b88d3-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b88d3-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b88d3-107">Attributes and Elements</span></span>

<span data-ttu-id="b88d3-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ExpressionBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="b88d3-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b88d3-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b88d3-109">Attributes</span></span>

<span data-ttu-id="b88d3-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b88d3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b88d3-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="b88d3-111">Child Elements</span></span>

|<span data-ttu-id="b88d3-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b88d3-112">Element</span></span>|<span data-ttu-id="b88d3-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b88d3-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="b88d3-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b88d3-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b88d3-115">Define um controle que é utilizado por este controlo.</span><span class="sxs-lookup"><span data-stu-id="b88d3-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="b88d3-116">Elemento de CustomControlName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b88d3-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b88d3-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b88d3-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b88d3-118">Especifica o nome de um controle comum ou um controle de exibição.</span><span class="sxs-lookup"><span data-stu-id="b88d3-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="b88d3-119">[Elemento de EnumerateCollection para ExpressionBinding para GroupBy (formato)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection elemento para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b88d3-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="b88d3-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b88d3-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b88d3-121">Especificar que os elementos de coleções são apresentados.</span><span class="sxs-lookup"><span data-stu-id="b88d3-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="b88d3-122">Elemento de ItemSelectionCondition para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b88d3-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b88d3-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b88d3-123">Optional element.</span></span><br /><br /> <span data-ttu-id="b88d3-124">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="b88d3-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="b88d3-125">Elemento de PropertyName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b88d3-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b88d3-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b88d3-126">Optional element.</span></span><br /><br /> <span data-ttu-id="b88d3-127">Especifica a propriedade de .NET cujo valor é apresentado pelo controle.</span><span class="sxs-lookup"><span data-stu-id="b88d3-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="b88d3-128">Elemento de ScriptBlock para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b88d3-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b88d3-129">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b88d3-129">Optional element.</span></span><br /><br /> <span data-ttu-id="b88d3-130">Especifica o script cujo valor é apresentado pelo controle.</span><span class="sxs-lookup"><span data-stu-id="b88d3-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b88d3-131">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="b88d3-131">Parent Elements</span></span>

|<span data-ttu-id="b88d3-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="b88d3-132">Element</span></span>|<span data-ttu-id="b88d3-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="b88d3-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b88d3-134">Elemento de CustomItem para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b88d3-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="b88d3-135">Define os dados que são apresentados pela vista do controle personalizado e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="b88d3-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b88d3-136">Veja Também</span><span class="sxs-lookup"><span data-stu-id="b88d3-136">See Also</span></span>

[<span data-ttu-id="b88d3-137">Elemento de CustomControlName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b88d3-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b88d3-138">Elemento de EnumerateCollection para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b88d3-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b88d3-139">Elemento de ItemSelectionCondition para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b88d3-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b88d3-140">Elemento de PropertyName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b88d3-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b88d3-141">Elemento de ScriptBlock para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b88d3-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b88d3-142">Elemento de CustomItem para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="b88d3-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="b88d3-143">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b88d3-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
