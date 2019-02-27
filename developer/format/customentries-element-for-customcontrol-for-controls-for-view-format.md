---
title: Elemento de CustomEntries para CustomControl para controles para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850877"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>CustomEntries Element for CustomControl for Controls for View (Format) (Elemento CustomEntries para CustomControl para Controls para View [Formatação])

Fornece as definições para o controle. Este elemento é utilizado ao definir os controles que podem ser utilizados por uma vista.

Configuração elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) controles elemento (formato) elemento de controle para controles para exibição (formato) CustomControl elemento de controle para controles para exibição (formato) CustomEntries elemento para CustomControl para controles para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos de principal de elementos filho do `CustomEntries` elemento. Não existe nenhum limite máximo para o número de elementos filho que podem ser especificados.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomEntry para CustomEntries para controles para exibição (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Elemento necessário.<br /><br /> Fornece uma definição do controle.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomControl para o controle para controles para exibição (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Define o controle usado pela exibição.|

## <a name="remarks"></a>Observações

Na maioria dos casos, um controle tiver apenas uma definição, o que é especificada num único `CustomEntry` elemento. No entanto, é possível fornecer várias definições, se pretender utilizar o mesmo controlo para apresentar diferentes objetos do .NET. Nesses casos, pode definir um `CustomEntry` elemento para cada objeto ou conjunto de objetos.

## <a name="see-also"></a>Consulte Também

[Elemento de CustomEntry para CustomEntries para controles para exibição (formato)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Elemento de CustomControl para o controle para controles para exibição (formato)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
