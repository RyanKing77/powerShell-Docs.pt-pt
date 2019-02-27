---
title: Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848224"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>SelectionCondition Element for EntrySelectedBy for Controls for View (Format) (Elemento SelectionCondition para EntrySelectedBy para Controls para View [Formatação])

Define uma condição que tem de existir durante a definição de controlo a ser utilizado. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para controles para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) EntrySelectedBy elemento para CustomEntry para controles para exibição (formato) SelectionCondition elemento para EntrySelectedBy para controles para exibição ( Formato)

## <a name="syntax"></a>Sintaxe

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionCondition` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de PropertyName para SelectionCondition para controles para exibição (formato)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica uma propriedade de .NET que aciona a condição.|
|[Elemento de ScriptBlock para SelectionCondition para controles para exibição (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o script que aciona a condição.|
|[Elemento de SelectionSetName para SelectionCondition para controles para exibição (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o conjunto de tipos do .NET que aciona a condição.|
|[Elemento de TypeName para SelectionCondition para controles para exibição (formato)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que aciona a condição.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de EntrySelectedBy para CustomEntry para controles para exibição (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar.|

## <a name="remarks"></a>Observações

Quando está a definir uma condição de seleção, aplicam-se os seguintes requisitos:

- A condição de seleção tem de especificar um nome de uma propriedade, pelo menos, ou um bloco de script, mas não é possível especificar ambos.

- A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.

Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Veja Também

[Elemento de PropertyName para SelectionCondition para controles para exibição (formato)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento de ScriptBlock para SelectionCondition para controles para exibição (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento de SelectionSetName para SelectionCondition para controles para exibição (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento de TypeName para SelectionCondition para controles para exibição (formato)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[Elemento de EntrySelectedBy para CustomEntry para controles para exibição (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
