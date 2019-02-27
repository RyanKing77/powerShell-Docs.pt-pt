---
title: Elemento de TypeName para EntrySelectedBy para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850779"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="04bb5-102">TypeName Element for EntrySelectedBy for GroupBy (Format) (Elemento TypeName para EntrySelectedBy para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="04bb5-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="04bb5-103">Especifica um tipo .NET que utiliza esta definição do controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="04bb5-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="04bb5-104">Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="04bb5-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="04bb5-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de EntrySelectedBy GroupBy (formato) para CustomEntry para o elemento de TypeName GroupBy (formato) para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="04bb5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="04bb5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04bb5-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="04bb5-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="04bb5-107">Attributes and Elements</span></span>

<span data-ttu-id="04bb5-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="04bb5-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="04bb5-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="04bb5-109">Attributes</span></span>

<span data-ttu-id="04bb5-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="04bb5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="04bb5-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="04bb5-111">Child Elements</span></span>

<span data-ttu-id="04bb5-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="04bb5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="04bb5-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="04bb5-113">Parent Elements</span></span>

|<span data-ttu-id="04bb5-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="04bb5-114">Element</span></span>|<span data-ttu-id="04bb5-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="04bb5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04bb5-116">Elemento de EntrySelectedBy para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="04bb5-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="04bb5-117">Define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="04bb5-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="04bb5-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="04bb5-118">Text Value</span></span>

<span data-ttu-id="04bb5-119">Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="04bb5-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="04bb5-120">Observações</span><span class="sxs-lookup"><span data-stu-id="04bb5-120">Remarks</span></span>

<span data-ttu-id="04bb5-121">Cada definição de controlo tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.</span><span class="sxs-lookup"><span data-stu-id="04bb5-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="04bb5-122">Para obter mais informações sobre os componentes de uma vista de controle personalizado, consulte [criar controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="04bb5-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="04bb5-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="04bb5-123">See Also</span></span>

[<span data-ttu-id="04bb5-124">Criação de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="04bb5-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="04bb5-125">Elemento de EntrySelectedBy para CustomEntry para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="04bb5-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="04bb5-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="04bb5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
