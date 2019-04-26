---
title: Elemento de ItemSelectionCondition para ListItem para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065449"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a>ItemSelectionCondition Element for ListItem for ListControl (Format) (Elemento ItemSelectionCondition para ListItem para ListControl [Formatação])

Define a condição de que tem de existir para este item de lista a ser utilizado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry ListControl (formato) para ListEntries para o elemento de ListItems ListControl (formato) para ListEntry para o elemento de ListItem ListControl (formato) para ListItems para o elemento de ItemSelectionCondition ListControl (formato) para ListItem para ListControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ItemSelectionCondition` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de PropertyName para ItemSelectionCondition para ListControl (formato)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade do .NET que aciona a condição.|
|[Elemento de ScriptBlock para ItemSelectionCondition para ListControl (formato)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica o script que aciona a condição.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ListItem para ListItems para ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Define a propriedade ou um script cujo valor é apresentado numa linha da exibição de lista.|

## <a name="remarks"></a>Observações

Pode especificar um nome de propriedade ou um script para esta condição, mas não é possível especificar ambos.

## <a name="see-also"></a>Veja Também

[Elemento de ListItem para ListItems para ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Elemento de PropertyName para ItemSelectionCondition para ListControl (formato)](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[Elemento de ScriptBlock para ItemSelectionCondition para ListControl (formato)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
