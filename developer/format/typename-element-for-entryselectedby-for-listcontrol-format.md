---
title: Elemento de TypeName para EntrySelectedBy para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 3f0c0ba1fe85d70557e67a30b3a9a59a33043475
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846887"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>TypeName Element for EntrySelectedBy for ListControl (Format) (Elemento TypeName para EntrySelectedBy para ListControl [Formatação])

Especifica um tipo .NET que utiliza esta entrada da exibição de lista. Não existe nenhum limite para o número de tipos que podem ser especificados para uma entrada na lista.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento (formato) ListEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de TypeName ListEntry (formato) para EntrySelectedBy para ListControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de EntrySelectedBy para ListEntry (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Define os tipos do .NET que utilizam esta entrada da lista ou a condição que tem de existir para esta entrada a ser utilizado.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observações

Cada entrada da lista tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.

Para obter mais informações sobre como este elemento é usado numa exibição de lista, consulte [vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como especificar uma seleção definido para uma entrada de uma vista de lista.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Veja Também

[Criar uma vista de lista](./creating-a-list-view.md)

[Elemento de EntrySelectedBy para ListEntry (formato)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Elemento de SelectionSetName para EnrtySelectedBy para ListEntry (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
