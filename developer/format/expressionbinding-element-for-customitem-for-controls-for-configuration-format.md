---
title: Elemento de ExpressionBinding para CustomItem para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846208"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>ExpressionBinding Element for CustomItem for Controls for Configuration (Format) (Elemento ExpressionBinding para CustomItem para Controls para Configuration [Formatação])

Define os dados que são apresentados pelo controle. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de CustomItem de configuração (formato) para CustomEntry para controles para o elemento de configuração ExpressionBinding para CustomItem para controles de configuração (formato)

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
|[Elemento de CustomControlName para ExpressionBinding para controles de configuração (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica o nome de um controle comum ou um controle de exibição.|
|[Elemento de EnumerateCollection para ExpressionBinding para controles de configuração (formato)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especificar que os elementos de coleções são apresentados pelo controle.|
|[Elemento de ItemSelectionCondition para ExpressionBinding para controles de configuração (formato)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Define a condição de que tem de existir para este controlo comum a ser utilizado.|
|[Elemento de PropertyName para ExpressionBinding para controles de configuração (formato)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade de .NET cujo valor é apresentado pelo controle comum.|
|[Elemento de ScriptBlock para ExpressionBinding para controles de configuração (formato)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica o script cujo valor é apresentado pelo controle comum.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomItem para CustomEntry para controles de configuração](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Define os dados que são apresentados pela vista do controle personalizado e como ele é exibido.|

## <a name="remarks"></a>Observações

## <a name="see-also"></a>Veja Também

[Elemento de CustomItem para CustomEntry para controles de configuração](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
