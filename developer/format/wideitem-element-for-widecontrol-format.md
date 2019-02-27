---
title: Elemento de WideItem para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851451"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="7aaff-102">WideItem Element for WideControl (Format) (Elemento WideItem para WideControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="7aaff-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="7aaff-103">Define a propriedade ou um script cujo valor é apresentado.</span><span class="sxs-lookup"><span data-stu-id="7aaff-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="7aaff-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) WideItem elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="7aaff-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7aaff-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7aaff-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7aaff-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="7aaff-106">Attributes and Elements</span></span>

<span data-ttu-id="7aaff-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `WideItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="7aaff-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="7aaff-108">O `FormatString` elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="7aaff-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="7aaff-109">No entanto, tem de especificar um `PropertyName` ou `ScriptBlock` elemento, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="7aaff-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="7aaff-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="7aaff-110">Attributes</span></span>

<span data-ttu-id="7aaff-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7aaff-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7aaff-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="7aaff-112">Child Elements</span></span>

|<span data-ttu-id="7aaff-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="7aaff-113">Element</span></span>|<span data-ttu-id="7aaff-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="7aaff-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7aaff-115">Elemento de FormatString para WideItem para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="7aaff-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="7aaff-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="7aaff-116">Optional element.</span></span><br /><br /> <span data-ttu-id="7aaff-117">Especifica um padrão de formato que define como o valor de propriedade ou um script é apresentado na vista.</span><span class="sxs-lookup"><span data-stu-id="7aaff-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="7aaff-118">Elemento de PropertyName para WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="7aaff-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="7aaff-119">Especifica a propriedade do objeto cujo valor é apresentado na vista alargada.</span><span class="sxs-lookup"><span data-stu-id="7aaff-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="7aaff-120">Elemento de ScriptBlock para WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="7aaff-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="7aaff-121">Especifica o script cujo valor é apresentado na vista alargada.</span><span class="sxs-lookup"><span data-stu-id="7aaff-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7aaff-122">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="7aaff-122">Parent Elements</span></span>

|<span data-ttu-id="7aaff-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="7aaff-123">Element</span></span>|<span data-ttu-id="7aaff-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="7aaff-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7aaff-125">Elemento de WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="7aaff-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="7aaff-126">Fornece uma definição da vista ampla.</span><span class="sxs-lookup"><span data-stu-id="7aaff-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7aaff-127">Observações</span><span class="sxs-lookup"><span data-stu-id="7aaff-127">Remarks</span></span>

<span data-ttu-id="7aaff-128">Para obter mais informações sobre os componentes de uma vista alargada, consulte [vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="7aaff-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7aaff-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7aaff-129">Example</span></span>

<span data-ttu-id="7aaff-130">A exemplo a seguir mostra um `WideEntry` elemento que define uma única `WideItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="7aaff-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="7aaff-131">O `WideItem` elemento define a propriedade ou um script cujo valor é apresentado na vista.</span><span class="sxs-lookup"><span data-stu-id="7aaff-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="7aaff-132">Para obter um exemplo completo de uma vista alargada, consulte [vista alargada (básico)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="7aaff-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7aaff-133">Veja Também</span><span class="sxs-lookup"><span data-stu-id="7aaff-133">See Also</span></span>

[<span data-ttu-id="7aaff-134">Elemento de FormatString para WideItem para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="7aaff-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="7aaff-135">Elemento de PropertyName para WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="7aaff-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="7aaff-136">Elemento de ScriptBlock para WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="7aaff-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="7aaff-137">Elemento de WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="7aaff-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="7aaff-138">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="7aaff-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
