---
title: O elemento de EnumerableExpansions (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066095"
---
# <a name="enumerableexpansions-element-format"></a>EnumerableExpansions Element (Format) (Elemento EnumerableExpansions [Formatação])

Define como os objetos da coleção de .NET são expandidos quando são apresentados numa vista.

Elemento de configuração do EnumerableExpansions elemento (formato) DefaultSettings elemento (formato) (formato)

## <a name="syntax"></a>Sintaxe

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `EnumerableExpansions` elemento. Não existe nenhum limite para o número de elementos filho que pode utilizar.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de EnumerableExpansion (formato)](./enumerableexpansion-element-format.md)|Elemento opcional.<br /><br /> Define os objetos de coleção específicos do .NET que são expandidos quando são apresentados numa vista.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de DefaultSettings (formato)](./defaultsettings-element-format.md)|Define configurações comuns que se aplicam a todas as vistas do ficheiro de formatação.|

## <a name="remarks"></a>Observações

Este elemento é usado para definir a forma como são apresentados os objetos da coleção e os objetos da coleção. Neste caso, um objeto de coleção refere-se a qualquer objeto que suporte o **System.Collections.ICollection** interface.

## <a name="see-also"></a>Veja Também

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
