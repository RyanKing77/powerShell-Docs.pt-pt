---
title: Elemento de CustomControlName para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066550"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="86fe5-102">CustomControlName Element for GroupBy (Format) (Elemento CustomControlName para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="86fe5-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="86fe5-103">Especifica o nome de um controle personalizado que é utilizado para apresentar o novo grupo.</span><span class="sxs-lookup"><span data-stu-id="86fe5-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="86fe5-104">Este elemento é utilizado ao definir uma tabela, a lista, o modo de exibição control ampla ou personalizado.</span><span class="sxs-lookup"><span data-stu-id="86fe5-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="86fe5-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o modo de exibição (formato) CustomControlName elemento de GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="86fe5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="86fe5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86fe5-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="86fe5-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="86fe5-107">Attributes and Elements</span></span>

<span data-ttu-id="86fe5-108">As secções seguintes descrevem os atributos, elementos filho e elementos pai do `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="86fe5-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="86fe5-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="86fe5-109">Attributes</span></span>

<span data-ttu-id="86fe5-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="86fe5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="86fe5-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="86fe5-111">Child Elements</span></span>

<span data-ttu-id="86fe5-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="86fe5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="86fe5-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="86fe5-113">Parent Elements</span></span>

|<span data-ttu-id="86fe5-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="86fe5-114">Element</span></span>|<span data-ttu-id="86fe5-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="86fe5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86fe5-116">GroupBy elemento para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="86fe5-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="86fe5-117">Define como o Windows PowerShell apresenta um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="86fe5-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="86fe5-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="86fe5-118">Text Value</span></span>

<span data-ttu-id="86fe5-119">Especifique o nome do controle personalizado que é utilizado para apresentar um novo grupo.</span><span class="sxs-lookup"><span data-stu-id="86fe5-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="86fe5-120">Observações</span><span class="sxs-lookup"><span data-stu-id="86fe5-120">Remarks</span></span>

<span data-ttu-id="86fe5-121">Pode criar controles comuns que podem ser utilizados por todas as vistas de um ficheiro de formatação, e pode criar controles de exibição que podem ser utilizados por uma vista específica.</span><span class="sxs-lookup"><span data-stu-id="86fe5-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="86fe5-122">Os seguintes elementos especifique os nomes desses controles personalizados:</span><span class="sxs-lookup"><span data-stu-id="86fe5-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="86fe5-123">Elemento de nome para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="86fe5-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="86fe5-124">Elemento de nome para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="86fe5-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="86fe5-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="86fe5-125">See Also</span></span>

[<span data-ttu-id="86fe5-126">GroupBy elemento para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="86fe5-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="86fe5-127">Elemento de nome para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="86fe5-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="86fe5-128">Elemento de nome para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="86fe5-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="86fe5-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="86fe5-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
