---
title: Elemento de PropertyName para ListItem para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064922"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="fc79b-102">PropertyName Element for ListItem for ListControl (Format) (Elemento PropertyName para ListItem para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="fc79b-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="fc79b-103">Especifica a propriedade de .NET cujo valor é apresentado na lista.</span><span class="sxs-lookup"><span data-stu-id="fc79b-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="fc79b-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento (formato) ListEntry elemento (formato) ListItems elemento (formato) ListItem elemento (formato) PropertyName elemento de configuração para ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="fc79b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fc79b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc79b-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fc79b-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fc79b-106">Attributes and Elements</span></span>

<span data-ttu-id="fc79b-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="fc79b-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fc79b-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="fc79b-108">Attributes</span></span>

<span data-ttu-id="fc79b-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fc79b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fc79b-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="fc79b-110">Child Elements</span></span>

<span data-ttu-id="fc79b-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fc79b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fc79b-112">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="fc79b-112">Parent Elements</span></span>

|<span data-ttu-id="fc79b-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="fc79b-113">Element</span></span>|<span data-ttu-id="fc79b-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc79b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fc79b-115">Elemento de ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="fc79b-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="fc79b-116">Define a propriedade ou um script cujo valor é apresentado na linha da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="fc79b-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fc79b-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="fc79b-117">Text Value</span></span>

<span data-ttu-id="fc79b-118">Especifique o nome da propriedade cujo valor é apresentado.</span><span class="sxs-lookup"><span data-stu-id="fc79b-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc79b-119">Observações</span><span class="sxs-lookup"><span data-stu-id="fc79b-119">Remarks</span></span>

<span data-ttu-id="fc79b-120">Quando este elemento é especificado, não é possível especificar a [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="fc79b-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="fc79b-121">Além de exibir o valor da propriedade, também pode especificar uma etiqueta para o valor ou uma cadeia de caracteres de formato que pode ser utilizada para alterar a apresentação do valor.</span><span class="sxs-lookup"><span data-stu-id="fc79b-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="fc79b-122">Para obter mais informações sobre como especificar os dados numa vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="fc79b-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fc79b-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fc79b-123">Example</span></span>

<span data-ttu-id="fc79b-124">O exemplo seguinte mostra como especificar o rótulo e uma propriedade cujo valor é apresentado.</span><span class="sxs-lookup"><span data-stu-id="fc79b-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="fc79b-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="fc79b-125">See Also</span></span>

[<span data-ttu-id="fc79b-126">Elemento de ScriptBlock para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="fc79b-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="fc79b-127">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="fc79b-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="fc79b-128">Elemento de ListItem para ListControl(Format)</span><span class="sxs-lookup"><span data-stu-id="fc79b-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="fc79b-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc79b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
