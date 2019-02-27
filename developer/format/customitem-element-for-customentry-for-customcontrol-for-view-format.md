---
title: Elemento de CustomItem para CustomEntry para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846943"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>CustomItem Element for CustomEntry for CustomControl for View (Format) (Elemento CustomItem para CustomEntry para CustomControl para View [Formatação])

Define os dados que são apresentados pela vista do controle personalizado e como ele é exibido. Este elemento é utilizado ao definir uma vista de controle personalizado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para exibição (formato) CustomItem elemento para CustomEntry para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomItem` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ExpressionBinding para CustomItem para CustomControl para exibição (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Define os dados que são apresentados pelo controle.|
|[Elemento de quadro para CustomItem para CustomControl para exibição (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Define os dados que são apresentados pela vista do controle personalizado e como ele é exibido.|
|[Elemento de nova linha para CustomItem para controle personalizado para a exibição (formato)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Adiciona uma linha em branco para a exibição do controle.|
|[Elemento de texto para CustomItem para CustomControl para exibição (formato)](./text-element-for-customitem-for-customview-for-view-format.md)|Elemento opcional.<br /><br /> Especifica o texto adicional para os dados apresentados pelo controle.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomEntry para CustomEntries para CustomControl para exibição (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Fornece uma definição de vista do controle personalizado.|

## <a name="remarks"></a>Observações

## <a name="see-also"></a>Consulte Também

[Elemento de CustomEntry para CustomEntries para exibição (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Elemento de ExpressionBinding para CustomItem para CustomControl para exibição (formato)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento de quadro para CustomItem para CustomControl para exibição (formato)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento de nova linha para CustomItem para CustomControl para exibição (formato)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Elemento de texto para CustomItem para CustomControl para exibição (formato)](./text-element-for-customitem-for-customview-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
