---
title: Elemento de TypeName para SelectionCondition para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7141aefc-6656-4c52-8a9c-c2bfc9c87be9
caps.latest.revision: 6
ms.openlocfilehash: 7a697c286ec9efe750930739cdfa2580003365dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851213"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-view-format"></a>TypeName Element for SelectionCondition for Controls for View (Format) (Elemento TypeName para SelectionCondition para Controls para View [Formatação])

Especifica um tipo .NET que aciona a condição. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para controles para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) EntrySelectedBy elemento para CustomEntry para controles para exibição (formato) SelectionCondition elemento para EntrySelectedBy para controles para exibição ( Elemento de TypeName de formato) para SelectionCondition para controles para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Define uma condição que tem de existir durante a definição de controlo a ser utilizado.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observações

## <a name="see-also"></a>Veja Também

[Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
