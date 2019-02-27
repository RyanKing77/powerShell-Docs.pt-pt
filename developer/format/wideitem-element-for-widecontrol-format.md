---
title: Elemento de WideItem para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851451"
---
# <a name="wideitem-element-for-widecontrol-format"></a>WideItem Element for WideControl (Format) (Elemento WideItem para WideControl [Formatação])

Define a propriedade ou um script cujo valor é apresentado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento (formato) WideItem elemento de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `WideItem` elemento. O `FormatString` elemento é opcional. No entanto, tem de especificar um `PropertyName` ou `ScriptBlock` elemento, mas não é possível especificar ambos.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de FormatString para WideItem para WideControl (formato)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|Elemento opcional.<br /><br /> Especifica um padrão de formato que define como o valor de propriedade ou um script é apresentado na vista.|
|[Elemento de PropertyName para WideItem (formato)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Especifica a propriedade do objeto cujo valor é apresentado na vista alargada.|
|[Elemento de ScriptBlock para WideItem (formato)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Especifica o script cujo valor é apresentado na vista alargada.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)|Fornece uma definição da vista ampla.|

## <a name="remarks"></a>Observações

Para obter mais informações sobre os componentes de uma vista alargada, consulte [vista alargada](./creating-a-wide-view.md).

## <a name="example"></a>Exemplo

A exemplo a seguir mostra um `WideEntry` elemento que define uma única `WideItem` elemento. O `WideItem` elemento define a propriedade ou um script cujo valor é apresentado na vista.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Para obter um exemplo completo de uma vista alargada, consulte [vista alargada (básico)](./wide-view-basic.md).

## <a name="see-also"></a>Veja Também

[Elemento de FormatString para WideItem para WideControl (formato)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[Elemento de PropertyName para WideItem (formato)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[Elemento de ScriptBlock para WideItem (formato)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[Elemento de WideEntry (formato)](./wideentry-element-for-widecontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
