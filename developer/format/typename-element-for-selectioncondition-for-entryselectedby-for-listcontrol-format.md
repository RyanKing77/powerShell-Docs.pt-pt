---
title: Elemento de TypeName para SelectionCondition para EntrySelectedBy para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851556"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format) (Elemento TypeName para SelectionCondition para EntrySelectedBy para ListControl [Formatação])

Especifica um tipo .NET que aciona a condição. Quando este tipo está presente, é utilizada a entrada da lista.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry ListControl (formato) para ListEntries para o elemento de EntrySelectedBy ListControl (formato) para ListEntry para o elemento de SelectionCondition ListControl (formato) para EntrySelectedBy para o elemento de TypeName ListControl (formato) para SelectionCondition para EntrySelectedBy para ListControl (formato)

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
|[Elemento de SelectionCondition para EntrySelectedBy para ListControl (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Define a condição de que tem de existir para esta entrada da lista a ser utilizado.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observações

A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos. Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).

Para obter mais informações sobre outras os componentes de uma vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).

## <a name="see-also"></a>Consulte Também

[Criar uma vista de lista](./creating-a-list-view.md)

[Definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md)

[Elemento de SelectionCondition para EntrySelectedBy para ListControl (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
