---
title: Elemento de ScriptBlock para SelectionCondition para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844864"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="4237c-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format) (Elemento ScriptBlock para SelectionCondition para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="4237c-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="4237c-103">Especifica o script que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="4237c-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="4237c-104">Quando esse script é avaliado para `true`, a condição é cumprida e a definição é utilizada.</span><span class="sxs-lookup"><span data-stu-id="4237c-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="4237c-105">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="4237c-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="4237c-106">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de EntrySelectedBy de configuração (formato) para CustomEntry para controles para o elemento de SelectionCondition de configuração (formato) para EntrySelectedBy para controles de configuração (formato) Elemento de ScriptBlock para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="4237c-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4237c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4237c-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4237c-108">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="4237c-108">Attributes and Elements</span></span>

<span data-ttu-id="4237c-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="4237c-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4237c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="4237c-110">Attributes</span></span>

<span data-ttu-id="4237c-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="4237c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4237c-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="4237c-112">Child Elements</span></span>

<span data-ttu-id="4237c-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="4237c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4237c-114">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="4237c-114">Parent Elements</span></span>

|<span data-ttu-id="4237c-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="4237c-115">Element</span></span>|<span data-ttu-id="4237c-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="4237c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4237c-117">Elemento de SelectionCondition para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="4237c-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="4237c-118">Define uma condição que tem de existir durante a definição de controle comum a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="4237c-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4237c-119">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="4237c-119">Text Value</span></span>

<span data-ttu-id="4237c-120">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="4237c-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="4237c-121">Observações</span><span class="sxs-lookup"><span data-stu-id="4237c-121">Remarks</span></span>

<span data-ttu-id="4237c-122">A condição de seleção tem de especificar um, pelo menos, um script ou a propriedade nome para avaliar, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="4237c-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="4237c-123">Para obter mais informações sobre como as condições de seleção podem ser utilizadas, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="4237c-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4237c-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="4237c-124">See Also</span></span>

[<span data-ttu-id="4237c-125">Elemento de SelectionCondition para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="4237c-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="4237c-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4237c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
