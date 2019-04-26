---
title: Elemento da etiqueta para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065415"
---
# <a name="label-element-for-groupby-format"></a>Label Element for GroupBy (Format) (Elemento Label para GroupBy [Formatação])

Especifica uma etiqueta que é apresentada quando for detetado um novo grupo.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de etiqueta de modo de exibição (formato) para GroupBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `Label` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[GroupBy elemento para a exibição (formato)](./groupby-element-for-view-format.md)|Define a forma como é apresentado um novo grupo de objetos.|

## <a name="text-value"></a>Valor de texto

Especifique o texto que é apresentado sempre que o Windows PowerShell encontra uma nova propriedade ou o valor de script.

## <a name="remarks"></a>Observações

Além do texto especificado por este elemento, o Windows PowerShell apresenta o novo valor que é iniciado o grupo e adiciona uma linha em branco antes e depois o grupo.

## <a name="example"></a>Exemplo

O exemplo seguinte mostra a etiqueta para um novo grupo. A etiqueta apresentada teria uma aparência semelhante a este: `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Para obter um exemplo de um ficheiro de formatação completado que inclui esse elemento, consulte [vista alargada (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Veja Também

[GroupBy elemento para a exibição (formato)](./groupby-element-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
