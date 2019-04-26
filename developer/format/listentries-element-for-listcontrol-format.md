---
title: Elemento de ListEntries para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065398"
---
# <a name="listentries-element-for-listcontrol-format"></a>ListEntries Element for ListControl (Format) (Elemento ListEntries para ListControl [Formatação])

Fornece definições de vista de lista. A vista de lista tem de especificar uma ou mais definições.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries o elemento de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ListEntries` elemento. Elemento, pelo menos, um subordinado tem de ser especificado.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ListEntry (formato)](./listentry-element-for-listcontrol-format.md)|Fornece uma definição de vista de lista.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[ListControl elemento (formato)](./listcontrol-element-format.md)|Define um formato de lista para a vista.|

## <a name="remarks"></a>Observações

Para obter mais informações sobre vistas de lista, consulte [vista de lista](./creating-a-list-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra os elementos XML que definem a vista de lista para o [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Veja Também

[ListControl elemento (formato)](./listcontrol-element-format.md)

[Elemento de ListEntry (formato)](./listentry-element-for-listcontrol-format.md)

[Vista de lista](./creating-a-list-view.md)

[Escrever do Windows PowerShell, formatação e os tipos de ficheiro](./writing-a-powershell-formatting-file.md)
