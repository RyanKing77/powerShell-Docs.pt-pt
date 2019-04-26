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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066673"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="f2f67-102">CustomControl Element for View (Format) (Elemento CustomControl para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="f2f67-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="f2f67-103">Define um formato de controle personalizado para a vista.</span><span class="sxs-lookup"><span data-stu-id="f2f67-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="f2f67-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="f2f67-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f2f67-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2f67-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2f67-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f2f67-106">Attributes and Elements</span></span>

<span data-ttu-id="f2f67-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomControl` elemento.</span><span class="sxs-lookup"><span data-stu-id="f2f67-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="f2f67-108">Tem de especificar um elemento subordinado.</span><span class="sxs-lookup"><span data-stu-id="f2f67-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2f67-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="f2f67-109">Attributes</span></span>

<span data-ttu-id="f2f67-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f2f67-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f2f67-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="f2f67-111">Child Elements</span></span>

|<span data-ttu-id="f2f67-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="f2f67-112">Element</span></span>|<span data-ttu-id="f2f67-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2f67-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2f67-114">Elemento de CustomEntries para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="f2f67-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="f2f67-115">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="f2f67-115">Required element.</span></span><br /><br /> <span data-ttu-id="f2f67-116">Fornece definições de vista do controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="f2f67-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f2f67-117">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="f2f67-117">Parent Elements</span></span>

|<span data-ttu-id="f2f67-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="f2f67-118">Element</span></span>|<span data-ttu-id="f2f67-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="f2f67-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2f67-120">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="f2f67-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="f2f67-121">Define uma vista que é utilizada para apresentar um ou mais objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="f2f67-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f2f67-122">Observações</span><span class="sxs-lookup"><span data-stu-id="f2f67-122">Remarks</span></span>

<span data-ttu-id="f2f67-123">Na maioria dos casos, apenas uma definição é necessária para cada modo de exibição control, mas é possível fornecer várias definições, se pretender utilizar a mesma vista para apresentar diferentes objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="f2f67-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="f2f67-124">Nesses casos, pode fornecer uma definição de separado para cada objeto ou conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="f2f67-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2f67-125">Veja Também</span><span class="sxs-lookup"><span data-stu-id="f2f67-125">See Also</span></span>

[<span data-ttu-id="f2f67-126">Elemento de CustomEntries para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="f2f67-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f2f67-127">Elemento de exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="f2f67-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="f2f67-128">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2f67-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
