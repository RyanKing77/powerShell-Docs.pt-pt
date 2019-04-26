---
title: Elemento de SelectionCondition para EntrySelectedBy para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064002"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a>SelectionCondition Element for EntrySelectedBy for WideControl (Format) (Elemento SelectionCondition para EntrySelectedBy para WideControl [Formatação])

Define a condição de que tem de existir para esta definição a utilizar. Não existe nenhum limite para o número de condições de seleção que podem ser especificados para uma definição de entrada ampla.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition WideEntry (formato) para EntrySelectedBy para WideEntry (formato)

## <a name="syntax"></a>Sintaxe

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionCondition` elemento. Tem de especificar um único `PropertyName` ou `ScriptBlock` elemento. O `SelectionSetName` e `TypeName` elementos são opcionais. Pode especificar um de qualquer elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade do .NET que aciona a condição.|
|[Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica o bloco de script que aciona a condição.|
|[Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Elemento opcional.<br /><br /> Especifica o conjunto de tipos do .NET que aciona a condição.|
|[Elemento de TypeName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que aciona a condição.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de EntrySelectedBy para WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)|Define os tipos do .NET que utilizam esta entrada ampla ou a condição que tem de existir para esta entrada a ser utilizado.|

## <a name="remarks"></a>Observações

Cada entrada ampla tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.

Quando está a definir uma condição de seleção, aplicam-se os seguintes requisitos:

- A condição de seleção tem de especificar um nome de uma propriedade, pelo menos, ou um bloco de script, mas não é possível especificar ambos.

- A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.

Para obter mais informações sobre como utilizar condições de seleção, consulte [Defining condições para quando uma entrada de exibição ou Item serve](./defining-conditions-for-displaying-data.md).

Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).

## <a name="see-also"></a>Veja Também

[Criar uma vista alargada](./creating-a-wide-view.md)

[Definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md)

[Elemento de EntrySelectedBy para WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)

[Elemento de PropertyName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Elemento de TypeName para SelectionCondition para EntrySelectedBy para WideEntry (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
