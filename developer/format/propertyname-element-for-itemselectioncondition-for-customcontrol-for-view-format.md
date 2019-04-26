---
title: Elemento de PropertyName para ItemSelectionCondition para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064871"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="590b1-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format) (Elemento PropertyName para ItemSelectionCondition para CustomControl para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="590b1-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="590b1-103">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="590b1-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="590b1-104">Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e o controle é usado.</span><span class="sxs-lookup"><span data-stu-id="590b1-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="590b1-105">Este elemento é utilizado ao definir uma vista de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="590b1-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="590b1-106">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para exibição (formato) CustomItem elemento para CustomEntry para exibição (formato) ExpressionBinding elemento para CustomItem para CustomControl para exibição (formato) ItemSelectionCondition elemento para a ligação de expressão para CustomControl para exibição (formato) PropertyName elemento para ItemSelectionCondition para CustomControl para exibição (formato</span><span class="sxs-lookup"><span data-stu-id="590b1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="590b1-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="590b1-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="590b1-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="590b1-108">Attributes and Elements</span></span>

<span data-ttu-id="590b1-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="590b1-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="590b1-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="590b1-110">Attributes</span></span>

<span data-ttu-id="590b1-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="590b1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="590b1-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="590b1-112">Child Elements</span></span>

<span data-ttu-id="590b1-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="590b1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="590b1-114">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="590b1-114">Parent Elements</span></span>

|<span data-ttu-id="590b1-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="590b1-115">Element</span></span>|<span data-ttu-id="590b1-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="590b1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="590b1-117">Elemento de ItemSelectionCondition para enlace de expressão para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="590b1-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="590b1-118">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="590b1-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="590b1-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="590b1-119">Text Value</span></span>

<span data-ttu-id="590b1-120">Especifique o nome da propriedade .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="590b1-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="590b1-121">Observações</span><span class="sxs-lookup"><span data-stu-id="590b1-121">Remarks</span></span>

<span data-ttu-id="590b1-122">Se este elemento é utilizado, não é possível especificar a [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) elemento ao definir a condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="590b1-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="590b1-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="590b1-123">See Also</span></span>

[<span data-ttu-id="590b1-124">Elemento de ScriptBlock para ItemSelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="590b1-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="590b1-125">Elemento de ItemSelectionCondition para enlace de expressão para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="590b1-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="590b1-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="590b1-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
