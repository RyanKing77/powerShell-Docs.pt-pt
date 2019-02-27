---
title: Quadro elemento para CustomItem para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851696"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Frame Element for CustomItem for Controls for Configuration (Format) (Elemento Frame para CustomItem para Controls para Configuration [Formatação])

Define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de CustomItem de configuração (formato) para CustomEntry para controles para o elemento de quadro de configuração para CustomItem para controles de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Frame` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|`CustomItem Element`|Elemento necessário|
|[Elemento de FirstLineHanging para quadro para controles de configuração (formato)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica o número de carateres a primeira linha dos dados é desviada à esquerda.|
|[Elemento de FirstLineIndent para quadro para controles de configuração (formato)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica o número de carateres a primeira linha dos dados é desviada à direita.|
|[Elemento de LeftIndent para quadro para controles de configuração (formato)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica o número de carateres de dados são desviados da margem esquerda.|
|[Elemento de RightIndent para quadro para controles de configuração (formato)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Especifica o número de carateres de dados são desviados da margem direita.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomItem para CustomEntry para controles de configuração](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Define os dados que são apresentados pelo controle e como ele é exibido.|

## <a name="remarks"></a>Observações

Não é possível especificar a [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elementos na mesma `Frame` elemento.

## <a name="see-also"></a>Consulte Também

[Elemento de FirstLineHanging para quadro para controles de configuração (formato)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Elemento de FirstLineIndent para quadro para controles de configuração (formato)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento de LeftIndent para quadro para controles de configuração (formato)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento de RightIndent para quadro para controles de configuração (formato)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[Elemento de CustomItem para CustomEntry para controles de configuração](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
