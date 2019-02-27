---
title: Elemento de CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850492"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="d8904-102">CustomControl Element for View (Format) (Elemento CustomControl para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="d8904-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="d8904-103">Define um formato de controle personalizado para a vista.</span><span class="sxs-lookup"><span data-stu-id="d8904-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="d8904-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="d8904-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d8904-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8904-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d8904-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="d8904-106">Attributes and Elements</span></span>

<span data-ttu-id="d8904-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="d8904-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="d8904-108">Tem de especificar um elemento subordinado.</span><span class="sxs-lookup"><span data-stu-id="d8904-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d8904-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="d8904-109">Attributes</span></span>

<span data-ttu-id="d8904-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d8904-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d8904-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="d8904-111">Child Elements</span></span>

|<span data-ttu-id="d8904-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="d8904-112">Element</span></span>|<span data-ttu-id="d8904-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8904-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8904-114">Elemento de CustomEntries para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d8904-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="d8904-115">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="d8904-115">Required element.</span></span><br /><br /> <span data-ttu-id="d8904-116">Fornece definições de vista do controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="d8904-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d8904-117">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="d8904-117">Parent Elements</span></span>

|<span data-ttu-id="d8904-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="d8904-118">Element</span></span>|<span data-ttu-id="d8904-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8904-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8904-120">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d8904-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="d8904-121">Define uma vista que é utilizada para apresentar um ou mais objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="d8904-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d8904-122">Observações</span><span class="sxs-lookup"><span data-stu-id="d8904-122">Remarks</span></span>

<span data-ttu-id="d8904-123">Na maioria dos casos, apenas uma definição é necessária para cada modo de exibição control, mas é possível fornecer várias definições, se pretender utilizar a mesma vista para apresentar diferentes objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="d8904-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="d8904-124">Nesses casos, pode fornecer uma definição de separado para cada objeto ou conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="d8904-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8904-125">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d8904-125">See Also</span></span>

[<span data-ttu-id="d8904-126">Elemento de CustomEntries para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d8904-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d8904-127">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="d8904-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="d8904-128">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d8904-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
