---
title: Elemento de CustomControlName para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066550"
---
# <a name="customcontrolname-element-for-groupby-format"></a>CustomControlName Element for GroupBy (Format) (Elemento CustomControlName para GroupBy [Formatação])

Especifica o nome de um controle personalizado que é utilizado para apresentar o novo grupo. Este elemento é utilizado ao definir uma tabela, a lista, o modo de exibição control ampla ou personalizado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o modo de exibição (formato) CustomControlName elemento de GroupBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos, elementos filho e elementos pai do `CustomControlName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[GroupBy elemento para a exibição (formato)](./groupby-element-for-view-format.md)|Define como o Windows PowerShell apresenta um novo grupo de objetos.|

## <a name="text-value"></a>Valor de texto

Especifique o nome do controle personalizado que é utilizado para apresentar um novo grupo.

## <a name="remarks"></a>Observações

Pode criar controles comuns que podem ser utilizados por todas as vistas de um ficheiro de formatação, e pode criar controles de exibição que podem ser utilizados por uma vista específica. Os seguintes elementos especifique os nomes desses controles personalizados:

- [Elemento de nome para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Elemento de nome para o controle para controles para exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Veja Também

[GroupBy elemento para a exibição (formato)](./groupby-element-for-view-format.md)

[Elemento de nome para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[Elemento de nome para o controle para controles para exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
