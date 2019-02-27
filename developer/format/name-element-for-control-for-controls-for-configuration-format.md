---
title: Nome de elemento para controle para controles para a configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849673"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Name Element for Control for Controls for Configuration (Format) (Elemento Name para Control para Controls para Configuration [Formatação])

Especifica o nome do controle. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de nome de configuração (formato) para o controle para controles de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Name>NameOfControl</Name>

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
|[Elemento de controle para controles de configuração (formato)](./control-element-for-controls-for-configuration-format.md)|Define um controle comum que pode ser utilizado por todas as vistas do ficheiro formatação e o nome que é utilizado para referenciar o controle.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome que é utilizado para referenciar esse controle.

## <a name="remarks"></a>Observações

O nome especificado aqui pode servir os seguintes elementos para fazer referência a esse controle.

- Ao criar uma tabela, a lista, o modo de exibição control ampla ou personalizadas, o controle pode ser especificado pelo elemento do seguinte: [GroupBy elemento para a exibição (formato)](./groupby-element-for-view-format.md)

- Ao criar outro controle comum, esse controle pode ser especificado pelo elemento do seguinte: [Elemento de ExpressionBinding para CustomItem para controles de configuração (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- Quando criar um controle que pode ser utilizado por uma vista, esse controle pode ser especificado pelo elemento do seguinte: [Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Consulte Também

[Elemento de controle para controles de configuração (formato)](./control-element-for-controls-for-configuration-format.md)

[Elemento de ExpressionBinding para CustomItem para controles de configuração (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[GroupBy elemento para a exibição (formato)](./groupby-element-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
