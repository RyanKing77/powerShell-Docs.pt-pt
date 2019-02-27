---
title: Elemento de PropertyName para ItemSelectionCondition para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846488"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>PropertyName Element for ItemSelectionCondition for ListControl (Format) (Elemento PropertyName para ItemSelectionCondition para ListControl [Formatação])

Especifica a propriedade do .NET que aciona a condição. Quando esta propriedade está presente ou quando ela é avaliada como `true`, a condição é cumprida e o modo de exibição é utilizado. Este elemento é utilizado ao definir uma vista de lista.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento (formato) ListEntry elemento de configuração para o elemento de ListItems ListControl (formato) para ListEntry para ListItem ListControl (formato) Elemento para ListItems para o elemento de ItemSelectionCondition ListControl (formato) para ListItem ListControls PropertyName elemento para ItemSelectionCondition para ListControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e os elementos pai do `PropertyName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ItemSelectionCondition para ListItem para ListControl (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a>Valor do Texto

Especifique o nome da propriedade cujo valor é apresentado.

## <a name="remarks"></a>Observações

Se este elemento é utilizado, não é possível especificar a [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) elemento ao definir a condição de seleção.

## <a name="see-also"></a>Consulte Também

[Elemento de ScriptBlock para ItemSelectionCondition para ListIControl (formato)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Elemento de ItemSelectionCondition para ListItem para ListControl (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
