---
title: Elemento de PropertyName para SelectionCondition para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850331"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="cea34-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format) (Elemento PropertyName para SelectionCondition para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="cea34-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="cea34-103">Especifica a propriedade do .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="cea34-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="cea34-104">Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e a entrada é utilizada.</span><span class="sxs-lookup"><span data-stu-id="cea34-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="cea34-105">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="cea34-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="cea34-106">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de EntrySelectedBy de configuração (formato) para CustomEntry para controles para o elemento de SelectionCondition de configuração (formato) para EntrySelectedBy para CustomEntry para (de configuração Elemento de PropertyName de formato) para SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="cea34-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cea34-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cea34-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cea34-108">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="cea34-108">Attributes and Elements</span></span>

<span data-ttu-id="cea34-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="cea34-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cea34-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="cea34-110">Attributes</span></span>

<span data-ttu-id="cea34-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cea34-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cea34-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="cea34-112">Child Elements</span></span>

<span data-ttu-id="cea34-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cea34-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cea34-114">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="cea34-114">Parent Elements</span></span>

|<span data-ttu-id="cea34-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="cea34-115">Element</span></span>|<span data-ttu-id="cea34-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="cea34-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cea34-117">Elemento de SelectionCondition para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="cea34-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="cea34-118">Define uma condição que tem de existir uma definição de controle comum a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="cea34-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cea34-119">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="cea34-119">Text Value</span></span>

<span data-ttu-id="cea34-120">Especifique o nome de propriedade do .NET.</span><span class="sxs-lookup"><span data-stu-id="cea34-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="cea34-121">Observações</span><span class="sxs-lookup"><span data-stu-id="cea34-121">Remarks</span></span>

<span data-ttu-id="cea34-122">A condição de seleção tem de especificar um nome de uma propriedade, pelo menos, ou um script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="cea34-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="cea34-123">Para obter mais informações sobre como as condições de seleção podem ser utilizadas, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="cea34-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cea34-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="cea34-124">See Also</span></span>

[<span data-ttu-id="cea34-125">Elemento de SelectionCondition para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="cea34-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="cea34-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cea34-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
