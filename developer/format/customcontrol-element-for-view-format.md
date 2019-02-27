---
title: Elemento de CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850492"
---
# <a name="customcontrol-element-for-view-format"></a>CustomControl Element for View (Format) (Elemento CustomControl para View [Formatação])

Define um formato de controle personalizado para a vista.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomControl` elemento. Tem de especificar um elemento subordinado.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomEntries para CustomControl para exibição (formato)](./customentries-element-for-customcontrol-for-view-format.md)|Elemento necessário.<br /><br /> Fornece definições de vista do controle personalizado.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de exibição (formato)](./view-element-format.md)|Define uma vista que é utilizada para apresentar um ou mais objetos do .NET.|

## <a name="remarks"></a>Observações

Na maioria dos casos, apenas uma definição é necessária para cada modo de exibição control, mas é possível fornecer várias definições, se pretender utilizar a mesma vista para apresentar diferentes objetos do .NET. Nesses casos, pode fornecer uma definição de separado para cada objeto ou conjunto de objetos.

## <a name="see-also"></a>Consulte Também

[Elemento de CustomEntries para CustomControl para exibição (formato)](./customentries-element-for-customcontrol-for-view-format.md)

[Elemento de exibição (formato)](./view-element-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
