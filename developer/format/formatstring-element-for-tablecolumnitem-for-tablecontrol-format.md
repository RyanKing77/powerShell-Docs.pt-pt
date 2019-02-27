---
title: Elemento de FormatString para TableColumnItem para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845641"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>FormatString Element for TableColumnItem for TableControl (Format) (Elemento FormatString para TableColumnItem para TableControl [Formatação])

Especifica um padrão de formato que define como o valor de propriedade ou do script da tabela é exibido.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento (formato) TableRowEntry elemento (formato) TableColumnItems elemento (formato) TableColumnItem elemento de configuração (formato) Elemento de FormatString para TableColumnItem (formato)

## <a name="syntax"></a>Sintaxe

```xml
<FormatString>FormatPattern</FormatString>
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
|[Elemento de TableColumnItem (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Define a propriedade ou um script cujo valor é apresentado na coluna da linha.|

## <a name="text-value"></a>Valor do Texto

Especifique o padrão que é utilizado para formatar os dados. Por exemplo, este padrão pode ser utilizado para formatar o valor de qualquer propriedade que é do tipo [TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: dd} {0:HH}: {0:mm}.

## <a name="remarks"></a>Observações

Cadeias de caracteres de formato podem ser utilizadas ao criar exibições de tabela, vistas de lista, modos de exibição amplo ou vistas personalizadas. Para obter mais informações sobre a formatação de um valor apresentado numa vista, consulte [formatação de dados apresentada](./formatting-displayed-data.md).

Para obter mais informações sobre os componentes de uma vista de tabela, consulte [vista de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como definir uma cadeia de caracteres de formatação para o valor do `StartTime` propriedade.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a>Veja Também

[Criar uma vista de tabela](./creating-a-table-view.md)

[Formatação apresentados dados](./formatting-displayed-data.md)

[Elemento de TableColumnItem (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
