---
title: Quadro elemento para CustomItem para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851696"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="a1f0b-102">Frame Element for CustomItem for Controls for Configuration (Format) (Elemento Frame para CustomItem para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="a1f0b-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="a1f0b-103">Define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="a1f0b-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="a1f0b-104">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="a1f0b-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="a1f0b-105">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de CustomItem de configuração (formato) para CustomEntry para controles para o elemento de quadro de configuração para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a1f0b-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a1f0b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1f0b-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a1f0b-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="a1f0b-107">Attributes and Elements</span></span>

<span data-ttu-id="a1f0b-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="a1f0b-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a1f0b-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="a1f0b-109">Attributes</span></span>

<span data-ttu-id="a1f0b-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a1f0b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a1f0b-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="a1f0b-111">Child Elements</span></span>

|<span data-ttu-id="a1f0b-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1f0b-112">Element</span></span>|<span data-ttu-id="a1f0b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1f0b-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="a1f0b-114">Elemento necessário</span><span class="sxs-lookup"><span data-stu-id="a1f0b-114">Required Element</span></span>|
|[<span data-ttu-id="a1f0b-115">Elemento de FirstLineHanging para quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a1f0b-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="a1f0b-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a1f0b-116">Optional element.</span></span><br /><br /> <span data-ttu-id="a1f0b-117">Especifica o número de carateres a primeira linha dos dados é desviada à esquerda.</span><span class="sxs-lookup"><span data-stu-id="a1f0b-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="a1f0b-118">Elemento de FirstLineIndent para quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a1f0b-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="a1f0b-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a1f0b-119">Optional element.</span></span><br /><br /> <span data-ttu-id="a1f0b-120">Especifica o número de carateres a primeira linha dos dados é desviada à direita.</span><span class="sxs-lookup"><span data-stu-id="a1f0b-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="a1f0b-121">Elemento de LeftIndent para quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a1f0b-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="a1f0b-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a1f0b-122">Optional element.</span></span><br /><br /> <span data-ttu-id="a1f0b-123">Especifica o número de carateres de dados são desviados da margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="a1f0b-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="a1f0b-124">Elemento de RightIndent para quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a1f0b-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="a1f0b-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="a1f0b-125">Optional element.</span></span><br /><br /> <span data-ttu-id="a1f0b-126">Especifica o número de carateres de dados são desviados da margem direita.</span><span class="sxs-lookup"><span data-stu-id="a1f0b-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a1f0b-127">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="a1f0b-127">Parent Elements</span></span>

|<span data-ttu-id="a1f0b-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="a1f0b-128">Element</span></span>|<span data-ttu-id="a1f0b-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1f0b-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1f0b-130">Elemento de CustomItem para CustomEntry para controles de configuração</span><span class="sxs-lookup"><span data-stu-id="a1f0b-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="a1f0b-131">Define os dados que são apresentados pelo controle e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="a1f0b-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a1f0b-132">Observações</span><span class="sxs-lookup"><span data-stu-id="a1f0b-132">Remarks</span></span>

<span data-ttu-id="a1f0b-133">Não é possível especificar a [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elementos na mesma `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="a1f0b-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1f0b-134">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="a1f0b-134">See Also</span></span>

[<span data-ttu-id="a1f0b-135">Elemento de FirstLineHanging para quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a1f0b-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="a1f0b-136">Elemento de FirstLineIndent para quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a1f0b-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="a1f0b-137">Elemento de LeftIndent para quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a1f0b-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="a1f0b-138">Elemento de RightIndent para quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="a1f0b-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="a1f0b-139">Elemento de CustomItem para CustomEntry para controles de configuração</span><span class="sxs-lookup"><span data-stu-id="a1f0b-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="a1f0b-140">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a1f0b-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
