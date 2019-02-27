---
title: Estruturar o elemento para CustomItem para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849484"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="dee3e-102">Frame Element for CustomItem for Controls for View (Format) (Elemento Frame para CustomItem para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="dee3e-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="dee3e-103">Define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="dee3e-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="dee3e-104">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="dee3e-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="dee3e-105">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) CustomItem elemento para CustomEntry para controles para o elemento de quadro de modo de exibição (formato) para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="dee3e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dee3e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dee3e-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dee3e-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="dee3e-107">Attributes and Elements</span></span>

<span data-ttu-id="dee3e-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="dee3e-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dee3e-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="dee3e-109">Attributes</span></span>

<span data-ttu-id="dee3e-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="dee3e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dee3e-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="dee3e-111">Child Elements</span></span>

|<span data-ttu-id="dee3e-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="dee3e-112">Element</span></span>|<span data-ttu-id="dee3e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="dee3e-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="dee3e-114">Elemento necessário</span><span class="sxs-lookup"><span data-stu-id="dee3e-114">Required Element</span></span>|
|[<span data-ttu-id="dee3e-115">Elemento de FirstLineHanging do quadro de controles de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="dee3e-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="dee3e-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="dee3e-116">Optional element.</span></span><br /><br /> <span data-ttu-id="dee3e-117">Especifica o número de carateres a primeira linha é desviada à esquerda.</span><span class="sxs-lookup"><span data-stu-id="dee3e-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="dee3e-118">Elemento de FirstLineIndent do quadro de controles de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="dee3e-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="dee3e-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="dee3e-119">Optional element.</span></span><br /><br /> <span data-ttu-id="dee3e-120">Especifica o número de carateres a primeira linha é desviada à direita.</span><span class="sxs-lookup"><span data-stu-id="dee3e-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="dee3e-121">Elemento de LeftIndent do quadro de controles de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="dee3e-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="dee3e-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="dee3e-122">Optional element.</span></span><br /><br /> <span data-ttu-id="dee3e-123">Especifica o número de carateres de dados são desviados da margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="dee3e-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="dee3e-124">Elemento de RightIndent do quadro de controles de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="dee3e-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="dee3e-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="dee3e-125">Optional element.</span></span><br /><br /> <span data-ttu-id="dee3e-126">Especifica o número de carateres de dados são desviados da margem direita.</span><span class="sxs-lookup"><span data-stu-id="dee3e-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dee3e-127">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="dee3e-127">Parent Elements</span></span>

|<span data-ttu-id="dee3e-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="dee3e-128">Element</span></span>|<span data-ttu-id="dee3e-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="dee3e-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dee3e-130">Elemento de CustomItem para CustomEntry para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="dee3e-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="dee3e-131">Define os dados que são apresentados pelo controle e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="dee3e-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dee3e-132">Observações</span><span class="sxs-lookup"><span data-stu-id="dee3e-132">Remarks</span></span>

<span data-ttu-id="dee3e-133">Não é possível especificar a [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elementos na mesma `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="dee3e-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="dee3e-134">Veja Também</span><span class="sxs-lookup"><span data-stu-id="dee3e-134">See Also</span></span>

[<span data-ttu-id="dee3e-135">Elemento de FirstLineHanging do quadro de controles de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="dee3e-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="dee3e-136">Elemento de FirstLineIndent do quadro de controles de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="dee3e-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="dee3e-137">Elemento de LeftIndent do quadro de controles de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="dee3e-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="dee3e-138">Elemento de RightIndent do quadro de controles de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="dee3e-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="dee3e-139">Elemento de CustomItem para CustomEntry para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="dee3e-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="dee3e-140">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="dee3e-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
