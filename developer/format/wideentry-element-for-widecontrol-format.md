---
title: Elemento de WideEntry para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847181"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="f9e85-102">WideEntry Element for WideControl (Format) (Elemento WideEntry para WideControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="f9e85-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="f9e85-103">Fornece uma definição da vista ampla.</span><span class="sxs-lookup"><span data-stu-id="f9e85-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="f9e85-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry o elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="f9e85-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f9e85-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9e85-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f9e85-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="f9e85-106">Attributes and Elements</span></span>

<span data-ttu-id="f9e85-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `WideEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="f9e85-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="f9e85-108">Tem de especificar um único `WideItem` elemento subordinado.</span><span class="sxs-lookup"><span data-stu-id="f9e85-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f9e85-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f9e85-109">Attributes</span></span>

<span data-ttu-id="f9e85-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f9e85-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f9e85-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="f9e85-111">Child Elements</span></span>

|<span data-ttu-id="f9e85-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="f9e85-112">Element</span></span>|<span data-ttu-id="f9e85-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9e85-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f9e85-114">Elemento de EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f9e85-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="f9e85-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="f9e85-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f9e85-116">Define os tipos do .NET que usam essa definição ampla de entrada ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="f9e85-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="f9e85-117">Elemento de WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="f9e85-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="f9e85-118">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="f9e85-118">Required element.</span></span><br /><br /> <span data-ttu-id="f9e85-119">Define a propriedade ou um script cujo valor é apresentado.</span><span class="sxs-lookup"><span data-stu-id="f9e85-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f9e85-120">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="f9e85-120">Parent Elements</span></span>

|<span data-ttu-id="f9e85-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="f9e85-121">Element</span></span>|<span data-ttu-id="f9e85-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9e85-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f9e85-123">Elemento de WideEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="f9e85-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="f9e85-124">Fornece as definições da vista ampla.</span><span class="sxs-lookup"><span data-stu-id="f9e85-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f9e85-125">Observações</span><span class="sxs-lookup"><span data-stu-id="f9e85-125">Remarks</span></span>

<span data-ttu-id="f9e85-126">Uma vista alargada é um formato de lista que mostra um valor de propriedade de único ou um valor de script para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="f9e85-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="f9e85-127">Ao contrário de outros tipos de vistas, pode especificar apenas um elemento de item para cada definição de vista.</span><span class="sxs-lookup"><span data-stu-id="f9e85-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="f9e85-128">Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f9e85-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f9e85-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f9e85-129">Example</span></span>

<span data-ttu-id="f9e85-130">A exemplo a seguir mostra um `WideEntry` elemento que define uma única `WideItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="f9e85-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="f9e85-131">O `WideItem` elemento define a propriedade cujo valor é apresentado na vista.</span><span class="sxs-lookup"><span data-stu-id="f9e85-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="f9e85-132">Para obter um exemplo completo de uma vista alargada, consulte [vista alargada (básico)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="f9e85-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f9e85-133">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="f9e85-133">See Also</span></span>

[<span data-ttu-id="f9e85-134">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="f9e85-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f9e85-135">Elemento de SelectionCondition para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f9e85-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f9e85-136">Elemento de SelectionSetName para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f9e85-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="f9e85-137">Elemento de TypeName para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="f9e85-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="f9e85-138">Elemento de WideEntries (formato)</span><span class="sxs-lookup"><span data-stu-id="f9e85-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="f9e85-139">Elemento de WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="f9e85-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="f9e85-140">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f9e85-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
