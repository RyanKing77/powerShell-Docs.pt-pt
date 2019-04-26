---
title: Elemento de PropertyName para ItemSelectionCondition para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075856"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="53128-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format) (Elemento PropertyName para ItemSelectionCondition para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="53128-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="53128-103">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="53128-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="53128-104">Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e o controle é usado.</span><span class="sxs-lookup"><span data-stu-id="53128-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="53128-105">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="53128-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="53128-106">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) CustomItem elemento para CustomEntry para controles para exibição (formato) ExpressionBinding elemento para CustomItem para controles para exibição (formato) Elemento de ItemSelectionCondition de ExpressionBinding para controles para exibição (formato) PropertyName elemento para ItemSelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="53128-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="53128-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53128-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="53128-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="53128-108">Attributes and Elements</span></span>

<span data-ttu-id="53128-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="53128-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="53128-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="53128-110">Attributes</span></span>

<span data-ttu-id="53128-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="53128-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="53128-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="53128-112">Child Elements</span></span>

<span data-ttu-id="53128-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="53128-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="53128-114">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="53128-114">Parent Elements</span></span>

|<span data-ttu-id="53128-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="53128-115">Element</span></span>|<span data-ttu-id="53128-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="53128-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="53128-117">Elemento de ItemSelectionCondition de ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="53128-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="53128-118">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="53128-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="53128-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="53128-119">Text Value</span></span>

<span data-ttu-id="53128-120">Especifique o nome da propriedade .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="53128-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="53128-121">Observações</span><span class="sxs-lookup"><span data-stu-id="53128-121">Remarks</span></span>

<span data-ttu-id="53128-122">Se este elemento é utilizado, não é possível especificar a [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) elemento ao definir a condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="53128-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="53128-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="53128-123">See Also</span></span>

[<span data-ttu-id="53128-124">Elemento de ScriptBlock para ItemSelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="53128-124">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="53128-125">Elemento de ItemSelectionCondition de ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="53128-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="53128-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="53128-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
