---
title: Elemento de CustomEntries para CustomControl para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850877"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="8f1a3-102">CustomEntries Element for CustomControl for Controls for View (Format) (Elemento CustomEntries para CustomControl para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="8f1a3-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="8f1a3-103">Fornece as definições para o controle.</span><span class="sxs-lookup"><span data-stu-id="8f1a3-103">Provides the definitions for the control.</span></span> <span data-ttu-id="8f1a3-104">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="8f1a3-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="8f1a3-105">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="8f1a3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8f1a3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f1a3-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8f1a3-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="8f1a3-107">Attributes and Elements</span></span>

<span data-ttu-id="8f1a3-108">As secções seguintes descrevem os atributos e elementos de principal de elementos filho do `CustomEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="8f1a3-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="8f1a3-109">Não existe nenhum limite máximo para o número de elementos filho que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="8f1a3-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="8f1a3-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8f1a3-110">Attributes</span></span>

<span data-ttu-id="8f1a3-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8f1a3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8f1a3-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="8f1a3-112">Child Elements</span></span>

|<span data-ttu-id="8f1a3-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="8f1a3-113">Element</span></span>|<span data-ttu-id="8f1a3-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f1a3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f1a3-115">Elemento de CustomEntry para CustomEntries para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="8f1a3-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="8f1a3-116">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="8f1a3-116">Required element.</span></span><br /><br /> <span data-ttu-id="8f1a3-117">Fornece uma definição do controle.</span><span class="sxs-lookup"><span data-stu-id="8f1a3-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8f1a3-118">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="8f1a3-118">Parent Elements</span></span>

|<span data-ttu-id="8f1a3-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="8f1a3-119">Element</span></span>|<span data-ttu-id="8f1a3-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f1a3-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f1a3-121">Elemento de CustomControl para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="8f1a3-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="8f1a3-122">Define o controle usado pela exibição.</span><span class="sxs-lookup"><span data-stu-id="8f1a3-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8f1a3-123">Observações</span><span class="sxs-lookup"><span data-stu-id="8f1a3-123">Remarks</span></span>

<span data-ttu-id="8f1a3-124">Na maioria dos casos, um controle tiver apenas uma definição, o que é especificada num único `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="8f1a3-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="8f1a3-125">No entanto, é possível fornecer várias definições, se pretender utilizar o mesmo controlo para apresentar diferentes objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="8f1a3-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="8f1a3-126">Nesses casos, pode definir um `CustomEntry` elemento para cada objeto ou conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="8f1a3-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f1a3-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="8f1a3-127">See Also</span></span>

[<span data-ttu-id="8f1a3-128">Elemento de CustomEntry para CustomEntries para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="8f1a3-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="8f1a3-129">Elemento de CustomControl para o controle para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="8f1a3-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="8f1a3-130">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f1a3-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
