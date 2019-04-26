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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064005"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="8b873-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format) (Elemento SelectionSetName para EntrySelectedBy para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="8b873-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="8b873-103">Especifica um conjunto de tipos do .NET que utilizam esta definição do controle.</span><span class="sxs-lookup"><span data-stu-id="8b873-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="8b873-104">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="8b873-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="8b873-105">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de EntrySelectedBy de configuração (formato) para CustomEntry para controles para o elemento de SelectionSetName de configuração (formato) para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="8b873-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8b873-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b873-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="8b873-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8b873-107">Attributes and Elements</span></span>

<span data-ttu-id="8b873-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.</span><span class="sxs-lookup"><span data-stu-id="8b873-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8b873-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="8b873-109">Attributes</span></span>

<span data-ttu-id="8b873-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8b873-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="8b873-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="8b873-111">Child Elements</span></span>

<span data-ttu-id="8b873-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8b873-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8b873-113">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="8b873-113">Parent Elements</span></span>

|<span data-ttu-id="8b873-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="8b873-114">Element</span></span>|<span data-ttu-id="8b873-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b873-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8b873-116">Elemento de EntrySelectedBy para CustomEntry para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="8b873-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="8b873-117">Define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="8b873-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8b873-118">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="8b873-118">Text Value</span></span>

<span data-ttu-id="8b873-119">Especifique o nome do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="8b873-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="8b873-120">Observações</span><span class="sxs-lookup"><span data-stu-id="8b873-120">Remarks</span></span>

<span data-ttu-id="8b873-121">Cada definição de controlo tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.</span><span class="sxs-lookup"><span data-stu-id="8b873-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="8b873-122">Conjuntos de seleção são normalmente utilizados quando quiser definir um grupo de objetos que são utilizados em vários modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="8b873-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="8b873-123">Para obter mais informações sobre como definir conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="8b873-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8b873-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="8b873-124">See Also</span></span>

[<span data-ttu-id="8b873-125">Elemento de EntrySelectedBy para CustomEntry para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="8b873-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="8b873-126">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b873-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
