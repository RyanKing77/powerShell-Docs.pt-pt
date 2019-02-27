---
title: Elemento de ItemSelectionCondition para ExpressionBinding para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844808"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="a20eb-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) (Elemento ItemSelectionCondition para ExpressionBinding para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="a20eb-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="a20eb-103">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="a20eb-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="a20eb-104">Não existe nenhum limite para o número de condições de seleção que pode ser especificado para um item de controlo.</span><span class="sxs-lookup"><span data-stu-id="a20eb-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="a20eb-105">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="a20eb-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="a20eb-106">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de CustomItem GroupBy (formato) para CustomEntry para o elemento de ExpressionBinding GroupBy (formato) para CustomItem para o elemento de ItemSelectionCondition GroupBy (formato) para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="a20eb-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a20eb-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a20eb-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a20eb-108">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="a20eb-108">Attributes and Elements</span></span>

<span data-ttu-id="a20eb-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="a20eb-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a20eb-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="a20eb-110">Attributes</span></span>

<span data-ttu-id="a20eb-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a20eb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a20eb-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="a20eb-112">Child Elements</span></span>

|<span data-ttu-id="a20eb-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="a20eb-113">Element</span></span>|<span data-ttu-id="a20eb-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a20eb-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a20eb-115">Elemento de PropertyName para ItemSelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="a20eb-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="a20eb-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a20eb-116">Optional element.</span></span><br /><br /> <span data-ttu-id="a20eb-117">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="a20eb-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a20eb-118">Elemento de ScriptBlock para ItemSelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="a20eb-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="a20eb-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a20eb-119">Optional element.</span></span><br /><br /> <span data-ttu-id="a20eb-120">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="a20eb-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a20eb-121">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="a20eb-121">Parent Elements</span></span>

|<span data-ttu-id="a20eb-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="a20eb-122">Element</span></span>|<span data-ttu-id="a20eb-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="a20eb-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a20eb-124">Elemento de ExpressionBinding para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="a20eb-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="a20eb-125">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="a20eb-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a20eb-126">Observações</span><span class="sxs-lookup"><span data-stu-id="a20eb-126">Remarks</span></span>

<span data-ttu-id="a20eb-127">Pode especificar um nome de propriedade ou um script para esta condição, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="a20eb-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="a20eb-128">Veja Também</span><span class="sxs-lookup"><span data-stu-id="a20eb-128">See Also</span></span>

[<span data-ttu-id="a20eb-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a20eb-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="a20eb-130">Elemento de ExpressionBinding para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="a20eb-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
