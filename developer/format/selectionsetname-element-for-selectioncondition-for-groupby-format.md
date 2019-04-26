---
title: Elemento de SelectionSetName para SelectionCondition para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063771"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a>SelectionSetName Element for SelectionCondition for GroupBy (Format) (Elemento SelectionSetName para SelectionCondition para GroupBy [Formatação])

Especifica o conjunto de tipos do .NET que acionam a condição. Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado ao utilizar este controlo. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de EntrySelectedBy GroupBy (formato) para CustomEntry para o elemento de SelectionCondition GroupBy (formato) para EntrySelectedBy para o elemento de SelectionSetName GroupBy (formato) para SelectionCondition para GroupBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de SelectionCondition para EntrySelectedBy para GroupBy (formato)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Define uma condição que tem de existir durante a definição de controlo a ser utilizado.|

## <a name="text-value"></a>Valor de texto

Especifique o nome do conjunto de seleção.

## <a name="remarks"></a>Observações

Conjuntos de seleção são comuns grupos de objetos .NET que podem ser utilizados por qualquer vista que define o ficheiro de formatação. Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).

Quando este elemento é especificado, não é possível especificar a [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) elemento. Para obter mais informações sobre como definir condições de seleção, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Veja Também

[Elemento de TypeName para SelectionCondition para GroupBy (formato)](./typename-element-for-selectioncondition-for-groupby-format.md)

[Elemento de SelectionCondition para EntrySelectedBy para GroupBy (formato)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md)

[Definir conjuntos de seleção](./defining-selection-sets.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
