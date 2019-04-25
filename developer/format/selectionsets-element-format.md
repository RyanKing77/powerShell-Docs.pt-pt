---
title: O elemento de SelectionSets (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063782"
---
# <a name="selectionsets-element-format"></a>SelectionSets Element (Format) (Elemento SelectionSets [Formatação])

Define os conjuntos comuns de objetos .NET que podem ser utilizados por todas as vistas do ficheiro de formatação. As vistas e os controles do arquivo formatação podem referenciar o conjunto completo de objetos ao utilizar apenas o nome do conjunto de seleção.

Formato de SelectionSets elemento do elemento de configuração

## <a name="syntax"></a>Sintaxe

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `SelectionSets` elemento. Cada elemento subordinado define um conjunto de objetos que pode ser referenciado pelo nome do conjunto. A ordem dos elementos subordinados não é significativa.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de SelectionSet (formato)](./selectionset-element-format.md)|Elemento necessário.<br /><br /> Define um único conjunto de objetos do .NET que pode ser referenciado pelo nome do conjunto.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de configuração](./configuration-element-format.md)|Representa o elemento de nível superior de um ficheiro de formatação.|

## <a name="remarks"></a>Observações

É possível utilizar conjuntos de seleção quando tem um conjunto de objetos relacionados que deseja fazer referência ao utilizar um nome único, como um conjunto de objetos que estão relacionados por meio de herança. Ao definir suas Exibições, pode especificar o conjunto de objetos usando o nome da seleção, em vez de listagem de todos os objetos dentro de cada vista.

Conjuntos de seleção comuns são especificados pelo respetivo nome quando definir as exibições do arquivo formatação ou as definições das vistas. Nestes casos, o `SelectionSetName` elemento subordinado do `ViewSelectedBy` e `EntrySelectedBy` elementos Especifica o conjunto a ser utilizado. Para obter mais informações sobre os conjuntos de seleção, consulte [definir conjuntos de objetos](./defining-selection-sets.md).

## <a name="see-also"></a>Veja Também

[Elemento de configuração](./configuration-element-format.md)

[Definir conjuntos de seleção](./defining-selection-sets.md)

[Elemento de SelectionSet (formato)](./selectionset-element-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
