---
title: Elemento de PropertyName para ItemSeclectionCondition para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064910"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format) (Elemento PropertyName para ItemSelectionCondition para Controls para Configuration [Formatação])

Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e o controle é usado. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de CustomItem de configuração (formato) para CustomEntry para controles para o elemento de configuração ExpressionBinding para CustomItem para controles de configuração (formato) Elemento de ItemSelectionCondition para ExpressionBinding para controles para o elemento de PropertyName de configuração (formato) para ItemSeclectionCondition para controles de configuração (formato)

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
|[Elemento de ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Define a condição de que tem de existir para este controlo a ser utilizado.|

## <a name="text-value"></a>Valor de texto

Especifique o nome da propriedade .NET que aciona a condição.

## <a name="remarks"></a>Observações

Se este elemento é utilizado, não é possível especificar a [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) elemento ao definir a condição de seleção.

## <a name="see-also"></a>Veja Também

[Elemento de ScriptBlock para ItemSeclectionCondition para controles de configuração (formato)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Elemento de ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
