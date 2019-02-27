---
title: Elemento da etiqueta para TableColumnHeader para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 59dfd40b95d5088a711eb89cf101eb31a4b159f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846873"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Label Element for TableColumnHeader for TableControl (Format) (Elemento Label para TableColumnHeader para TableControl [Formatação])

Define a etiqueta que é apresentada na parte superior de uma coluna. Este elemento é utilizado ao definir uma vista de tabela.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableHeaders elemento de configuração para o elemento de TableColumnHeader TableControl (formato) para TableHeaders para o elemento de etiqueta TableControl (formato) para TableColumnHeader para TablControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Label` elemento. Apenas uma etiqueta é permitida para cada coluna.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de TableColumnHeader para TableHeaders para TableControl (formato)](./tablecolumnheader-element-format.md)|Define uma etiqueta, a largura e o alinhamento dos dados para uma coluna da tabela.|

## <a name="text-value"></a>Valor do Texto

Especifique o texto que é apresentado na parte superior da coluna da tabela. Não há nenhum caráter restrito para a etiqueta de coluna.

## <a name="remarks"></a>Observações

Se nenhuma etiqueta for especificada, é utilizado o nome da propriedade cujo valor é apresentado nas linhas.

Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra um `TableColumnHeader` elemento cuja etiqueta é "Coluna 1".

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Veja Também

[Criar uma vista de tabela](./creating-a-table-view.md)

[Elemento de TableColumnHeader (formato)](./tablecolumnheader-element-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)