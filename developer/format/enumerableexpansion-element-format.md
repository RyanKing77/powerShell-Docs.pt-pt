---
title: O elemento de EnumerableExpansion (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847398"
---
# <a name="enumerableexpansion-element-format"></a>EnumerableExpansion Element (Format) (Elemento EnumerableExpansion [Formatação])

Define a coleção de .NET como específica objetos são expandidos quando são apresentados numa vista.

O elemento (formato) DefaultSettings elemento (formato) EnumerableExpansions elemento (formato) EnumerableExpansion o elemento de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `EnumerableExpansion` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de EntrySelectedBy para EnumerableExpansion (formato)](./entryselectedby-element-for-enumerableexpansion-format.md)|Elemento opcional.<br /><br /> Define os objetos da coleção de .NET são expandidos por esta definição.|
|[Expanda o elemento (formato)](./expand-element-format.md)|Especifica a forma como o objeto de coleção é expandido para esta definição.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de EnumerableExpansions (formato)](./enumerableexpansions-element-format.md)|Define as diferentes formas essa coleção de .NET objetos são expandidos quando são apresentados numa vista.|

## <a name="remarks"></a>Observações

Este elemento é usado para definir a forma como são apresentados os objetos da coleção e os objetos da coleção. Neste caso, um objeto de coleção refere-se a qualquer objeto que suporte o **System.Collections.ICollection** interface.

O comportamento padrão é apresentar apenas as propriedades dos objetos na coleção.

## <a name="see-also"></a>Veja Também

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
