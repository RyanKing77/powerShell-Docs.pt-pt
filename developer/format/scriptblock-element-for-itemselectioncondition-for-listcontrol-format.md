---
title: Elemento de ScriptBlock para ItemSelectionCondition para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064412"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>ScriptBlock Element for ItemSelectionCondition for ListControl (Format) (Elemento ScriptBlock para ItemSelectionCondition para ListControl [Formatação])

Especifica o script que aciona a condição. Quando esse script é avaliado para `true`, a condição é cumprida e é utilizado o item da lista. Este elemento é utilizado ao definir uma vista de lista.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry ListControl (formato) para ListEntries para o elemento de ListItems ListControl (formato) para ListEntry para o elemento de ListItem ListControl (formato) para ListItems para o elemento de ItemSelectionCondition de controle (formato) de lista para ListItem para o elemento de ScriptBlock ListControl (formato) para ItemSelectionCondition para ListControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e os elementos pai do `ScriptBlock` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ItemSelectionCondition para ListItem para ListControl (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Define a condição de que tem de existir para este item de lista a ser utilizado.|

## <a name="text-value"></a>Valor de texto

Especifique o script que é avaliado.

## <a name="remarks"></a>Observações

Se este elemento é utilizado, não é possível especificar o `PropertyName` elemento ao definir a condição de seleção.

## <a name="see-also"></a>Veja Também

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
