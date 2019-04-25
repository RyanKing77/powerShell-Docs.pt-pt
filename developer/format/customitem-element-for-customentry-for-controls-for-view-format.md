---
title: Elemento de CustomItem para CustomEntry para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066386"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="13d51-102">CustomItem Element for CustomEntry for Controls for View (Format) (Elemento CustomItem para CustomEntry para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="13d51-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="13d51-103">Define os dados que são apresentados pelo controle e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="13d51-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="13d51-104">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="13d51-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="13d51-105">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) CustomItem elemento para CustomEntry para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="13d51-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="13d51-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13d51-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="13d51-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="13d51-107">Attributes and Elements</span></span>

<span data-ttu-id="13d51-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="13d51-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="13d51-109">Para obter mais informações, consulte observações.</span><span class="sxs-lookup"><span data-stu-id="13d51-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="13d51-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="13d51-110">Attributes</span></span>

<span data-ttu-id="13d51-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="13d51-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="13d51-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="13d51-112">Child Elements</span></span>

|<span data-ttu-id="13d51-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="13d51-113">Element</span></span>|<span data-ttu-id="13d51-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="13d51-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13d51-115">Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="13d51-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="13d51-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="13d51-116">Optional element.</span></span><br /><br /> <span data-ttu-id="13d51-117">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="13d51-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="13d51-118">Elemento de quadro para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="13d51-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="13d51-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="13d51-119">Optional element.</span></span><br /><br /> <span data-ttu-id="13d51-120">Define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="13d51-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="13d51-121">Elemento de nova linha para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="13d51-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="13d51-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="13d51-122">Optional element.</span></span><br /><br /> <span data-ttu-id="13d51-123">Adiciona uma linha em branco para a exibição do controle.</span><span class="sxs-lookup"><span data-stu-id="13d51-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="13d51-124">Elemento de texto para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="13d51-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="13d51-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="13d51-125">Optional element.</span></span><br /><br /> <span data-ttu-id="13d51-126">Adiciona o texto, como parênteses ou entre colchetes, para a exibição do controle.</span><span class="sxs-lookup"><span data-stu-id="13d51-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="13d51-127">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="13d51-127">Parent Elements</span></span>

|<span data-ttu-id="13d51-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="13d51-128">Element</span></span>|<span data-ttu-id="13d51-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="13d51-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13d51-130">Elemento de CustomEntry para CustomEntries para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="13d51-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="13d51-131">Fornece uma definição do controle.</span><span class="sxs-lookup"><span data-stu-id="13d51-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="13d51-132">Observações</span><span class="sxs-lookup"><span data-stu-id="13d51-132">Remarks</span></span>

<span data-ttu-id="13d51-133">Ao especificar os elementos filho do `CustomItem` elemento, tenha em atenção o seguinte:</span><span class="sxs-lookup"><span data-stu-id="13d51-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="13d51-134">Os elementos filho tem de ser adicionados a seguinte sequência: `ExpressionBinding`, `NewLine`, `Text`, e `Frame`.</span><span class="sxs-lookup"><span data-stu-id="13d51-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="13d51-135">Não existe nenhum limite máximo para o número de sequências de que pode especificar.</span><span class="sxs-lookup"><span data-stu-id="13d51-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="13d51-136">Em cada sequência, não há nenhum limite máximo para o número de `ExpressionBinding` elementos que pode utilizar.</span><span class="sxs-lookup"><span data-stu-id="13d51-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="13d51-137">Veja Também</span><span class="sxs-lookup"><span data-stu-id="13d51-137">See Also</span></span>

[<span data-ttu-id="13d51-138">Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="13d51-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="13d51-139">Elemento de quadro para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="13d51-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="13d51-140">Elemento de nova linha para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="13d51-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="13d51-141">Elemento de texto para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="13d51-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="13d51-142">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="13d51-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
