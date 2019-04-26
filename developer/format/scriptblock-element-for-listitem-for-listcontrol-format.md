---
title: Elemento de ScriptBlock para ListItem para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064582"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>ScriptBlock Element for ListItem for ListControl (Format) (Elemento ScriptBlock para ListItem para ListControl [Formatação])

Especifica o script cujo valor é apresentado na linha.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry ListControl (formato) para ListEntries para o elemento de ListItems ListControl (formato) para ListEntry para o elemento de ListItem ListControl (formato) para ListItems para o elemento de ScriptBlock ListControl (formato) para ListItem para ListControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ListItem (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Define a propriedade ou um script cujo valor é apresentado numa linha da exibição de lista.|

## <a name="text-value"></a>Valor de texto

Especifique o script cujo valor é apresentado na linha.

## <a name="remarks"></a>Observações

Quando este elemento é especificado, não é possível especificar a [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento.

Para obter mais informações sobre como especificar scripts numa vista de lista, consulte [vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como especificar a propriedade cujo valor é apresentado.

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>Veja Também

[Elemento de PropertyName para ListItem para ListControl (formato)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Criar uma vista de lista](./creating-a-list-view.md)

[Elemento de ListItem para ListItems para ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
