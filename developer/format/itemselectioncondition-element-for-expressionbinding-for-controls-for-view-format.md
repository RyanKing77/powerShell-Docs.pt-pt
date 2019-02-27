---
title: Elemento de ItemSelectionCondition para ExpressionBinding para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850905"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="45bf7-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format) (Elemento ItemSelectionCondition para ExpressionBinding para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="45bf7-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="45bf7-103">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="45bf7-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="45bf7-104">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="45bf7-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="45bf7-105">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) CustomItem elemento para CustomEntry para controles para exibição (formato) ExpressionBinding elemento para CustomItem para controles para exibição (formato) Elemento de ItemSelectionCondition de ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="45bf7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="45bf7-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45bf7-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="45bf7-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="45bf7-107">Attributes and Elements</span></span>

<span data-ttu-id="45bf7-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="45bf7-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="45bf7-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="45bf7-109">Attributes</span></span>

<span data-ttu-id="45bf7-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="45bf7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="45bf7-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="45bf7-111">Child Elements</span></span>

|<span data-ttu-id="45bf7-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="45bf7-112">Element</span></span>|<span data-ttu-id="45bf7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="45bf7-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="45bf7-114">Elemento de PropertyName para ItemSelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="45bf7-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="45bf7-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="45bf7-115">Optional element.</span></span><br /><br /> <span data-ttu-id="45bf7-116">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="45bf7-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="45bf7-117">Elemento de ScriptBlock para ItemSelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="45bf7-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="45bf7-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="45bf7-118">Optional element.</span></span><br /><br /> <span data-ttu-id="45bf7-119">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="45bf7-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="45bf7-120">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="45bf7-120">Parent Elements</span></span>

|<span data-ttu-id="45bf7-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="45bf7-121">Element</span></span>|<span data-ttu-id="45bf7-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="45bf7-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="45bf7-123">Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="45bf7-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="45bf7-124">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="45bf7-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="45bf7-125">Observações</span><span class="sxs-lookup"><span data-stu-id="45bf7-125">Remarks</span></span>

<span data-ttu-id="45bf7-126">Pode especificar um nome de propriedade ou um script para esta condição, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="45bf7-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="45bf7-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="45bf7-127">See Also</span></span>

[<span data-ttu-id="45bf7-128">Elemento de PropertyName para ItemSelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="45bf7-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="45bf7-129">Elemento de ScriptBlock para ItemSelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="45bf7-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="45bf7-130">Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="45bf7-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="45bf7-131">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="45bf7-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
