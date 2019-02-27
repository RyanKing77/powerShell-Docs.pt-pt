---
title: Elemento de PropertyName para WideItem para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850282"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a>PropertyName Element for WideItem for WideControl (Format) (Elemento PropertyName para WideItem para WideControl [Formatação])

Especifica a propriedade do objeto cujo valor é apresentado na vista alargada.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) WideItem elemento (formato) PropertyName elemento de configuração para WideItem (formato)

## <a name="syntax"></a>Sintaxe

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `PropertyName` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de WideItem (formato)](./wideitem-element-for-widecontrol-format.md)|Define a propriedade ou um script cujo valor é apresentado na vista alargada.|

## <a name="text-value"></a>Valor do Texto

Especifique o nome da propriedade cujo valor é apresentado.

## <a name="remarks"></a>Observações

Para obter mais informações sobre os componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra uma vista alargada, que exibe o valor da propriedade ProcessName a [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a>Veja Também

[Elemento de WideItem (formato)](./wideitem-element-for-widecontrol-format.md)

[Criar uma vista alargada](./creating-a-wide-view.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
