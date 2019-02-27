---
title: Elemento de SelectionSetName para EntrySelectedBy para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846880"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>SelectionSetName Element for EntrySelectedBy for TableControl (Format) (Elemento SelectionSetName para EntrySelectedBy para TableControl [Formatação])

Especifica que a utilização de tipos de um conjunto de .NET, esta entrada da vista de tabela. Não existe nenhum limite para o número de conjuntos de seleção que podem ser especificados para uma entrada.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento (formato) TableRowEntry elemento (formato) EntrySelectedBy elemento (formato) SelectionSetName elemento de configuração para EntrySelectedBy para TableRowEntry (formato)

## <a name="syntax"></a>Sintaxe

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos principais elementos filho.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de EntrySelectedBy (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Define os tipos do .NET que utilizam esta entrada ou a condição que tem de existir para esta entrada a ser utilizado.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome do conjunto de seleção.

## <a name="remarks"></a>Observações

Conjuntos de seleção são normalmente utilizados quando quiser definir um grupo de objetos que são utilizados em vários modos de exibição. Por exemplo, pode querer criar uma vista de tabela e uma vista de lista para o mesmo conjunto de objetos. Para obter mais informações sobre como definir conjuntos de seleção, consulte [definir conjuntos de objetos para uma visão](./defining-selection-sets.md).

Se especificar uma seleção definido para uma entrada, não é possível especificar um nome de tipo. Para obter mais informações sobre como especificar um tipo .NET, consulte [elemento TypeName para EntrySelectedBy para TableRowEntry (formato)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).

Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).

## <a name="see-also"></a>Consulte Também

[Elemento de EntrySelectedBy (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Definir conjuntos de objetos para uma visão](./defining-selection-sets.md)

[Criar uma vista de tabela](./creating-a-table-view.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
