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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065483"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="5141c-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format) (Elemento ItemSelectionCondition para ExpressionBinding para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="5141c-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="5141c-103">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="5141c-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="5141c-104">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="5141c-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="5141c-105">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) CustomItem elemento para CustomEntry para controles para exibição (formato) ExpressionBinding elemento para CustomItem para controles para exibição (formato) Elemento de ItemSelectionCondition de ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5141c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5141c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5141c-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5141c-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5141c-107">Attributes and Elements</span></span>

<span data-ttu-id="5141c-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="5141c-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5141c-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="5141c-109">Attributes</span></span>

<span data-ttu-id="5141c-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5141c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5141c-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="5141c-111">Child Elements</span></span>

|<span data-ttu-id="5141c-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="5141c-112">Element</span></span>|<span data-ttu-id="5141c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="5141c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5141c-114">Elemento de PropertyName para ItemSelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5141c-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="5141c-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5141c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5141c-116">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="5141c-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="5141c-117">Elemento de ScriptBlock para ItemSelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5141c-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="5141c-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5141c-118">Optional element.</span></span><br /><br /> <span data-ttu-id="5141c-119">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="5141c-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5141c-120">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="5141c-120">Parent Elements</span></span>

|<span data-ttu-id="5141c-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="5141c-121">Element</span></span>|<span data-ttu-id="5141c-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="5141c-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5141c-123">Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5141c-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="5141c-124">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="5141c-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5141c-125">Observações</span><span class="sxs-lookup"><span data-stu-id="5141c-125">Remarks</span></span>

<span data-ttu-id="5141c-126">Pode especificar um nome de propriedade ou um script para esta condição, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="5141c-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="5141c-127">Veja Também</span><span class="sxs-lookup"><span data-stu-id="5141c-127">See Also</span></span>

[<span data-ttu-id="5141c-128">Elemento de PropertyName para ItemSelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5141c-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="5141c-129">Elemento de ScriptBlock para ItemSelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5141c-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="5141c-130">Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5141c-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="5141c-131">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5141c-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
