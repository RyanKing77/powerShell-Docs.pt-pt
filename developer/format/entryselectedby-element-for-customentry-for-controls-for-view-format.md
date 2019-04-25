---
title: Elemento de EntrySelectedBy para CustomEntry para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066248"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a>EntrySelectedBy Element for CustomEntry for Controls for View (Format) (Elemento EntrySelectedBy para CustomEntry para Controls para View [Formatação])

Define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para controles para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) EntrySelectedBy elemento para CustomEntry para controles para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elemento pai de elementos filho do `EntrySelectedBy` elemento. Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção de uma definição. Não existe nenhum limite máximo para o número de elementos filho que pode utilizar.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de SelectionCondition para EntrySelectedBy para controles para exibição (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Define a condição de que tem de existir para esta definição a utilizar.|
|[Elemento de SelectionSetName para EntrySelectedBy para controles para exibição (formato)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica um conjunto de tipos do .NET que utilizam esta definição do controle.|
|[Elemento de TypeName para EntrySelectedBy para controles para exibição (formato)](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que utiliza esta definição do controle.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomEntry para CustomEntries para controles para exibição (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Fornece uma definição do controle.|

## <a name="remarks"></a>Observações

Condições de seleção são utilizadas para definir uma condição que tem de existir para a definição a utilizar, como quando um objeto tem uma propriedade específica ou quando um valor de propriedade específica ou script que é avaliada como `true`. Para obter mais informações sobre as condições de seleção, consulte [Defining condições para quando uma entrada de exibição ou Item serve](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Veja Também

[Elemento de CustomEntry para CustomEntries para controles para exibição (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
