---
title: Elemento de WideEntry para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083676"
---
# <a name="wideentry-element-for-widecontrol-format"></a>WideEntry Element for WideControl (Format) (Elemento WideEntry para WideControl [Formatação])

Fornece uma definição da vista ampla.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry o elemento de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `WideEntry` elemento. Tem de especificar um único `WideItem` elemento subordinado.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de EntrySelectedBy para WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)|Elemento opcional.<br /><br /> Define os tipos do .NET que usam essa definição ampla de entrada ou a condição que tem de existir para esta definição a utilizar.|
|[Elemento de WideItem (formato)](./wideitem-element-for-widecontrol-format.md)|Elemento necessário.<br /><br /> Define a propriedade ou um script cujo valor é apresentado.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de WideEntries (formato)](./wideentries-element-for-widecontrol-format.md)|Fornece as definições da vista ampla.|

## <a name="remarks"></a>Observações

Uma vista alargada é um formato de lista que mostra um valor de propriedade de único ou um valor de script para cada objeto. Ao contrário de outros tipos de vistas, pode especificar apenas um elemento de item para cada definição de vista. Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra um `WideEntry` elemento que define uma única `WideItem` elemento. O `WideItem` elemento define a propriedade cujo valor é apresentado na vista.

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

Para obter um exemplo completo de uma vista alargada, consulte [vista alargada (básico)](./wide-view-basic.md).

## <a name="see-also"></a>Veja Também

[Criar uma vista alargada](./creating-a-wide-view.md)

[Elemento de SelectionCondition para WideEntry (formato)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento de SelectionSetName para WideEntry (formato)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Elemento de TypeName para WideEntry (formato)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Elemento de WideEntries (formato)](./wideentries-element-for-widecontrol-format.md)

[Elemento de WideItem (formato)](./wideitem-element-for-widecontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
