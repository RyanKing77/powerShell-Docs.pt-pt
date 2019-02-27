---
title: Elemento de ScriptBlock para SelectionCondition para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847804"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="397fc-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format) (Elemento ScriptBlock para SelectionCondition para CustomControl para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="397fc-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="397fc-103">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="397fc-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="397fc-104">Quando esse script é avaliado para `true`, a condição é cumprida e a definição é utilizada.</span><span class="sxs-lookup"><span data-stu-id="397fc-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="397fc-105">Este elemento é utilizado ao definir uma vista de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="397fc-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="397fc-106">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento de configuração para o modo de exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para CustomControl para exibição ( Elemento de CustomItem de formato) para CustomEntry para CustomControl para exibição (formato) SelectionCondition elemento para EntrySelectedBy para CustomControl para exibição (formato) ScriptBlock elemento para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="397fc-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="397fc-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="397fc-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="397fc-108">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="397fc-108">Attributes and Elements</span></span>

<span data-ttu-id="397fc-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="397fc-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="397fc-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="397fc-110">Attributes</span></span>

<span data-ttu-id="397fc-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="397fc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="397fc-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="397fc-112">Child Elements</span></span>

<span data-ttu-id="397fc-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="397fc-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="397fc-114">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="397fc-114">Parent Elements</span></span>

|<span data-ttu-id="397fc-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="397fc-115">Element</span></span>|<span data-ttu-id="397fc-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="397fc-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="397fc-117">Elemento de SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="397fc-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="397fc-118">Define uma condição que tem de existir durante a definição de controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="397fc-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="397fc-119">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="397fc-119">Text Value</span></span>

<span data-ttu-id="397fc-120">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="397fc-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="397fc-121">Observações</span><span class="sxs-lookup"><span data-stu-id="397fc-121">Remarks</span></span>

<span data-ttu-id="397fc-122">A condição de seleção tem de especificar um, pelo menos, um script ou a propriedade nome para avaliar, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="397fc-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="397fc-123">Para obter mais informações sobre como as condições de seleção podem ser utilizadas, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="397fc-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="397fc-124">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="397fc-124">See Also</span></span>

[<span data-ttu-id="397fc-125">Elemento de SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="397fc-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="397fc-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="397fc-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
