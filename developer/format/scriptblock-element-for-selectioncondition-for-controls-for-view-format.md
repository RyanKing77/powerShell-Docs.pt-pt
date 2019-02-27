---
title: Elemento de ScriptBlock para SelectionCondition para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850898"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="d1d45-102">ScriptBlock Element for SelectionCondition for Controls for View (Format) (Elemento ScriptBlock para SelectionCondition para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="d1d45-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="d1d45-103">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="d1d45-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="d1d45-104">Quando esse script é avaliado para `true`, a condição é cumprida e a definição é utilizada.</span><span class="sxs-lookup"><span data-stu-id="d1d45-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="d1d45-105">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="d1d45-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="d1d45-106">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para controles para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) EntrySelectedBy elemento para CustomEntry para controles para exibição (formato) SelectionCondition elemento para EntrySelectedBy para controles para exibição ( Elemento de ScriptBlock de formato) para SelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d1d45-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d1d45-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1d45-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d1d45-108">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="d1d45-108">Attributes and Elements</span></span>

<span data-ttu-id="d1d45-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="d1d45-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d1d45-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d1d45-110">Attributes</span></span>

<span data-ttu-id="d1d45-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d1d45-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d1d45-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="d1d45-112">Child Elements</span></span>

<span data-ttu-id="d1d45-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d1d45-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d1d45-114">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="d1d45-114">Parent Elements</span></span>

|<span data-ttu-id="d1d45-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="d1d45-115">Element</span></span>|<span data-ttu-id="d1d45-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1d45-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d1d45-117">Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d1d45-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="d1d45-118">Define uma condição que tem de existir durante a definição de controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="d1d45-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d1d45-119">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="d1d45-119">Text Value</span></span>

<span data-ttu-id="d1d45-120">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="d1d45-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="d1d45-121">Observações</span><span class="sxs-lookup"><span data-stu-id="d1d45-121">Remarks</span></span>

<span data-ttu-id="d1d45-122">A condição de seleção tem de especificar um, pelo menos, um script ou a propriedade nome para avaliar, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="d1d45-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="d1d45-123">Para obter mais informações sobre como as condições de seleção podem ser utilizadas, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d1d45-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d1d45-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="d1d45-124">See Also</span></span>

[<span data-ttu-id="d1d45-125">Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d1d45-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="d1d45-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1d45-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
