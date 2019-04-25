---
title: Definir conjuntos de seleção | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066316"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="17711-102">Defining Selection Sets (Eliminar Conjuntos de Seleção)</span><span class="sxs-lookup"><span data-stu-id="17711-102">Defining Selection Sets</span></span>

<span data-ttu-id="17711-103">Ao criar vários modos de exibição e controles, pode definir conjuntos de objetos que são referidos como conjuntos de seleção.</span><span class="sxs-lookup"><span data-stu-id="17711-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="17711-104">Um conjunto de seleção permite-lhe definir os objetos de uma vez, sem ter de defini-los repetidamente para cada vista ou o controle.</span><span class="sxs-lookup"><span data-stu-id="17711-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="17711-105">Normalmente, os conjuntos de seleção são utilizados quando tem um conjunto de objetos relacionados do .NET.</span><span class="sxs-lookup"><span data-stu-id="17711-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="17711-106">Por exemplo, o `FileSystem` arquivo formatação (FileSystem.format.ps1xml) define um conjunto de seleção dos tipos de sistema de ficheiros que utilizam vários modos de exibição.</span><span class="sxs-lookup"><span data-stu-id="17711-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="17711-107">Em que os conjuntos de seleção são definidas e referenciado</span><span class="sxs-lookup"><span data-stu-id="17711-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="17711-108">Definir conjuntos de seleção como parte dos dados comuns que podem ser utilizados por todas as vistas e os controles definidos no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="17711-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="17711-109">O exemplo seguinte mostra como definir três conjuntos de seleção.</span><span class="sxs-lookup"><span data-stu-id="17711-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="17711-110">Pode fazer referência a uma seleção define das seguintes formas:</span><span class="sxs-lookup"><span data-stu-id="17711-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="17711-111">Cada vista tem um `ViewSelectedBy` elemento que define quais os objetos são apresentados utilizando a vista.</span><span class="sxs-lookup"><span data-stu-id="17711-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="17711-112">O `ViewSelectedBy` elemento tem um `SelectionSetName` elemento subordinado que especifica a seleção que defina todas as definições de utilização do modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="17711-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="17711-113">Não existe nenhuma restrição no número de conjuntos de seleção que pode fazer referência a partir de uma vista.</span><span class="sxs-lookup"><span data-stu-id="17711-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="17711-114">Em cada definição de uma vista ou o controle, o `EntrySelectedBy` elemento define quais os objetos são apresentados utilizando essa definição.</span><span class="sxs-lookup"><span data-stu-id="17711-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="17711-115">Normalmente, uma vista ou o controle tem apenas uma definição para que os objetos são definidos pelo `ViewSelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="17711-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="17711-116">O `EntrySelectedBy` elemento da definição tem um `SelectionSetName` elemento subordinado que especifica o conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="17711-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="17711-117">Se especificar a seleção definido para uma definição, não é possível especificar qualquer um dos outros elementos filho do `EntrySelectedBy` elemento.</span><span class="sxs-lookup"><span data-stu-id="17711-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="17711-118">Em cada definição de uma vista ou o controle, o `SelectionCondition` elemento pode ser utilizado para especificar uma condição para quando a definição é utilizada.</span><span class="sxs-lookup"><span data-stu-id="17711-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="17711-119">O `SelectionCondition` elemento tem um `SelectionSetName` elemento subordinado que especifica a seleção definir que aciona a condição.</span><span class="sxs-lookup"><span data-stu-id="17711-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="17711-120">A condição é acionada quando qualquer um dos objetos definidos no conjunto de seleção são exibidas.</span><span class="sxs-lookup"><span data-stu-id="17711-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="17711-121">Para obter mais informações sobre como definir essas condições, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="17711-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="17711-122">Exemplo de conjunto de seleção</span><span class="sxs-lookup"><span data-stu-id="17711-122">Selection Set Example</span></span>

<span data-ttu-id="17711-123">O exemplo seguinte mostra um conjunto de seleção que está a ser utilizado diretamente a partir do `FileSystem` formatação ficheiro fornecido pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="17711-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="17711-124">Para obter mais informações sobre outros do Windows PowerShell, formatação de ficheiros, consulte [arquivos de formatação do Windows PowerShell](./powershell-formatting-files.md).</span><span class="sxs-lookup"><span data-stu-id="17711-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

<span data-ttu-id="17711-125">O conjunto de seleção anterior é referenciado no `ViewSelectedBy` elemento de uma vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="17711-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a><span data-ttu-id="17711-126">Elementos XML</span><span class="sxs-lookup"><span data-stu-id="17711-126">XML Elements</span></span>

 <span data-ttu-id="17711-127">Não existe nenhum limite para o número de conjuntos de seleção que pode definir.</span><span class="sxs-lookup"><span data-stu-id="17711-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="17711-128">Os seguintes elementos XML são utilizados para criar um conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="17711-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="17711-129">O [SelectionSets](./selectionsets-element-format.md) elemento define os conjuntos de objetos do .NET que são referenciados pelas exibições e controles do arquivo formatação.</span><span class="sxs-lookup"><span data-stu-id="17711-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="17711-130">O [SelectionSet](./selectionset-element-format.md) elemento define um único conjunto de objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="17711-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="17711-131">O [nome](./name-element-for-selectionset-format.md) elemento Especifica o nome que é utilizado para referenciar o conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="17711-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="17711-132">O [tipos](./types-element-for-selectionset-format.md) elemento Especifica os tipos do .NET dos objetos do conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="17711-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="17711-133">(Dentro de arquivos de formatação, são especificados objetos por tipo .NET.)</span><span class="sxs-lookup"><span data-stu-id="17711-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="17711-134">Os seguintes elementos XML são utilizados para especificar um conjunto de seleção.</span><span class="sxs-lookup"><span data-stu-id="17711-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="17711-135">O elemento seguinte especifica a seleção para utilizar em todas as definições da vista:</span><span class="sxs-lookup"><span data-stu-id="17711-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

    - [<span data-ttu-id="17711-136">Elemento de SelectionSetName para ViewSelectedBy (formato)</span><span class="sxs-lookup"><span data-stu-id="17711-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

    - [<span data-ttu-id="17711-137">Elemento de SelectionSetName para EntrySelectedBy para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="17711-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="17711-138">Os seguintes elementos especificam o conjunto de seleção utilizado por uma definição de vista única:</span><span class="sxs-lookup"><span data-stu-id="17711-138">The following elements specify the selection set used by a single view definition:</span></span>

    - [<span data-ttu-id="17711-139">Elemento de SelectionSetName para EntrySelectedBy para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="17711-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="17711-140">Elemento de SelectionSetName para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="17711-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="17711-141">Elemento de SelectionSetName para EntrySelectedBy para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="17711-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="17711-142">Elemento de SelectionSetName para EntrySelectedBy para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="17711-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="17711-143">Os seguintes elementos especificam o conjunto de seleção utilizado pelo comuns e veja as definições de controlo:</span><span class="sxs-lookup"><span data-stu-id="17711-143">The following elements specify the selection set used by common and view control definitions:</span></span>

    - [<span data-ttu-id="17711-144">Elemento de SelectionSetName para EntrySelectedBy para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="17711-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [<span data-ttu-id="17711-145">Elemento de SelectionSetName para EntrySelectedBy para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="17711-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="17711-146">Os seguintes elementos especificam o conjunto de seleção utilizado quando define em qual objeto para expandir:</span><span class="sxs-lookup"><span data-stu-id="17711-146">The following elements specify the selection set used when you define which object to expand:</span></span>

    - [<span data-ttu-id="17711-147">Elemento de SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="17711-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="17711-148">Os seguintes elementos especifiquem o conjunto de seleção utilizado pelas condições de seleção.</span><span class="sxs-lookup"><span data-stu-id="17711-148">The following elements specify the selection set used by selection conditions.</span></span>

    - [<span data-ttu-id="17711-149">Elemento de SelectionSetName para SelectionCondition para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="17711-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="17711-150">Elemento de SelectionSetName para SelectionCondition para controles para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="17711-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [<span data-ttu-id="17711-151">Elemento de SelectionSetName para SelectionCondition para CustomControl para exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="17711-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [<span data-ttu-id="17711-152">Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)</span><span class="sxs-lookup"><span data-stu-id="17711-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [<span data-ttu-id="17711-153">Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="17711-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [<span data-ttu-id="17711-154">Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para TableControl (formato)</span><span class="sxs-lookup"><span data-stu-id="17711-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="17711-155">Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)</span><span class="sxs-lookup"><span data-stu-id="17711-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [<span data-ttu-id="17711-156">Elemento de SelectionSetName para SelectionCondition para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="17711-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="17711-157">Veja Também</span><span class="sxs-lookup"><span data-stu-id="17711-157">See Also</span></span>

[<span data-ttu-id="17711-158">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="17711-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="17711-159">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="17711-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="17711-160">Nome</span><span class="sxs-lookup"><span data-stu-id="17711-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="17711-161">Tipos</span><span class="sxs-lookup"><span data-stu-id="17711-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="17711-162">Arquivos de formatação do PowerShell</span><span class="sxs-lookup"><span data-stu-id="17711-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="17711-163">Definir condições para quando os dados são apresentados</span><span class="sxs-lookup"><span data-stu-id="17711-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="17711-164">Escrever uma formatação de PowerShell e tipos de ficheiro</span><span class="sxs-lookup"><span data-stu-id="17711-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
