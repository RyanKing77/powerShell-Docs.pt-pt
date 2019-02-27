---
title: Estruturar o elemento para CustomItem para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849484"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Frame Element for CustomItem for Controls for View (Format) (Elemento Frame para CustomItem para Controls para View [Formatação])

Define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) CustomItem elemento para CustomEntry para controles para o elemento de quadro de modo de exibição (formato) para CustomItem para controles para exibição (formato)

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
|[Elemento de FirstLineHanging do quadro de controles de exibição (formato)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o número de carateres a primeira linha é desviada à esquerda.|
|[Elemento de FirstLineIndent do quadro de controles de exibição (formato)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o número de carateres a primeira linha é desviada à direita.|
|[Elemento de LeftIndent do quadro de controles de exibição (formato)](./leftindent-element-for-frame-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o número de carateres de dados são desviados da margem esquerda.|
|[Elemento de RightIndent do quadro de controles de exibição (formato)](./rightindent-element-for-frame-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o número de carateres de dados são desviados da margem direita.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomItem para CustomEntry para controles para exibição (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Define os dados que são apresentados pelo controle e como ele é exibido.|

## <a name="remarks"></a>Observações

Não é possível especificar a [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elementos na mesma `Frame` elemento.

## <a name="see-also"></a>Veja Também

[Elemento de FirstLineHanging do quadro de controles de exibição (formato)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[Elemento de FirstLineIndent do quadro de controles de exibição (formato)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[Elemento de LeftIndent do quadro de controles de exibição (formato)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[Elemento de RightIndent do quadro de controles de exibição (formato)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[Elemento de CustomItem para CustomEntry para controles para exibição (formato)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
