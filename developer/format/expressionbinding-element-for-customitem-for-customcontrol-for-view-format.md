---
title: Elemento de ExpressionBinding para CustomItem para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065925"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>ExpressionBinding Element for CustomItem for CustomControl for View (Format) (Elemento ExpressionBinding para CustomItem para CustomControl para View [Formatação])

Define os dados que são apresentados pelo controle. Este elemento é utilizado ao definir uma vista de controle personalizado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento de configuração para o modo de exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para CustomControl para exibição ( Elemento de CustomItem de formato) para CustomEntry para CustomControl para exibição (formato) ExpressionBinding elemento para CustomItem para CustomControl para exibição (formato)

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
|[Elemento de CustomControlName para ExpressionBinding para CustomControl para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o nome de um controle comum ou um controle de exibição.|
|[Elemento de EnumerateCollection para ExpressionBinding para CustomControl para exibição (formato)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especificar que os elementos de coleções são apresentados.|
|[Elemento de ItemSelectionCondition para ExpressionBinding para CustomControl para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Elemento opcional.<br /><br /> Define a condição de que tem de existir para este controlo a ser utilizado.|
|[Elemento de PropertyName para ExpressionBinding para CustomControl para exibição (formato)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade de .NET cujo valor é apresentado pelo controle.|
|[Elemento de ScriptBlock para ExpressionBinding para CustomCustomControl para exibição (formato)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o script cujo valor é apresentado pelo controle.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomItem para CustomEntry para CustomControl para exibição (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Define os dados que são apresentados pela vista do controle personalizado e como ele é exibido.|

## <a name="remarks"></a>Observações

## <a name="see-also"></a>Veja Também

[Elemento de CustomControlName para ExpressionBinding para CustomControl para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento de EnumerateCollection para ExpressionBinding para CustomControl para exibição (formato)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento de ItemSelectionCondition para ExpressionBinding para CustomControl para exibição (formato)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Elemento de PropertyName para ExpressionBinding para CustomControl para exibição (formato)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento de ScriptBlock para ExpressionBinding para CustomControl para exibição (formato)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento de CustomItem para CustomEntry para CustomControl para exibição (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
