---
title: O elemento de DisplayError (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056486"
---
# <a name="displayerror-element-format"></a>DisplayError Element (Format) (Elemento DisplayError [Formatação])

Especifica que a cadeia de caracteres #ERR é apresentada quando ocorre um erro de apresentar um conjunto de dados.

Elemento de configuração do DisplayError elemento (formato) DefaultSettings elemento (formato) (formato)

## <a name="syntax"></a>Sintaxe

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `DisplayError` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de DefaultSettings (formato)](./defaultsettings-element-format.md)|Define configurações comuns que se aplicam a todas as vistas do ficheiro de formatação.|

## <a name="remarks"></a>Observações

Por predefinição, quando ocorre um erro ao tentar exibir um conjunto de dados, a localização dos dados é deixada em branco. Quando este elemento está definido como true, a cadeia de caracteres #ERR será apresentado.

## <a name="see-also"></a>Veja Também

[Elemento de DefaultSettings (formato)](./defaultsettings-element-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
