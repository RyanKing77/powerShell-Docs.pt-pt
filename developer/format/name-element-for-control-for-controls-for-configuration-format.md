---
title: Nome de elemento para controle para controles para a configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065194"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="8889c-102">Name Element for Control for Controls for Configuration (Format) (Elemento Name para Control para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="8889c-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="8889c-103">Especifica o nome do controle.</span><span class="sxs-lookup"><span data-stu-id="8889c-103">Specifies the name of the control.</span></span> <span data-ttu-id="8889c-104">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="8889c-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="8889c-105">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de nome de configuração (formato) para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="8889c-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8889c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8889c-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="8889c-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8889c-107">Attributes and Elements</span></span>

<span data-ttu-id="8889c-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Name` elemento.</span><span class="sxs-lookup"><span data-stu-id="8889c-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8889c-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="8889c-109">Attributes</span></span>

<span data-ttu-id="8889c-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8889c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8889c-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="8889c-111">Child Elements</span></span>

<span data-ttu-id="8889c-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8889c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8889c-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="8889c-113">Parent Elements</span></span>

|<span data-ttu-id="8889c-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="8889c-114">Element</span></span>|<span data-ttu-id="8889c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="8889c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8889c-116">Elemento de controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="8889c-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="8889c-117">Define um controle comum que pode ser utilizado por todas as vistas do ficheiro formatação e o nome que é utilizado para referenciar o controle.</span><span class="sxs-lookup"><span data-stu-id="8889c-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8889c-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="8889c-118">Text Value</span></span>

<span data-ttu-id="8889c-119">Especifique o nome que é utilizado para referenciar esse controle.</span><span class="sxs-lookup"><span data-stu-id="8889c-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="8889c-120">Observações</span><span class="sxs-lookup"><span data-stu-id="8889c-120">Remarks</span></span>

<span data-ttu-id="8889c-121">O nome especificado aqui pode servir os seguintes elementos para fazer referência a esse controle.</span><span class="sxs-lookup"><span data-stu-id="8889c-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="8889c-122">Ao criar uma tabela, a lista, o modo de exibição control ampla ou personalizadas, o controle pode ser especificado pelo elemento do seguinte: [GroupBy elemento para a exibição (formato)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="8889c-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="8889c-123">Ao criar outro controle comum, esse controle pode ser especificado pelo elemento do seguinte: [Elemento de ExpressionBinding para CustomItem para controles de configuração (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="8889c-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="8889c-124">Quando criar um controle que pode ser utilizado por uma vista, esse controle pode ser especificado pelo elemento do seguinte: [Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="8889c-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="8889c-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="8889c-125">See Also</span></span>

[<span data-ttu-id="8889c-126">Elemento de controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="8889c-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="8889c-127">Elemento de ExpressionBinding para CustomItem para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="8889c-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="8889c-128">Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="8889c-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="8889c-129">GroupBy elemento para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="8889c-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="8889c-130">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8889c-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
