---
title: Elemento de CustomEntry para CustomEntries para CustomControl para exibição (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066452"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>CustomEntry Element for CustomEntries for CustomControl for View (Format) (Elemento CustomEntry para CustomEntries para CustomControl para View [Formatação])

Fornece uma definição de vista do controle personalizado.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) CustomControl elemento (formato) CustomEntries elemento de configuração para CustomControl para exibição (formato) CustomEntry elemento para CustomEntries para exibição (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomEntry` elemento. Tem de especificar os itens exibidos pela definição.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de EntrySelectedBy para CustomEntry para exibição (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Elemento opcional.<br /><br /> Define os tipos do .NET que utilizam a definição de vista do controle personalizado ou a condição que tem de existir para esta definição a utilizar.|
|[Elemento de CustomItem para CustomEntry para exibição (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Define um controle para a definição de controle personalizado.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomEntries para CustomControl para exibição (formato)](./customentries-element-for-customcontrol-for-view-format.md)|Fornece definições de vista do controle personalizado. O modo de exibição do controle personalizado tem de especificar uma ou mais definições.|

## <a name="remarks"></a>Observações

Na maioria dos casos, apenas uma definição é necessária para cada exibição de controle personalizado, mas é possível ter várias definições, se pretender utilizar a mesma vista para apresentar diferentes objetos do .NET. Nesses casos, pode fornecer uma definição de separado para cada objeto ou conjunto de objetos.

## <a name="see-also"></a>Veja Também

[Elemento de CustomControl para exibição (formato)](./customcontrol-element-for-view-format.md)

[Elemento de CustomItem para CustomEntry para exibição (formato)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Elemento de EntrySelectedBy para CustomEntry para exibição (formato)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
