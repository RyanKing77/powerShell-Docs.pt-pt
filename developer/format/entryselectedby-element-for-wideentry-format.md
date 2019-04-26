---
title: Elemento de EntrySelectedBy para WideEntry (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066180"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>EntrySelectedBy Element for WideEntry (Format) (Elemento EntrySelectedBy para WideEntry [Formatação])

Define os tipos do .NET que utilizam esta definição da vista alargada ou a condição que tem de existir para esta definição a utilizar.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) EntrySelectedBy elemento de configuração para WideEntry (formato)

## <a name="syntax"></a>Sintaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `EntrySelectedBy` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Define a condição de que tem de existir para esta definição de vista alargada ser utilizado.|
|[Elemento de SelectionSetName para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica um conjunto de tipos do .NET que utilizam esta definição de vista alargada.|
|[Elemento de TypeName para EntrySelectedBy para WideEntry (formato)](./typename-element-for-entryselectedby-for-wideentry-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que utiliza esta definição de vista alargada.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)|Fornece uma definição da vista ampla.|

## <a name="remarks"></a>Observações

Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção de uma definição de vista alargada. Não existe nenhum limite máximo para o número de elementos filho que pode utilizar.

Condições de seleção são utilizadas para definir uma condição que tem de existir durante a definição a utilizar, por exemplo, quando um objeto tem uma propriedade específica ou um valor de propriedade específica ou um valor de script, que é avaliada como `true`. Para obter mais informações sobre as condições de seleção, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).

Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).

## <a name="see-also"></a>Veja Também

[Elemento de WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)

[Elemento de SelectionCondition para EntrySelectedBy para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento de SelectionSetName para EntrySelectedBy para WideEntry (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento de TypeName para EntrySelectedBy para WideEntry (formato)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Criar uma vista alargada](./creating-a-wide-view.md)

[Definir condições para apresentar os dados](./defining-conditions-for-displaying-data.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
