---
title: Elemento de ItemSelectionCondition para ExpressionBinding para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065517"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="fc50d-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) (Elemento ItemSelectionCondition para ExpressionBinding para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="fc50d-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="fc50d-103">Define a condição de que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="fc50d-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="fc50d-104">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="fc50d-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="fc50d-105">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de CustomItem de configuração (formato) para CustomEntry para controles para o elemento de configuração ExpressionBinding para CustomItem para controles de configuração (formato) Elemento de ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="fc50d-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fc50d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc50d-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fc50d-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fc50d-107">Attributes and Elements</span></span>

<span data-ttu-id="fc50d-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="fc50d-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fc50d-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="fc50d-109">Attributes</span></span>

<span data-ttu-id="fc50d-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fc50d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fc50d-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="fc50d-111">Child Elements</span></span>

|<span data-ttu-id="fc50d-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="fc50d-112">Element</span></span>|<span data-ttu-id="fc50d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc50d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fc50d-114">Elemento de PropertyName para ItemSelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="fc50d-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="fc50d-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="fc50d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="fc50d-116">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="fc50d-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="fc50d-117">Elemento de ScriptBlock para ItemSelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="fc50d-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="fc50d-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="fc50d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="fc50d-119">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="fc50d-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fc50d-120">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="fc50d-120">Parent Elements</span></span>

|<span data-ttu-id="fc50d-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="fc50d-121">Element</span></span>|<span data-ttu-id="fc50d-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc50d-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fc50d-123">Elemento de ExpressionBinding para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="fc50d-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="fc50d-124">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="fc50d-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fc50d-125">Observações</span><span class="sxs-lookup"><span data-stu-id="fc50d-125">Remarks</span></span>

<span data-ttu-id="fc50d-126">Pode especificar um nome de propriedade ou um script para esta condição, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="fc50d-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc50d-127">Veja Também</span><span class="sxs-lookup"><span data-stu-id="fc50d-127">See Also</span></span>

[<span data-ttu-id="fc50d-128">Elemento de PropertyName para ItemSelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="fc50d-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="fc50d-129">Elemento de ScriptBlock para ItemSelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="fc50d-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="fc50d-130">Elemento de ExpressionBinding para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="fc50d-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="fc50d-131">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc50d-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
