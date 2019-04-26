---
title: O elemento de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066826"
---
# <a name="configuration-element-format"></a>Configuration Element (Format) (Elemento Configuration [Formatação])

Representa o elemento de nível superior de um ficheiro de formatação.

Elemento de configuração

## <a name="syntax"></a>Sintaxe

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Configuration` elemento. Este elemento tem de ser o elemento de raiz para cada ficheiro de formatação e este elemento tem de conter, pelo menos, um elemento subordinado.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de controles para a configuração (formato)](./controls-element-for-configuration-format.md)|Elemento opcional.<br /><br /> Define os controles comuns que podem ser utilizados por todas as vistas do ficheiro de formatação.|
|[Elemento de DefaultSettings (formato)](./defaultsettings-element-format.md)|Elemento opcional.<br /><br /> Define configurações comuns que se aplicam a todas as vistas do ficheiro de formatação.|
|[Formato de elemento de SelectionSets](./selectionsets-element-format.md)|Elemento opcional.<br /><br /> Define os conjuntos comuns de objetos .NET que podem ser utilizados por todas as vistas do ficheiro de formatação.|
|[Elemento de ViewDefinitions (formato)](./viewdefinitions-element-format.md)|Elemento opcional.<br /><br /> Define os modos de exibição utilizados para apresentar os objetos.|

### <a name="parent-elements"></a>Elementos principais

Nenhum.

## <a name="remarks"></a>Observações

Arquivos de formatação definem a forma como os objetos são apresentados. Na maioria dos casos, esse elemento de raiz contém um [ViewDefinitions](./viewdefinitions-element-format.md) elemento que define a tabela, lista e vistas ampla do arquivo formatação. Além das definições de exibição, o ficheiro de formatação pode definir conjuntos de seleção, definições e controlos que podem utilizar esses modos de exibição comuns.

## <a name="see-also"></a>Veja Também

[Elemento de controles para a configuração (formato)](./controls-element-for-configuration-format.md)

[Elemento de DefaultSettings (formato)](./defaultsettings-element-format.md)

[Elemento de SelectionSets (formato)](./selectionsets-element-format.md)

[Elemento de ViewDefinitions (formato)](./viewdefinitions-element-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
