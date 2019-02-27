---
title: Elemento de ListItems para ListEntry para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848623"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>ListItems Element for ListEntry for ListControl (Format) (Elemento ListItems para ListEntry para ListControl [Formatação])

Define as propriedades e os scripts cujos valores são apresentados nas linhas da exibição de lista.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry de controle (formato) de lista para o elemento de ListItems ListControl (formato) para ListControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `ListItems` elemento. Não existe nenhum limite para o número de elementos filho que podem ser especificados. A ordem dos elementos subordinados define a ordem em que os valores são apresentados na vista de lista.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ListItem para ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)|Elemento necessário.<br /><br /> Define a propriedade ou um script cujo valor é apresentado pelo vista de lista.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ListEntry para ListControl (formato)](./listentry-element-for-listcontrol-format.md)|Fornece uma definição de vista de lista.|

## <a name="remarks"></a>Observações

Para obter mais informações sobre este tipo de vista, consulte [criar uma vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra os elementos XML que definem três linhas da exibição de lista.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a>Veja Também

[Elemento de ListEntry para ListControl (formato)](./listentry-element-for-listcontrol-format.md)

[Elemento de ListItem para ListControl (formato)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Criar uma vista de lista](./creating-a-list-view.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
