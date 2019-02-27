---
title: Elemento de SelectionCondition para EntrySelectedBy para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845515"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) (Elemento SelectionCondition para EntrySelectedBy para Controls para Configuration [Formatação])

Define uma condição que tem de existir uma definição de controle comum a ser utilizado. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para controles para Elemento de CustomEntry de configuração (formato) para CustomControl para controles para o elemento de EntrySelectedBy de configuração (formato) para CustomEntry para controles para o elemento de SelectionCondition de configuração (formato) para EntrySelectedBy para CustomEntry para Configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `SelectionCondition` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de PropertyName para SelectionCondition para controles de configuração (formato)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica uma propriedade de .NET que aciona a condição.|
|[Elemento de ScriptBlock para SelectionCondition para controles de configuração (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica o script que aciona a condição.|
|[Elemento de SelectionSetName para SelectionCondition para controles de configuração (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica o conjunto de tipos do .NET que aciona a condição.|
|[Elemento de TypeName para SelectionCondition para controles de configuração (formato)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica um tipo .NET que aciona a condição.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de EntrySelectedBy para CustomEntry para controles de configuração (formato)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Define os tipos do .NET que utilizam esta entrada da definição de controlo comuns.|

## <a name="remarks"></a>Observações

Devem ser seguidas as seguintes diretrizes ao definir uma condição de seleção:

- A condição de seleção tem de especificar um nome de uma propriedade, pelo menos, ou um bloco de script, mas não é possível especificar ambos.

- A condição de seleção, pode especificar qualquer número de tipos do .NET ou seleção define, mas não é possível especificar ambos.

Para obter mais informações sobre como as condições de seleção podem ser utilizadas, consulte [definir condições para quando os dados são apresentados](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Veja Também

[Elemento de PropertyName para SelectionCondition para controles de configuração (formato)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento de ScriptBlock para SelectionCondition para controles de configuração (formato)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento de SelectionSetName para SelectionCondition para controles de configuração (formato)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento de TypeName para SelectionCondition para controles de configuração (formato)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Elemento de EntrySelectedBy para CustomEntry para controles de configuração (formato)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Escrever do Windows PowerShell, formatação e os tipos de ficheiro](./writing-a-powershell-formatting-file.md)
