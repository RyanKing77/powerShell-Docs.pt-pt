---
title: Elemento de CustomControlName para ExpressionBinding para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846530"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a>CustomControlName Element for ExpressionBinding for Controls for View (Format) (Elemento CustomControlName para ExpressionBinding para Controls para View [Formatação])

Especifica o nome de um controle comum ou um controle de exibição. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) CustomItem elemento para CustomEntry para controles para exibição (formato) ExpressionBinding elemento para CustomItem para controles para exibição (formato) CustomControlName Elemento para ExpressionBindine para controles para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomControlName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Define os dados que são apresentados pelo controle.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome do controle.

## <a name="remarks"></a>Observações

Pode criar controles comuns que podem ser utilizados por todas as vistas de um ficheiro de formatação, e pode criar controles de exibição que podem ser utilizados por uma vista específica. Os seguintes elementos especifique os nomes desses controles:

- [Elemento de nome para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento de nome para o controle para controles para exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Veja Também

[Elemento de nome para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento de nome para o controle para controles para exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)

[Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
