---
title: Elemento de CustomControlName para ExpressionBinding para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845620"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="f15ec-102">CustomControlName Element for ExpressionBinding for GroupBy (Format) (Elemento CustomControlName para ExpressionBinding para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="f15ec-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="f15ec-103">Especifica o nome de um controle comum ou um controle de exibição.</span><span class="sxs-lookup"><span data-stu-id="f15ec-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="f15ec-104">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="f15ec-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="f15ec-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de CustomItem GroupBy (formato) para CustomEntry para o elemento de ExpressionBinding GroupBy (formato) para CustomItem para o elemento de CustomControlName GroupBy (formato) para ExpressionBinding para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f15ec-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f15ec-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f15ec-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f15ec-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="f15ec-107">Attributes and Elements</span></span>

<span data-ttu-id="f15ec-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="f15ec-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f15ec-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f15ec-109">Attributes</span></span>

<span data-ttu-id="f15ec-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f15ec-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f15ec-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="f15ec-111">Child Elements</span></span>

<span data-ttu-id="f15ec-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f15ec-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f15ec-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="f15ec-113">Parent Elements</span></span>

|<span data-ttu-id="f15ec-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="f15ec-114">Element</span></span>|<span data-ttu-id="f15ec-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="f15ec-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f15ec-116">Elemento de ExpressionBinding para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f15ec-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="f15ec-117">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="f15ec-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f15ec-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="f15ec-118">Text Value</span></span>

<span data-ttu-id="f15ec-119">Especifique o nome do controle.</span><span class="sxs-lookup"><span data-stu-id="f15ec-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="f15ec-120">Observações</span><span class="sxs-lookup"><span data-stu-id="f15ec-120">Remarks</span></span>

<span data-ttu-id="f15ec-121">Pode criar controles comuns que podem ser utilizados por todas as vistas de um ficheiro de formatação, e pode criar controles de exibição que podem ser utilizados por uma vista específica.</span><span class="sxs-lookup"><span data-stu-id="f15ec-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="f15ec-122">Os seguintes elementos especifique os nomes desses controles:</span><span class="sxs-lookup"><span data-stu-id="f15ec-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="f15ec-123">Elemento de nome para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="f15ec-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="f15ec-124">Elemento de nome para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="f15ec-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="f15ec-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="f15ec-125">See Also</span></span>

[<span data-ttu-id="f15ec-126">Elemento de nome para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="f15ec-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="f15ec-127">Elemento de nome para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="f15ec-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="f15ec-128">Elemento de ExpressionBinding para CustomItem para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="f15ec-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="f15ec-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f15ec-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
