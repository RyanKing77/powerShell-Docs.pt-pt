---
title: Elemento de CustomEntry para CustomEntries para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850884"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="45492-102">CustomEntry Element for CustomEntries for CustomControl for View (Format) (Elemento CustomEntry para CustomEntries para CustomControl para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="45492-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="45492-103">Fornece uma definição de vista do controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="45492-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="45492-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="45492-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="45492-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45492-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="45492-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="45492-106">Attributes and Elements</span></span>

<span data-ttu-id="45492-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="45492-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="45492-108">Tem de especificar os itens exibidos pela definição.</span><span class="sxs-lookup"><span data-stu-id="45492-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="45492-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="45492-109">Attributes</span></span>

<span data-ttu-id="45492-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="45492-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="45492-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="45492-111">Child Elements</span></span>

|<span data-ttu-id="45492-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="45492-112">Element</span></span>|<span data-ttu-id="45492-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="45492-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="45492-114">Elemento de EntrySelectedBy para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="45492-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="45492-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="45492-115">Optional element.</span></span><br /><br /> <span data-ttu-id="45492-116">Define os tipos do .NET que utilizam a definição de vista do controle personalizado ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="45492-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="45492-117">Elemento de CustomItem para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="45492-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="45492-118">Define um controle para a definição de controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="45492-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="45492-119">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="45492-119">Parent Elements</span></span>

|<span data-ttu-id="45492-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="45492-120">Element</span></span>|<span data-ttu-id="45492-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="45492-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="45492-122">Elemento de CustomEntries para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="45492-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="45492-123">Fornece definições de vista do controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="45492-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="45492-124">O modo de exibição do controle personalizado tem de especificar uma ou mais definições.</span><span class="sxs-lookup"><span data-stu-id="45492-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="45492-125">Observações</span><span class="sxs-lookup"><span data-stu-id="45492-125">Remarks</span></span>

<span data-ttu-id="45492-126">Na maioria dos casos, apenas uma definição é necessária para cada exibição de controle personalizado, mas é possível ter várias definições, se pretender utilizar a mesma vista para apresentar diferentes objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="45492-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="45492-127">Nesses casos, pode fornecer uma definição de separado para cada objeto ou conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="45492-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="45492-128">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="45492-128">See Also</span></span>

[<span data-ttu-id="45492-129">Elemento de CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="45492-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="45492-130">Elemento de CustomItem para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="45492-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="45492-131">Elemento de EntrySelectedBy para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="45492-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="45492-132">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="45492-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
