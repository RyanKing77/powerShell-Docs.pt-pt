---
title: O elemento de EnumerableExpansion (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847398"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="43489-102">EnumerableExpansion Element (Format) (Elemento EnumerableExpansion [Formatação])</span><span class="sxs-lookup"><span data-stu-id="43489-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="43489-103">Define a coleção de .NET como específica objetos são expandidos quando são apresentados numa vista.</span><span class="sxs-lookup"><span data-stu-id="43489-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="43489-104">O elemento (formato) DefaultSettings elemento (formato) EnumerableExpansions elemento (formato) EnumerableExpansion o elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="43489-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="43489-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43489-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="43489-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="43489-106">Attributes and Elements</span></span>

<span data-ttu-id="43489-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `EnumerableExpansion` elemento.</span><span class="sxs-lookup"><span data-stu-id="43489-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="43489-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="43489-108">Attributes</span></span>

<span data-ttu-id="43489-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="43489-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="43489-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="43489-110">Child Elements</span></span>

|<span data-ttu-id="43489-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="43489-111">Element</span></span>|<span data-ttu-id="43489-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="43489-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="43489-113">Elemento de EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="43489-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="43489-114">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="43489-114">Optional element.</span></span><br /><br /> <span data-ttu-id="43489-115">Define os objetos da coleção de .NET são expandidos por esta definição.</span><span class="sxs-lookup"><span data-stu-id="43489-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="43489-116">Expanda o elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="43489-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="43489-117">Especifica a forma como o objeto de coleção é expandido para esta definição.</span><span class="sxs-lookup"><span data-stu-id="43489-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="43489-118">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="43489-118">Parent Elements</span></span>

|<span data-ttu-id="43489-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="43489-119">Element</span></span>|<span data-ttu-id="43489-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="43489-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="43489-121">Elemento de EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="43489-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="43489-122">Define as diferentes formas essa coleção de .NET objetos são expandidos quando são apresentados numa vista.</span><span class="sxs-lookup"><span data-stu-id="43489-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="43489-123">Observações</span><span class="sxs-lookup"><span data-stu-id="43489-123">Remarks</span></span>

<span data-ttu-id="43489-124">Este elemento é usado para definir a forma como são apresentados os objetos da coleção e os objetos da coleção.</span><span class="sxs-lookup"><span data-stu-id="43489-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="43489-125">Neste caso, um objeto de coleção refere-se a qualquer objeto que suporte o **System.Collections.ICollection** interface.</span><span class="sxs-lookup"><span data-stu-id="43489-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="43489-126">O comportamento padrão é apresentar apenas as propriedades dos objetos na coleção.</span><span class="sxs-lookup"><span data-stu-id="43489-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="43489-127">Veja Também</span><span class="sxs-lookup"><span data-stu-id="43489-127">See Also</span></span>

[<span data-ttu-id="43489-128">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="43489-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
