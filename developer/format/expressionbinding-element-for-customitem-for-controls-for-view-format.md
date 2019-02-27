---
title: Elemento de ExpressionBinding para CustomItem para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848420"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="89fed-102">ExpressionBinding Element for CustomItem for Controls for View (Format) (Elemento ExpressionBinding para CustomItem para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="89fed-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="89fed-103">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="89fed-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="89fed-104">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="89fed-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="89fed-105">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) CustomItem elemento para CustomEntry para controles para exibição (formato) ExpressionBinding elemento para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="89fed-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="89fed-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89fed-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="89fed-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="89fed-107">Attributes and Elements</span></span>

<span data-ttu-id="89fed-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ExpressionBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="89fed-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="89fed-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="89fed-109">Attributes</span></span>

<span data-ttu-id="89fed-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="89fed-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="89fed-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="89fed-111">Child Elements</span></span>

|<span data-ttu-id="89fed-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="89fed-112">Element</span></span>|<span data-ttu-id="89fed-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="89fed-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="89fed-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="89fed-114">Optional element.</span></span><br /><br /> <span data-ttu-id="89fed-115">Define um controle que é utilizado por este controlo.</span><span class="sxs-lookup"><span data-stu-id="89fed-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="89fed-116">Elemento de CustomControlName para ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="89fed-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="89fed-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="89fed-117">Optional element.</span></span><br /><br /> <span data-ttu-id="89fed-118">Especifica o nome de um controle comum ou um controle de exibição.</span><span class="sxs-lookup"><span data-stu-id="89fed-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="89fed-119">Elemento de EnumerateCollection para ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="89fed-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="89fed-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="89fed-120">Optional element.</span></span><br /><br /> <span data-ttu-id="89fed-121">Especifica que os elementos de coleções são apresentados.</span><span class="sxs-lookup"><span data-stu-id="89fed-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="89fed-122">Elemento de ItemSelectionCondition de ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="89fed-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="89fed-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="89fed-123">Optional element.</span></span><br /><br /> <span data-ttu-id="89fed-124">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="89fed-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="89fed-125">Elemento de PropertyName para ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="89fed-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="89fed-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="89fed-126">Optional element.</span></span><br /><br /> <span data-ttu-id="89fed-127">Especifica a propriedade de .NET cujo valor é apresentado pelo controle.</span><span class="sxs-lookup"><span data-stu-id="89fed-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="89fed-128">Elemento de ScriptBlock para ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="89fed-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="89fed-129">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="89fed-129">Optional element.</span></span><br /><br /> <span data-ttu-id="89fed-130">Especifica o script cujo valor é apresentado pelo controle.</span><span class="sxs-lookup"><span data-stu-id="89fed-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="89fed-131">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="89fed-131">Parent Elements</span></span>

|<span data-ttu-id="89fed-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="89fed-132">Element</span></span>|<span data-ttu-id="89fed-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="89fed-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="89fed-134">Elemento de CustomItem para CustomEntry para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="89fed-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="89fed-135">Define os dados que são apresentados pelo controle e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="89fed-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="89fed-136">Observações</span><span class="sxs-lookup"><span data-stu-id="89fed-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="89fed-137">Veja Também</span><span class="sxs-lookup"><span data-stu-id="89fed-137">See Also</span></span>

[<span data-ttu-id="89fed-138">Elemento de CustomItem para CustomEntry para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="89fed-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="89fed-139">Elemento de CustomControlName para ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="89fed-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="89fed-140">Elemento de EnumerateCollection para ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="89fed-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="89fed-141">Elemento de ItemSelectionCondition de ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="89fed-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="89fed-142">Elemento de PropertyName para ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="89fed-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="89fed-143">Elemento de ScriptBlock para ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="89fed-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="89fed-144">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="89fed-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
