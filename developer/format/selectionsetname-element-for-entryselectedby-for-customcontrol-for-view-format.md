---
title: Elemento de SelectionSetName para EntrySelectedBy para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846131"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a>SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format) (Elemento SelectionSetName para EntrySelectedBy para CustomControl para View [Formatação])

Especifica um conjunto de objetos .NET para a entrada da lista. Não existe nenhum limite para o número de conjuntos de seleção que podem ser especificados para uma entrada.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para EntrySelectedBy de exibição (formato) Elemento para CustomEntry para exibição (formato) SelectionSetName elemento para EntrySelectedBy para CustomEntry (formato)

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
|[Elemento de EntrySelectedBy para CustomEntry para exibição (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Define os tipos do .NET que utilizam esta entrada personalizada ou a condição que tem de existir para esta entrada a ser utilizado.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome do conjunto de seleção.

## <a name="remarks"></a>Observações

Cada entrada de controle personalizado tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.

Conjuntos de seleção são normalmente utilizados quando quiser definir um grupo de objetos que são utilizados em vários modos de exibição. Por exemplo, pode querer criar uma vista de tabela e uma vista de lista para o mesmo conjunto de objetos. Para obter mais informações sobre como definir conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).

Para obter mais informações sobre os componentes de uma vista de controle personalizado, consulte [criar controles personalizados](./creating-custom-controls.md).

## <a name="see-also"></a>Consulte Também

[Elemento de EntrySelectedBy para CustomEntry para exibição (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Modo de exibição do controle personalizado](./creating-custom-controls.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
