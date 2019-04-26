---
title: Elemento de ScriptBlock para ItemSelectionCondition para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064412"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="1cd3a-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format) (Elemento ScriptBlock para ItemSelectionCondition para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="1cd3a-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="1cd3a-103">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="1cd3a-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="1cd3a-104">Quando esse script é avaliado para `true`, a condição é cumprida e é utilizado o item da lista.</span><span class="sxs-lookup"><span data-stu-id="1cd3a-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="1cd3a-105">Este elemento é utilizado ao definir uma vista de lista.</span><span class="sxs-lookup"><span data-stu-id="1cd3a-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="1cd3a-106">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry ListControl (formato) para ListEntries para o elemento de ListItems ListControl (formato) para ListEntry para o elemento de ListItem ListControl (formato) para ListItems para o elemento de ItemSelectionCondition de controle (formato) de lista para ListItem para o elemento de ScriptBlock ListControl (formato) para ItemSelectionCondition para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1cd3a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1cd3a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1cd3a-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1cd3a-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1cd3a-108">Attributes and Elements</span></span>

<span data-ttu-id="1cd3a-109">As secções seguintes descrevem os atributos e elementos filho e os elementos pai do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="1cd3a-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1cd3a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="1cd3a-110">Attributes</span></span>

<span data-ttu-id="1cd3a-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1cd3a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1cd3a-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="1cd3a-112">Child Elements</span></span>

<span data-ttu-id="1cd3a-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1cd3a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1cd3a-114">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="1cd3a-114">Parent Elements</span></span>

|<span data-ttu-id="1cd3a-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="1cd3a-115">Element</span></span>|<span data-ttu-id="1cd3a-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="1cd3a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1cd3a-117">Elemento de ItemSelectionCondition para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1cd3a-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="1cd3a-118">Define a condição de que tem de existir para este item de lista a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="1cd3a-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1cd3a-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="1cd3a-119">Text Value</span></span>

<span data-ttu-id="1cd3a-120">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="1cd3a-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="1cd3a-121">Observações</span><span class="sxs-lookup"><span data-stu-id="1cd3a-121">Remarks</span></span>

<span data-ttu-id="1cd3a-122">Se este elemento é utilizado, não é possível especificar o `PropertyName` elemento ao definir a condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="1cd3a-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="1cd3a-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="1cd3a-123">See Also</span></span>

[<span data-ttu-id="1cd3a-124">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1cd3a-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
