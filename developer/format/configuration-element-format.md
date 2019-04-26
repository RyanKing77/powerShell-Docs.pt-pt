---
title: O elemento de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066826"
---
# <a name="configuration-element-format"></a><span data-ttu-id="fdefb-102">Configuration Element (Format) (Elemento Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="fdefb-102">Configuration Element (Format)</span></span>

<span data-ttu-id="fdefb-103">Representa o elemento de nível superior de um ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="fdefb-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="fdefb-104">Elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="fdefb-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="fdefb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fdefb-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="fdefb-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fdefb-106">Attributes and Elements</span></span>

<span data-ttu-id="fdefb-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Configuration` elemento.</span><span class="sxs-lookup"><span data-stu-id="fdefb-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="fdefb-108">Este elemento tem de ser o elemento de raiz para cada ficheiro de formatação e este elemento tem de conter, pelo menos, um elemento subordinado.</span><span class="sxs-lookup"><span data-stu-id="fdefb-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fdefb-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="fdefb-109">Attributes</span></span>

<span data-ttu-id="fdefb-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fdefb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fdefb-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="fdefb-111">Child Elements</span></span>

|<span data-ttu-id="fdefb-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="fdefb-112">Element</span></span>|<span data-ttu-id="fdefb-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdefb-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fdefb-114">Elemento de controles para a configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="fdefb-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="fdefb-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="fdefb-115">Optional element.</span></span><br /><br /> <span data-ttu-id="fdefb-116">Define os controles comuns que podem ser utilizados por todas as vistas do ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="fdefb-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="fdefb-117">Elemento de DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="fdefb-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="fdefb-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="fdefb-118">Optional element.</span></span><br /><br /> <span data-ttu-id="fdefb-119">Define configurações comuns que se aplicam a todas as vistas do ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="fdefb-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="fdefb-120">Formato de elemento de SelectionSets</span><span class="sxs-lookup"><span data-stu-id="fdefb-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="fdefb-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="fdefb-121">Optional element.</span></span><br /><br /> <span data-ttu-id="fdefb-122">Define os conjuntos comuns de objetos .NET que podem ser utilizados por todas as vistas do ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="fdefb-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="fdefb-123">Elemento de ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="fdefb-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="fdefb-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="fdefb-124">Optional element.</span></span><br /><br /> <span data-ttu-id="fdefb-125">Define os modos de exibição utilizados para apresentar os objetos.</span><span class="sxs-lookup"><span data-stu-id="fdefb-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fdefb-126">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="fdefb-126">Parent Elements</span></span>

<span data-ttu-id="fdefb-127">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fdefb-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="fdefb-128">Observações</span><span class="sxs-lookup"><span data-stu-id="fdefb-128">Remarks</span></span>

<span data-ttu-id="fdefb-129">Arquivos de formatação definem a forma como os objetos são apresentados.</span><span class="sxs-lookup"><span data-stu-id="fdefb-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="fdefb-130">Na maioria dos casos, esse elemento de raiz contém um [ViewDefinitions](./viewdefinitions-element-format.md) elemento que define a tabela, lista e vistas ampla do arquivo formatação.</span><span class="sxs-lookup"><span data-stu-id="fdefb-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="fdefb-131">Além das definições de exibição, o ficheiro de formatação pode definir conjuntos de seleção, definições e controlos que podem utilizar esses modos de exibição comuns.</span><span class="sxs-lookup"><span data-stu-id="fdefb-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="fdefb-132">Veja Também</span><span class="sxs-lookup"><span data-stu-id="fdefb-132">See Also</span></span>

[<span data-ttu-id="fdefb-133">Elemento de controles para a configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="fdefb-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="fdefb-134">Elemento de DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="fdefb-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="fdefb-135">Elemento de SelectionSets (formato)</span><span class="sxs-lookup"><span data-stu-id="fdefb-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="fdefb-136">Elemento de ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="fdefb-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="fdefb-137">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="fdefb-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
