---
title: Elemento de TableColumnItem para TableColumnItems para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 159f943f6bfb33c5403b5714380631351523789f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056996"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>TableColumnItem Element for TableColumnItems for TableControl (Format) (Elemento TableColumnItem para TableColumnItems para TableControl [Formatação])

Define a propriedade ou um script cujo valor é apresentado na coluna da linha.

O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento de configuração para o elemento de TableRowEntry TableControl (formato) para TableRowEntries para TableControl (formato) Elemento de TableColumnItems para TableControlEntry para o elemento de TableColumnItem TableControl (formato) para TableColumnItems para TableControl (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `TableColumnItem` elemento.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de alinhamento para TableColumnItem para TableControl (formato)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Define como os dados numa coluna da linha são exibidos.|
|[Elemento de FormatString para TableColumnItem para TableControl (formato)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Especifica um padrão de formato utilizada para formatar os dados na coluna da linha.|
|[Elemento de PropertyName para TableColumnItem para TableControl (formato)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica o nome da propriedade cujo valor é apresentado.|
|[Elemento de ScriptBlock para TableColumnItem para TableControl (formato)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica o script cujo valor é apresentado na coluna de uma linha.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de TableColumnItems para TableControlEntry para TableControl (formato)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Define as propriedades ou scripts cujos valores são apresentados na linha.|

## <a name="remarks"></a>Observações

Pode especificar uma propriedade de um objeto ou um script em cada coluna da linha. Se nenhum elemento filho forem especificado, o item é um espaço reservado e não serem apresentados dados.

Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra uma `TableColumnItem` elemento que exibe o valor da `Status` propriedade da [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Veja Também

[Criar uma vista de tabela](./creating-a-table-view.md)

[Elemento de alinhamento para TableColumnItem para TableControl (formato)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Elemento de TableColumnItems (formato)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Elemento de FormatString para TableColumnItem para TableControl (formato)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Elemento de PropertyName para TableColumnItem para TableControl (formato)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Elemento de ScriptBlock para TableColumnItem para TableControl (formato)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
