---
title: Arquivos de formatação personalizada | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068305"
---
# <a name="custom-formatting-files"></a>Custom Formatting Files (Personalizar Ficheiros de Formatação)

O formato de apresentação para os objetos devolvidos por cmdlets, funções e scripts são definidos usando arquivos de formatação (format.ps1xml ficheiros). Vários desses arquivos são fornecidos pelo Windows PowerShell para definir o formato de exibição padrão para esses objetos devolvidos por cmdlets do Windows PowerShell. No entanto, também pode criar seus próprios arquivos de formatação personalizados para substituir os formatos de apresentação predefinido ou para definir a apresentação de objetos retornados por seus próprios comandos.

Windows PowerShell usa os dados nesses arquivos de formatação para determinar o que é apresentado e como os dados são formatados. Os dados apresentados podem incluir as propriedades de um objeto ou o valor de um bloco de script.  Blocos de script são usados se deseja exibir um valor que não está disponível diretamente a partir das propriedades de um objeto. Por exemplo, pode querer adicionar o valor de duas propriedades de um objeto e apresentar a soma como um conjunto separado de dados. Quando escreve o seu próprio formatação ficheiro, terá de definir *vistas* para os objetos que pretende apresentar. Pode definir uma vista única para cada objeto, pode definir uma única vista para múltiplos objetos ou pode definir vários modos de exibição para o mesmo objeto. Não existe nenhum limite para o número de modos de exibição que pode definir.

> [!IMPORTANT]
> Arquivos de formatação não determinar os elementos de um objeto que são devolvidos para o pipeline. Quando um objeto é devolvido para o pipeline, todos os membros desse objeto estão disponíveis.

## <a name="format-views"></a>Vistas de formato

Vistas de formatação podem apresentar os objetos no formato de tabela, um formato de lista, um formato de grande e um formato personalizado. Na maior parte, cada definição de formatação é descrita por um conjunto de marcas XML que descrevem um modo de exibição. Cada vista contém o nome da vista, os objetos que utilizam o modo de exibição e os elementos da exibição, como as informações de coluna e linha de uma vista de tabela.

As vistas seguintes estão disponíveis.

Vista de tabela lista as propriedades de um objeto ou um valor de bloco de script numa ou mais colunas. Cada coluna representa uma propriedade de objeto ou um valor de bloco de script. Pode definir uma vista de tabela que apresenta todas as propriedades de um objeto, um subconjunto das propriedades de um objeto ou uma combinação de propriedades e valores de bloco de script. Cada linha da tabela representa um objeto devolvido. Para obter mais informações sobre esta vista, consulte [vista de tabela](../format/creating-a-table-view.md).

Vista de lista lista as propriedades de um objeto ou um valor de bloco de script numa única coluna. Cada linha da lista apresenta uma etiqueta opcional ou o nome da propriedade seguido o valor do bloco de script ou de propriedade. Para obter mais informações sobre esta vista, consulte [vista de lista](../format/creating-a-list-view.md).

Vista alargada apresenta uma lista de uma única propriedade de um objeto ou um valor de bloco de script numa ou mais colunas. Não existe nenhuma etiqueta ou cabeçalho para esta vista. Para obter mais informações sobre esta vista, consulte [vista alargada](../format/creating-a-wide-view.md).

Exibição personalizada mostra uma vista personalizável de propriedades do objeto ou valores de bloco de script que não correspondem à estrutura rígida de exibições de tabela, vistas de lista ou vistas ampla. Pode definir uma vista personalizada de autónomo ou pode definir uma vista personalizada que é utilizada por outra vista, como uma vista de tabela ou vista de lista. Para obter mais informações sobre esta vista, consulte [vista personalizada](../format/creating-custom-controls.md).

## <a name="view-xml-elements"></a>Elementos XML do Vista

O exemplo seguinte mostra as marcas XML usadas para definir uma vista de tabela que contém duas colunas. O [ViewDefinitions](../format/viewdefinitions-element-format.md) elemento é o elemento de contêiner para todas as vistas definidas no ficheiro de formatação. O [vista](../format/view-element-format.md) elemento define a tabela específica, lista, vista ampla ou personalizada. Dentro de cada vista, o [Name](../format/name-element-for-view-format.md) elemento Especifica o nome da vista, o [ViewSelectedBy](../format/viewselectedby-element-format.md) elemento define os objetos que utilizam o modo de exibição e os elementos de controle diferentes (como o `TableControl` elemento) definir o formato da vista.

```xml
ViewDefinitions
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Veja Também

[Vista de tabela](../format/creating-a-table-view.md)

[Vista de lista](../format/creating-a-list-view.md)

[Vista alargada](../format/creating-a-wide-view.md)

[Vista personalizada](../format/creating-custom-controls.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
