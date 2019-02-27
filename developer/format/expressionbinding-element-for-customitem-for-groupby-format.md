---
title: Elemento de ExpressionBinding para CustomItem para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846061"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>ExpressionBinding Element for CustomItem for GroupBy (Format) (Elemento ExpressionBinding para CustomItem para GroupBy [Formatação])

Define os dados que são apresentados pelo controle. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de CustomItem GroupBy (formato) para CustomEntry para o elemento de ExpressionBinding GroupBy (formato) para CustomItem para GroupBy (formato)

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

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ExpressionBinding` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|`CustomControl Element`|Elemento opcional.<br /><br /> Define um controle que é utilizado por este controlo.|
|[Elemento de CustomControlName para ExpressionBinding para GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica o nome de um controle comum ou um controle de exibição.|
|[Elemento de EnumerateCollection para ExpressionBinding para GroupBy (formato)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection elemento para ExpressionBinding para GroupBy (formato)|Elemento opcional.<br /><br /> Especificar que os elementos de coleções são apresentados.|
|[Elemento de ItemSelectionCondition para ExpressionBinding para GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Elemento opcional.<br /><br /> Define a condição de que tem de existir para este controlo a ser utilizado.|
|[Elemento de PropertyName para ExpressionBinding para GroupBy (formato)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade de .NET cujo valor é apresentado pelo controle.|
|[Elemento de ScriptBlock para ExpressionBinding para GroupBy (formato)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica o script cujo valor é apresentado pelo controle.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomItem para CustomEntry para GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)|Define os dados que são apresentados pela vista do controle personalizado e como ele é exibido.|

## <a name="see-also"></a>Veja Também

[Elemento de CustomControlName para ExpressionBinding para GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Elemento de EnumerateCollection para ExpressionBinding para GroupBy (formato)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[Elemento de ItemSelectionCondition para ExpressionBinding para GroupBy (formato)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Elemento de PropertyName para ExpressionBinding para GroupBy (formato)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[Elemento de ScriptBlock para ExpressionBinding para GroupBy (formato)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[Elemento de CustomItem para CustomEntry para GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
