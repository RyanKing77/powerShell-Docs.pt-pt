---
title: Elemento da etiqueta para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851290"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="2ce2e-102">Label Element for GroupBy (Format) (Elemento Label para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="2ce2e-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="2ce2e-103">Especifica uma etiqueta que é apresentada quando for detetado um novo grupo.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="2ce2e-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de etiqueta de modo de exibição (formato) para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="2ce2e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2ce2e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ce2e-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2ce2e-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="2ce2e-106">Attributes and Elements</span></span>

<span data-ttu-id="2ce2e-107">As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `Label` elemento.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2ce2e-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="2ce2e-108">Attributes</span></span>

<span data-ttu-id="2ce2e-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2ce2e-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="2ce2e-110">Child Elements</span></span>

<span data-ttu-id="2ce2e-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2ce2e-112">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="2ce2e-112">Parent Elements</span></span>

|<span data-ttu-id="2ce2e-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="2ce2e-113">Element</span></span>|<span data-ttu-id="2ce2e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="2ce2e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ce2e-115">GroupBy elemento para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="2ce2e-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="2ce2e-116">Define a forma como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2ce2e-117">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="2ce2e-117">Text Value</span></span>

<span data-ttu-id="2ce2e-118">Especifique o texto que é apresentado sempre que o Windows PowerShell encontra uma nova propriedade ou o valor de script.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ce2e-119">Observações</span><span class="sxs-lookup"><span data-stu-id="2ce2e-119">Remarks</span></span>

<span data-ttu-id="2ce2e-120">Além do texto especificado por este elemento, o Windows PowerShell apresenta o novo valor que é iniciado o grupo e adiciona uma linha em branco antes e depois o grupo.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="2ce2e-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2ce2e-121">Example</span></span>

<span data-ttu-id="2ce2e-122">O exemplo seguinte mostra a etiqueta para um novo grupo.</span><span class="sxs-lookup"><span data-stu-id="2ce2e-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="2ce2e-123">A etiqueta apresentada teria uma aparência semelhante a este: `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="2ce2e-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="2ce2e-124">Para obter um exemplo de um ficheiro de formatação completado que inclui esse elemento, consulte [vista alargada (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="2ce2e-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2ce2e-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="2ce2e-125">See Also</span></span>

[<span data-ttu-id="2ce2e-126">GroupBy elemento para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="2ce2e-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="2ce2e-127">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="2ce2e-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
