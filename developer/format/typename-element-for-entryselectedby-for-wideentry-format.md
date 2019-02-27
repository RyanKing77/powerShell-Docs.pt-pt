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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851465"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="03bc0-102">TypeName Element for EntrySelectedBy for WideEntry (Format) (Elemento TypeName para EntrySelectedBy para WideEntry [Formatação])</span><span class="sxs-lookup"><span data-stu-id="03bc0-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="03bc0-103">Especifica um tipo de .NET para a definição.</span><span class="sxs-lookup"><span data-stu-id="03bc0-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="03bc0-104">A definição é utilizada sempre que este objeto é apresentado.</span><span class="sxs-lookup"><span data-stu-id="03bc0-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="03bc0-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de TypeName WideEntry (formato) para WideEntry ( Formato)</span><span class="sxs-lookup"><span data-stu-id="03bc0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="03bc0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03bc0-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="03bc0-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="03bc0-107">Attributes and Elements</span></span>

<span data-ttu-id="03bc0-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="03bc0-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="03bc0-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="03bc0-109">Attributes</span></span>

<span data-ttu-id="03bc0-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="03bc0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="03bc0-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="03bc0-111">Child Elements</span></span>

<span data-ttu-id="03bc0-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="03bc0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="03bc0-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="03bc0-113">Parent Elements</span></span>

|<span data-ttu-id="03bc0-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="03bc0-114">Element</span></span>|<span data-ttu-id="03bc0-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="03bc0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="03bc0-116">Elemento de EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="03bc0-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="03bc0-117">Define os tipos do .NET que utilizam esta entrada ampla ou a condição que tem de existir para esta entrada a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="03bc0-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="03bc0-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="03bc0-118">Text Value</span></span>

<span data-ttu-id="03bc0-119">Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="03bc0-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="03bc0-120">Observações</span><span class="sxs-lookup"><span data-stu-id="03bc0-120">Remarks</span></span>

<span data-ttu-id="03bc0-121">Cada entrada ampla tem de especificar um ou mais tipos de .NET, um conjunto de seleção ou a condição de seleção que tem de existir durante a definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="03bc0-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="03bc0-122">Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="03bc0-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="03bc0-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="03bc0-123">See Also</span></span>

[<span data-ttu-id="03bc0-124">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="03bc0-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="03bc0-125">Elemento de EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="03bc0-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="03bc0-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="03bc0-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
