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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849827"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="15598-102">CustomControlName Element for GroupBy (Format) (Elemento CustomControlName para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="15598-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="15598-103">Especifica o nome de um controle personalizado que é utilizado para apresentar o novo grupo.</span><span class="sxs-lookup"><span data-stu-id="15598-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="15598-104">Este elemento é utilizado ao definir uma tabela, a lista, o modo de exibição control ampla ou personalizado.</span><span class="sxs-lookup"><span data-stu-id="15598-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="15598-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o modo de exibição (formato) CustomControlName elemento de GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="15598-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="15598-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15598-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="15598-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="15598-107">Attributes and Elements</span></span>

<span data-ttu-id="15598-108">As secções seguintes descrevem os atributos, elementos filho e elementos pai do `CustomControlName` elemento.</span><span class="sxs-lookup"><span data-stu-id="15598-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="15598-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="15598-109">Attributes</span></span>

<span data-ttu-id="15598-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="15598-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="15598-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="15598-111">Child Elements</span></span>

<span data-ttu-id="15598-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="15598-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="15598-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="15598-113">Parent Elements</span></span>

|<span data-ttu-id="15598-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="15598-114">Element</span></span>|<span data-ttu-id="15598-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="15598-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="15598-116">GroupBy elemento para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="15598-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="15598-117">Define como o Windows PowerShell apresenta um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="15598-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="15598-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="15598-118">Text Value</span></span>

<span data-ttu-id="15598-119">Especifique o nome do controle personalizado que é utilizado para apresentar um novo grupo.</span><span class="sxs-lookup"><span data-stu-id="15598-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="15598-120">Observações</span><span class="sxs-lookup"><span data-stu-id="15598-120">Remarks</span></span>

<span data-ttu-id="15598-121">Pode criar controles comuns que podem ser utilizados por todas as vistas de um ficheiro de formatação, e pode criar controles de exibição que podem ser utilizados por uma vista específica.</span><span class="sxs-lookup"><span data-stu-id="15598-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="15598-122">Os seguintes elementos especifique os nomes desses controles personalizados:</span><span class="sxs-lookup"><span data-stu-id="15598-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="15598-123">Elemento de nome para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="15598-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="15598-124">Elemento de nome para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="15598-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="15598-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="15598-125">See Also</span></span>

[<span data-ttu-id="15598-126">GroupBy elemento para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="15598-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="15598-127">Elemento de nome para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="15598-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="15598-128">Elemento de nome para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="15598-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="15598-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="15598-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
