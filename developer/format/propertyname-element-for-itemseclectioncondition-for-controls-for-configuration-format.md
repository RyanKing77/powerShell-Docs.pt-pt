---
title: Elemento de PropertyName para ItemSeclectionCondition para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850261"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="0b1ff-102">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format) (Elemento PropertyName para ItemSelectionCondition para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="0b1ff-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0b1ff-103">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="0b1ff-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="0b1ff-104">Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e o controle é usado.</span><span class="sxs-lookup"><span data-stu-id="0b1ff-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="0b1ff-105">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="0b1ff-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0b1ff-106">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de CustomItem de configuração (formato) para CustomEntry para controles para o elemento de configuração ExpressionBinding para CustomItem para controles de configuração (formato) Elemento de ItemSelectionCondition para ExpressionBinding para controles para o elemento de PropertyName de configuração (formato) para ItemSeclectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="0b1ff-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0b1ff-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b1ff-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0b1ff-108">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="0b1ff-108">Attributes and Elements</span></span>

<span data-ttu-id="0b1ff-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="0b1ff-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0b1ff-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0b1ff-110">Attributes</span></span>

<span data-ttu-id="0b1ff-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0b1ff-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0b1ff-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="0b1ff-112">Child Elements</span></span>

<span data-ttu-id="0b1ff-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0b1ff-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0b1ff-114">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="0b1ff-114">Parent Elements</span></span>

|<span data-ttu-id="0b1ff-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="0b1ff-115">Element</span></span>|<span data-ttu-id="0b1ff-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="0b1ff-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0b1ff-117">Elemento de ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="0b1ff-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="0b1ff-118">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="0b1ff-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0b1ff-119">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="0b1ff-119">Text Value</span></span>

<span data-ttu-id="0b1ff-120">Especifique o nome da propriedade .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="0b1ff-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="0b1ff-121">Observações</span><span class="sxs-lookup"><span data-stu-id="0b1ff-121">Remarks</span></span>

<span data-ttu-id="0b1ff-122">Se este elemento é utilizado, não é possível especificar a [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) elemento ao definir a condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="0b1ff-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b1ff-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="0b1ff-123">See Also</span></span>

[<span data-ttu-id="0b1ff-124">Elemento de ScriptBlock para ItemSeclectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="0b1ff-124">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0b1ff-125">Elemento de ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="0b1ff-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="0b1ff-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b1ff-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
