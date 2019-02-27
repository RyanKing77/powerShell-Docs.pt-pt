---
title: Nome de elemento para controle para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851283"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>Name Element for Control for Controls for View (Format) (Elemento Name para Control para Controls para View [Formatação])

Especifica o nome do controle.

Elemento de configuração do modo de exibição elemento (formato) ViewDefinitions elemento (formato) (formato) controla o elemento de controle do elemento (formato) para controles em elemento de nome de exibição (formato) para o controlo para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Name` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de controle para controles para exibição (formato)](./control-element-for-controls-for-view-format.md)|Define um controle que pode ser utilizado pela exibição e o nome que é utilizado para referenciar o controle.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome que é utilizado para referenciar o controle.

## <a name="remarks"></a>Observações

O nome especificado aqui pode servir os seguintes elementos para fazer referência a esse controle.

- Ao criar uma tabela, a lista, o modo de exibição control ampla ou personalizadas, o controle pode ser especificado pelo elemento do seguinte: [GroupBy elemento para a exibição (formato)](./groupby-element-for-view-format.md)

- Quando criar outro controle que pode ser utilizado por uma vista, esse controle pode ser especificado pelo elemento do seguinte: [Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Consulte Também

[GroupBy elemento para a exibição (formato)](./groupby-element-for-view-format.md)

[Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Elemento de controle para controles para exibição (formato)](./control-element-for-controls-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
