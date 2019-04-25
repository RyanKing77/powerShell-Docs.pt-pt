---
title: O elemento de SelectionSets (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063782"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="a80b3-102">SelectionSets Element (Format) (Elemento SelectionSets [Formatação])</span><span class="sxs-lookup"><span data-stu-id="a80b3-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="a80b3-103">Define os conjuntos comuns de objetos .NET que podem ser utilizados por todas as vistas do ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="a80b3-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="a80b3-104">As vistas e os controles do arquivo formatação podem referenciar o conjunto completo de objetos ao utilizar apenas o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="a80b3-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="a80b3-105">Formato de SelectionSets elemento do elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="a80b3-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="a80b3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a80b3-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a80b3-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a80b3-107">Attributes and Elements</span></span>

<span data-ttu-id="a80b3-108">As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `SelectionSets` elemento.</span><span class="sxs-lookup"><span data-stu-id="a80b3-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="a80b3-109">Cada elemento subordinado define um conjunto de objetos que pode ser referenciado pelo nome do conjunto.</span><span class="sxs-lookup"><span data-stu-id="a80b3-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="a80b3-110">A ordem dos elementos subordinados não é significativa.</span><span class="sxs-lookup"><span data-stu-id="a80b3-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="a80b3-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="a80b3-111">Attributes</span></span>

<span data-ttu-id="a80b3-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a80b3-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a80b3-113">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="a80b3-113">Child Elements</span></span>

|<span data-ttu-id="a80b3-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="a80b3-114">Element</span></span>|<span data-ttu-id="a80b3-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a80b3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a80b3-116">Elemento de SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="a80b3-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="a80b3-117">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="a80b3-117">Required element.</span></span><br /><br /> <span data-ttu-id="a80b3-118">Define um único conjunto de objetos do .NET que pode ser referenciado pelo nome do conjunto.</span><span class="sxs-lookup"><span data-stu-id="a80b3-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a80b3-119">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="a80b3-119">Parent Elements</span></span>

|<span data-ttu-id="a80b3-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="a80b3-120">Element</span></span>|<span data-ttu-id="a80b3-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="a80b3-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a80b3-122">Elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="a80b3-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="a80b3-123">Representa o elemento de nível superior de um ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="a80b3-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a80b3-124">Observações</span><span class="sxs-lookup"><span data-stu-id="a80b3-124">Remarks</span></span>

<span data-ttu-id="a80b3-125">É possível utilizar conjuntos de seleção quando tem um conjunto de objetos relacionados que deseja fazer referência ao utilizar um nome único, como um conjunto de objetos que estão relacionados por meio de herança.</span><span class="sxs-lookup"><span data-stu-id="a80b3-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="a80b3-126">Ao definir suas Exibições, pode especificar o conjunto de objetos usando o nome da seleção, em vez de listagem de todos os objetos dentro de cada vista.</span><span class="sxs-lookup"><span data-stu-id="a80b3-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="a80b3-127">Conjuntos de seleção comuns são especificados pelo respetivo nome quando definir as exibições do arquivo formatação ou as definições das vistas.</span><span class="sxs-lookup"><span data-stu-id="a80b3-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="a80b3-128">Nestes casos, o `SelectionSetName` elemento subordinado do `ViewSelectedBy` e `EntrySelectedBy` elementos Especifica o conjunto a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="a80b3-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="a80b3-129">Para obter mais informações sobre os conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a80b3-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a80b3-130">Veja Também</span><span class="sxs-lookup"><span data-stu-id="a80b3-130">See Also</span></span>

[<span data-ttu-id="a80b3-131">Elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="a80b3-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="a80b3-132">Definir conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="a80b3-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a80b3-133">Elemento de SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="a80b3-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="a80b3-134">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a80b3-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
