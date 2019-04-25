---
title: Controlar o elemento para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066798"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="6fd11-102">Control Element for Controls for Configuration (Format) (Elemento Control para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="6fd11-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="6fd11-103">Define um controle comum que pode ser utilizado por todas as vistas do ficheiro formatação e o nome que é utilizado para referenciar o controle.</span><span class="sxs-lookup"><span data-stu-id="6fd11-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="6fd11-104">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="6fd11-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6fd11-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fd11-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6fd11-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6fd11-106">Attributes and Elements</span></span>

<span data-ttu-id="6fd11-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal para o `Control` elemento.</span><span class="sxs-lookup"><span data-stu-id="6fd11-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="6fd11-108">Tem de especificar apenas um de cada elemento filho.</span><span class="sxs-lookup"><span data-stu-id="6fd11-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6fd11-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="6fd11-109">Attributes</span></span>

<span data-ttu-id="6fd11-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6fd11-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6fd11-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="6fd11-111">Child Elements</span></span>

|<span data-ttu-id="6fd11-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="6fd11-112">Element</span></span>|<span data-ttu-id="6fd11-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fd11-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6fd11-114">Elemento de CustomControl para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="6fd11-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="6fd11-115">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="6fd11-115">Required element.</span></span><br /><br /> <span data-ttu-id="6fd11-116">Define o controlo.</span><span class="sxs-lookup"><span data-stu-id="6fd11-116">Defines the control.</span></span>|
|[<span data-ttu-id="6fd11-117">Elemento de nome para o controlo de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="6fd11-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="6fd11-118">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="6fd11-118">Required element.</span></span><br /><br /> <span data-ttu-id="6fd11-119">Especifica o nome utilizado para referenciar o controle.</span><span class="sxs-lookup"><span data-stu-id="6fd11-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6fd11-120">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="6fd11-120">Parent Elements</span></span>

|<span data-ttu-id="6fd11-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="6fd11-121">Element</span></span>|<span data-ttu-id="6fd11-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fd11-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6fd11-123">Elemento de controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="6fd11-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="6fd11-124">Define os controles comuns que podem ser utilizados por todas as vistas do arquivo formatação ou por outros controles.</span><span class="sxs-lookup"><span data-stu-id="6fd11-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6fd11-125">Observações</span><span class="sxs-lookup"><span data-stu-id="6fd11-125">Remarks</span></span>

<span data-ttu-id="6fd11-126">O nome atribuído a esse controle pode ser referenciado nos seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="6fd11-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="6fd11-127">Elemento de ExpressionBinding para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="6fd11-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="6fd11-128">Elemento de GroupBy para View(Format)</span><span class="sxs-lookup"><span data-stu-id="6fd11-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="6fd11-129">Veja Também</span><span class="sxs-lookup"><span data-stu-id="6fd11-129">See Also</span></span>

[<span data-ttu-id="6fd11-130">Elemento de controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="6fd11-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="6fd11-131">Elemento de CustomControl para controlo de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="6fd11-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="6fd11-132">Elemento de ExpressionBinding para CustomItem (formato)</span><span class="sxs-lookup"><span data-stu-id="6fd11-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="6fd11-133">Elemento de GroupBy para View(Format)</span><span class="sxs-lookup"><span data-stu-id="6fd11-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="6fd11-134">Elemento de nome para o controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="6fd11-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="6fd11-135">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="6fd11-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
