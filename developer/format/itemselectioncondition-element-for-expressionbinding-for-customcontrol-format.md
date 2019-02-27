---
title: Elemento de ItemSelectionCondition para ExpressionBinding para CustomControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848343"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="e3ac1-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format) (Elemento ItemSelectionCondition para ExpressionBinding para CustomControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="e3ac1-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="e3ac1-103">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="e3ac1-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="e3ac1-104">Não existe nenhum limite para o número de condições de seleção que pode ser especificado para um item de controlo.</span><span class="sxs-lookup"><span data-stu-id="e3ac1-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="e3ac1-105">Este elemento é utilizado ao definir uma vista de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="e3ac1-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="e3ac1-106">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para exibição (formato) CustomItem elemento para CustomEntry para exibição (formato) ExpressionBinding elemento para CustomItem para CustomControl para exibição (formato) ItemSelectionCondition elemento para a ligação de expressão para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="e3ac1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3ac1-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3ac1-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3ac1-108">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="e3ac1-108">Attributes and Elements</span></span>

<span data-ttu-id="e3ac1-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="e3ac1-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3ac1-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e3ac1-110">Attributes</span></span>

<span data-ttu-id="e3ac1-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e3ac1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3ac1-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="e3ac1-112">Child Elements</span></span>

|<span data-ttu-id="e3ac1-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="e3ac1-113">Element</span></span>|<span data-ttu-id="e3ac1-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3ac1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3ac1-115">Elemento de PropertyName para ItemSelectionCondition para CustomControl para exibição (formato</span><span class="sxs-lookup"><span data-stu-id="e3ac1-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="e3ac1-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e3ac1-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e3ac1-117">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="e3ac1-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="e3ac1-118">Elemento de ScriptBlock para ItemSelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="e3ac1-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="e3ac1-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e3ac1-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e3ac1-120">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="e3ac1-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e3ac1-121">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="e3ac1-121">Parent Elements</span></span>

|<span data-ttu-id="e3ac1-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="e3ac1-122">Element</span></span>|<span data-ttu-id="e3ac1-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3ac1-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3ac1-124">Elemento de ExpressionBinding para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="e3ac1-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="e3ac1-125">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="e3ac1-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e3ac1-126">Observações</span><span class="sxs-lookup"><span data-stu-id="e3ac1-126">Remarks</span></span>

<span data-ttu-id="e3ac1-127">Pode especificar um nome de propriedade ou um script para esta condição, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="e3ac1-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3ac1-128">Veja Também</span><span class="sxs-lookup"><span data-stu-id="e3ac1-128">See Also</span></span>

[<span data-ttu-id="e3ac1-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3ac1-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="e3ac1-130">Elemento de ExpressionBinding para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="e3ac1-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
