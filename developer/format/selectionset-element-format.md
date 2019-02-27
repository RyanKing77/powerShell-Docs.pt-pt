---
title: O elemento de SelectionSet (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850422"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="b5784-102">SelectionSet Element (Format) (Elemento SelectionSet [Formatação])</span><span class="sxs-lookup"><span data-stu-id="b5784-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="b5784-103">Define um conjunto de objetos do .NET que pode ser referenciado pelo nome do conjunto.</span><span class="sxs-lookup"><span data-stu-id="b5784-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="b5784-104">Elemento de configuração do SelectionSet elemento (formato) SelectionSets elemento (formato) (formato)</span><span class="sxs-lookup"><span data-stu-id="b5784-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5784-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5784-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5784-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="b5784-106">Attributes and Elements</span></span>

<span data-ttu-id="b5784-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSet` elemento.</span><span class="sxs-lookup"><span data-stu-id="b5784-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="b5784-108">Cada conjunto de seleção tem de ter um nome e tem de especificar os objetos de .NET do conjunto.</span><span class="sxs-lookup"><span data-stu-id="b5784-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5784-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b5784-109">Attributes</span></span>

<span data-ttu-id="b5784-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b5784-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5784-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="b5784-111">Child Elements</span></span>

|<span data-ttu-id="b5784-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b5784-112">Element</span></span>|<span data-ttu-id="b5784-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5784-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5784-114">Elemento de nome para SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="b5784-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="b5784-115">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="b5784-115">Required element.</span></span><br /><br /> <span data-ttu-id="b5784-116">Especifica o nome utilizado para referenciar o conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="b5784-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="b5784-117">Elemento de tipos (formato)</span><span class="sxs-lookup"><span data-stu-id="b5784-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="b5784-118">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="b5784-118">Required element.</span></span><br /><br /> <span data-ttu-id="b5784-119">Define os objetos .NET na seleção definidas.</span><span class="sxs-lookup"><span data-stu-id="b5784-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b5784-120">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="b5784-120">Parent Elements</span></span>

|<span data-ttu-id="b5784-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="b5784-121">Element</span></span>|<span data-ttu-id="b5784-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5784-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5784-123">Formato de elemento de SelectionSets</span><span class="sxs-lookup"><span data-stu-id="b5784-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="b5784-124">Define os conjuntos comuns de objetos .NET que podem ser utilizados por todas as vistas do ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="b5784-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b5784-125">Observações</span><span class="sxs-lookup"><span data-stu-id="b5784-125">Remarks</span></span>

<span data-ttu-id="b5784-126">É possível utilizar conjuntos de seleção quando tem um conjunto de objetos relacionados que deseja fazer referência ao utilizar um nome único, como um conjunto de objetos que estão relacionados por meio de herança.</span><span class="sxs-lookup"><span data-stu-id="b5784-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="b5784-127">Ao definir suas Exibições, pode especificar o conjunto de objetos usando o nome da seleção, em vez de listagem de todos os objetos dentro de cada vista.</span><span class="sxs-lookup"><span data-stu-id="b5784-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="b5784-128">Conjuntos de seleção comuns são especificados pelo respetivo nome quando definir as exibições do arquivo formatação ou as definições das vistas.</span><span class="sxs-lookup"><span data-stu-id="b5784-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="b5784-129">Nestes casos, o `SelectionSetName` elemento subordinado do `ViewSelectedBy` e `EntrySelectedBy` elementos Especifica o conjunto a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="b5784-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="b5784-130">Para obter mais informações sobre os conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b5784-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="b5784-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5784-131">Example</span></span>

<span data-ttu-id="b5784-132">A exemplo a seguir mostra um `SelectionSet` elemento que define quatro tipos de .NET.</span><span class="sxs-lookup"><span data-stu-id="b5784-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="b5784-133">Veja Também</span><span class="sxs-lookup"><span data-stu-id="b5784-133">See Also</span></span>

[<span data-ttu-id="b5784-134">Definir conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="b5784-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="b5784-135">Elemento de nome de SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="b5784-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="b5784-136">Elemento de SelectionSets (formato)</span><span class="sxs-lookup"><span data-stu-id="b5784-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="b5784-137">Elemento de tipos (formato)</span><span class="sxs-lookup"><span data-stu-id="b5784-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="b5784-138">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b5784-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
