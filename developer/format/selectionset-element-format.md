---
title: O elemento de SelectionSet (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850422"
---
# <a name="selectionset-element-format"></a>SelectionSet Element (Format) (Elemento SelectionSet [Formatação])

Define um conjunto de objetos do .NET que pode ser referenciado pelo nome do conjunto.

Elemento de configuração do SelectionSet elemento (formato) SelectionSets elemento (formato) (formato)

## <a name="syntax"></a>Sintaxe

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSet` elemento. Cada conjunto de seleção tem de ter um nome e tem de especificar os objetos de .NET do conjunto.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de nome para SelectionSet (formato)](./name-element-for-selectionset-format.md)|Elemento necessário.<br /><br /> Especifica o nome utilizado para referenciar o conjunto de seleção.|
|[Elemento de tipos (formato)](./types-element-for-selectionset-format.md)|Elemento necessário.<br /><br /> Define os objetos .NET na seleção definidas.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Formato de elemento de SelectionSets](./selectionsets-element-format.md)|Define os conjuntos comuns de objetos .NET que podem ser utilizados por todas as vistas do ficheiro de formatação.|

## <a name="remarks"></a>Observações

É possível utilizar conjuntos de seleção quando tem um conjunto de objetos relacionados que deseja fazer referência ao utilizar um nome único, como um conjunto de objetos que estão relacionados por meio de herança. Ao definir suas Exibições, pode especificar o conjunto de objetos usando o nome da seleção, em vez de listagem de todos os objetos dentro de cada vista.

Conjuntos de seleção comuns são especificados pelo respetivo nome quando definir as exibições do arquivo formatação ou as definições das vistas. Nestes casos, o `SelectionSetName` elemento subordinado do `ViewSelectedBy` e `EntrySelectedBy` elementos Especifica o conjunto a ser utilizado. Para obter mais informações sobre os conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra um `SelectionSet` elemento que define quatro tipos de .NET.

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

## <a name="see-also"></a>Veja Também

[Definir conjuntos de seleção](./defining-selection-sets.md)

[Elemento de nome de SelectionSet (formato)](./name-element-for-selectionset-format.md)

[Elemento de SelectionSets (formato)](./selectionsets-element-format.md)

[Elemento de tipos (formato)](./types-element-for-selectionset-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
