---
title: Elemento de CustomEntry para CustomControl para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066490"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="5219b-102">CustomEntry Element for CustomControl for GroupBy (Format) (Elemento CustomEntry para CustomControl para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="5219b-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="5219b-103">Fornece uma definição do controle.</span><span class="sxs-lookup"><span data-stu-id="5219b-103">Provides a definition of the control.</span></span> <span data-ttu-id="5219b-104">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="5219b-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="5219b-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="5219b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5219b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5219b-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5219b-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5219b-107">Attributes and Elements</span></span>

<span data-ttu-id="5219b-108">As secções seguintes descrevem os atributos e elementos filho e os elementos pai do `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="5219b-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5219b-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="5219b-109">Attributes</span></span>

<span data-ttu-id="5219b-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5219b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5219b-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="5219b-111">Child Elements</span></span>

|<span data-ttu-id="5219b-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="5219b-112">Element</span></span>|<span data-ttu-id="5219b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="5219b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5219b-114">Elemento de EntrySelectedBy para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="5219b-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="5219b-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5219b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5219b-116">Define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="5219b-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="5219b-117">Elemento de CustomItem para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="5219b-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="5219b-118">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="5219b-118">Required element.</span></span><br /><br /> <span data-ttu-id="5219b-119">Define como o controle exibe os dados.</span><span class="sxs-lookup"><span data-stu-id="5219b-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5219b-120">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="5219b-120">Parent Elements</span></span>

|<span data-ttu-id="5219b-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="5219b-121">Element</span></span>|<span data-ttu-id="5219b-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="5219b-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5219b-123">Elemento de CustomEntries para CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="5219b-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="5219b-124">Fornece as definições para o controle.</span><span class="sxs-lookup"><span data-stu-id="5219b-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5219b-125">Observações</span><span class="sxs-lookup"><span data-stu-id="5219b-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="5219b-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="5219b-126">See Also</span></span>

[<span data-ttu-id="5219b-127">Elemento de EntrySelectedBy para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="5219b-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="5219b-128">Elemento de CustomItem para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="5219b-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="5219b-129">Elemento de CustomEntries para CustomControl para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="5219b-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="5219b-130">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5219b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
