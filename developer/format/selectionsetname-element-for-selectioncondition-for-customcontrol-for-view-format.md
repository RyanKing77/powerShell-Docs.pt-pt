---
title: Elemento de SelectionSetName para SelectionCondition para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851549"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>SelectionSetName Element for SelectionCondition for CustomControl for View (Format) (Elemento SelectionSetName para SelectionCondition para CustomControl para View [Formatação])

Especifica o conjunto de tipos do .NET que acionam a condição. Quando qualquer um dos tipos neste conjunto estiverem presentes, a condição é cumprida e o objeto é apresentado com esse controle. Este elemento é utilizado ao definir uma vista de controle personalizado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para EntrySelectedBy de exibição (formato) Elemento para CustomEntry para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Define uma condição que tem de existir durante a definição de controlo a ser utilizado.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome do conjunto de seleção.

## <a name="remarks"></a>Observações

Conjuntos de seleção são comuns grupos de objetos .NET que podem ser utilizados por qualquer vista que define o ficheiro de formatação. Para obter mais informações sobre como criar e referenciar conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).

A condição de seleção pode especificar um conjunto de seleção ou o tipo .NET, mas não é possível especificar ambos. Para obter mais informações sobre como utilizar condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Veja Também

[Elemento de SelectionCondition para EntrySelectedBy para CustomControl para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md)

[Definir conjuntos de seleção](./defining-selection-sets.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
