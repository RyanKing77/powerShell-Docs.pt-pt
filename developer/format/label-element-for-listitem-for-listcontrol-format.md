---
title: Elemento da etiqueta para ListItem para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845956"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="51b70-102">Label Element for ListItem for ListControl (Format) (Elemento Label para ListItem para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="51b70-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="51b70-103">Especifica a etiqueta que é apresentada à esquerda do valor de propriedade ou um script na linha.</span><span class="sxs-lookup"><span data-stu-id="51b70-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="51b70-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry ListControl (formato) para ListItems ListControl (formato) para ListEntry para ListControl elemento ( Elemento de ListItem do formato) para ListItems para o elemento de etiqueta ListControl (formato) para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="51b70-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="51b70-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51b70-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="51b70-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="51b70-106">Attributes and Elements</span></span>

<span data-ttu-id="51b70-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Label` elemento.</span><span class="sxs-lookup"><span data-stu-id="51b70-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="51b70-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="51b70-108">Attributes</span></span>

<span data-ttu-id="51b70-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="51b70-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="51b70-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="51b70-110">Child Elements</span></span>

<span data-ttu-id="51b70-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="51b70-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="51b70-112">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="51b70-112">Parent Elements</span></span>

|<span data-ttu-id="51b70-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="51b70-113">Element</span></span>|<span data-ttu-id="51b70-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="51b70-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51b70-115">Elemento de ListItem para ListItems para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="51b70-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="51b70-116">Define a propriedade ou um script cujo valor é apresentado numa linha da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="51b70-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="51b70-117">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="51b70-117">Text Value</span></span>

<span data-ttu-id="51b70-118">Especifique a etiqueta a ser exibida para a esquerda do valor de propriedade ou script.</span><span class="sxs-lookup"><span data-stu-id="51b70-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="51b70-119">Observações</span><span class="sxs-lookup"><span data-stu-id="51b70-119">Remarks</span></span>

<span data-ttu-id="51b70-120">Se uma etiqueta não for especificada, é apresentado o nome da propriedade ou o script.</span><span class="sxs-lookup"><span data-stu-id="51b70-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="51b70-121">Para obter mais informações sobre como utilizar as etiquetas numa vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="51b70-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="51b70-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51b70-122">Example</span></span>

<span data-ttu-id="51b70-123">O exemplo seguinte mostra como adicionar uma etiqueta para uma linha.</span><span class="sxs-lookup"><span data-stu-id="51b70-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="51b70-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="51b70-124">See Also</span></span>

[<span data-ttu-id="51b70-125">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="51b70-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="51b70-126">Elemento de ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="51b70-126">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="51b70-127">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="51b70-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
