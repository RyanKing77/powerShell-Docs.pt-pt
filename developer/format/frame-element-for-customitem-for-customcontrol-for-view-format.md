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
ms.openlocfilehash: a7ee550527ec1cb00b4ed83478992c7ab54dbdb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850807"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="5a889-102">Frame Element for CustomItem for CustomControl for View (Format) (Elemento Frame para CustomItem para CustomControl para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="5a889-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="5a889-103">Define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita.</span><span class="sxs-lookup"><span data-stu-id="5a889-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="5a889-104">Este elemento é utilizado ao definir uma vista de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="5a889-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="5a889-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para exibição (formato) CustomItem elemento para CustomEntry para o elemento de quadro de CutomControlView (formato) para CustomItem para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5a889-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CutomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5a889-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a889-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5a889-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="5a889-107">Attributes and Elements</span></span>

<span data-ttu-id="5a889-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="5a889-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5a889-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="5a889-109">Attributes</span></span>

<span data-ttu-id="5a889-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5a889-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5a889-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="5a889-111">Child Elements</span></span>

|<span data-ttu-id="5a889-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="5a889-112">Element</span></span>|<span data-ttu-id="5a889-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a889-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="5a889-114">Elemento necessário</span><span class="sxs-lookup"><span data-stu-id="5a889-114">Required Element</span></span>|
|[<span data-ttu-id="5a889-115">Elemento de FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="5a889-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="5a889-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5a889-116">Optional element.</span></span><br /><br /> <span data-ttu-id="5a889-117">Especifica o número de carateres a primeira linha dos dados é desviada à esquerda.</span><span class="sxs-lookup"><span data-stu-id="5a889-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="5a889-118">Elemento de FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="5a889-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="5a889-119">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5a889-119">Optional element.</span></span><br /><br /> <span data-ttu-id="5a889-120">Especifica o número de carateres a primeira linha dos dados é desviada à direita.</span><span class="sxs-lookup"><span data-stu-id="5a889-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="5a889-121">Elemento de LeftIndent</span><span class="sxs-lookup"><span data-stu-id="5a889-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="5a889-122">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5a889-122">Optional element.</span></span><br /><br /> <span data-ttu-id="5a889-123">Especifica o número de carateres de dados são desviados da margem esquerda.</span><span class="sxs-lookup"><span data-stu-id="5a889-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="5a889-124">Elemento de RightIndent</span><span class="sxs-lookup"><span data-stu-id="5a889-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="5a889-125">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5a889-125">Optional element.</span></span><br /><br /> <span data-ttu-id="5a889-126">Especifica o número de carateres de dados são desviados da margem direita.</span><span class="sxs-lookup"><span data-stu-id="5a889-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5a889-127">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="5a889-127">Parent Elements</span></span>

|<span data-ttu-id="5a889-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="5a889-128">Element</span></span>|<span data-ttu-id="5a889-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a889-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5a889-130">Elemento de CustomItem para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5a889-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="5a889-131">Define os dados que são apresentados pelo controle e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="5a889-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5a889-132">Observações</span><span class="sxs-lookup"><span data-stu-id="5a889-132">Remarks</span></span>

<span data-ttu-id="5a889-133">Não é possível especificar a [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elementos na mesma `Frame` elemento.</span><span class="sxs-lookup"><span data-stu-id="5a889-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a889-134">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="5a889-134">See Also</span></span>

[<span data-ttu-id="5a889-135">Elemento de FirstLineHanging</span><span class="sxs-lookup"><span data-stu-id="5a889-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5a889-136">Elemento de FirstLineIndent</span><span class="sxs-lookup"><span data-stu-id="5a889-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5a889-137">Elemento de LeftIndent</span><span class="sxs-lookup"><span data-stu-id="5a889-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5a889-138">Elemento de RightIndent</span><span class="sxs-lookup"><span data-stu-id="5a889-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5a889-139">Elemento de CustomItem para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5a889-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5a889-140">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a889-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
