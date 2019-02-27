---
title: Elemento de SelectionSetName para EntrySelectedBy para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850247"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a>SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format) (Elemento SelectionSetName para EntrySelectedBy para Controls para Configuration [Formatação])

Especifica um conjunto de tipos do .NET que utilizam esta definição do controle. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de EntrySelectedBy de configuração (formato) para CustomEntry para controles para o elemento de SelectionSetName de configuração (formato) para EntrySelectedBy para controles de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionSetName` elemento.

### <a name="attributes"></a>Atributos

Nenhum

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de EntrySelectedBy para CustomEntry para controles de configuração (formato)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Define os tipos do .NET que utilizam esta definição de controlo ou a condição que tem de existir para esta definição a utilizar.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome do conjunto de seleção.

## <a name="remarks"></a>Observações

Cada definição de controlo tem de ter, pelo menos, um nome de tipo, conjunto de seleção ou condição de seleção definido.

Conjuntos de seleção são normalmente utilizados quando quiser definir um grupo de objetos que são utilizados em vários modos de exibição. Para obter mais informações sobre como definir conjuntos de seleção, consulte [definindo seleção define](./defining-selection-sets.md).

## <a name="see-also"></a>Veja Também

[Elemento de EntrySelectedBy para CustomEntry para controles de configuração (formato)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
