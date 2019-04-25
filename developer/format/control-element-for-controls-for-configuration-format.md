---
title: Controlar o elemento para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066798"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Control Element for Controls for Configuration (Format) (Elemento Control para Controls para Configuration [Formatação])

Define um controle comum que pode ser utilizado por todas as vistas do ficheiro formatação e o nome que é utilizado para referenciar o controle.

Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal para o `Control` elemento. Tem de especificar apenas um de cada elemento filho.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomControl para o controle para controles de configuração (formato)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Elemento necessário.<br /><br /> Define o controlo.|
|[Elemento de nome para o controlo de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)|Elemento necessário.<br /><br /> Especifica o nome utilizado para referenciar o controle.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de controles de configuração (formato)](./controls-element-for-configuration-format.md)|Define os controles comuns que podem ser utilizados por todas as vistas do arquivo formatação ou por outros controles.|

## <a name="remarks"></a>Observações

O nome atribuído a esse controle pode ser referenciado nos seguintes elementos:

- [Elemento de ExpressionBinding para CustomItem (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [Elemento de GroupBy para View(Format)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Veja Também

[Elemento de controles de configuração (formato)](./controls-element-for-configuration-format.md)

[Elemento de CustomControl para controlo de configuração (formato)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[Elemento de ExpressionBinding para CustomItem (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento de GroupBy para View(Format)](./groupby-element-for-view-format.md)

[Elemento de nome para o controle para controles de configuração (formato)](./name-element-for-control-for-controls-for-configuration-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
