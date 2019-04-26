---
title: Elemento de ColumnNumber para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066911"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>ColumnNumber Element for WideControl (Format) (Elemento ColumnNumber para WideControl [Formatação])

Especifica o número de colunas apresentadas na vista alargada.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) ColumnNumber elemento de configuração para WideControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ColumnNumber` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de WideControl (formato)](./widecontrol-element-format.md)|Define uma vasta (valor único) formato de lista para a vista.|

## <a name="text-value"></a>Valor de texto

Especifique um valor de número inteiro positivo.

## <a name="remarks"></a>Observações

Ao definir uma vista alargada, pode adicionar os `AutoSize` elemento ou o `ColumnNumber` elemento, mas não é possível adicionar ambos.

Para obter mais informações sobre os componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).

Para obter um exemplo de uma vista alargada, consulte [vista alargada (básico)](./wide-view-basic.md).

## <a name="see-also"></a>Veja Também

[Elemento de dimensionamento automático para WideControl (formato)](./autosize-element-for-widecontrol-format.md)

[Criar uma vista alargada](./creating-a-wide-view.md)

[Vista alargada (básico)](./wide-view-basic.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
