---
title: Elemento de ScriptBlock para ItemSeclectionCondition para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850912"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="a934f-102">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format) (Elemento ScriptBlock para ItemSelectionCondition para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="a934f-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="a934f-103">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="a934f-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="a934f-104">Quando esse script é avaliado para `true`, a condição é cumprida e o controle é usado.</span><span class="sxs-lookup"><span data-stu-id="a934f-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="a934f-105">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="a934f-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="a934f-106">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de CustomItem de configuração (formato) para CustomEntry para controles para o elemento de configuração ExpressionBinding para CustomItem para controles de configuração (formato) Elemento de ItemSelectionCondition para ExpressionBinding para controles para o elemento de ScriptBlock de configuração (formato) para ItemSelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a934f-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a934f-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a934f-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a934f-108">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="a934f-108">Attributes and Elements</span></span>

<span data-ttu-id="a934f-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="a934f-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a934f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="a934f-110">Attributes</span></span>

<span data-ttu-id="a934f-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a934f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a934f-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="a934f-112">Child Elements</span></span>

<span data-ttu-id="a934f-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a934f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a934f-114">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="a934f-114">Parent Elements</span></span>

|<span data-ttu-id="a934f-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="a934f-115">Element</span></span>|<span data-ttu-id="a934f-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="a934f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a934f-117">Elemento de ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a934f-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="a934f-118">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="a934f-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a934f-119">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="a934f-119">Text Value</span></span>

<span data-ttu-id="a934f-120">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="a934f-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="a934f-121">Observações</span><span class="sxs-lookup"><span data-stu-id="a934f-121">Remarks</span></span>

<span data-ttu-id="a934f-122">Se este elemento é utilizado, não é possível especificar a [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) elemento ao definir a condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="a934f-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="a934f-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="a934f-123">See Also</span></span>

[<span data-ttu-id="a934f-124">Elemento de PropertyName para ItemSeclectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a934f-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="a934f-125">Elemento de ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a934f-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="a934f-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a934f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
