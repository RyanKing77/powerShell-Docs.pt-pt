---
title: Elemento de PropertyName para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851899"
---
# <a name="propertyname-element-for-groupby-format"></a>PropertyName Element for GroupBy (Format) (Elemento PropertyName para GroupBy [Formatação])

Especifica a propriedade do .NET que inicia um novo grupo sempre que seu valor é alterado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o modo de exibição (formato) PropertyName elemento para GroupBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[GroupBy elemento para a exibição (formato)](./groupby-element-for-view-format.md)|Define como um grupo de objetos do .NET é exibido.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome de propriedade do .NET.

## <a name="remarks"></a>Observações

É iniciado um novo grupo do Windows PowerShell sempre que o valor desta propriedade é alterado.

Quando este elemento é especificado, não é possível especificar a [ScriptBlock](./scriptblock-element-for-groupby-format.md) elemento para iniciar um novo grupo.

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como iniciar um novo grupo, quando o valor de uma propriedade é alterado.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Para obter um exemplo de um ficheiro de formatação completado que inclui esse elemento, consulte [vista alargada (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Veja Também

[GroupBy elemento para a exibição (formato)](./groupby-element-for-view-format.md)

[Elemento de ScriptBlock para GroupBy (formato)](./scriptblock-element-for-groupby-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
