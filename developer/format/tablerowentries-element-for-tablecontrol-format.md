---
title: Elemento de TableRowEntries para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: d93750f919c1075f173dc9ac70324cc003e36879
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851143"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>TableRowEntries Element for TableControl (Format) (Elemento TableRowEntries para TableControl [Formatação])

Define as linhas da tabela.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento de configuração para TableControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `TableRowEntries` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de TableRowEntry para TableRowEntries para TableControl (formato)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|Elemento necessário.<br /><br /> Define os dados que são apresentados numa linha da tabela.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de TableControl (formato)](./tablecontrol-element-format.md)|Define um formato de tabela para obter uma exibição.|

## <a name="remarks"></a>Observações

Tem de especificar um ou mais `TableRowEntry` elementos para a vista de tabela. Não existe nenhum limite máximo para o número de `TableRowEntry` elementos que podem ser adicionados nem é sua ordem significativo.

Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra um `TableRowEntries` elemento que define uma linha que apresenta os valores das duas propriedades do [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.

```xml
<TableRowEntries>
  <TableRowEntry>
    <EntrySelectedBy>
      <TypeName>System.Diagnostics.Process</TypeName>
    </EntrySelectedBy>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName> Property for first column</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName> Property for second column</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>

```

## <a name="see-also"></a>Consulte Também

[Criar uma vista de tabela](./creating-a-table-view.md)

[Elemento de TableControl (formato)](./tablecontrol-element-format.md)

[Elemento de TableRowEntry (formato)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
