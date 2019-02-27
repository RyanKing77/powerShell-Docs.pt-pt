---
title: Elemento de FormatString para ListItem para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849848"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a>FormatString Element for ListItem for ListControl (Format) (Elemento FormatString para ListItem para ListControl [Formatação])

Especifica um padrão de formato que define como o valor de propriedade ou um script é apresentado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry ListControl (formato) para o elemento de ListItems ListControl (formato) para ListControl (formato) Elemento de ListItem para o elemento de FormatString ListControl (formato) para ListItem para ListControl (formato)

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
|[Elemento de ListItem (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Define a propriedade ou um script cujo valor é apresentado numa linha da exibição de lista.|

## <a name="text-value"></a>Valor do Texto

Especifique o padrão que é utilizado para formatar os dados. Por exemplo, pode utilizar este padrão para formatar o valor de qualquer propriedade que é do tipo [TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: dd} {0:HH}: {0:mm}.

## <a name="remarks"></a>Observações

Cadeias de caracteres de formato podem ser utilizadas ao criar exibições de tabela, vistas de lista, modos de exibição amplo ou vistas personalizadas. Para obter mais informações sobre a formatação de um valor apresentado numa vista, consulte [formatação de dados apresentada](./formatting-displayed-data.md).

Para obter mais informações sobre como utilizar cadeias de caracteres de formato nas vistas de lista, consulte [Criar vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como definir uma cadeia de caracteres de formatação para o valor do `StartTime` propriedade.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a>Veja Também

[Criar uma vista de lista](./creating-a-list-view.md)

[Elemento de ListItem (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Escrever do Windows PowerShell, formatação e os tipos de ficheiro](./writing-a-powershell-formatting-file.md)
