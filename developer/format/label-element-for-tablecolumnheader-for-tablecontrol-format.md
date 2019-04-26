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
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065755"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Label Element for TableColumnHeader for TableControl (Format) (Elemento Label para TableColumnHeader para TableControl [Formatação])

Define a etiqueta que é apresentada na parte superior de uma coluna. Este elemento é utilizado ao definir uma vista de tabela.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableHeaders elemento de configuração para o elemento de TableColumnHeader TableControl (formato) para TableHeaders para o elemento de etiqueta TableControl (formato) para TableColumnHeader para TableControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Label` elemento. Apenas uma etiqueta é permitida para cada coluna.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de TableColumnHeader para TableHeaders para TableControl (formato)](./tablecolumnheader-element-format.md)|Define uma etiqueta, a largura e o alinhamento dos dados para uma coluna da tabela.|

## <a name="text-value"></a>Valor de texto

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
