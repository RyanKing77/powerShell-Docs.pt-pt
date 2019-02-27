---
title: Elemento de SelectionSetName para ViewSelectedBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848448"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>SelectionSetName Element for ViewSelectedBy (Format) (Elemento SelectionSetName para ViewSelectedBy [Formatação])

Especifica um conjunto de objetos do .NET que são apresentados pela exibição.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ViewSelectedBy elemento (formato) SelectionSetName elemento de configuração para ViewSelectedBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
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
|[Elemento de ViewSelectedBy (formato)](./viewselectedby-element-format.md)|Define os objetos do .NET que são apresentados pela exibição.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome do conjunto de seleção que é definido pelo `Name` elemento para o conjunto de seleção.

## <a name="remarks"></a>Observações

É possível utilizar conjuntos de seleção quando tem um conjunto de objetos relacionados que deseja fazer referência ao utilizar um nome único, como um conjunto de objetos que estão relacionados por meio de herança. Para obter mais informações sobre como definir e fazer referência a conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como especificar uma seleção definido para uma vista de lista. O mesmo esquema é usado para exibições de tabela, ampla e personalizadas.

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Veja Também

[Definir conjuntos de seleção](./defining-selection-sets.md)

[Elemento de ViewSelectedBy (formato)](./viewselectedby-element-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
