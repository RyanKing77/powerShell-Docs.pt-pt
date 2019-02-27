---
title: Elemento de EntrySelectedBy para CustomEntry para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: e930e4422afd203feda6a389655ff8a355e3bec0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848679"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) (Elemento EntrySelectedBy para CustomEntry para Controls para Configuration [Formatação])

Define os tipos do .NET que utilizam a definição de controle comum ou a condição que tem de existir para este controlo a ser utilizado. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de EntrySelectedBy de configuração (formato) para CustomEntry para controles de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `EntrySelectedBy` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de SelectionCondition para EntrySelectedBy para controles de configuração (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Define a condição de que tem de existir durante a definição de controle comum a ser utilizado.|
|[Elemento de SelectionSetName para EntrySelectedBy para controles de configuração (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica um conjunto de tipos do .NET que utilizam esta definição do controle comum.|
|[Elemento de TypeName para EntrySelectedBy para controles de configuração (formato)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que utiliza esta definição do controle comum.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomEntry para CustomControl para controles de configuração (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Fornece uma definição do controle comum.|

## <a name="remarks"></a>Observações

No mínimo, cada definição tem de ter pelo menos um .NET tipo, o conjunto de seleção ou condição de seleção especificada. Não existe nenhum limite máximo para o número de tipos, conjuntos de seleção ou condições de seleção que pode ser especificado.

## <a name="see-also"></a>Consulte Também

[Elemento de SelectionCondition para EntrySelectedBy para controles de configuração (formato)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Elemento de SelectionSetName para EntrySelectedBy para controles de configuração (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento de CustomEntry para CustomControl para controles de configuração (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Elemento de TypeName para EntrySelectdBy para controles de configuração (formato)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
