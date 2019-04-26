---
title: Elemento de ItemSelectionCondition para ExpressionBinding para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065483"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a>ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format) (Elemento ItemSelectionCondition para ExpressionBinding para Controls para View [Formatação])

Define a condição de que tem de existir para este controlo a ser utilizado. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) CustomItem elemento para CustomEntry para controles para exibição (formato) ExpressionBinding elemento para CustomItem para controles para exibição (formato) Elemento de ItemSelectionCondition de ExpressionBinding para controles para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ItemSelectionCondition` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de PropertyName para ItemSelectionCondition para controles para exibição (formato)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade do .NET que aciona a condição.|
|[Elemento de ScriptBlock para ItemSelectionCondition para controles para exibição (formato)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o script que aciona a condição.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Define os dados que são apresentados pelo controle.|

## <a name="remarks"></a>Observações

Pode especificar um nome de propriedade ou um script para esta condição, mas não é possível especificar ambos.

## <a name="see-also"></a>Veja Também

[Elemento de PropertyName para ItemSelectionCondition para controles para exibição (formato)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Elemento de ScriptBlock para ItemSelectionCondition para controles para exibição (formato)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
