---
title: Elemento de SelectionSetName para EntrySelectedBy para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850310"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a>SelectionSetName Element for EntrySelectedBy for Controls for View (Format) (Elemento SelectionSetName para EntrySelectedBy para Controls para View [Formatação])

Especifica um conjunto de tipos do .NET que utilizam esta definição do controle. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para controles para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) EntrySelectedBy elemento para CustomEntry para controles para exibição (formato) SelectionSetName elemento para EntrySelectedBy para controles para exibição ( Formato)

## <a name="syntax"></a>Sintaxe

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.

### <a name="attributes"></a>Atributos

Nenhum

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de EntrySelectedBy para CustomEntry para controles para exibição (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome do conjunto de seleção.

## <a name="remarks"></a>Observações

Cada definição de controlo tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.

Conjuntos de seleção são normalmente utilizados quando quiser definir um grupo de objetos que são utilizados em vários modos de exibição. Para obter mais informações sobre como definir conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).

## <a name="see-also"></a>Veja Também

[Elemento de EntrySelectedBy para CustomEntry para controles para exibição (formato)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
