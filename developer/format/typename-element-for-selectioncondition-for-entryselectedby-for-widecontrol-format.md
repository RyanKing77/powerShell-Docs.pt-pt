---
title: Elemento de TypeName para SelectionCondition para EntrySelectedBy para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 0d7bbfd8be3bf2bd1af75a45ca4db016dfb6bff6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848182"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format) (Elemento TypeName para SelectionCondition para EntrySelectedBy para WideControl [Formatação])

Especifica um tipo .NET que aciona a condição. Quando este tipo está presente, a definição é utilizada.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition WideEntry (formato) para EntrySelectedBy para o elemento de TypeName WideEntry (formato) para SelectionCondition para EntrySelectedBy para WideEntry (formato)

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
|[Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Define a condição de que tem de existir para esta entrada grande ser utilizado.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observações

A condição de seleção, pode especificar um tipo .NET ou uma seleção definido, mas não é possível especificar ambos. Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).

Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).

## <a name="see-also"></a>Consulte Também

[É criada uma vista alargada](./creating-a-wide-view.md)

[Definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md)

[Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
