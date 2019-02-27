---
title: Elemento de FirstLineHanging para quadro para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846544"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>FirstLineHanging Element for Frame for GroupBy (Format) (Elemento FirstLineHanging para Frame para GroupBy [Formatação])

Especifica o número de carateres a primeira linha dos dados é desviada à esquerda. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de CustomItem GroupBy (formato) para CustomEntry para o elemento de quadro de GroupBy (formato) para CustomItem para o elemento de FirstLineHanging GroupBy (formato) para o quadro para GroupBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elemento pai de elementos filho do `FirstLineHanging` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

Nenhum.

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de quadro para CustomItem para GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md)|Define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita.|

## <a name="text-value"></a>Valor do Texto

Especifique o número de carateres que pretende mudar a primeira linha dos dados.

## <a name="remarks"></a>Observações

Se este elemento é especificado, não é possível especificar a [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elemento.

## <a name="see-also"></a>Consulte Também

[Elemento de FirstLineIndent para quadro para GroupBy (formato)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Elemento de quadro para CustomItem para GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
