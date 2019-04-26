---
title: Elemento de ScriptBlock para ListItem para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064582"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="c02ff-102">ScriptBlock Element for ListItem for ListControl (Format) (Elemento ScriptBlock para ListItem para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="c02ff-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="c02ff-103">Especifica o script cujo valor é apresentado na linha.</span><span class="sxs-lookup"><span data-stu-id="c02ff-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="c02ff-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry ListControl (formato) para ListEntries para o elemento de ListItems ListControl (formato) para ListEntry para o elemento de ListItem ListControl (formato) para ListItems para o elemento de ScriptBlock ListControl (formato) para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c02ff-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c02ff-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c02ff-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c02ff-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c02ff-106">Attributes and Elements</span></span>

<span data-ttu-id="c02ff-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="c02ff-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c02ff-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="c02ff-108">Attributes</span></span>

<span data-ttu-id="c02ff-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c02ff-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c02ff-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="c02ff-110">Child Elements</span></span>

<span data-ttu-id="c02ff-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c02ff-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c02ff-112">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="c02ff-112">Parent Elements</span></span>

|<span data-ttu-id="c02ff-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="c02ff-113">Element</span></span>|<span data-ttu-id="c02ff-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c02ff-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c02ff-115">Elemento de ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="c02ff-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="c02ff-116">Define a propriedade ou um script cujo valor é apresentado numa linha da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="c02ff-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c02ff-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="c02ff-117">Text Value</span></span>

<span data-ttu-id="c02ff-118">Especifique o script cujo valor é apresentado na linha.</span><span class="sxs-lookup"><span data-stu-id="c02ff-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="c02ff-119">Observações</span><span class="sxs-lookup"><span data-stu-id="c02ff-119">Remarks</span></span>

<span data-ttu-id="c02ff-120">Quando este elemento é especificado, não é possível especificar a [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="c02ff-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="c02ff-121">Para obter mais informações sobre como especificar scripts numa vista de lista, consulte [vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="c02ff-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c02ff-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c02ff-122">Example</span></span>

<span data-ttu-id="c02ff-123">O exemplo seguinte mostra como especificar a propriedade cujo valor é apresentado.</span><span class="sxs-lookup"><span data-stu-id="c02ff-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="c02ff-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="c02ff-124">See Also</span></span>

[<span data-ttu-id="c02ff-125">Elemento de PropertyName para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c02ff-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="c02ff-126">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="c02ff-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c02ff-127">Elemento de ListItem para ListItems para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="c02ff-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="c02ff-128">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c02ff-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
