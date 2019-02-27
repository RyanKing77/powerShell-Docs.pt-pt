---
title: Elemento de CustomItem para CustomEntry para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851668"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="23e84-102">CustomItem Element for CustomEntry for Controls for Configuration (Format) (Elemento CustomItem para CustomEntry para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="23e84-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="23e84-103">Define os dados que são apresentados pelo controle e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="23e84-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="23e84-104">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="23e84-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="23e84-105">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de CustomItem de configuração (formato) para CustomEntry para controles de configuração</span><span class="sxs-lookup"><span data-stu-id="23e84-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="23e84-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23e84-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="23e84-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="23e84-107">Attributes and Elements</span></span>

<span data-ttu-id="23e84-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="23e84-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="23e84-109">Para obter mais informações, consulte observações.</span><span class="sxs-lookup"><span data-stu-id="23e84-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="23e84-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="23e84-110">Attributes</span></span>

<span data-ttu-id="23e84-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="23e84-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="23e84-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="23e84-112">Child Elements</span></span>

|<span data-ttu-id="23e84-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="23e84-113">Element</span></span>|<span data-ttu-id="23e84-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="23e84-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="23e84-115">Elemento de ExpressionBinding para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="23e84-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="23e84-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="23e84-116">Optional element.</span></span><br /><br /> <span data-ttu-id="23e84-117">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="23e84-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="23e84-118">Elemento de quadro para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="23e84-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="23e84-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="23e84-119">Optional element.</span></span><br /><br /> <span data-ttu-id="23e84-120">Define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="23e84-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="23e84-121">Elemento de nova linha para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="23e84-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="23e84-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="23e84-122">Optional element.</span></span><br /><br /> <span data-ttu-id="23e84-123">Adiciona uma linha em branco para a exibição do controle.</span><span class="sxs-lookup"><span data-stu-id="23e84-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="23e84-124">Elemento de texto para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="23e84-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="23e84-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="23e84-125">Optional element.</span></span><br /><br /> <span data-ttu-id="23e84-126">Adiciona o texto, como parênteses ou entre colchetes, para a exibição do controle.</span><span class="sxs-lookup"><span data-stu-id="23e84-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="23e84-127">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="23e84-127">Parent Elements</span></span>

|<span data-ttu-id="23e84-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="23e84-128">Element</span></span>|<span data-ttu-id="23e84-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="23e84-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="23e84-130">Elemento de CustomEntry para CustomControl para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="23e84-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="23e84-131">Fornece uma definição do controle.</span><span class="sxs-lookup"><span data-stu-id="23e84-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="23e84-132">Observações</span><span class="sxs-lookup"><span data-stu-id="23e84-132">Remarks</span></span>

<span data-ttu-id="23e84-133">Ao especificar os elementos filho do `CustomItem` elemento, tenha em atenção o seguinte:</span><span class="sxs-lookup"><span data-stu-id="23e84-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="23e84-134">Os elementos filho tem de ser adicionados a seguinte sequência: `ExpressionBinding`, `NewLine`, `Text`, e `Frame`.</span><span class="sxs-lookup"><span data-stu-id="23e84-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="23e84-135">Não existe nenhum limite máximo para o número de sequências de que pode especificar.</span><span class="sxs-lookup"><span data-stu-id="23e84-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="23e84-136">Em cada sequência, não há nenhum limite máximo para o número de `ExpressionBinding` elementos que pode utilizar.</span><span class="sxs-lookup"><span data-stu-id="23e84-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="23e84-137">Veja Também</span><span class="sxs-lookup"><span data-stu-id="23e84-137">See Also</span></span>

[<span data-ttu-id="23e84-138">Elemento de ExpressionBinding para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="23e84-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="23e84-139">Elemento de quadro para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="23e84-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="23e84-140">Elemento de nova linha para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="23e84-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="23e84-141">Elemento de texto para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="23e84-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="23e84-142">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="23e84-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
