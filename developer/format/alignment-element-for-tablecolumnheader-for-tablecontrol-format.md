---
title: Elemento de alinhamento para TableColumnHeader para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845242"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>Alignment Element for TableColumnHeader for TableControl (Format) (Elemento Alignment para TableColumnHeader para TableControl [Formatação])

Define a forma como os dados num cabeçalho de coluna são apresentados.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableHeaders elemento (formato) TableColumnHeader elemento (formato) alinhamento elemento de configuração para TableColumnHeader (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `Alignment` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de TableColumnHeader (formato)](./tablecolumnheader-element-format.md)|Define uma etiqueta, a largura e o alinhamento dos dados para uma coluna da tabela.|

## <a name="text-value"></a>Valor do Texto

Especifique um dos seguintes valores. Estes valores não diferenciam maiúsculas de minúsculas.

Esta esquerda alinha os dados apresentados na coluna à esquerda é a predefinição se este elemento não for especificado.

Alinha o direito dos dados apresentados na coluna à direita.

Centros de centro de dados na coluna.

## <a name="remarks"></a>Observações

Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra um `TableColumnHeader` cujos dados são alinhados à esquerda do elemento.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Consulte Também

[Criar uma vista de tabela](./creating-a-table-view.md)

[Elemento de TableColumnHeader (formato)](./tablecolumnheader-element-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
