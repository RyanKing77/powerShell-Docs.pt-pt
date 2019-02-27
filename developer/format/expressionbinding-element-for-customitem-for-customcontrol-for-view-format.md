---
title: Elemento de ExpressionBinding para CustomItem para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850093"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="9f31b-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format) (Elemento ExpressionBinding para CustomItem para CustomControl para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="9f31b-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="9f31b-103">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="9f31b-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="9f31b-104">Este elemento é utilizado ao definir uma vista de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="9f31b-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="9f31b-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento de configuração para o modo de exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para CustomControl para exibição ( Elemento de CustomItem de formato) para CustomEntry para CustomControl para exibição (formato) ExpressionBinding elemento para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="9f31b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9f31b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f31b-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="9f31b-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="9f31b-107">Attributes and Elements</span></span>

<span data-ttu-id="9f31b-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ExpressionBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="9f31b-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9f31b-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="9f31b-109">Attributes</span></span>

<span data-ttu-id="9f31b-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9f31b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9f31b-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="9f31b-111">Child Elements</span></span>

|<span data-ttu-id="9f31b-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="9f31b-112">Element</span></span>|<span data-ttu-id="9f31b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f31b-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="9f31b-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9f31b-114">Optional element.</span></span><br /><br /> <span data-ttu-id="9f31b-115">Define um controle que é utilizado por este controlo.</span><span class="sxs-lookup"><span data-stu-id="9f31b-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="9f31b-116">Elemento de CustomControlName para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="9f31b-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="9f31b-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9f31b-117">Optional element.</span></span><br /><br /> <span data-ttu-id="9f31b-118">Especifica o nome de um controle comum ou um controle de exibição.</span><span class="sxs-lookup"><span data-stu-id="9f31b-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="9f31b-119">Elemento de EnumerateCollection para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="9f31b-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="9f31b-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9f31b-120">Optional element.</span></span><br /><br /> <span data-ttu-id="9f31b-121">Especificar que os elementos de coleções são apresentados.</span><span class="sxs-lookup"><span data-stu-id="9f31b-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="9f31b-122">Elemento de ItemSelectionCondition para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="9f31b-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="9f31b-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9f31b-123">Optional element.</span></span><br /><br /> <span data-ttu-id="9f31b-124">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="9f31b-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="9f31b-125">Elemento de PropertyName para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="9f31b-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="9f31b-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9f31b-126">Optional element.</span></span><br /><br /> <span data-ttu-id="9f31b-127">Especifica a propriedade de .NET cujo valor é apresentado pelo controle.</span><span class="sxs-lookup"><span data-stu-id="9f31b-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="9f31b-128">Elemento de ScriptBlock para ExpressionBinding para CustomCustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="9f31b-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="9f31b-129">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="9f31b-129">Optional element.</span></span><br /><br /> <span data-ttu-id="9f31b-130">Especifica o script cujo valor é apresentado pelo controle.</span><span class="sxs-lookup"><span data-stu-id="9f31b-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9f31b-131">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="9f31b-131">Parent Elements</span></span>

|<span data-ttu-id="9f31b-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="9f31b-132">Element</span></span>|<span data-ttu-id="9f31b-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f31b-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9f31b-134">Elemento de CustomItem para CustomEntry para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="9f31b-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="9f31b-135">Define os dados que são apresentados pela vista do controle personalizado e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="9f31b-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9f31b-136">Observações</span><span class="sxs-lookup"><span data-stu-id="9f31b-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="9f31b-137">Veja Também</span><span class="sxs-lookup"><span data-stu-id="9f31b-137">See Also</span></span>

[<span data-ttu-id="9f31b-138">Elemento de CustomControlName para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="9f31b-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9f31b-139">Elemento de EnumerateCollection para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="9f31b-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9f31b-140">Elemento de ItemSelectionCondition para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="9f31b-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="9f31b-141">Elemento de PropertyName para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="9f31b-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9f31b-142">Elemento de ScriptBlock para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="9f31b-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9f31b-143">Elemento de CustomItem para CustomEntry para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="9f31b-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9f31b-144">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9f31b-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
