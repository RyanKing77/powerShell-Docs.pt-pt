---
title: Elemento de FirstLineHanging para quadro para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53694f08-57f7-4185-b443-1636a0918afc
caps.latest.revision: 8
ms.openlocfilehash: 387340cd9b0aae2ad0419b187d96ab4fee183d5a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848714"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-view-format"></a>FirstLineHanging Element for Frame for Controls for View (Format) (Elemento FirstLineHanging para Frame para Controls para View [Formatação])

Especifica o número de carateres a primeira linha dos dados é desviada à esquerda. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) CustomItem elemento para CustomEntry para controles para o elemento de quadro de modo de exibição (formato) para CustomItem para controles para exibição (formato) FirstLineHanging elemento de Quadro de controles de exibição (formato)

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
|[Elemento de quadro para CustomItem para controles para exibição (formato)](./frame-element-for-customitem-for-controls-for-view-format.md)|Define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita.|

## <a name="text-value"></a>Valor do Texto

Especifique o número de carateres que pretende mudar a primeira linha dos dados.

## <a name="remarks"></a>Observações

Se este elemento é especificado, não é possível especificar a [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elemento.

## <a name="see-also"></a>Consulte Também

[Elemento de FirstLineIndent para quadro para controles para exibição (formato)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[Elemento de quadro para CustomItem para controles para exibição (formato)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
