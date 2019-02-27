---
title: Elemento de FirstLineIndent para quadro para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847055"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a>FirstLineIndent Element for Frame for Controls for Configuration (Format) (Elemento FirstLineIndent para Frame para Controls para Configuration [Formatação])

Especifica o número de carateres a primeira linha dos dados é desviada à direita. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de CustomItem de configuração (formato) para CustomEntry para controles para o elemento de quadro de configuração para CustomItem para controles de configuração (formato) FirstLineIndent elemento de quadro para os controles de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elemento pai de elementos filho do `FirstLineIndent` elemento.

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

Se este elemento é especificado, não é possível especificar a [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) elemento.

## <a name="see-also"></a>Consulte Também

[Elemento de FirstLineHanging para quadro para controles de configuração (formato)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Elemento de quadro para CustomItem para controles de configuração (formato)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
