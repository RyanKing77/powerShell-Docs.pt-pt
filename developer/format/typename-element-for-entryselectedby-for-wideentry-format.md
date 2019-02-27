---
title: Elemento de TypeName para EntrySelectedBy para WideEntry (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851465"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>TypeName Element for EntrySelectedBy for WideEntry (Format) (Elemento TypeName para EntrySelectedBy para WideEntry [Formatação])

Especifica um tipo de .NET para a definição. A definição é utilizada sempre que este objeto é apresentado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) EntrySelectedBy elemento de configuração para o elemento de TypeName WideEntry (formato) para WideEntry ( Formato)

## <a name="syntax"></a>Sintaxe

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `TypeName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de EntrySelectedBy para WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)|Define os tipos do .NET que utilizam esta entrada ampla ou a condição que tem de existir para esta entrada a ser utilizado.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observações

Cada entrada ampla tem de especificar um ou mais tipos de .NET, um conjunto de seleção ou a condição de seleção que tem de existir durante a definição a utilizar.

Para obter mais informações sobre os outros componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).

## <a name="see-also"></a>Veja Também

[Criar uma vista alargada](./creating-a-wide-view.md)

[Elemento de EntrySelectedBy para WideEntry (formato)](./entryselectedby-element-for-wideentry-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
