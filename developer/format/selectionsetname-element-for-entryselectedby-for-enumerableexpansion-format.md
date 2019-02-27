---
title: Elemento de SelectionSetName para EntrySelectedBy para EnumerableExpansion (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851535"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a>SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format) (Elemento SelectionSetName para EntrySelectedBy para EnumerableExpansion [Formatação])

Especifica o conjunto de tipos do .NET que são expandidas por esta definição.

O elemento (formato) DefaultSettings elemento (formato) EnumerableExpansions elemento (formato) EnumerableExpansion elemento (formato) EntrySelectedBy elemento de configuração para o elemento de SelectionSetName EnumerableExpansion (formato) para EntrySelectedBy para EnumerableExpansion (formato)

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
|[Elemento de EntrySelectedBy para EnumerableExpansion (formato)](./entryselectedby-element-for-enumerableexpansion-format.md)|Define os objetos da coleção de .NET que são expandidos por esta definição.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome do conjunto de seleção.

## <a name="remarks"></a>Observações

Cada definição tem de especificar um ou mais nomes de tipo, um conjunto de seleção ou uma condição de seleção.

Conjuntos de seleção são normalmente utilizados quando quiser definir um grupo de objetos que são utilizados em vários modos de exibição. Por exemplo, pode querer criar uma vista de tabela e uma vista de lista para o mesmo conjunto de objetos. Para obter mais informações sobre como definir conjuntos de seleção, consulte [definir conjuntos de objetos para uma visão](./defining-selection-sets.md).

## <a name="see-also"></a>Veja Também

[Definir conjuntos de seleção](./defining-selection-sets.md)

[Elemento de EntrySelectedBy para EnumerableExpansion (formato)](./entryselectedby-element-for-enumerableexpansion-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
