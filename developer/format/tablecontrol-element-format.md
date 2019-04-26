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
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063833"
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

## <a name="attributes-and-elements"></a>Atributos e elementos

As secções seguintes descrevem os atributos e elemento pai de elementos filho do `TableControl` elemento. Tem de especificar as linhas da tabela. Todos os outros elementos filho são opcionais.

### <a name="attributes"></a>Atributos

Nenhum.

### <a name="child-elements"></a>Elementos subordinados

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento de dimensionamento automático para TableControl (formato)](./autosize-element-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Especifica se o tamanho da coluna e o número de colunas são ajustados com base no tamanho dos dados.|
|[Elemento de HideTableHeaders para TableControl (formato)](./hidetableheaders-element-format.md)|Elemento opcional.<br /><br /> Indica se o cabeçalho da tabela não é apresentado.|
|[Elemento de TableHeaders para TableControl (formato)](./tableheaders-element-format.md)|Elemento necessário.<br /><br /> Define as etiquetas, as larguras e o alinhamento dos dados para as colunas de vista de tabela.|
|[Elemento de TableRowEntries para TableControl (formato)](./tablerowentries-element-for-tablecontrol-format.md)|Elemento opcional.<br /><br /> Fornece definições de vista de tabela.|

### <a name="parent-elements"></a>Elementos principais

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

## <a name="see-also"></a>Veja Também

[Criar uma vista de tabela](./creating-a-table-view.md)

[Elemento de exibição (formato)](./view-element-format.md)

[Elemento de dimensionamento automático para TableControl (formato)](./autosize-element-for-tablecontrol-format.md)

[Elemento de HideTableHeaders (formato)](./hidetableheaders-element-format.md)

[Elemento de TableHeaders (formato)](./tableheaders-element-format.md)

[Elemento de TableRowEntries (formato)](./tablerowentries-element-for-tablecontrol-format.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
