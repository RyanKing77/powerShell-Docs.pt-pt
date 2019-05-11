---
title: Elemento de ScriptBlock para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229310"
---
# <a name="scriptblock-element-for-groupby-format"></a>ScriptBlock Element for GroupBy (Format) (Elemento ScriptBlock para GroupBy [Formatação])

Especifica o script que inicia um novo grupo sempre que seu valor é alterado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o modo de exibição (formato) ScriptBlock elemento para GroupBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[GroupBy elemento para a exibição (formato)](./groupby-element-for-view-format.md)|Define como um grupo de objetos do .NET é exibido.|

## <a name="text-value"></a>Valor de texto

Especifique o script que é avaliado.

## <a name="remarks"></a>Observações

PowerShell inicia um novo grupo sempre que o valor desse script é alterado.

Quando este elemento é especificado, não é possível especificar a [PropertyName](propertyname-element-for-groupby-format.md) elemento para iniciar um novo grupo.

## <a name="see-also"></a>Veja Também

[Elemento de PropertyName para GroupBy (formato)](propertyname-element-for-groupby-format.md)

[GroupBy elemento para a exibição (formato)](groupby-element-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](writing-a-powershell-formatting-file.md)
