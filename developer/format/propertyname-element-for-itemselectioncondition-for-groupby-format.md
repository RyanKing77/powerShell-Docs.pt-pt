---
title: Elemento de PropertyName para ItemSelectionCondition para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064769"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="09d1c-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format) (Elemento PropertyName para ItemSelectionCondition para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="09d1c-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="09d1c-103">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="09d1c-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="09d1c-104">Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e o controle é usado.</span><span class="sxs-lookup"><span data-stu-id="09d1c-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="09d1c-105">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="09d1c-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="09d1c-106">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de CustomItem GroupBy (formato) para CustomEntry para o elemento de ExpressionBinding GroupBy (formato) para CustomItem para o elemento de ItemSelectionCondition GroupBy (formato) para ExpressionBinding para o elemento de PropertyName GroupBy (formato) para ItemSelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="09d1c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="09d1c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="09d1c-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="09d1c-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="09d1c-108">Attributes and Elements</span></span>

<span data-ttu-id="09d1c-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="09d1c-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="09d1c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="09d1c-110">Attributes</span></span>

<span data-ttu-id="09d1c-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="09d1c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="09d1c-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="09d1c-112">Child Elements</span></span>

<span data-ttu-id="09d1c-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="09d1c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="09d1c-114">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="09d1c-114">Parent Elements</span></span>

|<span data-ttu-id="09d1c-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="09d1c-115">Element</span></span>|<span data-ttu-id="09d1c-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="09d1c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="09d1c-117">Elemento de ItemSelectionCondition para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="09d1c-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="09d1c-118">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="09d1c-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="09d1c-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="09d1c-119">Text Value</span></span>

<span data-ttu-id="09d1c-120">Especifique o nome da propriedade .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="09d1c-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="09d1c-121">Observações</span><span class="sxs-lookup"><span data-stu-id="09d1c-121">Remarks</span></span>

<span data-ttu-id="09d1c-122">Se este elemento é utilizado, não é possível especificar a [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) elemento ao definir a condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="09d1c-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="09d1c-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="09d1c-123">See Also</span></span>

[<span data-ttu-id="09d1c-124">Elemento de ScriptBlock para ItemSelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="09d1c-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="09d1c-125">Elemento de ItemSelectionCondition para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="09d1c-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="09d1c-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="09d1c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
