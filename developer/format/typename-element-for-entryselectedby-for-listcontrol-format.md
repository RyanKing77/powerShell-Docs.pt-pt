---
title: Elemento de TypeName para EntrySelectedBy para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 3f0c0ba1fe85d70557e67a30b3a9a59a33043475
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846887"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="1db81-102">TypeName Element for EntrySelectedBy for ListControl (Format) (Elemento TypeName para EntrySelectedBy para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="1db81-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="1db81-103">Especifica um tipo .NET que utiliza esta entrada da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="1db81-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="1db81-104">Não existe nenhum limite para o número de tipos que podem ser especificados para uma entrada na lista.</span><span class="sxs-lookup"><span data-stu-id="1db81-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="1db81-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento (formato) ListEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de TypeName ListEntry (formato) para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="1db81-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1db81-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1db81-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1db81-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="1db81-107">Attributes and Elements</span></span>

<span data-ttu-id="1db81-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="1db81-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1db81-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="1db81-109">Attributes</span></span>

<span data-ttu-id="1db81-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1db81-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1db81-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="1db81-111">Child Elements</span></span>

<span data-ttu-id="1db81-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="1db81-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1db81-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="1db81-113">Parent Elements</span></span>

|<span data-ttu-id="1db81-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="1db81-114">Element</span></span>|<span data-ttu-id="1db81-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="1db81-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1db81-116">Elemento de EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1db81-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="1db81-117">Define os tipos do .NET que utilizam esta entrada da lista ou a condição que tem de existir para esta entrada a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="1db81-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1db81-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="1db81-118">Text Value</span></span>

<span data-ttu-id="1db81-119">Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="1db81-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="1db81-120">Observações</span><span class="sxs-lookup"><span data-stu-id="1db81-120">Remarks</span></span>

<span data-ttu-id="1db81-121">Cada entrada da lista tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.</span><span class="sxs-lookup"><span data-stu-id="1db81-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="1db81-122">Para obter mais informações sobre como este elemento é usado numa exibição de lista, consulte [vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="1db81-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1db81-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1db81-123">Example</span></span>

<span data-ttu-id="1db81-124">O exemplo seguinte mostra como especificar uma seleção definido para uma entrada de uma vista de lista.</span><span class="sxs-lookup"><span data-stu-id="1db81-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="1db81-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="1db81-125">See Also</span></span>

[<span data-ttu-id="1db81-126">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="1db81-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="1db81-127">Elemento de EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1db81-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="1db81-128">Elemento de SelectionSetName para EnrtySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="1db81-128">SelectionSetName Element for EnrtySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="1db81-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1db81-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
