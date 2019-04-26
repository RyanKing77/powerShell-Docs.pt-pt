---
title: Elemento de CustomItem para CustomEntry para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066418"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="423c5-102">CustomItem Element for CustomEntry for CustomControl for View (Format) (Elemento CustomItem para CustomEntry para CustomControl para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="423c5-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="423c5-103">Define os dados que são apresentados pela vista do controle personalizado e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="423c5-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="423c5-104">Este elemento é utilizado ao definir uma vista de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="423c5-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="423c5-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para exibição (formato) CustomItem elemento para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="423c5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="423c5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="423c5-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="423c5-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="423c5-107">Attributes and Elements</span></span>

<span data-ttu-id="423c5-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="423c5-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="423c5-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="423c5-109">Attributes</span></span>

<span data-ttu-id="423c5-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="423c5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="423c5-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="423c5-111">Child Elements</span></span>

|<span data-ttu-id="423c5-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="423c5-112">Element</span></span>|<span data-ttu-id="423c5-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="423c5-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="423c5-114">Elemento de ExpressionBinding para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="423c5-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="423c5-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="423c5-115">Optional element.</span></span><br /><br /> <span data-ttu-id="423c5-116">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="423c5-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="423c5-117">Elemento de quadro para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="423c5-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="423c5-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="423c5-118">Optional element.</span></span><br /><br /> <span data-ttu-id="423c5-119">Define os dados que são apresentados pela vista do controle personalizado e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="423c5-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="423c5-120">Elemento de nova linha para CustomItem para controle personalizado para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="423c5-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="423c5-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="423c5-121">Optional element.</span></span><br /><br /> <span data-ttu-id="423c5-122">Adiciona uma linha em branco para a exibição do controle.</span><span class="sxs-lookup"><span data-stu-id="423c5-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="423c5-123">Elemento de texto para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="423c5-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="423c5-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="423c5-124">Optional element.</span></span><br /><br /> <span data-ttu-id="423c5-125">Especifica o texto adicional para os dados apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="423c5-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="423c5-126">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="423c5-126">Parent Elements</span></span>

|<span data-ttu-id="423c5-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="423c5-127">Element</span></span>|<span data-ttu-id="423c5-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="423c5-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="423c5-129">Elemento de CustomEntry para CustomEntries para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="423c5-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="423c5-130">Fornece uma definição de vista do controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="423c5-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="423c5-131">Observações</span><span class="sxs-lookup"><span data-stu-id="423c5-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="423c5-132">Veja Também</span><span class="sxs-lookup"><span data-stu-id="423c5-132">See Also</span></span>

[<span data-ttu-id="423c5-133">Elemento de CustomEntry para CustomEntries para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="423c5-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="423c5-134">Elemento de ExpressionBinding para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="423c5-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="423c5-135">Elemento de quadro para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="423c5-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="423c5-136">Elemento de nova linha para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="423c5-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="423c5-137">Elemento de texto para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="423c5-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="423c5-138">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="423c5-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
