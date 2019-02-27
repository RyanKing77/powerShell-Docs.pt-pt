---
title: Elemento de EntrySelectedBy para CustomEntry para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849323"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) (Elemento EntrySelectedBy para CustomEntry para CustomControl para View [Formatação])

Define os tipos do .NET que utilizam esta entrada personalizada ou a condição que tem de existir para esta entrada a ser utilizado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para EntrySelectedBy de exibição (formato) Elemento para CustomEntry para exibição (formato)

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
|[Elemento de SelectionCondition para EntrySelectedBy para CustomEntry (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Elemento opcional.<br /><br /> Define a condição de que tem de existir para esta definição a utilizar.|
|[Elemento de SelectionSetName para EntrySelectedBy para CustomEntry (formato)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica um conjunto de tipos do .NET que utilizam esta definição do modo de exibição control.|
|[Elemento de TypeName para EntrySelectedBy para CustomEntry (formato)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que utiliza esta definição do modo de exibição control.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomEntry para CustomEntries para exibição (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Define os controlos utilizados por objetos específicos do .NET.|

## <a name="remarks"></a>Observações

Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para uma entrada. Não existe nenhum limite máximo para o número de elementos filho que pode utilizar.

Condições de seleção são utilizadas para definir uma condição que tem de existir para a entrada a ser utilizado, como quando um objeto tem uma propriedade específica ou quando um valor de propriedade específica ou script que é avaliada como `true`. Para obter mais informações sobre as condições de seleção, consulte [Defining condições para quando uma entrada de exibição ou Item serve](./defining-conditions-for-displaying-data.md).

Para obter mais informações sobre os componentes de uma vista de controle personalizado, consulte [modo de exibição de controle personalizado](./creating-custom-controls.md).

## <a name="see-also"></a>Veja Também

[Elemento de SelectionCondition para EntrySelectedBy para CustomEntry (formato)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Elemento de SelectionSetName para EntrySelectedBy para CustomEntry (formato)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[Elemento de TypeName para EntrySelectedBy para CustomEntry (formato)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Elemento de CustomEntry para CustomEntries para exibição (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Modo de exibição do controle personalizado](./creating-custom-controls.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
