---
title: O elemento de EnumerableExpansions (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066095"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="0a0c5-102">EnumerableExpansions Element (Format) (Elemento EnumerableExpansions [Formatação])</span><span class="sxs-lookup"><span data-stu-id="0a0c5-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="0a0c5-103">Define como os objetos da coleção de .NET são expandidos quando são apresentados numa vista.</span><span class="sxs-lookup"><span data-stu-id="0a0c5-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="0a0c5-104">Elemento de configuração do EnumerableExpansions elemento (formato) DefaultSettings elemento (formato) (formato)</span><span class="sxs-lookup"><span data-stu-id="0a0c5-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0a0c5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a0c5-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0a0c5-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0a0c5-106">Attributes and Elements</span></span>

<span data-ttu-id="0a0c5-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `EnumerableExpansions` elemento.</span><span class="sxs-lookup"><span data-stu-id="0a0c5-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="0a0c5-108">Não existe nenhum limite para o número de elementos filho que pode utilizar.</span><span class="sxs-lookup"><span data-stu-id="0a0c5-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="0a0c5-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="0a0c5-109">Attributes</span></span>

<span data-ttu-id="0a0c5-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0a0c5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0a0c5-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="0a0c5-111">Child Elements</span></span>

|<span data-ttu-id="0a0c5-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="0a0c5-112">Element</span></span>|<span data-ttu-id="0a0c5-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a0c5-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0a0c5-114">Elemento de EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="0a0c5-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="0a0c5-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="0a0c5-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0a0c5-116">Define os objetos de coleção específicos do .NET que são expandidos quando são apresentados numa vista.</span><span class="sxs-lookup"><span data-stu-id="0a0c5-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0a0c5-117">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="0a0c5-117">Parent Elements</span></span>

|<span data-ttu-id="0a0c5-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="0a0c5-118">Element</span></span>|<span data-ttu-id="0a0c5-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a0c5-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0a0c5-120">Elemento de DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="0a0c5-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="0a0c5-121">Define configurações comuns que se aplicam a todas as vistas do ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="0a0c5-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0a0c5-122">Observações</span><span class="sxs-lookup"><span data-stu-id="0a0c5-122">Remarks</span></span>

<span data-ttu-id="0a0c5-123">Este elemento é usado para definir a forma como são apresentados os objetos da coleção e os objetos da coleção.</span><span class="sxs-lookup"><span data-stu-id="0a0c5-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="0a0c5-124">Neste caso, um objeto de coleção refere-se a qualquer objeto que suporte o **System.Collections.ICollection** interface.</span><span class="sxs-lookup"><span data-stu-id="0a0c5-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a0c5-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="0a0c5-125">See Also</span></span>

[<span data-ttu-id="0a0c5-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0a0c5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
