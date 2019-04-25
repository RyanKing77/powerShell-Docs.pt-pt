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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065568"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="e25fa-102">Frame Element for CustomItem for Controls for Configuration (Format) (Elemento Frame para CustomItem para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="e25fa-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e25fa-103">Define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="e25fa-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="e25fa-104">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="e25fa-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e25fa-105">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de CustomItem de configuração (formato) para CustomEntry para controles para o elemento de quadro de configuração para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e25fa-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e25fa-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e25fa-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e25fa-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e25fa-107">Attributes and Elements</span></span>

<span data-ttu-id="e25fa-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="e25fa-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e25fa-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="e25fa-109">Attributes</span></span>

<span data-ttu-id="e25fa-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e25fa-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e25fa-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="e25fa-111">Child Elements</span></span>

|<span data-ttu-id="e25fa-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="e25fa-112">Element</span></span>|<span data-ttu-id="e25fa-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e25fa-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="e25fa-114">Elemento necessário</span><span class="sxs-lookup"><span data-stu-id="e25fa-114">Required Element</span></span>|
|[<span data-ttu-id="e25fa-115">Elemento de FirstLineHanging para quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e25fa-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="e25fa-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e25fa-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e25fa-117">Especifica o número de carateres a primeira linha dos dados é desviada à esquerda.</span><span class="sxs-lookup"><span data-stu-id="e25fa-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="e25fa-118">Elemento de FirstLineIndent para quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e25fa-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="e25fa-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e25fa-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e25fa-120">Especifica o número de carateres a primeira linha dos dados é desviada à direita.</span><span class="sxs-lookup"><span data-stu-id="e25fa-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="e25fa-121">Elemento de LeftIndent para quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e25fa-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="e25fa-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e25fa-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e25fa-123">Especifica o número de carateres de dados são desviados da margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="e25fa-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="e25fa-124">Elemento de RightIndent para quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e25fa-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="e25fa-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="e25fa-125">Optional element.</span></span><br /><br /> <span data-ttu-id="e25fa-126">Especifica o número de carateres de dados são desviados da margem direita.</span><span class="sxs-lookup"><span data-stu-id="e25fa-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e25fa-127">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="e25fa-127">Parent Elements</span></span>

|<span data-ttu-id="e25fa-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="e25fa-128">Element</span></span>|<span data-ttu-id="e25fa-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="e25fa-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e25fa-130">Elemento de CustomItem para CustomEntry para controles de configuração</span><span class="sxs-lookup"><span data-stu-id="e25fa-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="e25fa-131">Define os dados que são apresentados pelo controle e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="e25fa-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e25fa-132">Observações</span><span class="sxs-lookup"><span data-stu-id="e25fa-132">Remarks</span></span>

<span data-ttu-id="e25fa-133">Não é possível especificar a [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elementos na mesma `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="e25fa-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="e25fa-134">Veja Também</span><span class="sxs-lookup"><span data-stu-id="e25fa-134">See Also</span></span>

[<span data-ttu-id="e25fa-135">Elemento de FirstLineHanging para quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e25fa-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="e25fa-136">Elemento de FirstLineIndent para quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e25fa-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="e25fa-137">Elemento de LeftIndent para quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e25fa-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="e25fa-138">Elemento de RightIndent para quadro para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e25fa-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="e25fa-139">Elemento de CustomItem para CustomEntry para controles de configuração</span><span class="sxs-lookup"><span data-stu-id="e25fa-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="e25fa-140">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e25fa-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
