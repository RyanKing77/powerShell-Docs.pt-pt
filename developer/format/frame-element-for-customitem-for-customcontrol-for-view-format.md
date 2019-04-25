---
title: Estruturar o elemento para CustomItem para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065585"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="b47c6-102">Frame Element for CustomItem for CustomControl for View (Format) (Elemento Frame para CustomItem para CustomControl para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="b47c6-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="b47c6-103">Define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="b47c6-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="b47c6-104">Este elemento é utilizado ao definir uma vista de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="b47c6-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="b47c6-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para exibição (formato) CustomItem elemento para CustomEntry para o elemento de quadro de CustomControlView (formato) para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="b47c6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b47c6-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b47c6-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b47c6-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b47c6-107">Attributes and Elements</span></span>

<span data-ttu-id="b47c6-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="b47c6-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b47c6-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b47c6-109">Attributes</span></span>

<span data-ttu-id="b47c6-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b47c6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b47c6-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="b47c6-111">Child Elements</span></span>

|<span data-ttu-id="b47c6-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b47c6-112">Element</span></span>|<span data-ttu-id="b47c6-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b47c6-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="b47c6-114">Elemento necessário</span><span class="sxs-lookup"><span data-stu-id="b47c6-114">Required Element</span></span>|
|[<span data-ttu-id="b47c6-115">Elemento de FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="b47c6-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="b47c6-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b47c6-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b47c6-117">Especifica o número de carateres a primeira linha dos dados é desviada à esquerda.</span><span class="sxs-lookup"><span data-stu-id="b47c6-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="b47c6-118">Elemento de FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="b47c6-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="b47c6-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b47c6-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b47c6-120">Especifica o número de carateres a primeira linha dos dados é desviada à direita.</span><span class="sxs-lookup"><span data-stu-id="b47c6-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="b47c6-121">Elemento de LeftIndent</span><span class="sxs-lookup"><span data-stu-id="b47c6-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="b47c6-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b47c6-122">Optional element.</span></span><br /><br /> <span data-ttu-id="b47c6-123">Especifica o número de carateres de dados são desviados da margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="b47c6-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="b47c6-124">Elemento de RightIndent</span><span class="sxs-lookup"><span data-stu-id="b47c6-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="b47c6-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b47c6-125">Optional element.</span></span><br /><br /> <span data-ttu-id="b47c6-126">Especifica o número de carateres de dados são desviados da margem direita.</span><span class="sxs-lookup"><span data-stu-id="b47c6-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b47c6-127">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="b47c6-127">Parent Elements</span></span>

|<span data-ttu-id="b47c6-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="b47c6-128">Element</span></span>|<span data-ttu-id="b47c6-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="b47c6-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b47c6-130">Elemento de CustomItem para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="b47c6-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="b47c6-131">Define os dados que são apresentados pelo controle e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="b47c6-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b47c6-132">Observações</span><span class="sxs-lookup"><span data-stu-id="b47c6-132">Remarks</span></span>

<span data-ttu-id="b47c6-133">Não é possível especificar a [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elementos na mesma `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="b47c6-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="b47c6-134">Veja Também</span><span class="sxs-lookup"><span data-stu-id="b47c6-134">See Also</span></span>

[<span data-ttu-id="b47c6-135">Elemento de FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="b47c6-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b47c6-136">Elemento de FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="b47c6-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b47c6-137">Elemento de LeftIndent</span><span class="sxs-lookup"><span data-stu-id="b47c6-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b47c6-138">Elemento de RightIndent</span><span class="sxs-lookup"><span data-stu-id="b47c6-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b47c6-139">Elemento de CustomItem para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="b47c6-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b47c6-140">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b47c6-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
