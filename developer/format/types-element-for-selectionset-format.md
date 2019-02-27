---
title: Tipos de elemento para SelectionSet (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851276"
---
# <a name="types-element-for-selectionset-format"></a>Types Element for SelectionSet (Format) (Elemento Types para SelectionSet [Formatação])

Define os objetos .NET na seleção definidas.

Tipos de elemento de configuração do SelectionSet elemento (formato) SelectionSets elemento (formato) (formato) elemento (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Types` elemento. Tem de existir pelo menos um elemento subordinado, mas não existe nenhum limite máximo para o número de elementos filho que podem ser adicionados.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de TypeName dos tipos (formato)](./typename-element-for-types-format.md)|Elemento necessário.<br /><br /> Especifica o objeto do .NET que pertence ao conjunto de seleção.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de SelectionSet (formato)](./selectionset-element-format.md)|Define um conjunto de objetos do .NET que pode ser referenciado pelo nome do conjunto.|

## <a name="remarks"></a>Observações

Os objetos definidos por este elemento compõem um conjunto de seleção que pode ser utilizado por uma exibição, por uma definição de uma vista (modos de exibição podem ter várias definições), ou ao especificar uma condição de seleção.  Para obter mais informações sobre os conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).

## <a name="example"></a>Exemplo

Este exemplo mostra um `SelectionSet` elemento que define quatro tipos de .NET.

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

## <a name="see-also"></a>Consulte Também

[Definir conjuntos de objetos](./defining-selection-sets.md)

[Elemento de SelectionSet (formato)](./selectionset-element-format.md)

[Elemento de TypeName dos tipos (formato)](./typename-element-for-types-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
