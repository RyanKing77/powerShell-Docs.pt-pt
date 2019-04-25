---
title: Elemento de largura para TableColumnHeader para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083625"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>Width Element for TableColumnHeader for TableControl (Format) (Elemento Width para TableColumnHeader para TableControl [Formatação])

Define a largura (em carateres) de uma coluna.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableHeaders elemento de configuração para TableHeaders de elemento de TableColumnHeader TableControl (formato) para o elemento de largura de TableControl (formato) para TableColumnHeader para TableControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `Width` elemento usado ao definir cabeçalhos de coluna.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de TableColumnHeader para TableHeaders para TableControl (formato)](./tablecolumnheader-element-format.md)|Define uma etiqueta, largura e alinhamento de dados para uma coluna da tabela.|

## <a name="text-value"></a>Valor de texto

Quando em todos os possíveis, especifique uma largura (em carateres), que é superior ao comprimento dos valores de propriedade apresentado.

## <a name="remarks"></a>Observações

Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra um `TableColumnHeader` elemento cuja largura é de 16 carateres.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Veja Também

[Criar uma vista de tabela](./creating-a-table-view.md)

[Elemento de TableColumnHeader para TableHeader para TableControl (formato)](./tablecolumnheader-element-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
