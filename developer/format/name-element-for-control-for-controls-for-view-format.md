---
title: Nome de elemento para controle para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851283"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="bcad2-102">Name Element for Control for Controls for View (Format) (Elemento Name para Control para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="bcad2-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="bcad2-103">Especifica o nome do controle.</span><span class="sxs-lookup"><span data-stu-id="bcad2-103">Specifies the name of the control.</span></span>

<span data-ttu-id="bcad2-104">Elemento de configuração do modo de exibição elemento (formato) ViewDefinitions elemento (formato) (formato) controla o elemento de controle do elemento (formato) para controles em elemento de nome de exibição (formato) para o controlo para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="bcad2-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bcad2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bcad2-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bcad2-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="bcad2-106">Attributes and Elements</span></span>

<span data-ttu-id="bcad2-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Name` elemento.</span><span class="sxs-lookup"><span data-stu-id="bcad2-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bcad2-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="bcad2-108">Attributes</span></span>

<span data-ttu-id="bcad2-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="bcad2-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bcad2-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="bcad2-110">Child Elements</span></span>

<span data-ttu-id="bcad2-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="bcad2-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bcad2-112">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="bcad2-112">Parent Elements</span></span>

|<span data-ttu-id="bcad2-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="bcad2-113">Element</span></span>|<span data-ttu-id="bcad2-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="bcad2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bcad2-115">Elemento de controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="bcad2-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="bcad2-116">Define um controle que pode ser utilizado pela exibição e o nome que é utilizado para referenciar o controle.</span><span class="sxs-lookup"><span data-stu-id="bcad2-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bcad2-117">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="bcad2-117">Text Value</span></span>

<span data-ttu-id="bcad2-118">Especifique o nome que é utilizado para referenciar o controle.</span><span class="sxs-lookup"><span data-stu-id="bcad2-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="bcad2-119">Observações</span><span class="sxs-lookup"><span data-stu-id="bcad2-119">Remarks</span></span>

<span data-ttu-id="bcad2-120">O nome especificado aqui pode servir os seguintes elementos para fazer referência a esse controle.</span><span class="sxs-lookup"><span data-stu-id="bcad2-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="bcad2-121">Ao criar uma tabela, a lista, o modo de exibição control ampla ou personalizadas, o controle pode ser especificado pelo elemento do seguinte: [GroupBy elemento para a exibição (formato)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="bcad2-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="bcad2-122">Quando criar outro controle que pode ser utilizado por uma vista, esse controle pode ser especificado pelo elemento do seguinte: [Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="bcad2-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="bcad2-123">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="bcad2-123">See Also</span></span>

[<span data-ttu-id="bcad2-124">GroupBy elemento para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="bcad2-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="bcad2-125">Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="bcad2-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="bcad2-126">Elemento de controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="bcad2-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="bcad2-127">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="bcad2-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
