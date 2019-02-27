---
title: Elemento de ExpressionBinding para CustomItem para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846208"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="e5330-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format) (Elemento ExpressionBinding para CustomItem para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="e5330-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e5330-103">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="e5330-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="e5330-104">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="e5330-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e5330-105">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de CustomItem de configuração (formato) para CustomEntry para controles para o elemento de configuração ExpressionBinding para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e5330-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5330-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5330-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e5330-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="e5330-107">Attributes and Elements</span></span>

<span data-ttu-id="e5330-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ExpressionBinding` elemento.</span><span class="sxs-lookup"><span data-stu-id="e5330-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5330-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="e5330-109">Attributes</span></span>

<span data-ttu-id="e5330-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e5330-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5330-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="e5330-111">Child Elements</span></span>

|<span data-ttu-id="e5330-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="e5330-112">Element</span></span>|<span data-ttu-id="e5330-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5330-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="e5330-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e5330-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e5330-115">Define um controle que é utilizado por este controlo.</span><span class="sxs-lookup"><span data-stu-id="e5330-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="e5330-116">Elemento de CustomControlName para ExpressionBinding para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e5330-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e5330-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e5330-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e5330-118">Especifica o nome de um controle comum ou um controle de exibição.</span><span class="sxs-lookup"><span data-stu-id="e5330-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="e5330-119">Elemento de EnumerateCollection para ExpressionBinding para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e5330-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e5330-120">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e5330-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e5330-121">Especificar que os elementos de coleções são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="e5330-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="e5330-122">Elemento de ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e5330-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e5330-123">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e5330-123">Optional element.</span></span><br /><br /> <span data-ttu-id="e5330-124">Define a condição de que tem de existir para este controlo comum a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="e5330-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="e5330-125">Elemento de PropertyName para ExpressionBinding para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e5330-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e5330-126">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e5330-126">Optional element.</span></span><br /><br /> <span data-ttu-id="e5330-127">Especifica a propriedade de .NET cujo valor é apresentado pelo controle comum.</span><span class="sxs-lookup"><span data-stu-id="e5330-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="e5330-128">Elemento de ScriptBlock para ExpressionBinding para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e5330-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e5330-129">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e5330-129">Optional element.</span></span><br /><br /> <span data-ttu-id="e5330-130">Especifica o script cujo valor é apresentado pelo controle comum.</span><span class="sxs-lookup"><span data-stu-id="e5330-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e5330-131">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="e5330-131">Parent Elements</span></span>

|<span data-ttu-id="e5330-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="e5330-132">Element</span></span>|<span data-ttu-id="e5330-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="e5330-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5330-134">Elemento de CustomItem para CustomEntry para controles de configuração</span><span class="sxs-lookup"><span data-stu-id="e5330-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="e5330-135">Define os dados que são apresentados pela vista do controle personalizado e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="e5330-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5330-136">Observações</span><span class="sxs-lookup"><span data-stu-id="e5330-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e5330-137">Veja Também</span><span class="sxs-lookup"><span data-stu-id="e5330-137">See Also</span></span>

[<span data-ttu-id="e5330-138">Elemento de CustomItem para CustomEntry para controles de configuração</span><span class="sxs-lookup"><span data-stu-id="e5330-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="e5330-139">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5330-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
