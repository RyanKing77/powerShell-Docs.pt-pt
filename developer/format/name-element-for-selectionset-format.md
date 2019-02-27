---
title: Elemento de nome para SelectionSet (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848329"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="e3f22-102">Name Element for SelectionSet (Format) (Elemento Name para SelectionSet [Formatação])</span><span class="sxs-lookup"><span data-stu-id="e3f22-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="e3f22-103">Especifica o nome utilizado para referenciar o conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="e3f22-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="e3f22-104">Elemento de nome do elemento de SelectionSet (formato) do Configuration elemento (formato) SelectionSets elemento (formato) de SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="e3f22-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3f22-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3f22-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3f22-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="e3f22-106">Attributes and Elements</span></span>

<span data-ttu-id="e3f22-107">As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `Name` elemento.</span><span class="sxs-lookup"><span data-stu-id="e3f22-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3f22-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="e3f22-108">Attributes</span></span>

<span data-ttu-id="e3f22-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e3f22-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3f22-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="e3f22-110">Child Elements</span></span>

<span data-ttu-id="e3f22-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e3f22-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e3f22-112">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="e3f22-112">Parent Elements</span></span>

|<span data-ttu-id="e3f22-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="e3f22-113">Element</span></span>|<span data-ttu-id="e3f22-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3f22-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3f22-115">Elemento de SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="e3f22-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="e3f22-116">Define um único conjunto de objetos do .NET que pode ser referenciado pelo nome do conjunto.</span><span class="sxs-lookup"><span data-stu-id="e3f22-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e3f22-117">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="e3f22-117">Text Value</span></span>

<span data-ttu-id="e3f22-118">Especifique o nome para referenciar o conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="e3f22-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="e3f22-119">Existem não existem restrições quanto às quais caracteres podem ser utilizadas.</span><span class="sxs-lookup"><span data-stu-id="e3f22-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3f22-120">Observações</span><span class="sxs-lookup"><span data-stu-id="e3f22-120">Remarks</span></span>

<span data-ttu-id="e3f22-121">O nome especificado aqui é utilizado o `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="e3f22-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="e3f22-122">O conjunto de seleção que pode ser utilizado por uma exibição, por uma definição de uma vista (modos de exibição podem ter várias definições), ou ao especificar uma condição de seleção.</span><span class="sxs-lookup"><span data-stu-id="e3f22-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="e3f22-123">Para obter mais informações sobre os conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e3f22-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="e3f22-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3f22-124">Example</span></span>

<span data-ttu-id="e3f22-125">Este exemplo mostra um `SelectionSet` elemento que define quatro tipos de .NET.</span><span class="sxs-lookup"><span data-stu-id="e3f22-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="e3f22-126">O nome do conjunto de seleção é "FileSystemTypes".</span><span class="sxs-lookup"><span data-stu-id="e3f22-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e3f22-127">Veja Também</span><span class="sxs-lookup"><span data-stu-id="e3f22-127">See Also</span></span>

[<span data-ttu-id="e3f22-128">Definir conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="e3f22-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e3f22-129">Elemento de SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="e3f22-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="e3f22-130">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3f22-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
