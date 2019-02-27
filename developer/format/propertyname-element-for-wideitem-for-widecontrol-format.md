---
title: Elemento de PropertyName para WideItem para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850282"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="6d644-102">PropertyName Element for WideItem for WideControl (Format) (Elemento PropertyName para WideItem para WideControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="6d644-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="6d644-103">Especifica a propriedade do objeto cujo valor é apresentado na vista alargada.</span><span class="sxs-lookup"><span data-stu-id="6d644-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="6d644-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) WideItem elemento (formato) PropertyName elemento de configuração para WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="6d644-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6d644-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d644-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6d644-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="6d644-106">Attributes and Elements</span></span>

<span data-ttu-id="6d644-107">As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `PropertyName` elemento.</span><span class="sxs-lookup"><span data-stu-id="6d644-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6d644-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="6d644-108">Attributes</span></span>

<span data-ttu-id="6d644-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6d644-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6d644-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="6d644-110">Child Elements</span></span>

<span data-ttu-id="6d644-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6d644-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6d644-112">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="6d644-112">Parent Elements</span></span>

|<span data-ttu-id="6d644-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="6d644-113">Element</span></span>|<span data-ttu-id="6d644-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d644-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d644-115">Elemento de WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="6d644-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="6d644-116">Define a propriedade ou um script cujo valor é apresentado na vista alargada.</span><span class="sxs-lookup"><span data-stu-id="6d644-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6d644-117">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="6d644-117">Text Value</span></span>

<span data-ttu-id="6d644-118">Especifique o nome da propriedade cujo valor é apresentado.</span><span class="sxs-lookup"><span data-stu-id="6d644-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="6d644-119">Observações</span><span class="sxs-lookup"><span data-stu-id="6d644-119">Remarks</span></span>

<span data-ttu-id="6d644-120">Para obter mais informações sobre os componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="6d644-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6d644-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d644-121">Example</span></span>

<span data-ttu-id="6d644-122">Este exemplo mostra uma vista alargada, que exibe o valor da propriedade ProcessName a [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="6d644-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="6d644-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="6d644-123">See Also</span></span>

[<span data-ttu-id="6d644-124">Elemento de WideItem (formato)</span><span class="sxs-lookup"><span data-stu-id="6d644-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="6d644-125">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="6d644-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="6d644-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="6d644-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
