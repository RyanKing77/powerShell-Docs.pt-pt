---
title: Elemento de SelectionSetName para ViewSelectedBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848448"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="ef4a3-102">SelectionSetName Element for ViewSelectedBy (Format) (Elemento SelectionSetName para ViewSelectedBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="ef4a3-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="ef4a3-103">Especifica um conjunto de objetos do .NET que são apresentados pela exibição.</span><span class="sxs-lookup"><span data-stu-id="ef4a3-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="ef4a3-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ViewSelectedBy elemento (formato) SelectionSetName elemento de configuração para ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ef4a3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ef4a3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ef4a3-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef4a3-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="ef4a3-106">Attributes and Elements</span></span>

<span data-ttu-id="ef4a3-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="ef4a3-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef4a3-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="ef4a3-108">Attributes</span></span>

<span data-ttu-id="ef4a3-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ef4a3-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ef4a3-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="ef4a3-110">Child Elements</span></span>

<span data-ttu-id="ef4a3-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ef4a3-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ef4a3-112">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="ef4a3-112">Parent Elements</span></span>

|<span data-ttu-id="ef4a3-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="ef4a3-113">Element</span></span>|<span data-ttu-id="ef4a3-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef4a3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef4a3-115">Elemento de ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ef4a3-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="ef4a3-116">Define os objetos do .NET que são apresentados pela exibição.</span><span class="sxs-lookup"><span data-stu-id="ef4a3-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ef4a3-117">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="ef4a3-117">Text Value</span></span>

<span data-ttu-id="ef4a3-118">Especifique o nome do conjunto de seleção que é definido pelo `Name` elemento para o conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="ef4a3-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ef4a3-119">Observações</span><span class="sxs-lookup"><span data-stu-id="ef4a3-119">Remarks</span></span>

<span data-ttu-id="ef4a3-120">É possível utilizar conjuntos de seleção quando tem um conjunto de objetos relacionados que deseja fazer referência ao utilizar um nome único, como um conjunto de objetos que estão relacionados por meio de herança.</span><span class="sxs-lookup"><span data-stu-id="ef4a3-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="ef4a3-121">Para obter mais informações sobre como definir e fazer referência a conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ef4a3-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="ef4a3-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ef4a3-122">Example</span></span>

<span data-ttu-id="ef4a3-123">O exemplo seguinte mostra como especificar uma seleção definido para uma vista de lista.</span><span class="sxs-lookup"><span data-stu-id="ef4a3-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="ef4a3-124">O mesmo esquema é usado para exibições de tabela, ampla e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="ef4a3-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="ef4a3-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="ef4a3-125">See Also</span></span>

[<span data-ttu-id="ef4a3-126">Definir conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="ef4a3-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="ef4a3-127">Elemento de ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="ef4a3-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="ef4a3-128">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ef4a3-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
