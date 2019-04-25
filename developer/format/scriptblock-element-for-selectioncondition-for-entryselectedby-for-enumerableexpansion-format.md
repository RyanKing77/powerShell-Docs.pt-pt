---
title: Elemento de ScriptBlock para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064378"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format) (Elemento ScriptBlock para SelectionCondition para EntrySelectedBy para EnumerableExpansion [Formatação])

Especifica o script que aciona a condição.

O elemento (formato) DefaultSettings elemento (formato) EnumerableExpansions elemento (formato) EnumerableExpansion elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionCondition EnumerableExpansion (formato) para EntrySelectedBy para Elemento de ScriptBlock EnumerableExpansion (formato) para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Define a condição de que tem de existir para expandir os objetos da coleção desta definição.|

## <a name="text-value"></a>Valor de texto

Especifique o script que é avaliado.

## <a name="remarks"></a>Observações

A condição de seleção tem de especificar, pelo menos, um nome de script ou de propriedade para avaliar, mas não é possível especificar ambos. Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Veja Também

[Definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md)

[Elemento de PropertyName para SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[Elemento de SelectionCondition para EntrySelectedBy para EnumerableExpansion (formato)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
