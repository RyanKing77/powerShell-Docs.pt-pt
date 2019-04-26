---
title: O elemento de ViewSelectedBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083829"
---
# <a name="viewselectedby-element-format"></a>ViewSelectedBy Element (Format) (Elemento ViewSelectedBy [Formatação])

Define os objetos do .NET que são apresentados pela exibição. Cada vista tem de especificar pelo menos um objeto .NET.

O elemento de ViewDefinitions (formato) vista elemento (formato) ViewSelectedBy elemento (formato)

## <a name="syntax"></a>Sintaxe

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `ViewSelectedBy` elemento. Este elemento tem de conter, pelo menos, um `TypeName` ou `SelectionSetName` elemento subordinado. Não há limite para o número de elementos filho que podem ser especificados nem é sua ordem significativo.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de TypeName para ViewSelectedBy (formato)](./typename-element-for-viewselectedby-format.md)|Elemento opcional.<br /><br /> Especifica um objeto .NET que é apresentado pela vista.|
|[Elemento de SelectionSetName para ViewSelectedBy (formato)](./selectionsetname-element-for-viewselectedby-format.md)|Elemento opcional.<br /><br /> Especifica um conjunto de objetos do .NET que são apresentados pela exibição.|

### <a name="parent-elements"></a>Elementos principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de exibição (formato)](./view-element-format.md)|Define uma vista que apresente um ou mais objetos do .NET.|

## <a name="remarks"></a>Observações

Para obter mais informações sobre como este elemento é usado em exibições diferentes, consulte [componentes de exibição de tabela](./creating-a-table-view.md), [componentes de exibição de lista](./creating-a-list-view.md), [ampla componentes de exibição](./creating-a-wide-view.md)e [Componentes de controle personalizado](./creating-custom-controls.md).

O `SelectionSetName` elemento é usado quando o arquivo de formatação define um conjunto de objetos que são apresentadas por várias exibições. Para obter mais informações sobre como os conjuntos de seleção são definidos e referenciados, consulte [definir conjuntos de objetos](./defining-selection-sets.md).

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como especificar a [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto para uma vista de lista. O mesmo esquema é usado para exibições de tabela, ampla e personalizadas.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Veja Também

[Criar uma vista de lista](./creating-a-list-view.md)

[Criar uma vista de tabela](./creating-a-table-view.md)

[Criar uma vista alargada](./creating-a-wide-view.md)

[Criação de controles personalizados](./creating-custom-controls.md)

[Definir conjuntos de seleção](./defining-selection-sets.md)

[Elemento de SelectionSetName para ViewSelectedBy (formato)](./selectionsetname-element-for-viewselectedby-format.md)

[Elemento de TypeName (formato)](./typename-element-for-viewselectedby-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
