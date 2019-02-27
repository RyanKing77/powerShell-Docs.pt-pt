---
title: Expanda o elemento (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848616"
---
# <a name="expand-element-format"></a>Expand Element (Format) (Elemento Expand [Formatação])

Especifica a forma como o objeto de coleção é expandido para esta definição.

O elemento (formato) DefaultSettings elemento (formato) EnumerableExpansions elemento (formato) EnumerableExpansion o elemento de configuração (formato) expanda elemento (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Expand` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de EnumerableExpansion (formato)](./enumerableexpansion-element-format.md)|Define a coleção de .NET como específica objetos são expandidos quando são apresentados numa vista.|

## <a name="text-value"></a>Valor do Texto

Especifique um dos seguintes valores:

- EnumOnly: Mostra apenas as propriedades dos objetos na coleção.

- CoreOnly: Apresenta apenas as propriedades do objeto de coleção.

- Ambos: Apresenta as propriedades dos objetos da coleção e as propriedades do objeto de coleção.

## <a name="remarks"></a>Observações

Este elemento é usado para definir a forma como são apresentados os objetos da coleção e os objetos da coleção. Neste caso, um objeto de coleção refere-se a qualquer objeto que suporte o **System.Collections.ICollection** interface.

O comportamento padrão é apresentar apenas as propriedades dos objetos na coleção.

## <a name="see-also"></a>Consulte Também

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
