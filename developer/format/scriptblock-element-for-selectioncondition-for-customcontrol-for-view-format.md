---
title: Elemento de ScriptBlock para SelectionCondition para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847804"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a>ScriptBlock Element for SelectionCondition for CustomControl for View (Format) (Elemento ScriptBlock para SelectionCondition para CustomControl para View [Formatação])

Especifica o script que aciona a condição. Quando esse script é avaliado para `true`, a condição é cumprida e a definição é utilizada. Este elemento é utilizado ao definir uma vista de controle personalizado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento de configuração para o modo de exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para CustomControl para exibição ( Elemento de CustomItem de formato) para CustomEntry para CustomControl para exibição (formato) SelectionCondition elemento para EntrySelectedBy para CustomControl para exibição (formato) ScriptBlock elemento para SelectionCondition para CustomControl para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Define uma condição que tem de existir durante a definição de controlo a ser utilizado.|

## <a name="text-value"></a>Valor do Texto

Especifique o script que é avaliado.

## <a name="remarks"></a>Observações

A condição de seleção tem de especificar um, pelo menos, um script ou a propriedade nome para avaliar, mas não é possível especificar ambos. Para obter mais informações sobre como as condições de seleção podem ser utilizadas, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Consulte Também

[Elemento de SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
