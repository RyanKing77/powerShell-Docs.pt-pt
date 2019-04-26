---
title: Estruturar o elemento para CustomItem para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065602"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>Frame Element for CustomItem for GroupBy (Format) (Elemento Frame para CustomItem para GroupBy [Formatação])

Define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomEntry GroupBy (formato) para CustomControl para o elemento de CustomItem GroupBy (formato) para CustomEntry para o elemento de quadro de GroupBy (formato) para CustomItem para GroupBy (formato)

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

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Frame` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|`CustomItem Element`|Elemento necessário|
|[Elemento de FirstLineHanging para quadro para GroupBy (formato)](./firstlinehanging-element-for-frame-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica o número de carateres a primeira linha dos dados é desviada à esquerda.|
|[Elemento de FirstLineIndent para quadro para GroupBy (formato)](./firstlineindent-element-for-frame-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica o número de carateres a primeira linha dos dados é desviada à direita.|
|[Elemento de LeftIndent para quadro para GroupBy (formato)](./leftindent-element-for-frame-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica o número de carateres de dados são desviados da margem esquerda.|
|[Elemento de RightIndent para quadro para GroupBy (formato)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent elemento|Elemento opcional.<br /><br /> Especifica o número de carateres de dados são desviados da margem direita.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomItem para CustomEntry para GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)|Define os dados que são apresentados pelo controle e como ele é exibido.|

## <a name="remarks"></a>Observações

Não é possível especificar a [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) e o [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elementos na mesma `Frame` elemento.

## <a name="see-also"></a>Veja Também

[Elemento de FirstLineHanging para quadro para GroupBy (formato)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[Elemento de FirstLineIndent para quadro para GroupBy (formato)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Elemento de LeftIndent para quadro para GroupBy (formato)](./leftindent-element-for-frame-for-groupby-format.md)

[Elemento de RightIndent para quadro para GroupBy (formato)](./rightindent-element-for-frame-for-groupby-format.md)

[Elemento de CustomItem para CustomEntry para GroupBy (formato)](./customitem-element-for-customentry-for-groupby-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
