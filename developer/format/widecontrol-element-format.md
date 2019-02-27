---
title: O elemento de WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849491"
---
# <a name="widecontrol-element-format"></a>WideControl Element (Format) (Elemento WideControl [Formatação])

Define uma vasta (valor único) formato de lista para a vista. Esta vista apresenta um valor de propriedade de único ou um valor de script para cada objeto.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `WideControl` elemento. Não é possível especificar a `AutoSize` e `ColumnNumber` elementos ao mesmo tempo.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de dimensionamento automático para WideControl (formato)](./autosize-element-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica se o tamanho da coluna e o número de colunas são ajustados com base no tamanho dos dados.|
|[Elemento de ColumnNumber para WideControl (formato)](./columnnumber-element-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica o número de colunas apresentadas na vista alargada.|
|[Elemento de WideEntries (formato)](./wideentries-element-for-widecontrol-format.md)|Elemento necessário.<br /><br /> Fornece as definições da vista ampla.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de exibição (formato)](./view-element-format.md)|Define uma vista que é utilizada para apresentar um ou mais objetos do .NET.|

## <a name="remarks"></a>Observações

Ao definir uma vista alargada, pode adicionar os `AutoSize` elemento ou o `ColumnNumber` , mas não é possível adicionar ambos.

Na maioria dos casos, apenas uma definição é necessária para cada vista alargada, mas é possível ter várias definições, se pretender utilizar a mesma vista para apresentar diferentes objetos do .NET. Nesses casos, pode fornecer uma definição de separado para cada objeto ou conjunto de objetos.

Para obter mais informações sobre os componentes de uma vista alargada, consulte [ampla componentes de exibição](./creating-a-wide-view.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra um `WideControl` elemento que é utilizado para apresentar uma propriedade do [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

Para obter um exemplo completo de uma vista alargada, consulte [vista alargada (básico)](./wide-view-basic.md).

## <a name="see-also"></a>Consulte Também

[Elemento de dimensionamento automático para WideControl (formato)](./autosize-element-for-widecontrol-format.md)

[Elemento de ColumnNumber para WideControl (formato)](./columnnumber-element-for-widecontrol-format.md)

[Elemento de exibição (formato)](./view-element-format.md)

[Elemento de WideEntries (formato)](./wideentries-element-for-widecontrol-format.md)

[Vista alargada (básico)](./wide-view-basic.md)

[Criar uma vista alargada](./creating-a-wide-view.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
