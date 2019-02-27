---
title: Elemento da etiqueta para ListItem para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845956"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Label Element for ListItem for ListControl (Format) (Elemento Label para ListItem para ListControl [Formatação])

Especifica a etiqueta que é apresentada à esquerda do valor de propriedade ou um script na linha.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry ListControl (formato) para ListItems ListControl (formato) para ListEntry para ListControl elemento ( Elemento de ListItem do formato) para ListItems para o elemento de etiqueta ListControl (formato) para ListItem para ListControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Label` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ListItem para ListItems para ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Define a propriedade ou um script cujo valor é apresentado numa linha da exibição de lista.|

## <a name="text-value"></a>Valor do Texto

Especifique a etiqueta a ser exibida para a esquerda do valor de propriedade ou script.

## <a name="remarks"></a>Observações

Se uma etiqueta não for especificada, é apresentado o nome da propriedade ou o script. Para obter mais informações sobre como utilizar as etiquetas numa vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como adicionar uma etiqueta para uma linha.

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Veja Também

[Criar uma vista de lista](./creating-a-list-view.md)

[Elemento de ListItem (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
