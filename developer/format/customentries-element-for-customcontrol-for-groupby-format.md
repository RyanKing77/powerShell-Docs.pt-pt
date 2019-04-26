---
title: Elemento de CustomEntries para CustomControl para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066549"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="f7a81-102">CustomEntries Element for CustomControl for GroupBy (Format) (Elemento CustomEntries para CustomControl para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="f7a81-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="f7a81-103">Fornece as definições para o controle.</span><span class="sxs-lookup"><span data-stu-id="f7a81-103">Provides the definitions for the control.</span></span> <span data-ttu-id="f7a81-104">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="f7a81-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="f7a81-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f7a81-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f7a81-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7a81-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f7a81-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f7a81-107">Attributes and Elements</span></span>

<span data-ttu-id="f7a81-108">As secções seguintes descrevem os atributos e elementos de principal de elementos filho do `CustomEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="f7a81-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="f7a81-109">Não existe nenhum limite máximo para o número de elementos filho que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="f7a81-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="f7a81-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="f7a81-110">Attributes</span></span>

<span data-ttu-id="f7a81-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f7a81-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f7a81-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="f7a81-112">Child Elements</span></span>

|<span data-ttu-id="f7a81-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="f7a81-113">Element</span></span>|<span data-ttu-id="f7a81-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7a81-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7a81-115">Elemento de CustomEntry para CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f7a81-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="f7a81-116">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="f7a81-116">Required element.</span></span><br /><br /> <span data-ttu-id="f7a81-117">Fornece uma definição do controle.</span><span class="sxs-lookup"><span data-stu-id="f7a81-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f7a81-118">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="f7a81-118">Parent Elements</span></span>

|<span data-ttu-id="f7a81-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="f7a81-119">Element</span></span>|<span data-ttu-id="f7a81-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7a81-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7a81-121">Elemento de CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f7a81-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="f7a81-122">Define o controle personalizado que exibe o novo grupo.</span><span class="sxs-lookup"><span data-stu-id="f7a81-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f7a81-123">Observações</span><span class="sxs-lookup"><span data-stu-id="f7a81-123">Remarks</span></span>

<span data-ttu-id="f7a81-124">Na maioria dos casos, um controle tiver apenas uma definição, o que é especificada num único `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="f7a81-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="f7a81-125">No entanto, é possível fornecer várias definições, se pretender utilizar o mesmo controlo para apresentar grupos diferentes.</span><span class="sxs-lookup"><span data-stu-id="f7a81-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="f7a81-126">Nesses casos, pode definir um `CustomEntry` elemento para um grupo.</span><span class="sxs-lookup"><span data-stu-id="f7a81-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7a81-127">Veja Também</span><span class="sxs-lookup"><span data-stu-id="f7a81-127">See Also</span></span>

[<span data-ttu-id="f7a81-128">Elemento de CustomEntry para CustomEntries para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="f7a81-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="f7a81-129">Elemento de CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f7a81-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="f7a81-130">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f7a81-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
