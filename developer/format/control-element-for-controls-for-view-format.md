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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845221"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="44eff-102">Control Element for Controls for View (Format) (Elemento Control para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="44eff-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="44eff-103">Define um controle que pode ser utilizado pela exibição e o nome que é utilizado para referenciar o controle.</span><span class="sxs-lookup"><span data-stu-id="44eff-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="44eff-104">Elemento de configuração do modo de exibição elemento (formato) ViewDefinitions elemento (formato) (formato) controla o elemento de controle do elemento (formato) para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="44eff-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="44eff-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44eff-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="44eff-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="44eff-106">Attributes and Elements</span></span>

<span data-ttu-id="44eff-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Control` elemento.</span><span class="sxs-lookup"><span data-stu-id="44eff-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="44eff-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="44eff-108">Attributes</span></span>

<span data-ttu-id="44eff-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="44eff-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="44eff-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="44eff-110">Child Elements</span></span>

|<span data-ttu-id="44eff-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="44eff-111">Element</span></span>|<span data-ttu-id="44eff-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="44eff-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="44eff-113">Elemento de nome para o controlo para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="44eff-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="44eff-114">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="44eff-114">Required element.</span></span><br /><br /> <span data-ttu-id="44eff-115">Especifica o nome do controle.</span><span class="sxs-lookup"><span data-stu-id="44eff-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="44eff-116">Elemento de CustomControl para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="44eff-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="44eff-117">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="44eff-117">Required element.</span></span><br /><br /> <span data-ttu-id="44eff-118">Define o controle usado por esta vista.</span><span class="sxs-lookup"><span data-stu-id="44eff-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="44eff-119">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="44eff-119">Parent Elements</span></span>

|<span data-ttu-id="44eff-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="44eff-120">Element</span></span>|<span data-ttu-id="44eff-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="44eff-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="44eff-122">Elemento de controles (formato)</span><span class="sxs-lookup"><span data-stu-id="44eff-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="44eff-123">Define os controles de exibição que podem ser utilizados por uma vista específica.</span><span class="sxs-lookup"><span data-stu-id="44eff-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="44eff-124">Observações</span><span class="sxs-lookup"><span data-stu-id="44eff-124">Remarks</span></span>

<span data-ttu-id="44eff-125">Esse controle pode ser especificado pelos seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="44eff-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="44eff-126">Elemento de CustomControlName para ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="44eff-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="44eff-127">Elemento de CustomControlName para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="44eff-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="44eff-128">Elemento de CustomControlName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="44eff-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="44eff-129">Elemento de CustomControlName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="44eff-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="44eff-130">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="44eff-130">See Also</span></span>

[<span data-ttu-id="44eff-131">Elemento de CustomControl para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="44eff-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="44eff-132">Elemento de CustomControlName para ExpressionBinding para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="44eff-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="44eff-133">Elemento de CustomControlName para ExpressionBinding para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="44eff-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="44eff-134">Elemento de CustomControlName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="44eff-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="44eff-135">Elemento de CustomControlName para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="44eff-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="44eff-136">Elemento de controles (formato)</span><span class="sxs-lookup"><span data-stu-id="44eff-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="44eff-137">Elemento de nome para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="44eff-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="44eff-138">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="44eff-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
