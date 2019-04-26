---
title: Elemento de SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064140"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a>Elemento SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format) (Elemento SelectionCondition para EntrySelectedBy para EnumerableExpansion [Formatação])

Define a condição de que tem de existir para expandir os objetos da coleção desta definição.

O elemento (formato) DefaultSettings elemento (formato) EnumerableExpansions elemento (formato) EnumerableExpansion elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition EnumerableExpansion (formato) para EntrySelectedBy para EnumerableExpansion (formato)

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
|[Elemento de PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade do .NET que aciona a condição.|
|[Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica o script que aciona a condição.|
|[Elemento de SelectionSetName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica o conjunto de tipos do .NET que aciona a condição.|
|[Elemento de TypeName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que aciona a condição.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de EntrySelectedBy para EnumerableExpansion (formato)](./entryselectedby-element-for-enumerableexpansion-format.md)|Define os objetos da coleção de .NET são expandidos por esta definição.|

## <a name="remarks"></a>Observações

Cada definição tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.

Quando está a definir uma condição de seleção, aplicam-se os seguintes requisitos:

- A condição de seleção tem de especificar um nome de uma propriedade, pelo menos, ou um bloco de script, mas não é possível especificar ambos.

- A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.

Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para os dados de Diplaying](./defining-conditions-for-displaying-data.md).

Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [vista alargada](./creating-a-wide-view.md).

## <a name="see-also"></a>Veja Também

[Definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
