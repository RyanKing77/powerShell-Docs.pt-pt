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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076230"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="a518e-102">SelectionSetName Element for ViewSelectedBy (Format) (Elemento SelectionSetName para ViewSelectedBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="a518e-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="a518e-103">Especifica um conjunto de objetos do .NET que são apresentados pela exibição.</span><span class="sxs-lookup"><span data-stu-id="a518e-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="a518e-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ViewSelectedBy elemento (formato) SelectionSetName elemento de configuração para ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="a518e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a518e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a518e-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a518e-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a518e-106">Attributes and Elements</span></span>

<span data-ttu-id="a518e-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="a518e-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a518e-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="a518e-108">Attributes</span></span>

<span data-ttu-id="a518e-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a518e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a518e-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="a518e-110">Child Elements</span></span>

<span data-ttu-id="a518e-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a518e-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a518e-112">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="a518e-112">Parent Elements</span></span>

|<span data-ttu-id="a518e-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="a518e-113">Element</span></span>|<span data-ttu-id="a518e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a518e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a518e-115">Elemento de ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="a518e-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="a518e-116">Define os objetos do .NET que são apresentados pela exibição.</span><span class="sxs-lookup"><span data-stu-id="a518e-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a518e-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="a518e-117">Text Value</span></span>

<span data-ttu-id="a518e-118">Especifique o nome do conjunto de seleção que é definido pelo `Name` elemento para o conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="a518e-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="a518e-119">Observações</span><span class="sxs-lookup"><span data-stu-id="a518e-119">Remarks</span></span>

<span data-ttu-id="a518e-120">É possível utilizar conjuntos de seleção quando tem um conjunto de objetos relacionados que deseja fazer referência ao utilizar um nome único, como um conjunto de objetos que estão relacionados por meio de herança.</span><span class="sxs-lookup"><span data-stu-id="a518e-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="a518e-121">Para obter mais informações sobre como definir e fazer referência a conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a518e-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="a518e-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a518e-122">Example</span></span>

<span data-ttu-id="a518e-123">O exemplo seguinte mostra como especificar uma seleção definido para uma vista de lista.</span><span class="sxs-lookup"><span data-stu-id="a518e-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="a518e-124">O mesmo esquema é usado para exibições de tabela, ampla e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="a518e-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="a518e-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="a518e-125">See Also</span></span>

[<span data-ttu-id="a518e-126">Definir conjuntos de seleção</span><span class="sxs-lookup"><span data-stu-id="a518e-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a518e-127">Elemento de ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="a518e-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="a518e-128">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a518e-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
