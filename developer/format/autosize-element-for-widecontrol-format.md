---
title: Elemento de dimensionamento automático para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066928"
---
# <a name="autosize-element-for-widecontrol-format"></a>AutoSize Element for WideControl (Format) (Elemento AutoSize para WideControl [Formatação])

Especifica se o tamanho da coluna e o número de colunas são ajustados com base no tamanho dos dados.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) Autosize elemento de configuração para WideControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `AutoSize` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

Nenhum

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de WideControl (formato)](./widecontrol-element-format.md)|Define uma vasta (valor único) formato de lista para a vista.|

## <a name="remarks"></a>Observações

Ao definir uma vista alargada, pode adicionar os `AutoSize` elemento ou o [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) elemento, mas não é possível adicionar ambos.

Para obter mais informações sobre os componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).

Para obter um exemplo de uma vista alargada, consulte [vista alargada (básico)](./wide-view-basic.md).

## <a name="see-also"></a>Veja Também

[Elemento de ColumnNumber para WideControl (formato)](./columnnumber-element-for-widecontrol-format.md)

[Criar uma vista alargada](./creating-a-wide-view.md)

[Elemento de WideControl (formato)](./widecontrol-element-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
