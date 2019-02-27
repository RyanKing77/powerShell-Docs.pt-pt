---
title: Elemento de dimensionamento automático para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847573"
---
# <a name="autosize-element-for-widecontrol-format"></a><span data-ttu-id="43cfd-102">AutoSize Element for WideControl (Format) (Elemento AutoSize para WideControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="43cfd-102">AutoSize Element for WideControl (Format)</span></span>

<span data-ttu-id="43cfd-103">Especifica se o tamanho da coluna e o número de colunas são ajustados com base no tamanho dos dados.</span><span class="sxs-lookup"><span data-stu-id="43cfd-103">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>

<span data-ttu-id="43cfd-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) Autosize elemento de configuração para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="43cfd-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) Autosize Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="43cfd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43cfd-105">Syntax</span></span>

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="43cfd-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="43cfd-106">Attributes and Elements</span></span>

<span data-ttu-id="43cfd-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `AutoSize` elemento.</span><span class="sxs-lookup"><span data-stu-id="43cfd-107">The following sections describe attributes, child elements, and the parent element of the `AutoSize` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="43cfd-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="43cfd-108">Attributes</span></span>

<span data-ttu-id="43cfd-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="43cfd-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="43cfd-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="43cfd-110">Child Elements</span></span>

<span data-ttu-id="43cfd-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="43cfd-111">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="43cfd-112">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="43cfd-112">Parent Elements</span></span>

|<span data-ttu-id="43cfd-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="43cfd-113">Element</span></span>|<span data-ttu-id="43cfd-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="43cfd-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="43cfd-115">Elemento de WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="43cfd-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="43cfd-116">Define uma vasta (valor único) formato de lista para a vista.</span><span class="sxs-lookup"><span data-stu-id="43cfd-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="43cfd-117">Observações</span><span class="sxs-lookup"><span data-stu-id="43cfd-117">Remarks</span></span>

<span data-ttu-id="43cfd-118">Ao definir uma vista alargada, pode adicionar os `AutoSize` elemento ou o [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) elemento, mas não é possível adicionar ambos.</span><span class="sxs-lookup"><span data-stu-id="43cfd-118">When defining a wide view, you can add the `AutoSize` element or the [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element, but you cannot add both.</span></span>

<span data-ttu-id="43cfd-119">Para obter mais informações sobre os componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="43cfd-119">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="43cfd-120">Para obter um exemplo de uma vista alargada, consulte [vista alargada (básico)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="43cfd-120">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="43cfd-121">Veja Também</span><span class="sxs-lookup"><span data-stu-id="43cfd-121">See Also</span></span>

[<span data-ttu-id="43cfd-122">Elemento de ColumnNumber para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="43cfd-122">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="43cfd-123">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="43cfd-123">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="43cfd-124">Elemento de WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="43cfd-124">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="43cfd-125">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="43cfd-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
