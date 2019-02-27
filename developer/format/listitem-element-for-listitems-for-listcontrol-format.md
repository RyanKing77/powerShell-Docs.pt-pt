---
title: Elemento de ListItem para ListItems para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846222"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>ListItem Element for ListItems for ListControl (Format) (Elemento ListItem para ListItems para ListControl [Formatação])

Define a propriedade ou um script cujo valor é apresentado numa linha da exibição de lista.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry ListControl (formato) para o elemento de ListItems ListControl (formato) para ListControl (formato) ListItem ListControl elemento (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `ListItem` elemento. Pode ser especificado apenas uma propriedade ou script.

### <a name="attributes"></a>Atributos

Nenhum

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de FormatString para ListItem para ListControl (formato)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica uma cadeia de caracteres de formato que define como o valor de propriedade ou um script é apresentado.|
|[Elemento de ItemSelectionCondition para ListItem para ListControl (formato)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Define a condição de que tem de existir para este item de lista a ser utilizado.|
|[Elemento da etiqueta para ListItem para ListControl (formato)](./label-element-for-listitem-for-listcontrol-format.md)|Elemento opcional<br /><br /> Especifica a etiqueta que é apresentada à esquerda do valor de propriedade ou um script na linha.|
|[Elemento de PropertyName para ListItem para ListControl (formato)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica a propriedade de .NET cujo valor é apresentado na linha.|
|[Elemento de ScriptBlock para ListItem para ListControl (formato)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Elemento opcional.<br /><br /> Especifica o script cujo valor é apresentado na linha.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ListItems para controle de lista (formato)](./listitems-element-for-listentry-for-listcontrol-format.md)|Define as propriedades e os scripts cujos valores são apresentados na vista de lista.|

## <a name="remarks"></a>Observações

Para obter mais informações sobre os componentes de uma vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra os elementos XML que definem três linhas da exibição de lista. As primeiras duas linhas apresentam o valor de uma propriedade de .NET e a última linha apresenta um valor gerado por um script.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a>Veja Também

[Elemento de ListItems (formato)](./listitems-element-for-listentry-for-listcontrol-format.md)

[Elemento de FormatString para ListItem (formato)](./formatstring-element-for-listitem-for-listcontrol-format.md)

[Elemento da etiqueta para ListItem (formato)](./label-element-for-listitem-for-listcontrol-format.md)

[Elemento de PropertyName para ListItem (formato)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Elemento de ScriptBlock para ListItem (formato)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Criar uma vista de lista](./creating-a-list-view.md)

[Escrever do Windows PowerShell, formatação e os tipos de ficheiro](./writing-a-powershell-formatting-file.md)
