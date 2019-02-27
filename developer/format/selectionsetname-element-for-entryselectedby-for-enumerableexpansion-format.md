---
title: Elemento de SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851535"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="0e964-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format) (Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion [Formatação])</span><span class="sxs-lookup"><span data-stu-id="0e964-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="0e964-103">Especifica o conjunto de tipos do .NET que são expandidas por esta definição.</span><span class="sxs-lookup"><span data-stu-id="0e964-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="0e964-104">O elemento (formato) DefaultSettings elemento (formato) EnumerableExpansions elemento (formato) EnumerableExpansion elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionSetName EnumerableExpansion (formato) para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="0e964-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0e964-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e964-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="0e964-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="0e964-106">Attributes and Elements</span></span>

<span data-ttu-id="0e964-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="0e964-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0e964-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="0e964-108">Attributes</span></span>

<span data-ttu-id="0e964-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0e964-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0e964-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="0e964-110">Child Elements</span></span>

<span data-ttu-id="0e964-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0e964-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0e964-112">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="0e964-112">Parent Elements</span></span>

|<span data-ttu-id="0e964-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="0e964-113">Element</span></span>|<span data-ttu-id="0e964-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="0e964-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0e964-115">Elemento de EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="0e964-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="0e964-116">Define os objetos da coleção de .NET que são expandidos por esta definição.</span><span class="sxs-lookup"><span data-stu-id="0e964-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0e964-117">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="0e964-117">Text Value</span></span>

<span data-ttu-id="0e964-118">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="0e964-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e964-119">Observações</span><span class="sxs-lookup"><span data-stu-id="0e964-119">Remarks</span></span>

<span data-ttu-id="0e964-120">Cada definição tem de especificar um ou mais nomes de tipo, um conjunto de seleção ou uma condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="0e964-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="0e964-121">Conjuntos de seleção são normalmente utilizados quando quiser definir um grupo de objetos que são utilizados em vários modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="0e964-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="0e964-122">Por exemplo, pode querer criar uma vista de tabela e uma vista de lista para o mesmo conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="0e964-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="0e964-123">Para obter mais informações sobre como definir conjuntos de seleção, consulte [definir conjuntos de objetos para uma visão](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="0e964-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0e964-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="0e964-124">See Also</span></span>

[<span data-ttu-id="0e964-125">Definir conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="0e964-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="0e964-126">Elemento de EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="0e964-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="0e964-127">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e964-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
