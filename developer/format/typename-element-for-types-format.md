---
title: Elemento de TypeName para tipos (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083795"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="e563c-102">TypeName Element for Types (Format) (Elemento TypeName para Types [Formatação])</span><span class="sxs-lookup"><span data-stu-id="e563c-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="e563c-103">Especifica o tipo de .NET de um objeto que pertence ao conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="e563c-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="e563c-104">Tipos de elemento de configuração do SelectionSet elemento (formato) SelectionSets elemento (formato) (formato) elemento (formato) TypeName elemento de tipos (formato)</span><span class="sxs-lookup"><span data-stu-id="e563c-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e563c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e563c-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e563c-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e563c-106">Attributes and Elements</span></span>

<span data-ttu-id="e563c-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="e563c-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="e563c-108">Pelo menos um `TypeName` elemento tem de ser incluído no conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="e563c-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="e563c-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="e563c-109">Attributes</span></span>

<span data-ttu-id="e563c-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e563c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e563c-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="e563c-111">Child Elements</span></span>

<span data-ttu-id="e563c-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e563c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e563c-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="e563c-113">Parent Elements</span></span>

|<span data-ttu-id="e563c-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="e563c-114">Element</span></span>|<span data-ttu-id="e563c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="e563c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e563c-116">Elemento de tipos (formato)</span><span class="sxs-lookup"><span data-stu-id="e563c-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="e563c-117">Define os objetos .NET na seleção definidas.</span><span class="sxs-lookup"><span data-stu-id="e563c-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e563c-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="e563c-118">Text Value</span></span>

<span data-ttu-id="e563c-119">Especifique o nome completamente qualificado para o tipo de .NET.</span><span class="sxs-lookup"><span data-stu-id="e563c-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="e563c-120">Observações</span><span class="sxs-lookup"><span data-stu-id="e563c-120">Remarks</span></span>

<span data-ttu-id="e563c-121">É possível utilizar conjuntos de seleção quando tem um conjunto de objetos relacionados que deseja fazer referência ao utilizar um nome único, como um conjunto de objetos que estão relacionados por meio de herança.</span><span class="sxs-lookup"><span data-stu-id="e563c-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="e563c-122">Ao definir suas Exibições, pode especificar o conjunto de objetos usando o nome da seleção, em vez de listagem de todos os objetos dentro de cada vista.</span><span class="sxs-lookup"><span data-stu-id="e563c-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="e563c-123">Comum de seleção de conjuntos são especificados pelo respetivo nome quando definir as exibições do arquivo formatação.</span><span class="sxs-lookup"><span data-stu-id="e563c-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="e563c-124">Nestes casos, o `SelectionSetName` elemento subordinado do `ViewSelectedBy` elemento para a vista Especifica o conjunto.</span><span class="sxs-lookup"><span data-stu-id="e563c-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="e563c-125">No entanto, as entradas diferentes de uma vista também podem especificar um conjunto de seleção que se aplica a apenas essa entrada da vista.</span><span class="sxs-lookup"><span data-stu-id="e563c-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="e563c-126">Para obter mais informações sobre os conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e563c-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="e563c-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e563c-127">Example</span></span>

<span data-ttu-id="e563c-128">A exemplo a seguir mostra um `SelectionSet` elemento que define quatro tipos de .NET.</span><span class="sxs-lookup"><span data-stu-id="e563c-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```
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

## <a name="see-also"></a><span data-ttu-id="e563c-129">Veja Também</span><span class="sxs-lookup"><span data-stu-id="e563c-129">See Also</span></span>

[<span data-ttu-id="e563c-130">Definir conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="e563c-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e563c-131">Elemento de SelectionSet (formato)</span><span class="sxs-lookup"><span data-stu-id="e563c-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="e563c-132">Elemento de SelectionSets (formato)</span><span class="sxs-lookup"><span data-stu-id="e563c-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="e563c-133">Elemento de tipos (formato)</span><span class="sxs-lookup"><span data-stu-id="e563c-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="e563c-134">Escrever do Windows PowerShell formatação ficheiro</span><span class="sxs-lookup"><span data-stu-id="e563c-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
