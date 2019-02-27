---
title: Elemento de CustomEntries para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850800"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="87204-102">CustomEntries Element for CustomControl for View (Format) (Elemento CustomEntries para CustomControl para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="87204-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="87204-103">Fornece definições de vista do controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="87204-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="87204-104">O modo de exibição do controle personalizado tem de especificar uma ou mais definições.</span><span class="sxs-lookup"><span data-stu-id="87204-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="87204-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="87204-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="87204-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87204-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="87204-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="87204-107">Attributes and Elements</span></span>

<span data-ttu-id="87204-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomControlEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="87204-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="87204-109">Tem de especificar um ou mais elementos subordinados.</span><span class="sxs-lookup"><span data-stu-id="87204-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="87204-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="87204-110">Attributes</span></span>

<span data-ttu-id="87204-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="87204-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="87204-112">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="87204-112">Child Elements</span></span>

|<span data-ttu-id="87204-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="87204-113">Element</span></span>|<span data-ttu-id="87204-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="87204-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87204-115">Elemento de CustomEntry para CustomEntries para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="87204-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="87204-116">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="87204-116">Required element.</span></span><br /><br /> <span data-ttu-id="87204-117">Fornece uma definição de vista do controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="87204-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="87204-118">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="87204-118">Parent Elements</span></span>

|<span data-ttu-id="87204-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="87204-119">Element</span></span>|<span data-ttu-id="87204-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="87204-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87204-121">Elemento de CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="87204-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="87204-122">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="87204-122">Required element.</span></span><br /><br /> <span data-ttu-id="87204-123">Define um formato de controle personalizado para a vista.</span><span class="sxs-lookup"><span data-stu-id="87204-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="87204-124">Observações</span><span class="sxs-lookup"><span data-stu-id="87204-124">Remarks</span></span>

<span data-ttu-id="87204-125">Na maioria dos casos, um controle tiver apenas uma definição, o que é definida num único `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="87204-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="87204-126">No entanto, é possível ter várias definições de se pretender utilizar o mesmo controlo para apresentar diferentes objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="87204-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="87204-127">Nesses casos, pode definir um `CustomEntry` elemento para cada objeto ou conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="87204-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="87204-128">Veja Também</span><span class="sxs-lookup"><span data-stu-id="87204-128">See Also</span></span>

[<span data-ttu-id="87204-129">Elemento de CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="87204-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="87204-130">Elemento de CustomEntry para CustomEntries para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="87204-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="87204-131">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="87204-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
