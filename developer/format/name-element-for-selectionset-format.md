---
title: Elemento de nome para SelectionSet (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065160"
---
# <a name="name-element-for-selectionset-format"></a>Name Element for SelectionSet (Format) (Elemento Name para SelectionSet [Formatação])

Especifica o nome utilizado para referenciar o conjunto de seleção.

Elemento de nome do elemento de SelectionSet (formato) do Configuration elemento (formato) SelectionSets elemento (formato) de SelectionSet (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `Name` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de SelectionSet (formato)](./selectionset-element-format.md)|Define um único conjunto de objetos do .NET que pode ser referenciado pelo nome do conjunto.|

## <a name="text-value"></a>Valor de texto

Especifique o nome para referenciar o conjunto de seleção. Existem não existem restrições quanto às quais caracteres podem ser utilizadas.

## <a name="remarks"></a>Observações

O nome especificado aqui é utilizado o `SelectionSetName` elemento. O conjunto de seleção que pode ser utilizado por uma exibição, por uma definição de uma vista (modos de exibição podem ter várias definições), ou ao especificar uma condição de seleção. Para obter mais informações sobre os conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).

## <a name="example"></a>Exemplo

Este exemplo mostra um `SelectionSet` elemento que define quatro tipos de .NET. O nome do conjunto de seleção é "FileSystemTypes".

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

[Elemento de SelectionSet (formato)](./selectionset-element-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
