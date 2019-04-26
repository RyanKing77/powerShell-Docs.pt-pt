---
title: Elemento de CustomItem para CustomEntry para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066435"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>CustomItem Element for CustomEntry for Controls for Configuration (Format) (Elemento CustomItem para CustomEntry para Controls para Configuration [Formatação])

Define os dados que são apresentados pelo controle e como ele é exibido. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles para o elemento de CustomItem de configuração (formato) para CustomEntry para controles de configuração

## <a name="syntax"></a>Sintaxe

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomItem` elemento. Para obter mais informações, consulte observações.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ExpressionBinding para CustomItem para controles de configuração (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Define os dados que são apresentados pelo controle.|
|[Elemento de quadro para CustomItem para controles de configuração (formato)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Define a forma como os dados são apresentados, tais como mudar os dados para a esquerda ou direita.|
|[Elemento de nova linha para CustomItem para controles de configuração (formato)](./newline-element-for-customitem-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Adiciona uma linha em branco para a exibição do controle.|
|[Elemento de texto para CustomItem para controles de configuração (formato)](./text-element-for-customitem-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Adiciona o texto, como parênteses ou entre colchetes, para a exibição do controle.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomEntry para CustomControl para controles de configuração (formato)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Fornece uma definição do controle.|

## <a name="remarks"></a>Observações

Ao especificar os elementos filho do `CustomItem` elemento, tenha em atenção o seguinte:

- Os elementos filho tem de ser adicionados a seguinte sequência: `ExpressionBinding`, `NewLine`, `Text`, e `Frame`.

- Não existe nenhum limite máximo para o número de sequências de que pode especificar.

- Em cada sequência, não há nenhum limite máximo para o número de `ExpressionBinding` elementos que pode utilizar.

## <a name="see-also"></a>Veja Também

[Elemento de ExpressionBinding para CustomItem para controles de configuração (formato)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento de quadro para CustomItem para controles de configuração (formato)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento de nova linha para CustomItem para controles de configuração (formato)](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[Elemento de texto para CustomItem para controles de configuração (formato)](./text-element-for-customitem-for-controls-for-configuration-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
