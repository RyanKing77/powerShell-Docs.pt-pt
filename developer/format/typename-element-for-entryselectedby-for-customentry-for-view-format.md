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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848798"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="323c0-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format) (Elemento TypeName para EntrySelectedBy para CustomEntry para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="323c0-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="323c0-103">Especifica um tipo .NET que utiliza esta definição de vista do controle personalizado.</span><span class="sxs-lookup"><span data-stu-id="323c0-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="323c0-104">Não existe nenhum limite para o número de tipos que podem ser especificados para uma definição.</span><span class="sxs-lookup"><span data-stu-id="323c0-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="323c0-105">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para EntrySelectedBy de exibição (formato) Elemento para CustomEntry para exibição (formato) TypeName elemento para EntrySelectedBy para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="323c0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="323c0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="323c0-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="323c0-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="323c0-107">Attributes and Elements</span></span>

<span data-ttu-id="323c0-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento.</span><span class="sxs-lookup"><span data-stu-id="323c0-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="323c0-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="323c0-109">Attributes</span></span>

<span data-ttu-id="323c0-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="323c0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="323c0-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="323c0-111">Child Elements</span></span>

<span data-ttu-id="323c0-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="323c0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="323c0-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="323c0-113">Parent Elements</span></span>

|<span data-ttu-id="323c0-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="323c0-114">Element</span></span>|<span data-ttu-id="323c0-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="323c0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="323c0-116">Elemento de EntrySelectedBy para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="323c0-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="323c0-117">Define os tipos do .NET que utilizam esta definição de vista do controle personalizado ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="323c0-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="323c0-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="323c0-118">Text Value</span></span>

<span data-ttu-id="323c0-119">Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="323c0-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="323c0-120">Observações</span><span class="sxs-lookup"><span data-stu-id="323c0-120">Remarks</span></span>

<span data-ttu-id="323c0-121">Cada definição de vista do controle personalizado tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.</span><span class="sxs-lookup"><span data-stu-id="323c0-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="323c0-122">Para obter mais informações sobre os componentes de uma vista de controle personalizado, consulte [criar controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="323c0-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="323c0-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="323c0-123">See Also</span></span>

[<span data-ttu-id="323c0-124">Criação de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="323c0-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="323c0-125">Elemento de EntrySelectedBy para CustomEntry para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="323c0-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="323c0-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="323c0-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
