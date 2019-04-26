---
title: Elemento de ScriptBlock para WideItem para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064208"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="b4f7f-102">ScriptBlock Element for WideItem for WideControl (Format) (Elemento ScriptBlock para WideItem para WideControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="b4f7f-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="b4f7f-103">Especifica o script cujo valor é apresentado na vista alargada.</span><span class="sxs-lookup"><span data-stu-id="b4f7f-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="b4f7f-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) WideItem elemento (formato) ScriptBlock elemento de configuração para WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="b4f7f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b4f7f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4f7f-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b4f7f-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b4f7f-106">Attributes and Elements</span></span>

<span data-ttu-id="b4f7f-107">As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="b4f7f-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b4f7f-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="b4f7f-108">Attributes</span></span>

<span data-ttu-id="b4f7f-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b4f7f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b4f7f-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="b4f7f-110">Child Elements</span></span>

<span data-ttu-id="b4f7f-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b4f7f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b4f7f-112">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="b4f7f-112">Parent Elements</span></span>

|<span data-ttu-id="b4f7f-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="b4f7f-113">Element</span></span>|<span data-ttu-id="b4f7f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4f7f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4f7f-115">Elemento de WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="b4f7f-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="b4f7f-116">Define o bloco de script ou propriedade cujo valor é apresentado na vista alargada.</span><span class="sxs-lookup"><span data-stu-id="b4f7f-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b4f7f-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="b4f7f-117">Text Value</span></span>

<span data-ttu-id="b4f7f-118">Especifique o script cujo valor é apresentado.</span><span class="sxs-lookup"><span data-stu-id="b4f7f-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4f7f-119">Observações</span><span class="sxs-lookup"><span data-stu-id="b4f7f-119">Remarks</span></span>

<span data-ttu-id="b4f7f-120">Para obter mais informações sobre os componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="b4f7f-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b4f7f-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b4f7f-121">Example</span></span>

<span data-ttu-id="b4f7f-122">Este exemplo mostra um `WideItem` elemento que define um script cujo valor é apresentado na vista.</span><span class="sxs-lookup"><span data-stu-id="b4f7f-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="b4f7f-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="b4f7f-123">See Also</span></span>

[<span data-ttu-id="b4f7f-124">Elemento de WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="b4f7f-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="b4f7f-125">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="b4f7f-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b4f7f-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b4f7f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
