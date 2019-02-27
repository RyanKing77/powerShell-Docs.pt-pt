---
title: Estruturar o elemento para CustomItem para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846005"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="23126-102">Frame Element for CustomItem for GroupBy (Format) (Elemento Frame para CustomItem para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="23126-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="23126-103">Define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="23126-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="23126-104">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="23126-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="23126-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de CustomItem GroupBy (formato) para CustomEntry para o elemento de quadro de GroupBy (formato) para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="23126-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="23126-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23126-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="23126-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="23126-107">Attributes and Elements</span></span>

<span data-ttu-id="23126-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="23126-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="23126-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="23126-109">Attributes</span></span>

<span data-ttu-id="23126-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="23126-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="23126-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="23126-111">Child Elements</span></span>

|<span data-ttu-id="23126-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="23126-112">Element</span></span>|<span data-ttu-id="23126-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="23126-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="23126-114">Elemento necessário</span><span class="sxs-lookup"><span data-stu-id="23126-114">Required Element</span></span>|
|[<span data-ttu-id="23126-115">Elemento de FirstLineHanging para quadro para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="23126-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="23126-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="23126-116">Optional element.</span></span><br /><br /> <span data-ttu-id="23126-117">Especifica o número de carateres a primeira linha dos dados é desviada à esquerda.</span><span class="sxs-lookup"><span data-stu-id="23126-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="23126-118">Elemento de FirstLineIndent para quadro para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="23126-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="23126-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="23126-119">Optional element.</span></span><br /><br /> <span data-ttu-id="23126-120">Especifica o número de carateres a primeira linha dos dados é desviada à direita.</span><span class="sxs-lookup"><span data-stu-id="23126-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="23126-121">Elemento de LeftIndent para quadro para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="23126-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="23126-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="23126-122">Optional element.</span></span><br /><br /> <span data-ttu-id="23126-123">Especifica o número de carateres de dados são desviados da margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="23126-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="23126-124">[Elemento de RightIndent para quadro para GroupBy (formato)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent elemento</span><span class="sxs-lookup"><span data-stu-id="23126-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="23126-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="23126-125">Optional element.</span></span><br /><br /> <span data-ttu-id="23126-126">Especifica o número de carateres de dados são desviados da margem direita.</span><span class="sxs-lookup"><span data-stu-id="23126-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="23126-127">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="23126-127">Parent Elements</span></span>

|<span data-ttu-id="23126-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="23126-128">Element</span></span>|<span data-ttu-id="23126-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="23126-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="23126-130">Elemento de CustomItem para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="23126-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="23126-131">Define os dados que são apresentados pelo controle e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="23126-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="23126-132">Observações</span><span class="sxs-lookup"><span data-stu-id="23126-132">Remarks</span></span>

<span data-ttu-id="23126-133">Não é possível especificar a [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elementos na mesma `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="23126-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="23126-134">Veja Também</span><span class="sxs-lookup"><span data-stu-id="23126-134">See Also</span></span>

[<span data-ttu-id="23126-135">Elemento de FirstLineHanging para quadro para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="23126-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="23126-136">Elemento de FirstLineIndent para quadro para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="23126-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="23126-137">Elemento de LeftIndent para quadro para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="23126-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="23126-138">Elemento de RightIndent para quadro para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="23126-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="23126-139">Elemento de CustomItem para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="23126-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="23126-140">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="23126-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
