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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066622"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>CustomControlName Element for ExpressionBinding for CustomControl for View (Format) (Elemento CustomControlName para ExpressionBinding para CustomControl para View [Formatação])

Especifica o nome de um controle comum ou um controle de exibição. Este elemento é utilizado ao definir uma vista de controle personalizado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento de configuração para o modo de exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para CustomItem de exibição (formato) Elemento para CustomEntry para o elemento de ExpressionBinding de exibição (formato) para o elemento de CustomControlName CustomItem (formato) para a ligação de expressão para CustomItem (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomControlName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ExpressionBinding para CustomItem (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Define os dados que são apresentados pelo controle.|

## <a name="text-value"></a>Valor de texto

Especifique o nome do controle.

## <a name="remarks"></a>Observações

Pode criar controles comuns que podem ser utilizados por todas as vistas de um ficheiro de formatação e pode criar controles de exibição que podem ser utilizados por uma vista específica. Os nomes desses controles são especificados pelos seguintes elementos.

- [Elemento de nome para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento de nome para o controle para controles para exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Veja Também

[Elemento de nome para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento de nome para o controle para controles para exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)

[Elemento de ExpressionBinding para CustomItem (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
