---
title: Elemento de CustomControlName para ExpressionBinding para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5242935-2782-4d23-84f5-2446b2b7ba83
caps.latest.revision: 8
ms.openlocfilehash: c9abd9f22907b87323c16d603a9f75bb3d375a03
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847034"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a>CustomControlName Element for ExpressionBinding for Controls for Configuration (Format) (Elemento CustomControlName para ExpressionBinding para Controls para Configuration [Formatação])

Especifica o nome de um controle comum. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de CustomItem de configuração (formato) para CustomEntry para controles para o elemento de configuração ExpressionBinding para CustomItem para controles para CustomControlName de configuração (formato) Elemento para ExpressionBinding para controles de configuração (formato)

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
|[Elemento de ExpressionBinding para CustomItem para controles de configuração (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Define os dados que são apresentados pelo controle.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome do controle.

## <a name="remarks"></a>Observações

Pode criar controles comuns que podem ser utilizados por todas as vistas de um ficheiro de formatação, e pode criar controles de exibição que podem ser utilizados por uma vista específica. Os seguintes elementos especifique os nomes desses controles:

- [Elemento de nome para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento de nome para o controle para controles para exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Veja Também

[Elemento de nome para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento de nome para o controle para controles para exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)

[Elemento de ExpressionBinding para CustomItem para controles de configuração (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
