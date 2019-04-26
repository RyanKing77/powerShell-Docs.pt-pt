---
title: Elemento de ExpressionBinding para CustomItem para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065956"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>ExpressionBinding Element for CustomItem for Controls for View (Format) (Elemento ExpressionBinding para CustomItem para Controls para View [Formatação])

Define os dados que são apresentados pelo controle. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) CustomItem elemento para CustomEntry para controles para exibição (formato) ExpressionBinding elemento para CustomItem para controles para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ExpressionBinding` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|`CustomControl Element`|Elemento opcional.<br /><br /> Define um controle que é utilizado por este controlo.|
|[Elemento de CustomControlName para ExpressionBinding para controles para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o nome de um controle comum ou um controle de exibição.|
|[Elemento de EnumerateCollection para ExpressionBinding para controles para exibição (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica que os elementos de coleções são apresentados.|
|[Elemento de ItemSelectionCondition de ExpressionBinding para controles para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Define a condição de que tem de existir para este controlo a ser utilizado.|
|[Elemento de PropertyName para ExpressionBinding para controles para exibição (formato)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade de .NET cujo valor é apresentado pelo controle.|
|[Elemento de ScriptBlock para ExpressionBinding para controles para exibição (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o script cujo valor é apresentado pelo controle.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomItem para CustomEntry para controles para exibição (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Define os dados que são apresentados pelo controle e como ele é exibido.|

## <a name="remarks"></a>Observações

## <a name="see-also"></a>Veja Também

[Elemento de CustomItem para CustomEntry para controles para exibição (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Elemento de CustomControlName para ExpressionBinding para controles para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento de EnumerateCollection para ExpressionBinding para controles para exibição (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento de ItemSelectionCondition de ExpressionBinding para controles para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento de PropertyName para ExpressionBinding para controles para exibição (formato)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento de ScriptBlock para ExpressionBinding para controles para exibição (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
