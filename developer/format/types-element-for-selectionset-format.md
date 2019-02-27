---
title: Tipos de elemento para SelectionSet (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851276"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="38500-102">Types Element for SelectionSet (Format) (Elemento Types para SelectionSet [Formatação])</span><span class="sxs-lookup"><span data-stu-id="38500-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="38500-103">Define os objetos .NET na seleção definidas.</span><span class="sxs-lookup"><span data-stu-id="38500-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="38500-104">Tipos de elemento de configuração do SelectionSet elemento (formato) SelectionSets elemento (formato) (formato) elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="38500-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="38500-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38500-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="38500-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="38500-106">Attributes and Elements</span></span>

<span data-ttu-id="38500-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Types` elemento.</span><span class="sxs-lookup"><span data-stu-id="38500-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="38500-108">Tem de existir pelo menos um elemento subordinado, mas não existe nenhum limite máximo para o número de elementos filho que podem ser adicionados.</span><span class="sxs-lookup"><span data-stu-id="38500-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="38500-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="38500-109">Attributes</span></span>

<span data-ttu-id="38500-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="38500-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="38500-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="38500-111">Child Elements</span></span>

|<span data-ttu-id="38500-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="38500-112">Element</span></span>|<span data-ttu-id="38500-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="38500-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38500-114">Elemento de TypeName dos tipos (formato)</span><span class="sxs-lookup"><span data-stu-id="38500-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="38500-115">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="38500-115">Required element.</span></span><br /><br /> <span data-ttu-id="38500-116">Especifica o objeto do .NET que pertence ao conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="38500-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="38500-117">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="38500-117">Parent Elements</span></span>

|<span data-ttu-id="38500-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="38500-118">Element</span></span>|<span data-ttu-id="38500-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="38500-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38500-120">Elemento de SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="38500-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="38500-121">Define um conjunto de objetos do .NET que pode ser referenciado pelo nome do conjunto.</span><span class="sxs-lookup"><span data-stu-id="38500-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="38500-122">Observações</span><span class="sxs-lookup"><span data-stu-id="38500-122">Remarks</span></span>

<span data-ttu-id="38500-123">Os objetos definidos por este elemento compõem um conjunto de seleção que pode ser utilizado por uma exibição, por uma definição de uma vista (modos de exibição podem ter várias definições), ou ao especificar uma condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="38500-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="38500-124">Para obter mais informações sobre os conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="38500-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="38500-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="38500-125">Example</span></span>

<span data-ttu-id="38500-126">Este exemplo mostra um `SelectionSet` elemento que define quatro tipos de .NET.</span><span class="sxs-lookup"><span data-stu-id="38500-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="38500-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="38500-127">See Also</span></span>

[<span data-ttu-id="38500-128">Definir conjuntos de objetos</span><span class="sxs-lookup"><span data-stu-id="38500-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="38500-129">Elemento de SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="38500-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="38500-130">Elemento de TypeName dos tipos (formato)</span><span class="sxs-lookup"><span data-stu-id="38500-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="38500-131">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="38500-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
