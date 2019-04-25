---
title: Elemento de PropertyName para ItemSelectionCondition para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064752"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="facfc-102">PropertyName Element for ItemSelectionCondition for ListControl (Format) (Elemento PropertyName para ItemSelectionCondition para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="facfc-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="facfc-103">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="facfc-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="facfc-104">Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e o modo de exibição é utilizado.</span><span class="sxs-lookup"><span data-stu-id="facfc-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="facfc-105">Este elemento é utilizado ao definir uma vista de lista.</span><span class="sxs-lookup"><span data-stu-id="facfc-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="facfc-106">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento (formato) ListEntry elemento de configuração para o elemento de ListItems ListControl (formato) para ListEntry para ListItem ListControl (formato) Elemento para ListItems para o elemento de ItemSelectionCondition ListControl (formato) para ListItem ListControls PropertyName elemento para ItemSelectionCondition para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="facfc-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="facfc-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="facfc-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="facfc-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="facfc-108">Attributes and Elements</span></span>

<span data-ttu-id="facfc-109">As secções seguintes descrevem os atributos e elementos filho e os elementos pai do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="facfc-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="facfc-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="facfc-110">Attributes</span></span>

<span data-ttu-id="facfc-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="facfc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="facfc-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="facfc-112">Child Elements</span></span>

<span data-ttu-id="facfc-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="facfc-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="facfc-114">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="facfc-114">Parent Elements</span></span>

|<span data-ttu-id="facfc-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="facfc-115">Element</span></span>|<span data-ttu-id="facfc-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="facfc-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="facfc-117">Elemento de ItemSelectionCondition para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="facfc-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="facfc-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="facfc-118">Text Value</span></span>

<span data-ttu-id="facfc-119">Especifique o nome da propriedade cujo valor é apresentado.</span><span class="sxs-lookup"><span data-stu-id="facfc-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="facfc-120">Observações</span><span class="sxs-lookup"><span data-stu-id="facfc-120">Remarks</span></span>

<span data-ttu-id="facfc-121">Se este elemento é utilizado, não é possível especificar a [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) elemento ao definir a condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="facfc-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="facfc-122">Veja Também</span><span class="sxs-lookup"><span data-stu-id="facfc-122">See Also</span></span>

[<span data-ttu-id="facfc-123">Elemento de ScriptBlock para ItemSelectionCondition para ListIControl (formato)</span><span class="sxs-lookup"><span data-stu-id="facfc-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="facfc-124">Elemento de ItemSelectionCondition para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="facfc-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="facfc-125">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="facfc-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
