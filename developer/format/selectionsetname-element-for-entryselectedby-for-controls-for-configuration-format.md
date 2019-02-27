---
title: Elemento de SelectionSetName para EntrySelectedBy para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850247"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="e32c0-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format) (Elemento SelectionSetName para EntrySelectedBy para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="e32c0-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e32c0-103">Especifica um conjunto de tipos do .NET que utilizam esta definição do controle.</span><span class="sxs-lookup"><span data-stu-id="e32c0-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="e32c0-104">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="e32c0-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e32c0-105">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de EntrySelectedBy de configuração (formato) para CustomEntry para controles para o elemento de SelectionSetName de configuração (formato) para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e32c0-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e32c0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e32c0-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e32c0-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="e32c0-107">Attributes and Elements</span></span>

<span data-ttu-id="e32c0-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="e32c0-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e32c0-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="e32c0-109">Attributes</span></span>

<span data-ttu-id="e32c0-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e32c0-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="e32c0-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="e32c0-111">Child Elements</span></span>

<span data-ttu-id="e32c0-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e32c0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e32c0-113">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="e32c0-113">Parent Elements</span></span>

|<span data-ttu-id="e32c0-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="e32c0-114">Element</span></span>|<span data-ttu-id="e32c0-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="e32c0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e32c0-116">Elemento de EntrySelectedBy para CustomEntry para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e32c0-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="e32c0-117">Define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="e32c0-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e32c0-118">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="e32c0-118">Text Value</span></span>

<span data-ttu-id="e32c0-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="e32c0-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e32c0-120">Observações</span><span class="sxs-lookup"><span data-stu-id="e32c0-120">Remarks</span></span>

<span data-ttu-id="e32c0-121">Cada definição de controlo tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.</span><span class="sxs-lookup"><span data-stu-id="e32c0-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="e32c0-122">Conjuntos de seleção são normalmente utilizados quando quiser definir um grupo de objetos que são utilizados em vários modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="e32c0-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="e32c0-123">Para obter mais informações sobre como definir conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e32c0-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e32c0-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="e32c0-124">See Also</span></span>

[<span data-ttu-id="e32c0-125">Elemento de EntrySelectedBy para CustomEntry para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="e32c0-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="e32c0-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e32c0-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
