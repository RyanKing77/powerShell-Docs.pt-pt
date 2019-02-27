---
title: Elemento de CustomEntry para CustomEntries para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848756"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="5e569-102">CustomEntry Element for CustomEntries for Controls for View (Format) (Elemento CustomEntry para CustomEntries para Controls para View [Formatação])</span><span class="sxs-lookup"><span data-stu-id="5e569-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="5e569-103">Fornece uma definição do controle.</span><span class="sxs-lookup"><span data-stu-id="5e569-103">Provides a definition of the control.</span></span> <span data-ttu-id="5e569-104">Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.</span><span class="sxs-lookup"><span data-stu-id="5e569-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="5e569-105">Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5e569-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5e569-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e569-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5e569-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="5e569-107">Attributes and Elements</span></span>

<span data-ttu-id="5e569-108">As secções seguintes descrevem os atributos e elementos filho e os elementos pai do `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="5e569-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5e569-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="5e569-109">Attributes</span></span>

<span data-ttu-id="5e569-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5e569-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5e569-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="5e569-111">Child Elements</span></span>

|<span data-ttu-id="5e569-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="5e569-112">Element</span></span>|<span data-ttu-id="5e569-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e569-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5e569-114">Elemento de EntrySelectedBy para CustomEntry para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5e569-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="5e569-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="5e569-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5e569-116">Define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="5e569-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="5e569-117">Elemento de CustomItem para CustomEntry para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5e569-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="5e569-118">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="5e569-118">Required element.</span></span><br /><br /> <span data-ttu-id="5e569-119">Define como o controle exibe os dados.</span><span class="sxs-lookup"><span data-stu-id="5e569-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5e569-120">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="5e569-120">Parent Elements</span></span>

|<span data-ttu-id="5e569-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="5e569-121">Element</span></span>|<span data-ttu-id="5e569-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e569-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5e569-123">Elemento de CustomEntries para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5e569-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="5e569-124">Fornece as definições para o controle.</span><span class="sxs-lookup"><span data-stu-id="5e569-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5e569-125">Observações</span><span class="sxs-lookup"><span data-stu-id="5e569-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="5e569-126">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="5e569-126">See Also</span></span>

[<span data-ttu-id="5e569-127">Elemento de CustomEntries para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="5e569-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5e569-128">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="5e569-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
