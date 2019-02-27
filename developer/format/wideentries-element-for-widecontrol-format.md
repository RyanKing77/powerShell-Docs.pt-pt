---
title: Elemento de WideEntries para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844906"
---
# <a name="wideentries-element-for-widecontrol-format"></a>WideEntries Element for WideControl (Format) (Elemento WideEntries para WideControl [Formatação])

Fornece as definições da vista ampla. A vista alargada tem de especificar uma ou mais definições.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries o elemento de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `WideEntries` elemento. Elemento, pelo menos, um subordinado tem de ser especificado.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)|Fornece uma definição da vista ampla.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de WideControl (formato)](./widecontrol-element-format.md)|Define uma vasta (valor único) formato de lista para a vista.|

## <a name="remarks"></a>Observações

Uma vista alargada é um formato de lista que mostra um valor de propriedade de único ou um valor de script para cada objeto. Para obter mais informações sobre os componentes de uma vista alargada, consulte [ampla componentes de exibição](./creating-a-wide-view.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra um `WideEntries` elemento que define uma única `WideEntry` elemento. O `WideEntry` elemento contém um único `WideItem` elemento que define qual o valor de propriedade ou um script é apresentado na vista.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

Para obter um exemplo completo de uma vista alargada, consulte [vista alargada (básico)](./wide-view-basic.md).

## <a name="see-also"></a>Veja Também

[Criar uma vista alargada](./creating-a-wide-view.md)

[Elemento de WideControl (formato)](./widecontrol-element-format.md)

[Elemento de WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
