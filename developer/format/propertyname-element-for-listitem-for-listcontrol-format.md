---
title: Elemento de PropertyName para ListItem para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846628"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>PropertyName Element for ListItem for ListControl (Format) (Elemento PropertyName para ListItem para ListControl [Formatação])

Especifica a propriedade de .NET cujo valor é apresentado na lista.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento (formato) ListEntry elemento (formato) ListItems elemento (formato) ListItem elemento (formato) PropertyName elemento de configuração para ListItem (formato)

## <a name="syntax"></a>Sintaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `PropertyName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ListItem (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Define a propriedade ou um script cujo valor é apresentado na linha da exibição de lista.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome da propriedade cujo valor é apresentado.

## <a name="remarks"></a>Observações

Quando este elemento é especificado, não é possível especificar a [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento.

Além de exibir o valor da propriedade, também pode especificar uma etiqueta para o valor ou uma cadeia de caracteres de formato que pode ser utilizada para alterar a apresentação do valor. Para obter mais informações sobre como especificar os dados numa vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como especificar o rótulo e uma propriedade cujo valor é apresentado.

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Veja Também

[Elemento de ScriptBlock para ListItem para ListControl (formato)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Criar uma vista de lista](./creating-a-list-view.md)

[Elemento de ListItem para ListControl(Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
