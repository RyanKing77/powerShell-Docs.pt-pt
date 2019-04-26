---
title: Definir condições para a exibição de dados | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066333"
---
# <a name="defining-conditions-for-displaying-data"></a>Defining Conditions for Displaying Data (Definir Condições para Apresentar Dados)

Ao definir os dados que são apresentados por um modo de exibição ou um controle, pode especificar uma condição que tem de existir para os dados a serem exibidos. A condição pode ser acionada por uma propriedade específica ou quando um script ou valor da propriedade é avaliada como `true`. Quando a condição de seleção for cumprida, é utilizada a definição da vista ou do controle.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Especificar uma condição de seleção de uma definição

Ao criar uma definição para uma vista ou o controle, o `EntrySelectedBy` elemento é utilizado para especificar quais os objetos que irão utilizar a definição ou que condição tem de existir durante a definição a utilizar. A condição é especificada pelo `SelectionCondition` elemento.

No exemplo a seguir, uma condição de seleção está especificada para uma definição de uma vista de tabela. Neste exemplo, a definição é utilizada apenas quando o script especificado é avaliado para `true`.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

Não existe nenhum limite para o número de condições de seleção que pode especificar uma definição de uma vista ou o controle. Os únicos requisitos são os seguintes:

- A condição de seleção tem de especificar um nome de propriedade ou script para acionar a condição, mas não é possível especificar ambos.

- A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.

## <a name="specifying-a-selection-condition-for-an-item"></a>Especificar uma condição de seleção de um Item

Também pode especificar quando um item de uma vista de lista ou um controlo é utilizado, incluindo o `ItemSelectionCondition` elemento na definição do item. No exemplo a seguir, uma condição de seleção está especificada para um item de uma vista de lista. Neste exemplo, o item é utilizado apenas quando o script é avaliado para `true`.

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

Pode especificar a condição de apenas uma seleção de um item. E a condição tem de especificar um nome de propriedade ou script para acionar a condição, mas não é possível especificar ambos.

## <a name="xml-elements"></a>Elementos XML

 Os seguintes elementos XML são utilizados para criar uma condição de seleção.

- Condições de seleção para definições de exibição de especificar os seguintes elementos:

    - [Elemento de SelectionCondition para EntrySelectedBy para TableControl (formato)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Elemento de SelectionCondition para EntrySelectedBy para ListControl (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [Elemento de SelectionCondition para EntrySelectedBy para WideControl (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [Elemento de SelectionCondition para EntrySelectedBy para CustomControl (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- Seleção de especificar os elementos seguintes condições para comum e vista de controlam definições:

    - [Elemento de SelectionCondition para EntrySelectedBy para controles de configuração (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- O elemento seguinte especifica as condições de seleção para expandir os objetos da coleção:

    - [Elemento de SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- O elemento seguinte especifica as condições de seleção para exibir um novo grupo de dados:

    - [Elemento de SelectionCondition para EntrySelectedBy para GroupBy (formato)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- O elemento seguinte especifica uma condição de seleção de item para uma vista de lista:

    - [Elemento de ItemSelectionCondition para ListItem para ListControl (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- Os seguintes elementos especificar uma condição de seleção de item para controles:

    - [Elemento de ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [Elemento de ItemSelectionCondition para ExpressionBinding para controles para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [Elemento de ItemSelectionCondition para ExpressionBinding para CustomControl (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Veja Também

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
