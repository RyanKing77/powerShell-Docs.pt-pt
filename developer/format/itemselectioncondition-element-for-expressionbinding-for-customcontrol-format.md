---
title: Elemento de ItemSelectionCondition para ExpressionBinding para CustomControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848343"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format) (Elemento ItemSelectionCondition para ExpressionBinding para CustomControl [Formatação])

Define a condição de que tem de existir para este controlo a ser utilizado. Não existe nenhum limite para o número de condições de seleção que pode ser especificado para um item de controlo. Este elemento é utilizado ao definir uma vista de controle personalizado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para exibição (formato) CustomItem elemento para CustomEntry para exibição (formato) ExpressionBinding elemento para CustomItem para CustomControl para exibição (formato) ItemSelectionCondition elemento para a ligação de expressão para CustomControl para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ItemSelectionCondition` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de PropertyName para ItemSelectionCondition para CustomControl para exibição (formato](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade do .NET que aciona a condição.|
|[Elemento de ScriptBlock para ItemSelectionCondition para CustomControl para exibição (formato)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o script que aciona a condição.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ExpressionBinding para CustomItem para CustomControl para exibição (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Define os dados que são apresentados pelo controle.|

## <a name="remarks"></a>Observações

Pode especificar um nome de propriedade ou um script para esta condição, mas não é possível especificar ambos.

## <a name="see-also"></a>Veja Também

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)

[Elemento de ExpressionBinding para CustomItem para CustomControl para exibição (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
