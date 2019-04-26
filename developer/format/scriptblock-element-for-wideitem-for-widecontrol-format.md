---
title: Elemento de ScriptBlock para WideItem para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064208"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>ScriptBlock Element for WideItem for WideControl (Format) (Elemento ScriptBlock para WideItem para WideControl [Formatação])

Especifica o script cujo valor é apresentado na vista alargada.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) WideItem elemento (formato) ScriptBlock elemento de configuração para WideItem (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `ScriptBlock` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de WideItem (formato)](./wideitem-element-for-widecontrol-format.md)|Define o bloco de script ou propriedade cujo valor é apresentado na vista alargada.|

## <a name="text-value"></a>Valor de texto

Especifique o script cujo valor é apresentado.

## <a name="remarks"></a>Observações

Para obter mais informações sobre os componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra um `WideItem` elemento que define um script cujo valor é apresentado na vista.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>Veja Também

[Elemento de WideItem (formato)](./wideitem-element-for-widecontrol-format.md)

[Criar uma vista alargada](./creating-a-wide-view.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
