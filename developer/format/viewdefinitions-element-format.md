---
title: O elemento de ViewDefinitions (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083710"
---
# <a name="viewdefinitions-element-format"></a>ViewDefinitions Element (Format) (Elemento ViewDefinitions [Formatação])

Define os modos de exibição utilizados para apresentar os objetos .NET. Estas vistas podem apresentar as propriedades e valores de script de um objeto num formato de tabela, o formato de lista, a amplo formato e o formato de controle personalizado.

Elemento de configuração do elemento (formato) ViewDefinitions (formato XML)

## <a name="syntax"></a>Sintaxe

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `ViewDefinitions` elemento. Não há limite para o número de visualizações que podem ser definidos num arquivo de formatação e podem ser adicionados por qualquer ordem.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de exibição (formato)](./view-element-format.md)|Define uma vista que é utilizada para apresentar um ou mais objetos do .NET.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de configuração (formato)](./configuration-element-format.md)|Representa o elemento de nível superior de um ficheiro de formatação.|

## <a name="remarks"></a>Observações

Para obter mais informações sobre os componentes dos diferentes tipos de vistas, consulte os seguintes tópicos:

- [Criar uma vista de tabela](./creating-a-table-view.md)

- [Criar uma vista de lista](./creating-a-list-view.md)

- [Criar uma vista alargada](./creating-a-wide-view.md)

- [Controles personalizados](./creating-custom-controls.md)

## <a name="example"></a>Exemplo

Este exemplo mostra um `ViewDefinitions` elemento que contém os elementos de principal para uma vista de tabela e uma vista de lista.

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a>Veja Também

[Elemento de configuração (formato)](./configuration-element-format.md)

[Elemento de exibição (formato)](./view-element-format.md)

[Criar uma vista de tabela](./creating-a-table-view.md)

[Criar uma vista de lista](./creating-a-list-view.md)

[Criar uma vista alargada](./creating-a-wide-view.md)

[Controles personalizados](./creating-custom-controls.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
