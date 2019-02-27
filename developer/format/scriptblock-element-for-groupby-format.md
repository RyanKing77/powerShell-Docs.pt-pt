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
ms.openlocfilehash: 41a6aaa24e5850bd390c8e3b6505cc88fc80b7b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846957"
---
# <a name="scriptblock-element-for-groupby-format"></a>ScriptBlock Element for GroupBy (Format) (Elemento ScriptBlock para GroupBy [Formatação])

Especifica o script que inicia um novo grupo sempre que seu valor é alterado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o modo de exibição (formato) ScriptBlock elemento para GroupBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ScriptBolck>ScriptToEvaluate</ScriptBlock>
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

## <a name="text-value"></a>Valor do Texto

Especifique o script que é avaliado.

## <a name="remarks"></a>Observações

É iniciado um novo grupo do Windows PowerShell sempre que o valor desse script é alterado.

Quando este elemento é especificado, não é possível especificar a [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) elemento para iniciar um novo grupo.

## <a name="see-also"></a>Veja Também

[Elemento de PropertyName para GroupBy (formato)](./propertyname-element-for-groupby-format.md)

[GroupBy elemento para a exibição (formato)](./groupby-element-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)