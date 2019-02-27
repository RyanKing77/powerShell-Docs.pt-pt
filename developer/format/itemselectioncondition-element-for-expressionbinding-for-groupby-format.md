---
title: Elemento de ItemSelectionCondition para ExpressionBinding para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844808"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a>ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) (Elemento ItemSelectionCondition para ExpressionBinding para GroupBy [Formatação])

Define a condição de que tem de existir para este controlo a ser utilizado. Não existe nenhum limite para o número de condições de seleção que pode ser especificado para um item de controlo. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de CustomItem GroupBy (formato) para CustomEntry para o elemento de ExpressionBinding GroupBy (formato) para CustomItem para o elemento de ItemSelectionCondition GroupBy (formato) para ExpressionBinding para GroupBy (formato)

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
|[Elemento de PropertyName para ItemSelectionCondition para GroupBy (formato)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade do .NET que aciona a condição.|
|[Elemento de ScriptBlock para ItemSelectionCondition para GroupBy (formato)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica o script que aciona a condição.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ExpressionBinding para CustomItem para GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Define os dados que são apresentados pelo controle.|

## <a name="remarks"></a>Observações

Pode especificar um nome de propriedade ou um script para esta condição, mas não é possível especificar ambos.

## <a name="see-also"></a>Veja Também

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)

[Elemento de ExpressionBinding para CustomItem para GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md)
