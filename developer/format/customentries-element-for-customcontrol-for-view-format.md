---
title: Elemento de CustomEntries para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850800"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>CustomEntries Element for CustomControl for View (Format) (Elemento CustomEntries para CustomControl para View [Formatação])

Fornece definições de vista do controle personalizado. O modo de exibição do controle personalizado tem de especificar uma ou mais definições.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomControlEntries` elemento. Tem de especificar um ou mais elementos subordinados.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomEntry para CustomEntries para exibição (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Elemento necessário.<br /><br /> Fornece uma definição de vista do controle personalizado.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomControl para exibição (formato)](./customcontrol-element-for-view-format.md)|Elemento necessário.<br /><br /> Define um formato de controle personalizado para a vista.|

## <a name="remarks"></a>Observações

Na maioria dos casos, um controle tiver apenas uma definição, o que é definida num único `CustomEntry` elemento. No entanto, é possível ter várias definições de se pretender utilizar o mesmo controlo para apresentar diferentes objetos do .NET. Nesses casos, pode definir um `CustomEntry` elemento para cada objeto ou conjunto de objetos.

## <a name="see-also"></a>Veja Também

[Elemento de CustomControl para exibição (formato)](./customcontrol-element-for-view-format.md)

[Elemento de CustomEntry para CustomEntries para exibição (formato)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
