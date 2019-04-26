---
title: Elemento de PropertyName para ItemSelectionCondition para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064871"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>PropertyName Element for ItemSelectionCondition for CustomControl for View (Format) (Elemento PropertyName para ItemSelectionCondition para CustomControl para View [Formatação])

Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e o controle é usado. Este elemento é utilizado ao definir uma vista de controle personalizado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para exibição (formato) CustomItem elemento para CustomEntry para exibição (formato) ExpressionBinding elemento para CustomItem para CustomControl para exibição (formato) ItemSelectionCondition elemento para a ligação de expressão para CustomControl para exibição (formato) PropertyName elemento para ItemSelectionCondition para CustomControl para exibição (formato

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
|[Elemento de ItemSelectionCondition para enlace de expressão para CustomControl para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Define a condição de que tem de existir para este controlo a ser utilizado.|

## <a name="text-value"></a>Valor de texto

Especifique o nome da propriedade .NET que aciona a condição.

## <a name="remarks"></a>Observações

Se este elemento é utilizado, não é possível especificar a [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) elemento ao definir a condição de seleção.

## <a name="see-also"></a>Veja Também

[Elemento de ScriptBlock para ItemSelectionCondition para CustomControl para exibição (formato)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[Elemento de ItemSelectionCondition para enlace de expressão para CustomControl para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
