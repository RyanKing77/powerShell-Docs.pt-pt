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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064910"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="e050a-102">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format) (Elemento PropertyName para ItemSelectionCondition para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="e050a-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e050a-103">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="e050a-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="e050a-104">Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e o controle é usado.</span><span class="sxs-lookup"><span data-stu-id="e050a-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="e050a-105">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="e050a-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e050a-106">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de CustomItem de configuração (formato) para CustomEntry para controles para o elemento de configuração ExpressionBinding para CustomItem para controles de configuração (formato) Elemento de ItemSelectionCondition para ExpressionBinding para controles para o elemento de PropertyName de configuração (formato) para ItemSeclectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e050a-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e050a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e050a-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e050a-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e050a-108">Attributes and Elements</span></span>

<span data-ttu-id="e050a-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="e050a-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e050a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e050a-110">Attributes</span></span>

<span data-ttu-id="e050a-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e050a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e050a-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="e050a-112">Child Elements</span></span>

<span data-ttu-id="e050a-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e050a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e050a-114">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="e050a-114">Parent Elements</span></span>

|<span data-ttu-id="e050a-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="e050a-115">Element</span></span>|<span data-ttu-id="e050a-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="e050a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e050a-117">Elemento de ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e050a-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e050a-118">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="e050a-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e050a-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="e050a-119">Text Value</span></span>

<span data-ttu-id="e050a-120">Especifique o nome da propriedade .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="e050a-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="e050a-121">Observações</span><span class="sxs-lookup"><span data-stu-id="e050a-121">Remarks</span></span>

<span data-ttu-id="e050a-122">Se este elemento é utilizado, não é possível especificar a [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) elemento ao definir a condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="e050a-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="e050a-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="e050a-123">See Also</span></span>

[<span data-ttu-id="e050a-124">Elemento de ScriptBlock para ItemSeclectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e050a-124">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="e050a-125">Elemento de ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e050a-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="e050a-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e050a-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
