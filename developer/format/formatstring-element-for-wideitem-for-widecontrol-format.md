---
title: Elemento de FormatString para WideItem para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850268"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>FormatString Element for WideItem for WideControl (Format) (Elemento FormatString para WideItem para WideControl [Formatação])

Especifica um padrão de formato que define como o valor de propriedade ou um script é apresentado na vista.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento de configuração para o elemento de WideItem WideControl (formato) para o elemento de FormatString WideControl (formato) para WideItem para WideControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `FormatString` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de WideItem para WideControl (formato)](./wideitem-element-for-widecontrol-format.md)|Define a propriedade ou um script cujo valor é apresentado numa linha da exibição de lista.|

## <a name="text-value"></a>Valor do Texto

Especifique o padrão que é utilizado para formatar os dados. Por exemplo, pode utilizar este padrão para formatar o valor de qualquer propriedade que é do tipo [TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: dd} {0:HH}: {0:mm}.

## <a name="remarks"></a>Observações

Cadeias de caracteres de formato podem ser utilizadas ao criar exibições de tabela, vistas de lista, modos de exibição amplo ou vistas personalizadas. Para obter mais informações sobre a formatação de um valor apresentado numa vista, consulte [formatação de dados apresentada](./formatting-displayed-data.md).

Para obter mais informações sobre como utilizar cadeias de caracteres de formato em modos de exibição amplo, consulte [criar uma vista alargada](./creating-a-wide-view.md).

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como definir uma cadeia de caracteres de formatação para o valor do `StartTime` propriedade.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>Veja Também

[Criar uma vista alargada](./creating-a-wide-view.md)

[Elemento de WideItem para WideControl (formato)](./wideitem-element-for-widecontrol-format.md)

[Escrever do Windows PowerShell, formatação e os tipos de ficheiro](./writing-a-powershell-formatting-file.md)
