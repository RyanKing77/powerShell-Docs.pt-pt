---
title: Elemento de TypeName para EntrySelectedBy para CustomEntry para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848798"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>TypeName Element for EntrySelectedBy for CustomEntry for View (Format) (Elemento TypeName para EntrySelectedBy para CustomEntry para View [Formatação])

Especifica um tipo .NET que utiliza esta definição de vista do controle personalizado. Não existe nenhum limite para o número de tipos que podem ser especificados para uma definição.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para EntrySelectedBy de exibição (formato) Elemento para CustomEntry para exibição (formato) TypeName elemento para EntrySelectedBy para CustomEntry para exibição (formato)

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
|[Elemento de EntrySelectedBy para CustomEntry para exibição (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Define os tipos do .NET que utilizam esta definição de vista do controle personalizado ou a condição que tem de existir para esta definição a utilizar.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome completamente qualificado do tipo .NET, tal como `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Observações

Cada definição de vista do controle personalizado tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.

Para obter mais informações sobre os componentes de uma vista de controle personalizado, consulte [criar controles personalizados](./creating-custom-controls.md).

## <a name="see-also"></a>Veja Também

[Criação de controles personalizados](./creating-custom-controls.md)

[Elemento de EntrySelectedBy para CustomEntry para exibição (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
