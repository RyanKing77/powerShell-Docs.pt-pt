---
title: O elemento de TableHeaders (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847426"
---
# <a name="tableheaders-element-format"></a>TableHeaders Element (Format) (Elemento TableHeaders [Formatação])

Define os cabeçalhos das colunas de uma tabela.

O elemento de ViewDefinitions (formato) vista elemento (formato) TableControl elemento (formato) TableHeaders elemento para TableControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos, elementos filho e elementos pai do `TableHeaders` elemento. Tem de existir um elemento filho para cada propriedade do objeto que está a ser exibido. As informações de cabeçalho de coluna são apresentadas na ordem em que os elementos filho são especificados.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de TableColumnHeader (formato)](./tablecolumnheader-element-format.md)|Elemento opcional.<br /><br /> Define o alinhamento dos dados para uma coluna de uma vista de tabela, a largura e a etiqueta.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de TableControl (formato)](./tablecontrol-element-format.md)|Define um formato de tabela para obter uma exibição.|

## <a name="remarks"></a>Observações

Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra um `TableHeaders` elemento que define dois cabeçalhos de coluna.

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

## <a name="see-also"></a>Consulte Também

[Criar uma vista de tabela](./creating-a-table-view.md)

[Elemento de TableColumnHeader (formato)](./tablecolumnheader-element-format.md)

[Elemento de TableControl (formato)](./tablecontrol-element-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
