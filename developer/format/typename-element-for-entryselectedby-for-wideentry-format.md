---
title: Elemento de TypeName para EntrySelectedBy para WideEntry (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083931"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="5ed63-102">TypeName Element for EntrySelectedBy for WideEntry (Format) (Elemento TypeName para EntrySelectedBy para WideEntry [Formatação])</span><span class="sxs-lookup"><span data-stu-id="5ed63-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="5ed63-103">Especifica um tipo de .NET para a definição.</span><span class="sxs-lookup"><span data-stu-id="5ed63-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="5ed63-104">A definição é utilizada sempre que este objeto é apresentado.</span><span class="sxs-lookup"><span data-stu-id="5ed63-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="5ed63-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de TypeName WideEntry (formato) para WideEntry ( Formato)</span><span class="sxs-lookup"><span data-stu-id="5ed63-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5ed63-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ed63-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ed63-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5ed63-107">Attributes and Elements</span></span>

<span data-ttu-id="5ed63-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="5ed63-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ed63-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="5ed63-109">Attributes</span></span>

<span data-ttu-id="5ed63-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5ed63-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ed63-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="5ed63-111">Child Elements</span></span>

<span data-ttu-id="5ed63-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5ed63-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5ed63-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="5ed63-113">Parent Elements</span></span>

|<span data-ttu-id="5ed63-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ed63-114">Element</span></span>|<span data-ttu-id="5ed63-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ed63-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ed63-116">Elemento de EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="5ed63-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="5ed63-117">Define os tipos do .NET que utilizam esta entrada ampla ou a condição que tem de existir para esta entrada a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="5ed63-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5ed63-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="5ed63-118">Text Value</span></span>

<span data-ttu-id="5ed63-119">Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="5ed63-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ed63-120">Observações</span><span class="sxs-lookup"><span data-stu-id="5ed63-120">Remarks</span></span>

<span data-ttu-id="5ed63-121">Cada entrada ampla tem de especificar um ou mais tipos de .NET, um conjunto de seleção ou a condição de seleção que tem de existir durante a definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="5ed63-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="5ed63-122">Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="5ed63-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5ed63-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="5ed63-123">See Also</span></span>

[<span data-ttu-id="5ed63-124">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="5ed63-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="5ed63-125">Elemento de EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="5ed63-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="5ed63-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5ed63-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
