---
title: ListControl elemento (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847832"
---
# <a name="listcontrol-element-format"></a>ListControl Element (Format) (Elemento ListControl [Formatação])

Define um formato de lista para a vista.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ListControl` elemento. Este elemento tem de conter apenas um elemento único filho.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ListEntries (formato)](./listentries-element-for-listcontrol-format.md)|Elemento necessário.<br /><br /> Fornece definições de vista de lista.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de exibição (formato)](./view-element-format.md)|Define uma vista que é utilizada para apresentar os membros de um ou mais objetos.|

## <a name="remarks"></a>Observações

Para obter mais informações sobre como criar uma vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra uma vista de lista para o [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Veja Também

[Elemento de exibição (formato)](./view-element-format.md)

[Elemento de ListEntries (formato)](./listentries-element-for-listcontrol-format.md)

[Criar uma vista de lista](./creating-a-list-view.md)

[Escrever do Windows PowerShell, formatação e os tipos de ficheiro](./writing-a-powershell-formatting-file.md)
