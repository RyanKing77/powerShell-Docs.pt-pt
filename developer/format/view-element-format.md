---
title: Ver o elemento (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846915"
---
# <a name="view-element-format"></a>View Element (Format) (Elemento View [Formatação])

Define uma vista que apresente um ou mais objetos do .NET. Não existe nenhum limite para o número de visualizações que podem ser definidos num arquivo de formatação.

Elemento de configuração do modo de exibição elemento (formato) ViewDefinitions elemento (formato) (formato)

## <a name="syntax"></a>Sintaxe

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `View` elemento. Tem de especificar um e apenas um dos elementos subordinados controle e tem de especificar o nome de exibição e os objetos que utilizam a vista. Definir controlos personalizados, como agrupar objetos e especificar se a vista está fora de banda são opcionais.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de controles para exibição (formato)](./controls-element-for-view-format.md)|Elemento opcional.<br /><br /> Define um conjunto de controlos que pode ser referenciado pelo nome, a partir do modo de exibição.|
|[Elemento de CustomControl (formato)](./customcontrol-element-for-groupby-format.md)|Elemento opcional.<br /><br /> Define um formato de controle personalizado para a vista.|
|[GroupBy elemento para a exibição (formato)](./groupby-element-for-view-format.md)|Elemento opcional.<br /><br /> Define a forma como os membros dos objetos .NET são agrupados.|
|[ListControl elemento (formato)](./listcontrol-element-format.md)|Elemento opcional.<br /><br /> Define um formato de lista para a vista.|
|[Elemento de nome para exibição (formato)](./name-element-for-view-format.md)|Elemento necessário.<br /><br /> Especifica o nome utilizado para referenciar o modo de exibição.|
|[Elemento de TableControl (formato)](./tablecontrol-element-format.md)|Elemento opcional.<br /><br /> Define um formato de tabela para a vista.|
|[Elemento de ViewSelectedBy para exibição (formato)](./viewselectedby-element-format.md)|Elemento necessário.<br /><br /> Define os objetos do .NET que esta vista apresenta.|
|[Elemento de WideControl (formato)](./widecontrol-element-format.md)|Elemento opcional.<br /><br /> Define uma vasta (valor único) formato de lista para a vista.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de ViewDefinitions (formato)](./viewdefinitions-element-format.md)|Define os modos de exibição utilizados para apresentar os objetos.|

## <a name="remarks"></a>Observações

Para obter mais informações sobre os componentes de diferentes modos de exibição e controles personalizados, consulte os seguintes tópicos:

- [Componentes de exibição de tabela](./creating-a-table-view.md)

- [Componentes de exibição de lista](./creating-a-list-view.md)

- [Componentes de vista alargada](./creating-a-wide-view.md)

- [Controles personalizados](./creating-custom-controls.md)

## <a name="example"></a>Exemplo

Este exemplo mostra uma `View` elemento que define uma vista de tabela para o [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Veja Também

[Elemento de ViewDefinitions (formato)](./viewdefinitions-element-format.md)

[Elemento de nome para exibição (formato)](./name-element-for-view-format.md)

[Elemento de ViewSelectedBy (formato)](./viewselectedby-element-format.md)

[Elemento de controles para exibição (formato)](./controls-element-for-view-format.md)

[GroupBy elemento para a exibição (formato)](./groupby-element-for-view-format.md)

[Elemento de TableControl (formato)](./tablecontrol-element-format.md)

[ListControl elemento (formato)](./listcontrol-element-format.md)

[Elemento de WideControl (formato)](./widecontrol-element-format.md)

[Elemento de CustomControl (formato)](./customcontrol-element-for-groupby-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
