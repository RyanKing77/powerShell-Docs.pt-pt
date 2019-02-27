---
title: Elemento de CustomControlName para ExpressionBinding para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849918"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>CustomControlName Element for ExpressionBinding for CustomControl for View (Format) (Elemento CustomControlName para ExpressionBinding para CustomControl para View [Formatação])

Especifica o nome de um controle comum ou um controle de exibição. Este elemento é utilizado ao definir uma vista de controle personalizado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento de configuração para o modo de exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para CustomItem de exibição (formato) Elemento para CustomEntry para o elemento de ExpressionBinding de exibição (formato) para o elemento de CustomControlName CustomItem (formato) para a ligação de expressão para CustomItem (formato)

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
|[Elemento de ExpressionBinding para CustomItem (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Define os dados que são apresentados pelo controle.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome do controle.

## <a name="remarks"></a>Observações

Pode criar controles comuns que podem ser utilizados por todas as vistas de um ficheiro de formatação e pode criar controles de exibição que podem ser utilizados por uma vista específica. Os nomes desses controles são especificados pelos seguintes elementos.

- [Elemento de nome para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento de nome para o controle para controles para exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Consulte Também

[Elemento de nome para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento de nome para o controle para controles para exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)

[Elemento de ExpressionBinding para CustomItem (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
