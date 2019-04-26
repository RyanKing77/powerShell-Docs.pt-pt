---
title: Elemento de TypeName para EntrySelectedBy para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083965"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="4798a-102">TypeName Element for EntrySelectedBy for TableControl (Format) (Elemento TypeName para EntrySelectedBy para TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="4798a-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="4798a-103">Especifica um tipo .NET que utiliza esta entrada da vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="4798a-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="4798a-104">Não existe nenhum limite para o número de tipos que podem ser especificados para uma entrada de tabela.</span><span class="sxs-lookup"><span data-stu-id="4798a-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="4798a-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento (formato) TableRowEntry elemento (formato) EntrySelectedBy elemento (formato) TypeName elemento de configuração para EntrySelectedBy para TableRowEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="4798a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4798a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4798a-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4798a-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4798a-107">Attributes and Elements</span></span>

<span data-ttu-id="4798a-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="4798a-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4798a-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="4798a-109">Attributes</span></span>

<span data-ttu-id="4798a-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="4798a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4798a-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="4798a-111">Child Elements</span></span>

<span data-ttu-id="4798a-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="4798a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4798a-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="4798a-113">Parent Elements</span></span>

|<span data-ttu-id="4798a-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="4798a-114">Element</span></span>|<span data-ttu-id="4798a-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="4798a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4798a-116">Elemento de EntrySelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="4798a-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="4798a-117">Define os tipos do .NET que utilizam esta entrada ou a condição que tem de existir para esta entrada a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="4798a-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4798a-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="4798a-118">Text Value</span></span>

<span data-ttu-id="4798a-119">Especifique o nome do tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="4798a-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="4798a-120">Observações</span><span class="sxs-lookup"><span data-stu-id="4798a-120">Remarks</span></span>

<span data-ttu-id="4798a-121">Cada entrada da lista tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.</span><span class="sxs-lookup"><span data-stu-id="4798a-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="4798a-122">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="4798a-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4798a-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="4798a-123">See Also</span></span>

[<span data-ttu-id="4798a-124">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="4798a-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="4798a-125">Elemento de EntrySelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="4798a-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="4798a-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4798a-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
