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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846061"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="f3b68-102">ExpressionBinding Element for CustomItem for GroupBy (Format) (Elemento ExpressionBinding para CustomItem para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="f3b68-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="f3b68-103">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="f3b68-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="f3b68-104">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="f3b68-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="f3b68-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de CustomItem GroupBy (formato) para CustomEntry para o elemento de ExpressionBinding GroupBy (formato) para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f3b68-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f3b68-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3b68-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="f3b68-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="f3b68-107">Attributes and Elements</span></span>

<span data-ttu-id="f3b68-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ExpressionBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="f3b68-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f3b68-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f3b68-109">Attributes</span></span>

<span data-ttu-id="f3b68-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f3b68-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f3b68-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="f3b68-111">Child Elements</span></span>

|<span data-ttu-id="f3b68-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="f3b68-112">Element</span></span>|<span data-ttu-id="f3b68-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3b68-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="f3b68-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f3b68-114">Optional element.</span></span><br /><br /> <span data-ttu-id="f3b68-115">Define um controle que é utilizado por este controlo.</span><span class="sxs-lookup"><span data-stu-id="f3b68-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="f3b68-116">Elemento de CustomControlName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f3b68-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="f3b68-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f3b68-117">Optional element.</span></span><br /><br /> <span data-ttu-id="f3b68-118">Especifica o nome de um controle comum ou um controle de exibição.</span><span class="sxs-lookup"><span data-stu-id="f3b68-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="f3b68-119">[Elemento de EnumerateCollection para ExpressionBinding para GroupBy (formato)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection elemento para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f3b68-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="f3b68-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f3b68-120">Optional element.</span></span><br /><br /> <span data-ttu-id="f3b68-121">Especificar que os elementos de coleções são apresentados.</span><span class="sxs-lookup"><span data-stu-id="f3b68-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="f3b68-122">Elemento de ItemSelectionCondition para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f3b68-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="f3b68-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f3b68-123">Optional element.</span></span><br /><br /> <span data-ttu-id="f3b68-124">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="f3b68-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="f3b68-125">Elemento de PropertyName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f3b68-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="f3b68-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f3b68-126">Optional element.</span></span><br /><br /> <span data-ttu-id="f3b68-127">Especifica a propriedade de .NET cujo valor é apresentado pelo controle.</span><span class="sxs-lookup"><span data-stu-id="f3b68-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="f3b68-128">Elemento de ScriptBlock para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f3b68-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="f3b68-129">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f3b68-129">Optional element.</span></span><br /><br /> <span data-ttu-id="f3b68-130">Especifica o script cujo valor é apresentado pelo controle.</span><span class="sxs-lookup"><span data-stu-id="f3b68-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f3b68-131">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="f3b68-131">Parent Elements</span></span>

|<span data-ttu-id="f3b68-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="f3b68-132">Element</span></span>|<span data-ttu-id="f3b68-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3b68-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f3b68-134">Elemento de CustomItem para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f3b68-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="f3b68-135">Define os dados que são apresentados pela vista do controle personalizado e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="f3b68-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="f3b68-136">Veja Também</span><span class="sxs-lookup"><span data-stu-id="f3b68-136">See Also</span></span>

[<span data-ttu-id="f3b68-137">Elemento de CustomControlName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f3b68-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="f3b68-138">Elemento de EnumerateCollection para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f3b68-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="f3b68-139">Elemento de ItemSelectionCondition para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f3b68-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="f3b68-140">Elemento de PropertyName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f3b68-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="f3b68-141">Elemento de ScriptBlock para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f3b68-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="f3b68-142">Elemento de CustomItem para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f3b68-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="f3b68-143">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f3b68-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
