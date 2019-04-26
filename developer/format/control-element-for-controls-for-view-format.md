---
title: Controlar o elemento para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066775"
---
# <a name="control-element-for-controls-for-view--format"></a>Control Element for Controls for View (Format) (Elemento Control para Controls para View [Formatação])

Define um controle que pode ser utilizado pela exibição e o nome que é utilizado para referenciar o controle.

Elemento de configuração do modo de exibição elemento (formato) ViewDefinitions elemento (formato) (formato) controla o elemento de controle do elemento (formato) para controles para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Control` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de nome para o controlo para exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)|Elemento necessário.<br /><br /> Especifica o nome do controle.|
|[Elemento de CustomControl para o controle para controles para exibição (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Elemento necessário.<br /><br /> Define o controle usado por esta vista.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de controles (formato)](./controls-element-for-view-format.md)|Define os controles de exibição que podem ser utilizados por uma vista específica.|

## <a name="remarks"></a>Observações

Esse controle pode ser especificado pelos seguintes elementos:

- [Elemento de CustomControlName para ExpressionBinding para controles para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [Elemento de CustomControlName para ExpressionBinding para CustomControl para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [Elemento de CustomControlName para ExpressionBinding para GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [Elemento de CustomControlName para GroupBy (formato)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Veja Também

[Elemento de CustomControl para o controle para controles para exibição (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Elemento de CustomControlName para ExpressionBinding para controles para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Elemento de CustomControlName para ExpressionBinding para CustomControl para exibição (formato)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Elemento de CustomControlName para ExpressionBinding para GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Elemento de CustomControlName para ExpressionBinding para GroupBy (formato)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Elemento de controles (formato)](./controls-element-for-view-format.md)

[Elemento de nome para o controle para controles para exibição (formato)](./name-element-for-control-for-controls-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
