---
title: Elemento de EntrySelectedBy para ListEntry para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054948"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>EntrySelectedBy Element for ListEntry for ListControl (Format) (Elemento EntrySelectedBy para ListEntry para ListControl [Formatação])

Define os tipos do .NET que utilizam esta definição de vista de lista ou a condição que tem de existir para esta definição a utilizar. Na maioria dos casos, apenas uma definição é necessária para uma vista de lista. No entanto, pode fornecer várias definições para a vista de lista, se pretender utilizar a mesma vista de lista para apresentar dados diferentes para objetos diferentes.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry ListControl (formato) para ListEntry para o elemento de EntrySelectedBy ListControl (formato) para ListEntry para ListControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `EntrySelectedBy` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de SelectionCondition para EntrySelectedBy para ListControl (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Define a condição de que tem de existir para esta definição de vista de lista a ser utilizado.|
|[Elemento de SelectionSetName para EntrySelectedBy para ListControl (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica um conjunto de tipos do .NET que utilizam esta definição de vista de lista.|
|[Elemento de TypeName para EntrySelectedBy para ListControl (formato)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que utiliza esta definição de vista de lista.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ListEntry para ListControl (formato)](./listentry-element-for-listcontrol-format.md)|Define a forma como são apresentadas as linhas da lista.|

## <a name="remarks"></a>Observações

Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para uma definição de vista de lista. Não existe nenhum limite máximo para o número de elementos filho que pode utilizar.

Condições de seleção são utilizadas para definir uma condição que tem de existir durante a definição a utilizar, por exemplo, quando um objeto tem uma propriedade específica ou um valor de propriedade específica ou um script é avaliada como `true`. Para obter mais informações sobre as condições de seleção, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).

Para obter mais informações sobre os componentes de uma vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como definir os objetos para uma vista de lista com o respetivo nome de tipo .NET.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>Veja Também

[Elemento de ListEntry para ListControl (formato)](./listentry-element-for-listcontrol-format.md)

[Elemento de SelectionCondition para EntrySelectedBy para ListControl (formato)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Elemento de SelectionSetName para EntrySelectedBy para ListControl (formato)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Elemento de TypeName para EntrySelectedBy para ListControl (formato)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[Criar uma vista de lista](./creating-a-list-view.md)

[Definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
