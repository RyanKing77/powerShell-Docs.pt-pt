---
title: Elemento de ScriptBlock para SelectionCondition para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850898"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a>ScriptBlock Element for SelectionCondition for Controls for View (Format) (Elemento ScriptBlock para SelectionCondition para Controls para View [Formatação])

Especifica o script que aciona a condição. Quando esse script é avaliado para `true`, a condição é cumprida e a definição é utilizada. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para controles para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) EntrySelectedBy elemento para CustomEntry para controles para exibição (formato) SelectionCondition elemento para EntrySelectedBy para controles para exibição ( Elemento de ScriptBlock de formato) para SelectionCondition para controles para exibição (formato)

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
|[Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Define uma condição que tem de existir durante a definição de controlo a ser utilizado.|

## <a name="text-value"></a>Valor do Texto

Especifique o script que é avaliado.

## <a name="remarks"></a>Observações

A condição de seleção tem de especificar um, pelo menos, um script ou a propriedade nome para avaliar, mas não é possível especificar ambos. Para obter mais informações sobre como as condições de seleção podem ser utilizadas, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Veja Também

[Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
