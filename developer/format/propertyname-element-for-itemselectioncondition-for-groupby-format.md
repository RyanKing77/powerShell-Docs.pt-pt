---
title: Elemento de PropertyName para ItemSelectionCondition para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064769"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a>PropertyName Element for ItemSelectionCondition for GroupBy (Format) (Elemento PropertyName para ItemSelectionCondition para GroupBy [Formatação])

Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e o controle é usado. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de CustomItem GroupBy (formato) para CustomEntry para o elemento de ExpressionBinding GroupBy (formato) para CustomItem para o elemento de ItemSelectionCondition GroupBy (formato) para ExpressionBinding para o elemento de PropertyName GroupBy (formato) para ItemSelectionCondition para GroupBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ItemSelectionCondition para ExpressionBinding para GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Define a condição de que tem de existir para este controlo a ser utilizado.|

## <a name="text-value"></a>Valor de texto

Especifique o nome da propriedade .NET que aciona a condição.

## <a name="remarks"></a>Observações

Se este elemento é utilizado, não é possível especificar a [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) elemento ao definir a condição de seleção.

## <a name="see-also"></a>Veja Também

[Elemento de ScriptBlock para ItemSelectionCondition para GroupBy (formato)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[Elemento de ItemSelectionCondition para ExpressionBinding para GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
