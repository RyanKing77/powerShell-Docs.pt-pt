---
title: Elemento de TypeName para EntrySelectedBy para CustomEntry para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083982"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="bd032-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format) (Elemento TypeName para EntrySelectedBy para CustomEntry para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="bd032-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="bd032-103">Especifica um tipo .NET que utiliza esta definição de vista do controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="bd032-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="bd032-104">Não existe nenhum limite para o número de tipos que podem ser especificados para uma definição.</span><span class="sxs-lookup"><span data-stu-id="bd032-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="bd032-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para EntrySelectedBy de exibição (formato) Elemento para CustomEntry para exibição (formato) TypeName elemento para EntrySelectedBy para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="bd032-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bd032-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd032-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bd032-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bd032-107">Attributes and Elements</span></span>

<span data-ttu-id="bd032-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="bd032-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bd032-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="bd032-109">Attributes</span></span>

<span data-ttu-id="bd032-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="bd032-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bd032-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="bd032-111">Child Elements</span></span>

<span data-ttu-id="bd032-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="bd032-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bd032-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="bd032-113">Parent Elements</span></span>

|<span data-ttu-id="bd032-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="bd032-114">Element</span></span>|<span data-ttu-id="bd032-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="bd032-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bd032-116">Elemento de EntrySelectedBy para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="bd032-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="bd032-117">Define os tipos do .NET que utilizam esta definição de vista do controle personalizado ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="bd032-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bd032-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="bd032-118">Text Value</span></span>

<span data-ttu-id="bd032-119">Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="bd032-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd032-120">Observações</span><span class="sxs-lookup"><span data-stu-id="bd032-120">Remarks</span></span>

<span data-ttu-id="bd032-121">Cada definição de vista do controle personalizado tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.</span><span class="sxs-lookup"><span data-stu-id="bd032-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="bd032-122">Para obter mais informações sobre os componentes de uma vista de controle personalizado, consulte [criar controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="bd032-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bd032-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="bd032-123">See Also</span></span>

[<span data-ttu-id="bd032-124">Criação de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="bd032-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="bd032-125">Elemento de EntrySelectedBy para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="bd032-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="bd032-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="bd032-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
