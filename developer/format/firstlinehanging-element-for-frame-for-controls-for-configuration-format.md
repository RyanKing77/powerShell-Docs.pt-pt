---
title: Elemento de FirstLineHanging para quadro para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 679c8bcb-b49d-4bb4-91f5-ea1af6c217e3
caps.latest.revision: 8
ms.openlocfilehash: 4553f95e48a2b1440c00b4951bea56376b00628a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850548"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a>FirstLineHanging Element for Frame for Controls for Configuration (Format) (Elemento FirstLineHanging para Frame para Controls para Configuration [Formatação])

Especifica o número de carateres a primeira linha dos dados é desviada à esquerda. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de CustomItem de configuração (formato) para CustomEntry para controles para o elemento de quadro de configuração para CustomItem para controles de configuração (formato) FirstLineHanging elemento de quadro para os controles de configuração (formato)

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
|[Elemento de quadro para CustomItem para controles de configuração (formato)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita.|

## <a name="text-value"></a>Valor do Texto

Especifique o número de carateres que pretende mudar a primeira linha dos dados.

## <a name="remarks"></a>Observações

Se este elemento é especificado, não é possível especificar o `FirstLineIndent` elemento.

## <a name="see-also"></a>Veja Também

[Elemento de quadro para CustomItem para controles de configuração (formato)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
