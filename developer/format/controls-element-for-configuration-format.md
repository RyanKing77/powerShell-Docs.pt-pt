---
title: Controla o elemento de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850436"
---
# <a name="controls-element-for-configuration-format"></a>Controls Element for Configuration (Format) (Elemento Controls para Configuration [Formatação])

Define os controles comuns que podem ser utilizados por todas as vistas do ficheiro de formatação.

Elemento de controles de elemento (formato) de configuração da configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Controls` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de controle para controles de configuração (formato)](./control-element-for-controls-for-configuration-format.md)|Elemento necessário.<br /><br /> Define um controle comum que pode ser utilizado por todas as vistas do ficheiro de formatação.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de configuração (formato)](./configuration-element-format.md)|Representa o elemento de nível superior de um ficheiro de formatação.|

## <a name="remarks"></a>Observações

Pode criar qualquer número de controles comuns. Para cada controle, tem de especificar o nome que é utilizado para referenciar o controle e os componentes do controle.

## <a name="see-also"></a>Veja Também

[Elemento de configuração (formato)](./configuration-element-format.md)

[Elemento de controle para controles de configuração (formato)](./control-element-for-controls-for-configuration-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
