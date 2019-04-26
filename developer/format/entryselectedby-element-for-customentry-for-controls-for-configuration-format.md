---
title: Elemento de EntrySelectedBy para CustomEntry para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066299"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="b370d-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) (Elemento EntrySelectedBy para CustomEntry para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="b370d-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b370d-103">Define os tipos do .NET que utilizam a definição de controle comum ou a condição que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="b370d-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="b370d-104">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="b370d-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="b370d-105">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de EntrySelectedBy de configuração (formato) para CustomEntry para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="b370d-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b370d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b370d-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b370d-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b370d-107">Attributes and Elements</span></span>

<span data-ttu-id="b370d-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="b370d-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b370d-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b370d-109">Attributes</span></span>

<span data-ttu-id="b370d-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="b370d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b370d-111">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="b370d-111">Child Elements</span></span>

|<span data-ttu-id="b370d-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b370d-112">Element</span></span>|<span data-ttu-id="b370d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b370d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b370d-114">Elemento de SelectionCondition para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="b370d-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="b370d-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b370d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b370d-116">Define a condição de que tem de existir durante a definição de controle comum a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="b370d-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="b370d-117">Elemento de SelectionSetName para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="b370d-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="b370d-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b370d-118">Optional element.</span></span><br /><br /> <span data-ttu-id="b370d-119">Especifica um conjunto de tipos do .NET que utilizam esta definição do controle comum.</span><span class="sxs-lookup"><span data-stu-id="b370d-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="b370d-120">Elemento de TypeName para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="b370d-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="b370d-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="b370d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="b370d-122">Especifica um tipo .NET que utiliza esta definição do controle comum.</span><span class="sxs-lookup"><span data-stu-id="b370d-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b370d-123">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="b370d-123">Parent Elements</span></span>

|<span data-ttu-id="b370d-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="b370d-124">Element</span></span>|<span data-ttu-id="b370d-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="b370d-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b370d-126">Elemento de CustomEntry para CustomControl para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="b370d-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="b370d-127">Fornece uma definição do controle comum.</span><span class="sxs-lookup"><span data-stu-id="b370d-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b370d-128">Observações</span><span class="sxs-lookup"><span data-stu-id="b370d-128">Remarks</span></span>

<span data-ttu-id="b370d-129">No mínimo, cada definição tem de ter pelo menos um .NET tipo, o conjunto de seleção ou condição de seleção especificada.</span><span class="sxs-lookup"><span data-stu-id="b370d-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="b370d-130">Não existe nenhum limite máximo para o número de tipos, conjuntos de seleção ou condições de seleção que pode ser especificado.</span><span class="sxs-lookup"><span data-stu-id="b370d-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="b370d-131">Veja Também</span><span class="sxs-lookup"><span data-stu-id="b370d-131">See Also</span></span>

[<span data-ttu-id="b370d-132">Elemento de SelectionCondition para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="b370d-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="b370d-133">Elemento de SelectionSetName para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="b370d-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="b370d-134">Elemento de CustomEntry para CustomControl para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="b370d-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="b370d-135">Elemento de TypeName para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="b370d-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="b370d-136">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b370d-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
