---
title: Elemento de TypeName para tipos (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: 4f463ac6b70a00f628c5b93b112c5fa510ff3bfb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845116"
---
# <a name="typename-element-for-types-format"></a>TypeName Element for Types (Format) (Elemento TypeName para Types [Formatação])

Especifica o tipo de .NET de um objeto que pertence ao conjunto de seleção.

Tipos de elemento de configuração do SelectionSet elemento (formato) SelectionSets elemento (formato) (formato) elemento (formato) TypeName elemento de tipos (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento. Pelo menos um `TypeName` elemento tem de ser incluído no conjunto de seleção.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de tipos (formato)](./types-element-for-selectionset-format.md)|Define os objetos .NET na seleção definidas.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome completamente qualificado para o tipo de .NET.

## <a name="remarks"></a>Observações

É possível utilizar conjuntos de seleção quando tem um conjunto de objetos relacionados que deseja fazer referência ao utilizar um nome único, como um conjunto de objetos que estão relacionados por meio de herança. Ao definir suas Exibições, pode especificar o conjunto de objetos usando o nome da seleção, em vez de listagem de todos os objetos dentro de cada vista.

Comum de seleção de conjuntos são especificados pelo respetivo nome quando definir as exibições do arquivo formatação. Nestes casos, o `SelectionSetName` elemento subordinado do `ViewSelectedBy` elemento para a vista Especifica o conjunto. No entanto, as entradas diferentes de uma vista também podem especificar um conjunto de seleção que se aplica a apenas essa entrada da vista. Para obter mais informações sobre os conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra um `SelectionSet` elemento que define quatro tipos de .NET.

```
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

[Elemento de SelectionSets (formato)](./selectionsets-element-format.md)

[Elemento de tipos (formato)](./types-element-for-selectionset-format.md)

[Escrever um Windows PowDefining conjuntos de ObjecterShell formatação ficheiro](./writing-a-powershell-formatting-file.md)
