---
title: Elemento de CustomEntries para CustomControl para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066549"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>CustomEntries Element for CustomControl for GroupBy (Format) (Elemento CustomEntries para CustomControl para GroupBy [Formatação])

Fornece as definições para o controle. Este elemento é utilizado quando se definem como é apresentado um novo grupo de objetos.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o elemento de CustomControl de exibição (formato) para o elemento de CustomEntries GroupBy (formato) para CustomControl para GroupBy (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos de principal de elementos filho do `CustomEntries` elemento. Não existe nenhum limite máximo para o número de elementos filho que podem ser especificados.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomEntry para CustomControl para GroupBy (formato)](./customentry-element-for-customcontrol-for-groupby-format.md)|Elemento necessário.<br /><br /> Fornece uma definição do controle.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomControl para GroupBy (formato)](./customcontrol-element-for-groupby-format.md)|Define o controle personalizado que exibe o novo grupo.|

## <a name="remarks"></a>Observações

Na maioria dos casos, um controle tiver apenas uma definição, o que é especificada num único `CustomEntry` elemento. No entanto, é possível fornecer várias definições, se pretender utilizar o mesmo controlo para apresentar grupos diferentes. Nesses casos, pode definir um `CustomEntry` elemento para um grupo.

## <a name="see-also"></a>Veja Também

[Elemento de CustomEntry para CustomEntries para controles para exibição (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Elemento de CustomControl para GroupBy (formato)](./customcontrol-element-for-groupby-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
