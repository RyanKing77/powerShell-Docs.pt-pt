---
title: Elemento de ItemSelectionCondition para ListItem para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065449"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="3d493-102">ItemSelectionCondition Element for ListItem for ListControl (Format) (Elemento ItemSelectionCondition para ListItem para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="3d493-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="3d493-103">Define a condição de que tem de existir para este item de lista a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="3d493-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="3d493-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry ListControl (formato) para ListEntries para o elemento de ListItems ListControl (formato) para ListEntry para o elemento de ListItem ListControl (formato) para ListItems para o elemento de ItemSelectionCondition ListControl (formato) para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3d493-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3d493-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d493-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3d493-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3d493-106">Attributes and Elements</span></span>

<span data-ttu-id="3d493-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ItemSelectionCondition` elemento.</span><span class="sxs-lookup"><span data-stu-id="3d493-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3d493-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="3d493-108">Attributes</span></span>

<span data-ttu-id="3d493-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3d493-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3d493-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="3d493-110">Child Elements</span></span>

|<span data-ttu-id="3d493-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="3d493-111">Element</span></span>|<span data-ttu-id="3d493-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d493-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d493-113">Elemento de PropertyName para ItemSelectionCondition para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3d493-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="3d493-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3d493-114">Optional element.</span></span><br /><br /> <span data-ttu-id="3d493-115">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="3d493-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="3d493-116">Elemento de ScriptBlock para ItemSelectionCondition para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3d493-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="3d493-117">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="3d493-117">Optional element.</span></span><br /><br /> <span data-ttu-id="3d493-118">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="3d493-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3d493-119">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="3d493-119">Parent Elements</span></span>

|<span data-ttu-id="3d493-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="3d493-120">Element</span></span>|<span data-ttu-id="3d493-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d493-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d493-122">Elemento de ListItem para ListItems para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3d493-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="3d493-123">Define a propriedade ou um script cujo valor é apresentado numa linha da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="3d493-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3d493-124">Observações</span><span class="sxs-lookup"><span data-stu-id="3d493-124">Remarks</span></span>

<span data-ttu-id="3d493-125">Pode especificar um nome de propriedade ou um script para esta condição, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="3d493-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d493-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="3d493-126">See Also</span></span>

[<span data-ttu-id="3d493-127">Elemento de ListItem para ListItems para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3d493-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="3d493-128">Elemento de PropertyName para ItemSelectionCondition para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3d493-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="3d493-129">Elemento de ScriptBlock para ItemSelectionCondition para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="3d493-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="3d493-130">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="3d493-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
