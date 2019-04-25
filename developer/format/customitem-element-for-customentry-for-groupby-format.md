---
title: Elemento de CustomItem para CustomEntry para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066403"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>CustomItem Element for CustomEntry for GroupBy (Format) (Elemento CustomItem para CustomEntry para GroupBy [Formatação])

Define os dados que são apresentados pela vista do controle personalizado e como ele é exibido. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para o elemento de CustomItem GroupBy (formato) para CustomEntry para GroupBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomItem` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ExpressionBinding para CustomItem para GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Elemento opcional.<br /><br /> Define os dados que são apresentados pelo controle.|
|[Elemento de quadro para CustomItem para GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md)|Elemento opcional.<br /><br /> Define os dados que são apresentados pela vista do controle personalizado e como ele é exibido.|
|[Elemento de nova linha para CustomItem para GroupBy (formato)](./newline-element-for-customitem-for-groupby-format.md)|Elemento opcional.<br /><br /> Adiciona uma linha em branco para a exibição do controle.|
|[Elemento de texto para CustomItem para GroupBy (formato)](./text-element-for-customitem-for-groupby-format.md)|Elemento opcional.<br /><br /> Especifica o texto adicional para os dados apresentados pelo controle.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomEntry para CustomControl para GroupBy (formato)](./customentry-element-for-customcontrol-for-groupby-format.md)|Fornece uma definição de vista do controle personalizado.|

## <a name="remarks"></a>Observações

## <a name="see-also"></a>Veja Também

[Elemento de CustomEntry para CustomControl para GroupBy (formato)](./customentry-element-for-customcontrol-for-groupby-format.md)

[Elemento de ExpressionBinding para CustomItem para GroupBy (formato)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Elemento de quadro para CustomItem para GroupBy (formato)](./frame-element-for-customitem-for-groupby-format.md)

[Elemento de nova linha para CustomItem para GroupBy (formato)](./newline-element-for-customitem-for-groupby-format.md)

[Elemento de texto para CustomItem para GroupBy (formato)](./text-element-for-customitem-for-groupby-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
