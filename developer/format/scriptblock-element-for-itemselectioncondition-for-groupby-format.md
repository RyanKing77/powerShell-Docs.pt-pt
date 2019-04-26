---
title: Elemento de ScriptBlock para ItemSelectionCondition para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064548"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="76e40-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format) (Elemento ScriptBlock para ItemSelectionCondition para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="76e40-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="76e40-103">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="76e40-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="76e40-104">Quando esse script é avaliado para `true`, a condição é cumprida e o controle é usado.</span><span class="sxs-lookup"><span data-stu-id="76e40-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="76e40-105">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="76e40-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="76e40-106">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de CustomItem GroupBy (formato) para CustomEntry para o elemento de ExpressionBinding GroupBy (formato) para CustomItem para o elemento de ItemSelectionCondition GroupBy (formato) para ExpressionBinding para o elemento de ScriptBlock GroupBy (formato) para ItemSelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="76e40-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="76e40-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76e40-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="76e40-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="76e40-108">Attributes and Elements</span></span>

<span data-ttu-id="76e40-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="76e40-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="76e40-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="76e40-110">Attributes</span></span>

<span data-ttu-id="76e40-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="76e40-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="76e40-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="76e40-112">Child Elements</span></span>

<span data-ttu-id="76e40-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="76e40-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="76e40-114">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="76e40-114">Parent Elements</span></span>

|<span data-ttu-id="76e40-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="76e40-115">Element</span></span>|<span data-ttu-id="76e40-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="76e40-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="76e40-117">Elemento de ItemSelectionCondition para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="76e40-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="76e40-118">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="76e40-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="76e40-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="76e40-119">Text Value</span></span>

<span data-ttu-id="76e40-120">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="76e40-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="76e40-121">Observações</span><span class="sxs-lookup"><span data-stu-id="76e40-121">Remarks</span></span>

<span data-ttu-id="76e40-122">Se este elemento é utilizado, não é possível especificar a [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) elemento ao definir a condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="76e40-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="76e40-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="76e40-123">See Also</span></span>

[<span data-ttu-id="76e40-124">Elemento de ItemSelectionCondition para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="76e40-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="76e40-125">Elemento de PropertyName para ItemSelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="76e40-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="76e40-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="76e40-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
