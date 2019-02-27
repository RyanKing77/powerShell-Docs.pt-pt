---
title: Elemento de CustomItem para CustomEntry para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846537"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>CustomItem Element for CustomEntry for Controls for View (Format) (Elemento CustomItem para CustomEntry para Controls para View [Formatação])

Define os dados que são apresentados pelo controle e como ele é exibido. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para controles para exibição (formato) CustomItem elemento para CustomEntry para controles para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomItem` elemento. Para obter mais informações, consulte observações.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Define os dados que são apresentados pelo controle.|
|[Elemento de quadro para CustomItem para controles para exibição (formato)](./frame-element-for-customitem-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita.|
|[Elemento de nova linha para CustomItem para controles para exibição (formato)](./newline-element-for-customitem-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Adiciona uma linha em branco para a exibição do controle.|
|[Elemento de texto para CustomItem para controles para exibição (formato)](./text-element-for-customitem-for-controls-for-view-format.md)|Elemento opcional.<br /><br /> Adiciona o texto, como parênteses ou entre colchetes, para a exibição do controle.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomEntry para CustomEntries para controles para exibição (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Fornece uma definição do controle.|

## <a name="remarks"></a>Observações

Ao especificar os elementos filho do `CustomItem` elemento, tenha em atenção o seguinte:

- Os elementos filho tem de ser adicionados a seguinte sequência: `ExpressionBinding`, `NewLine`, `Text`, e `Frame`.

- Não existe nenhum limite máximo para o número de sequências de que pode especificar.

- Em cada sequência, não há nenhum limite máximo para o número de `ExpressionBinding` elementos que pode utilizar.

## <a name="see-also"></a>Veja Também

[Elemento de ExpressionBinding para CustomItem para controles para exibição (formato)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Elemento de quadro para CustomItem para controles para exibição (formato)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Elemento de nova linha para CustomItem para controles para exibição (formato)](./newline-element-for-customitem-for-controls-for-view-format.md)

[Elemento de texto para CustomItem para controles para exibição (formato)](./text-element-for-customitem-for-controls-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
