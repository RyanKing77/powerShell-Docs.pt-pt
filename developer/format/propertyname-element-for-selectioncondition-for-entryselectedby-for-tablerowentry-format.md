---
title: Elemento de PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064667"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a>PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format) (Elemento PropertyName para SelectionCondition para EntrySelectedBy para TableRowEntry [Formatação])

Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e é utilizada a entrada da tabela.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento (formato) TableRowEntry elemento (formato) EntrySelectedBy elemento de configuração para TableRowEntry (formato) Elemento de SelectionCondition para EntrySelectedBy para o elemento de PropertyName TableRowEntry (formato) para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)

## <a name="syntax"></a>Sintaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Define a condição de que tem de existir para esta entrada de tabela a ser utilizado.|

## <a name="text-value"></a>Valor de texto

Especifique o nome de propriedade do .NET.

## <a name="remarks"></a>Observações

A condição de seleção tem de especificar o nome de pelo menos uma propriedade ou um bloco de script, mas não é possível especificar ambos. Para obter mais informações sobre como as condições de seleção podem ser utilizadas, consulte [Defining condições para quando uma entrada de exibição ou Item serve](./defining-conditions-for-displaying-data.md).

Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).

## <a name="see-also"></a>Veja Também

[Criar uma vista de tabela](./creating-a-table-view.md)

[Definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md)

[Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Elemento de SelectionCondition para EntrySelectedBy para TableRowEntry (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
