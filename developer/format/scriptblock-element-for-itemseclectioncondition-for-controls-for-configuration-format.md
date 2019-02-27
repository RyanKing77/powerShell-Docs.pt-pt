---
title: Elemento de ScriptBlock para ItemSeclectionCondition para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850912"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format) (Elemento ScriptBlock para ItemSelectionCondition para Controls para Configuration [Formatação])

Especifica o script que aciona a condição. Quando esse script é avaliado para `true`, a condição é cumprida e o controle é usado. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de CustomItem de configuração (formato) para CustomEntry para controles para o elemento de configuração ExpressionBinding para CustomItem para controles de configuração (formato) Elemento de ItemSelectionCondition para ExpressionBinding para controles para o elemento de ScriptBlock de configuração (formato) para ItemSelectionCondition para controles de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Define a condição de que tem de existir para este controlo a ser utilizado.|

## <a name="text-value"></a>Valor do Texto

Especifique o script que é avaliado.

## <a name="remarks"></a>Observações

Se este elemento é utilizado, não é possível especificar a [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) elemento ao definir a condição de seleção.

## <a name="see-also"></a>Veja Também

[Elemento de PropertyName para ItemSeclectionCondition para controles de configuração (formato)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Elemento de ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
