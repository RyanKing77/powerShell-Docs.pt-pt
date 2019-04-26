---
title: Controlar o elemento para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066775"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="99d7f-102">Control Element for Controls for View (Format) (Elemento Control para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="99d7f-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="99d7f-103">Define um controle que pode ser utilizado pela exibição e o nome que é utilizado para referenciar o controle.</span><span class="sxs-lookup"><span data-stu-id="99d7f-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="99d7f-104">Elemento de configuração do modo de exibição elemento (formato) ViewDefinitions elemento (formato) (formato) controla o elemento de controle do elemento (formato) para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="99d7f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="99d7f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99d7f-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="99d7f-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="99d7f-106">Attributes and Elements</span></span>

<span data-ttu-id="99d7f-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Control` elemento.</span><span class="sxs-lookup"><span data-stu-id="99d7f-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="99d7f-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="99d7f-108">Attributes</span></span>

<span data-ttu-id="99d7f-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="99d7f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="99d7f-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="99d7f-110">Child Elements</span></span>

|<span data-ttu-id="99d7f-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="99d7f-111">Element</span></span>|<span data-ttu-id="99d7f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="99d7f-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="99d7f-113">Elemento de nome para o controlo para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="99d7f-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="99d7f-114">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="99d7f-114">Required element.</span></span><br /><br /> <span data-ttu-id="99d7f-115">Especifica o nome do controle.</span><span class="sxs-lookup"><span data-stu-id="99d7f-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="99d7f-116">Elemento de CustomControl para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="99d7f-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="99d7f-117">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="99d7f-117">Required element.</span></span><br /><br /> <span data-ttu-id="99d7f-118">Define o controle usado por esta vista.</span><span class="sxs-lookup"><span data-stu-id="99d7f-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="99d7f-119">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="99d7f-119">Parent Elements</span></span>

|<span data-ttu-id="99d7f-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="99d7f-120">Element</span></span>|<span data-ttu-id="99d7f-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="99d7f-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="99d7f-122">Elemento de controles (formato)</span><span class="sxs-lookup"><span data-stu-id="99d7f-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="99d7f-123">Define os controles de exibição que podem ser utilizados por uma vista específica.</span><span class="sxs-lookup"><span data-stu-id="99d7f-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="99d7f-124">Observações</span><span class="sxs-lookup"><span data-stu-id="99d7f-124">Remarks</span></span>

<span data-ttu-id="99d7f-125">Esse controle pode ser especificado pelos seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="99d7f-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="99d7f-126">Elemento de CustomControlName para ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="99d7f-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="99d7f-127">Elemento de CustomControlName para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="99d7f-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="99d7f-128">Elemento de CustomControlName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="99d7f-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="99d7f-129">Elemento de CustomControlName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="99d7f-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="99d7f-130">Veja Também</span><span class="sxs-lookup"><span data-stu-id="99d7f-130">See Also</span></span>

[<span data-ttu-id="99d7f-131">Elemento de CustomControl para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="99d7f-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="99d7f-132">Elemento de CustomControlName para ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="99d7f-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="99d7f-133">Elemento de CustomControlName para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="99d7f-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="99d7f-134">Elemento de CustomControlName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="99d7f-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="99d7f-135">Elemento de CustomControlName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="99d7f-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="99d7f-136">Elemento de controles (formato)</span><span class="sxs-lookup"><span data-stu-id="99d7f-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="99d7f-137">Elemento de nome para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="99d7f-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="99d7f-138">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="99d7f-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
