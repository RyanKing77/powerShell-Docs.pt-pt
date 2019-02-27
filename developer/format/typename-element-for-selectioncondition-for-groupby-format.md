---
title: Elemento de TypeName para SelectionCondition para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848777"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="d21a9-102">TypeName Element for SelectionCondition for GroupBy (Format) (Elemento TypeName para SelectionCondition para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="d21a9-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="d21a9-103">Especifica um tipo .NET que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="d21a9-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="d21a9-104">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="d21a9-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="d21a9-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de EntrySelectedBy GroupBy (formato) para CustomEntry para o elemento de SelectionCondition GroupBy (formato) para EntrySelectedBy para o elemento de TypeName GroupBy (formato) para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d21a9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d21a9-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d21a9-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d21a9-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="d21a9-107">Attributes and Elements</span></span>

<span data-ttu-id="d21a9-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="d21a9-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d21a9-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="d21a9-109">Attributes</span></span>

<span data-ttu-id="d21a9-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d21a9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d21a9-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="d21a9-111">Child Elements</span></span>

<span data-ttu-id="d21a9-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d21a9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d21a9-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="d21a9-113">Parent Elements</span></span>

|<span data-ttu-id="d21a9-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="d21a9-114">Element</span></span>|<span data-ttu-id="d21a9-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="d21a9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d21a9-116">Elemento de SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d21a9-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="d21a9-117">Define uma condição que tem de existir durante a definição de controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="d21a9-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d21a9-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="d21a9-118">Text Value</span></span>

<span data-ttu-id="d21a9-119">Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="d21a9-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="d21a9-120">Observações</span><span class="sxs-lookup"><span data-stu-id="d21a9-120">Remarks</span></span>

<span data-ttu-id="d21a9-121">Quando este elemento é especificado, não é possível especificar o `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="d21a9-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="d21a9-122">Para obter mais informações sobre como definir condições de seleção, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d21a9-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d21a9-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="d21a9-123">See Also</span></span>

[<span data-ttu-id="d21a9-124">Elemento de SelectionCondition para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="d21a9-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="d21a9-125">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d21a9-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
