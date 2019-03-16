---
title: O elemento de TableColumnHeader (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057880"
---
# <a name="tablecolumnheader-element-format"></a>TableColumnHeader Element (Format) (Elemento TableColumnHeader [Formatação])

Define a etiqueta, a largura da coluna e o alinhamento da etiqueta para uma coluna da tabela.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableHeaders elemento de configuração para o elemento de TableColumnHeader TableControl (formato) para TableHeaders para TableControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TableColumnHeader` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento da etiqueta para TableColumnHeader para TableControl (formato)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Define a etiqueta que é apresentada na parte superior da coluna. Se nenhuma etiqueta for especificada, é utilizado o nome da propriedade cujo valor é apresentado nas linhas.|
|[Elemento de largura para TableColumnHeader para TableControl (formato)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento necessário.<br /><br /> Especifica a largura (em carateres) da coluna.|
|[Elemento de alinhamento para TableColumnHeader para TableControl (formato)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica como a etiqueta da coluna é exibida. Se não for especificado nenhum alinhamento, a etiqueta é alinhada à esquerda.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de TableHeaders (formato)](./tableheaders-element-format.md)|Define as colunas de uma vista de tabela.|

## <a name="remarks"></a>Observações

Especifique um cabeçalho de cada coluna da tabela. As colunas são apresentadas na ordem em que o `TableColumnHeader` elementos são definidos.

Uma tabela tem de ter o mesmo número de `TableColumnHeader` elementos como `TableRowEntry` elementos. No cabeçalho da coluna define como o texto na parte superior da tabela é exibido. As entradas de linha definem que dados são apresentados nas linhas da tabela.

Para obter mais informações sobre os componentes de uma vista de tabela, consulte [vista de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

O exemplo seguinte mostra dois `TableColumnHeader` elementos. O primeiro elemento define uma coluna cuja etiqueta é "Coluna 1", tem uma largura de 16 carateres e cuja etiqueta está alinhada à esquerda. O segundo elemento define uma coluna cuja etiqueta é "Coluna 2", tem uma largura de 10 caracteres, e cuja etiqueta centra-se na coluna.

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
    <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a>Veja Também

[Elemento de alinhamento para TableColumnHeader para TableControl (formato)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Criar uma vista de tabela](./creating-a-table-view.md)

[Elemento da etiqueta para TableColumnHeader para TableControl (formato)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Elemento de TableHeaders para TableControl (formato)](./tableheaders-element-format.md)

[Largura para TableColumnHeader TableControl elemento (formato)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
