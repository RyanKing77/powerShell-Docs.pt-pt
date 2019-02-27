---
title: Elemento de TableColumnItems para TableRowEntry para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: faa9ba78397e713400f6072df9915f20d966bb37
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849225"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>TableColumnItems Element for TableRowEntry for TableControl (Format) (Elemento TableColumnItems para TableRowEntry para TableControl [Formatação])

Define as propriedades ou scripts cujos valores são exibidos numa linha.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento de configuração para o elemento de TableRowEntry TableControl (formato) para TableRowEntries para TableControl (formato) Elemento de TableColumnItems para TableControlEntry para TableControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `TableColumnItems` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de TableColumnItem para TableColumnItems para TableControl (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Elemento necessário.<br /><br /> Define a propriedade ou um script cujo valor é apresentado numa coluna da linha.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de TableRowEntry para TableRowEntries para TableControl (formato)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|Define os dados que são apresentados numa linha da tabela.|

## <a name="remarks"></a>Observações

A `TableColumnItem` elemento é necessário para cada coluna da linha. A primeira entrada é apresentada na primeira coluna, a segunda entrada na segunda coluna e assim por diante.

Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra um `TableColumnItems` elemento que define três propriedades do [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a>Veja Também

[Criar uma vista de tabela](./creating-a-table-view.md)

[Elemento de TableColumnItem (formato)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Elemento de TableRowEntry (formato)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
