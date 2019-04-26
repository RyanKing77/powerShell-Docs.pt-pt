---
title: Elemento de SelectionSetName para SelectionCondition para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064030"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="092bf-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format) (Elemento SelectionSetName para SelectionCondition para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="092bf-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="092bf-103">Especifica o conjunto de tipos do .NET que acionam a condição.</span><span class="sxs-lookup"><span data-stu-id="092bf-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="092bf-104">Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado ao utilizar este controlo.</span><span class="sxs-lookup"><span data-stu-id="092bf-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="092bf-105">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="092bf-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="092bf-106">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para controles para Elemento de CustomEntry de configuração (formato) para CustomControl para controles para o elemento de EntrySelectedBy de configuração (formato) para CustomEntry para controles para o elemento de SelectionCondition de configuração (formato) para EntrySelectedBy para controles para Elemento de SelectionSetName de configuração (formato) para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="092bf-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="092bf-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="092bf-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="092bf-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="092bf-108">Attributes and Elements</span></span>

<span data-ttu-id="092bf-109">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="092bf-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="092bf-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="092bf-110">Attributes</span></span>

<span data-ttu-id="092bf-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="092bf-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="092bf-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="092bf-112">Child Elements</span></span>

<span data-ttu-id="092bf-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="092bf-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="092bf-114">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="092bf-114">Parent Elements</span></span>

|<span data-ttu-id="092bf-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="092bf-115">Element</span></span>|<span data-ttu-id="092bf-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="092bf-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="092bf-117">Elemento de SelectionCondition para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="092bf-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="092bf-118">Define uma condição que tem de existir durante a definição de controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="092bf-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="092bf-119">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="092bf-119">Text Value</span></span>

<span data-ttu-id="092bf-120">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="092bf-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="092bf-121">Observações</span><span class="sxs-lookup"><span data-stu-id="092bf-121">Remarks</span></span>

<span data-ttu-id="092bf-122">Conjuntos de seleção são comuns grupos de objetos .NET que podem ser utilizados por qualquer vista que define o ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="092bf-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="092bf-123">Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="092bf-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="092bf-124">A condição de seleção pode especificar um conjunto de seleção ou o tipo .NET, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="092bf-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="092bf-125">Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="092bf-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="092bf-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="092bf-126">See Also</span></span>

[<span data-ttu-id="092bf-127">Elemento de SelectionCondition para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="092bf-127">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="092bf-128">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="092bf-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="092bf-129">Definir conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="092bf-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="092bf-130">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="092bf-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
