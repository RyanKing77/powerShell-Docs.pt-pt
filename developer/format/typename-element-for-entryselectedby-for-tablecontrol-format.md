---
title: Elemento de TypeName para EntrySelectedBy para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846621"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a>TypeName Element for EntrySelectedBy for TableControl (Format) (Elemento TypeName para EntrySelectedBy para TableControl [Formatação])

Especifica um tipo .NET que utiliza esta entrada da vista de tabela. Não existe nenhum limite para o número de tipos que podem ser especificados para uma entrada de tabela.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento (formato) TableRowEntry elemento (formato) EntrySelectedBy elemento (formato) TypeName elemento de configuração para EntrySelectedBy para TableRowEntry (formato)

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
|[Elemento de EntrySelectedBy (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Define os tipos do .NET que utilizam esta entrada ou a condição que tem de existir para esta entrada a ser utilizado.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome do tipo .NET.

## <a name="remarks"></a>Observações

Cada entrada da lista tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.

Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).

## <a name="see-also"></a>Consulte Também

[Criar uma vista de tabela](./creating-a-table-view.md)

[Elemento de EntrySelectedBy (formato)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
