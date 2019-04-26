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
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084033"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="80e33-102">TypeName Element for EntrySelectedBy for ListControl (Format) (Elemento TypeName para EntrySelectedBy para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="80e33-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="80e33-103">Especifica um tipo .NET que utiliza esta entrada da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="80e33-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="80e33-104">Não existe nenhum limite para o número de tipos que podem ser especificados para uma entrada na lista.</span><span class="sxs-lookup"><span data-stu-id="80e33-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="80e33-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento (formato) ListEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de TypeName ListEntry (formato) para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="80e33-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="80e33-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80e33-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="80e33-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="80e33-107">Attributes and Elements</span></span>

<span data-ttu-id="80e33-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="80e33-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="80e33-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="80e33-109">Attributes</span></span>

<span data-ttu-id="80e33-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="80e33-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="80e33-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="80e33-111">Child Elements</span></span>

<span data-ttu-id="80e33-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="80e33-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="80e33-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="80e33-113">Parent Elements</span></span>

|<span data-ttu-id="80e33-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="80e33-114">Element</span></span>|<span data-ttu-id="80e33-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="80e33-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80e33-116">Elemento de EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="80e33-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="80e33-117">Define os tipos do .NET que utilizam esta entrada da lista ou a condição que tem de existir para esta entrada a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="80e33-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="80e33-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="80e33-118">Text Value</span></span>

<span data-ttu-id="80e33-119">Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="80e33-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="80e33-120">Observações</span><span class="sxs-lookup"><span data-stu-id="80e33-120">Remarks</span></span>

<span data-ttu-id="80e33-121">Cada entrada da lista tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.</span><span class="sxs-lookup"><span data-stu-id="80e33-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="80e33-122">Para obter mais informações sobre como este elemento é usado numa exibição de lista, consulte [vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="80e33-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="80e33-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="80e33-123">Example</span></span>

<span data-ttu-id="80e33-124">O exemplo seguinte mostra como especificar uma seleção definido para uma entrada de uma vista de lista.</span><span class="sxs-lookup"><span data-stu-id="80e33-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="80e33-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="80e33-125">See Also</span></span>

[<span data-ttu-id="80e33-126">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="80e33-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="80e33-127">Elemento de EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="80e33-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="80e33-128">Elemento de SelectionSetName para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="80e33-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="80e33-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="80e33-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
