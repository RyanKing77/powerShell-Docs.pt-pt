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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847041"
---
# <a name="configuration-element-format"></a><span data-ttu-id="877af-102">Configuration Element (Format) (Elemento Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="877af-102">Configuration Element (Format)</span></span>

<span data-ttu-id="877af-103">Representa o elemento de nível superior de um ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="877af-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="877af-104">Elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="877af-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="877af-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="877af-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="877af-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="877af-106">Attributes and Elements</span></span>

<span data-ttu-id="877af-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Configuration` elemento.</span><span class="sxs-lookup"><span data-stu-id="877af-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="877af-108">Este elemento tem de ser o elemento de raiz para cada ficheiro de formatação e este elemento tem de conter, pelo menos, um elemento subordinado.</span><span class="sxs-lookup"><span data-stu-id="877af-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="877af-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="877af-109">Attributes</span></span>

<span data-ttu-id="877af-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="877af-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="877af-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="877af-111">Child Elements</span></span>

|<span data-ttu-id="877af-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="877af-112">Element</span></span>|<span data-ttu-id="877af-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="877af-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="877af-114">Elemento de controles para a configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="877af-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="877af-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="877af-115">Optional element.</span></span><br /><br /> <span data-ttu-id="877af-116">Define os controles comuns que podem ser utilizados por todas as vistas do ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="877af-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="877af-117">Elemento de DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="877af-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="877af-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="877af-118">Optional element.</span></span><br /><br /> <span data-ttu-id="877af-119">Define configurações comuns que se aplicam a todas as vistas do ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="877af-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="877af-120">Formato de elemento de SelectionSets</span><span class="sxs-lookup"><span data-stu-id="877af-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="877af-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="877af-121">Optional element.</span></span><br /><br /> <span data-ttu-id="877af-122">Define os conjuntos comuns de objetos .NET que podem ser utilizados por todas as vistas do ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="877af-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="877af-123">Elemento de ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="877af-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="877af-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="877af-124">Optional element.</span></span><br /><br /> <span data-ttu-id="877af-125">Define os modos de exibição utilizados para apresentar os objetos.</span><span class="sxs-lookup"><span data-stu-id="877af-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="877af-126">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="877af-126">Parent Elements</span></span>

<span data-ttu-id="877af-127">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="877af-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="877af-128">Observações</span><span class="sxs-lookup"><span data-stu-id="877af-128">Remarks</span></span>

<span data-ttu-id="877af-129">Arquivos de formatação definem a forma como os objetos são apresentados.</span><span class="sxs-lookup"><span data-stu-id="877af-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="877af-130">Na maioria dos casos, esse elemento de raiz contém um [ViewDefinitions](./viewdefinitions-element-format.md) elemento que define a tabela, lista e vistas ampla do arquivo formatação.</span><span class="sxs-lookup"><span data-stu-id="877af-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="877af-131">Além das definições de exibição, o ficheiro de formatação pode definir conjuntos de seleção, definições e controlos que podem utilizar esses modos de exibição comuns.</span><span class="sxs-lookup"><span data-stu-id="877af-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="877af-132">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="877af-132">See Also</span></span>

[<span data-ttu-id="877af-133">Elemento de controles para a configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="877af-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="877af-134">Elemento de DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="877af-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="877af-135">Elemento de SelectionSets (formato)</span><span class="sxs-lookup"><span data-stu-id="877af-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="877af-136">Elemento de ViewDefinitions (formato)</span><span class="sxs-lookup"><span data-stu-id="877af-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="877af-137">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="877af-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
