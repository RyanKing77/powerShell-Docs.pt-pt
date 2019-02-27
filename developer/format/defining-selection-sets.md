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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848861"
---
# <a name="defining-selection-sets"></a>Defining Selection Sets (Eliminar Conjuntos de Seleção)

Ao criar vários modos de exibição e controles, pode definir conjuntos de objetos que são referidos como conjuntos de seleção. Um conjunto de seleção permite-lhe definir os objetos de uma vez, sem ter de defini-los repetidamente para cada vista ou o controle. Normalmente, os conjuntos de seleção são utilizados quando tem um conjunto de objetos relacionados do .NET. Por exemplo, o `FileSystem` arquivo formatação (FileSystem.format.ps1xml) define um conjunto de seleção dos tipos de sistema de ficheiros que utilizam vários modos de exibição.

## <a name="where-selection-sets-are-defined-and-referenced"></a>Em que os conjuntos de seleção são definidas e referenciado

Definir conjuntos de seleção como parte dos dados comuns que podem ser utilizados por todas as vistas e os controles definidos no ficheiro de formatação. O exemplo seguinte mostra como definir três conjuntos de seleção.

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

Pode fazer referência a uma seleção define das seguintes formas:

- Cada vista tem um `ViewSelectedBy` elemento que define quais os objetos são apresentados utilizando a vista. O `ViewSelectedBy` elemento tem um `SelectionSetName` elemento subordinado que especifica a seleção que defina todas as definições de utilização do modo de exibição. Não existe nenhuma restrição no número de conjuntos de seleção que pode fazer referência a partir de uma vista.

- Em cada definição de uma vista ou o controle, o `EntrySelectedBy` elemento define quais os objetos são apresentados utilizando essa definição. Normalmente, uma vista ou o controle tem apenas uma definição para que os objetos são definidos pelo `ViewSelectedBy` elemento. O `EntrySelectedBy` elemento da definição tem um `SelectionSetName` elemento subordinado que especifica o conjunto de seleção. Se especificar a seleção definido para uma definição, não é possível especificar qualquer um dos outros elementos filho do `EntrySelectedBy` elemento.

- Em cada definição de uma vista ou o controle, o `SelectionCondition` elemento pode ser utilizado para especificar uma condição para quando a definição é utilizada. O `SelectionCondition` elemento tem um `SelectionSetName` elemento subordinado que especifica a seleção definir que aciona a condição. A condição é acionada quando qualquer um dos objetos definidos no conjunto de seleção são exibidas. Para obter mais informações sobre como definir essas condições, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).

## <a name="selection-set-example"></a>Exemplo de conjunto de seleção

O exemplo seguinte mostra um conjunto de seleção que está a ser utilizado diretamente a partir do `FileSystem` formatação ficheiro fornecido pelo Windows PowerShell. Para obter mais informações sobre outros do Windows PowerShell, formatação de ficheiros, consulte [arquivos de formatação do Windows PowerShell](./powershell-formatting-files.md).

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

O conjunto de seleção anterior é referenciado no `ViewSelectedBy` elemento de uma vista de tabela.

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

## <a name="xml-elements"></a>Elementos XML

 Não existe nenhum limite para o número de conjuntos de seleção que pode definir. Os seguintes elementos XML são utilizados para criar um conjunto de seleção.

- O [SelectionSets](./selectionsets-element-format.md) elemento define os conjuntos de objetos do .NET que são referenciados pelas exibições e controles do arquivo formatação.

- O [SelectionSet](./selectionset-element-format.md) elemento define um único conjunto de objetos .NET.

- O [nome](./name-element-for-selectionset-format.md) elemento Especifica o nome que é utilizado para referenciar o conjunto de seleção.

- O [tipos](./types-element-for-selectionset-format.md) elemento Especifica os tipos do .NET dos objetos do conjunto de seleção. (Dentro de arquivos de formatação, são especificados objetos por tipo .NET.)

 Os seguintes elementos XML são utilizados para especificar um conjunto de seleção.

- O elemento seguinte especifica a seleção para utilizar em todas as definições da vista:

    - [Elemento de SelectionSetName para ViewSelectedBy (formato)](./selectionsetname-element-for-viewselectedby-format.md)

    - [Elemento de SelectionSetName para EntrySelectedBy para GroupBy (formato)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- Os seguintes elementos especificam o conjunto de seleção utilizado por uma definição de vista única:

    - [Elemento de SelectionSetName para EntrySelectedBy para ListControl (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [Elemento de SelectionSetName para EntrySelectedBy para TableControl (formato)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento de SelectionSetName para EntrySelectedBy para WideControl (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [Elemento de SelectionSetName para EntrySelectedBy para CustomControl para exibição (formato)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- Os seguintes elementos especificam o conjunto de seleção utilizado pelo comuns e veja as definições de controlo:

    - [Elemento de SelectionSetName para EntrySelectedBy para controles para exibição (formato)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [Elemento de SelectionSetName para EntrySelectedBy para controles de configuração (formato)](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- Os seguintes elementos especificam o conjunto de seleção utilizado quando define em qual objeto para expandir:

    - [Elemento de SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Os seguintes elementos especifiquem o conjunto de seleção utilizado pelas condições de seleção.

    - [Elemento de SelectionSetName para SelectionCondition para controles de configuração (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [Elemento de SelectionSetName para SelectionCondition para controles para exibição (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [Elemento de SelectionSetName para SelectionCondition para CustomControl para exibição (formato)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para ListEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para TableControl (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [Elemento de SelectionSetName para SelectionCondition para GroupBy (formato)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>Veja Também

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[Nome](./name-element-for-selectionset-format.md)

[Tipos](./types-element-for-selectionset-format.md)

[Arquivos de formatação do PowerShell](./powershell-formatting-files.md)

[Definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md)

[Escrever uma formatação de PowerShell e tipos de ficheiro](./writing-a-powershell-formatting-file.md)
