---
title: Elemento de CustomControlName para ExpressionBinding para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066656"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="37e13-102">CustomControlName Element for ExpressionBinding for Controls for View (Format) (Elemento CustomControlName para ExpressionBinding para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="37e13-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="37e13-103">Especifica o nome de um controle comum ou um controle de exibição.</span><span class="sxs-lookup"><span data-stu-id="37e13-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="37e13-104">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="37e13-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="37e13-105">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) CustomItem elemento para CustomEntry para controles para exibição (formato) ExpressionBinding elemento para CustomItem para controles para exibição (formato) CustomControlName Elemento para ExpressionBindine para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="37e13-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="37e13-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37e13-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="37e13-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="37e13-107">Attributes and Elements</span></span>

<span data-ttu-id="37e13-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="37e13-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="37e13-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="37e13-109">Attributes</span></span>

<span data-ttu-id="37e13-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="37e13-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="37e13-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="37e13-111">Child Elements</span></span>

<span data-ttu-id="37e13-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="37e13-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="37e13-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="37e13-113">Parent Elements</span></span>

|<span data-ttu-id="37e13-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="37e13-114">Element</span></span>|<span data-ttu-id="37e13-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="37e13-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37e13-116">Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="37e13-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="37e13-117">Define os dados que são apresentados pelo controle.</span><span class="sxs-lookup"><span data-stu-id="37e13-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="37e13-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="37e13-118">Text Value</span></span>

<span data-ttu-id="37e13-119">Especifique o nome do controle.</span><span class="sxs-lookup"><span data-stu-id="37e13-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="37e13-120">Observações</span><span class="sxs-lookup"><span data-stu-id="37e13-120">Remarks</span></span>

<span data-ttu-id="37e13-121">Pode criar controles comuns que podem ser utilizados por todas as vistas de um ficheiro de formatação, e pode criar controles de exibição que podem ser utilizados por uma vista específica.</span><span class="sxs-lookup"><span data-stu-id="37e13-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="37e13-122">Os seguintes elementos especifique os nomes desses controles:</span><span class="sxs-lookup"><span data-stu-id="37e13-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="37e13-123">Elemento de nome para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="37e13-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="37e13-124">Elemento de nome para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="37e13-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="37e13-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="37e13-125">See Also</span></span>

[<span data-ttu-id="37e13-126">Elemento de nome para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="37e13-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="37e13-127">Elemento de nome para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="37e13-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="37e13-128">Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="37e13-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="37e13-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="37e13-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
