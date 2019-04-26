---
title: Elemento de WideEntries para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083693"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="0158a-102">WideEntries Element for WideControl (Format) (Elemento WideEntries para WideControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="0158a-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="0158a-103">Fornece as definições da vista ampla.</span><span class="sxs-lookup"><span data-stu-id="0158a-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="0158a-104">A vista alargada tem de especificar uma ou mais definições.</span><span class="sxs-lookup"><span data-stu-id="0158a-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="0158a-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries o elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="0158a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0158a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0158a-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="0158a-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0158a-107">Attributes and Elements</span></span>

<span data-ttu-id="0158a-108">As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `WideEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="0158a-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="0158a-109">Elemento, pelo menos, um subordinado tem de ser especificado.</span><span class="sxs-lookup"><span data-stu-id="0158a-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="0158a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0158a-110">Attributes</span></span>

<span data-ttu-id="0158a-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0158a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0158a-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="0158a-112">Child Elements</span></span>

|<span data-ttu-id="0158a-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="0158a-113">Element</span></span>|<span data-ttu-id="0158a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="0158a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0158a-115">Elemento de WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="0158a-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="0158a-116">Fornece uma definição da vista ampla.</span><span class="sxs-lookup"><span data-stu-id="0158a-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0158a-117">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="0158a-117">Parent Elements</span></span>

|<span data-ttu-id="0158a-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="0158a-118">Element</span></span>|<span data-ttu-id="0158a-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="0158a-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0158a-120">Elemento de WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="0158a-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="0158a-121">Define uma vasta (valor único) formato de lista para a vista.</span><span class="sxs-lookup"><span data-stu-id="0158a-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0158a-122">Observações</span><span class="sxs-lookup"><span data-stu-id="0158a-122">Remarks</span></span>

<span data-ttu-id="0158a-123">Uma vista alargada é um formato de lista que mostra um valor de propriedade de único ou um valor de script para cada objeto.</span><span class="sxs-lookup"><span data-stu-id="0158a-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="0158a-124">Para obter mais informações sobre os componentes de uma vista alargada, consulte [ampla componentes de exibição](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="0158a-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0158a-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0158a-125">Example</span></span>

<span data-ttu-id="0158a-126">A exemplo a seguir mostra um `WideEntries` elemento que define uma única `WideEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="0158a-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="0158a-127">O `WideEntry` elemento contém um único `WideItem` elemento que define qual o valor de propriedade ou um script é apresentado na vista.</span><span class="sxs-lookup"><span data-stu-id="0158a-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="0158a-128">Para obter um exemplo completo de uma vista alargada, consulte [vista alargada (básico)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="0158a-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0158a-129">Veja Também</span><span class="sxs-lookup"><span data-stu-id="0158a-129">See Also</span></span>

[<span data-ttu-id="0158a-130">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="0158a-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="0158a-131">Elemento de WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="0158a-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="0158a-132">Elemento de WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="0158a-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="0158a-133">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="0158a-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
