---
title: O elemento de TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: dd48e82452e83f93e2e005c9db53bbc51d8b2eb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848854"
---
# <a name="tablecontrol-element-format"></a>TableControl Element (Format) (Elemento TableControl [Formatação])

Define um formato de tabela para obter uma exibição.

O elemento de ViewDefinitions (formato) vista elemento (formato) TableControl elemento (formato)

## <a name="syntax"></a>Sintaxe

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a>Atributos e Elementos

As secções seguintes descrevem os atributos e elemento pai de elementos filho do `TableControl` elemento. Tem de especificar as linhas da tabela. Todos os outros elementos filho são opcionais.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos Subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de dimensionamento automático para TableControl (formato)](./autosize-element-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica se o tamanho da coluna e o número de colunas são ajustados com base no tamanho dos dados.|
|[Elemento de HideTableHeaders para TableControl (formato)](./hidetableheaders-element-format.md)|Elemento opcional.<br /><br /> Indica se o cabeçalho da tabela não é apresentado.|
|[Elemento de TableHeaders para TableControl (formato)](./tableheaders-element-format.md)|Elemento necessário.<br /><br /> Define as etiquetas, as larguras e o alinhamento dos dados para as colunas de vista de tabela.|
|[Elemento de TableRowEntries para TableCotrol (formato)](./tablerowentries-element-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Fornece definições de vista de tabela.|

### <a name="parent-elements"></a>Elementos Principais

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de exibição (formato)](./view-element-format.md)|Define uma vista que é utilizada para apresentar os membros de um ou mais objetos.|

## <a name="remarks"></a>Observações

Para obter mais informações sobre os componentes de uma vista de tabela, consulte [criar uma vista de tabela](./creating-a-table-view.md).

## <a name="example"></a>Exemplo

Este exemplo mostra uma `TableControl` elemento que é utilizado para apresentar as propriedades do [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a>Consulte Também

[Criar uma vista de tabela](./creating-a-table-view.md)

[Elemento de exibição (formato)](./view-element-format.md)

[Elemento de dimensionamento automático para TableControl (formato)](./autosize-element-for-tablecontrol-format.md)

[Elemento de HideTableHeaders (formato)](./hidetableheaders-element-format.md)

[Elemento de TableHeaders (formato)](./tableheaders-element-format.md)

[Elemento de TableRowEntries (formato)](./tablerowentries-element-for-tablecontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
