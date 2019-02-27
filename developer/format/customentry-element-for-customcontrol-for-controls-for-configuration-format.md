---
title: Elemento de CustomEntry para CustomControl para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849477"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>CustomEntry Element for CustomControl for Controls for Configuration (Format) (Elemento CustomEntry para CustomControl para Controls para Configuration [Formatação])

Fornece uma definição do controle comum. Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.

Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles de configuração (formato)

## <a name="syntax"></a>Sintaxe

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomEntry` elemento. Tem de especificar os itens exibidos pela definição.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de EntrySelectedBy para CustomEntry para controles de configuração (formato)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Elemento opcional.<br /><br /> Define os tipos do .NET que utilizam a definição de controle comum ou a condição que tem de existir para este controlo a ser utilizado.|
|[Elemento de CustomItem para CustomEntry para controles de configuração](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Elemento necessário.<br /><br /> Define os dados que são apresentados pelo controle e como ele é exibido.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de CustomEntries para CustomControl para a configuração (formato)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Fornece as definições do controle comum.|

## <a name="remarks"></a>Observações

Na maioria dos casos, apenas uma definição é necessária para cada controlo personalizado comuns, mas é possível ter várias definições, se pretender utilizar o mesmo controlo para apresentar diferentes objetos do .NET. Nesses casos, pode fornecer uma definição de separado para cada objeto ou conjunto de objetos.

## <a name="see-also"></a>Veja Também

[Elemento de CustomEntries para CustomControl para a configuração (formato)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[Elemento de CustomItem para CustomEntry para controles de configuração](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
