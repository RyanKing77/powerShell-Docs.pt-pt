---
title: Descrição geral de ficheiros de formatação | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851920"
---
# <a name="formatting-file-overview"></a>Formatting File Overview (Ficheiros de Formatação: Descrição Geral)

O formato de apresentação para os objetos que são devolvidos pelo comandos (cmdlets, funções e scripts) são definidas usando arquivos de formatação (format.ps1xml ficheiros). Vários desses arquivos são fornecidos pelo PowerShell para definir o formato de apresentação para esses objetos devolvidos por comandos fornecidos pelo PowerShell, como o [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto devolvido pelo `Get-Process` cmdlet. No entanto, também pode criar seus próprios arquivos de formatação personalizados para substituir os formatos de exibição padrão ou pode escrever um arquivo personalizado de formatação para definir a apresentação de objetos retornados por seus próprios comandos.

> [!IMPORTANT]
> Arquivos de formatação não determinar os elementos de um objeto que são devolvidos para o pipeline. Quando um objeto é devolvido para o pipeline, todos os membros desse objeto estão disponíveis mesmo que alguns não são apresentados.

PowerShell utiliza os dados nesses arquivos de formatação para determinar o que é apresentado e como os dados apresentados são formatados. Os dados apresentados podem incluir as propriedades de um objeto ou o valor de um script. Os scripts são utilizados se deseja exibir um valor que não está disponível diretamente a partir das propriedades de um objeto, como o valor de duas propriedades de um objeto a adicionar e, em seguida, exibindo a soma como um conjunto de dados. Formatação dos dados apresentados é feito através da definição de vistas para os objetos que pretende apresentar. Pode definir uma vista única para cada objeto, pode definir uma única vista para múltiplos objetos ou pode definir vários modos de exibição para o mesmo objeto. Não existe nenhum limite para o número de modos de exibição que pode definir.

## <a name="common-features-of-formatting-files"></a>Recursos comuns de arquivos de formatação

Cada arquivo de formatação pode definir os seguintes componentes que podem ser partilhados entre todas as vistas definidas pelo ficheiro:

- Definição de configuração, por exemplo, se os dados apresentados nas linhas das tabelas serão apresentados na próxima linha se os dados são maiores do que a largura da coluna como padrão. Para obter mais informações sobre estas definições, consulte [definir definições de configuração comuns](./defining-common-configuration-features.md).

- Conjuntos de objetos que podem ser apresentados por qualquer um dos modos de exibição do arquivo formatação. Para obter mais informações sobre estes conjuntos de (denominados *conjuntos de seleção*), veja [definir conjuntos de objetos](./defining-selection-sets.md).

- Controles comuns que podem ser utilizados por todas as vistas do ficheiro de formatação. Controles dão-lhe um melhor controle sobre como os dados são apresentados. Para obter mais informações sobre controles, consulte [definição de controles de personalizado](./creating-custom-controls.md).

## <a name="formatting-views"></a>Vistas de formatação

Vistas de formatação podem apresentar os objetos num formato de tabela, o formato de lista, a grande formato e o formato personalizado. Na maior parte, cada definição de formatação é descrita por um conjunto de marcas XML que descrevem o modo de exibição. Cada vista contém o nome da vista, os objetos que utilizam o modo de exibição e os elementos da exibição, como as informações de coluna e linha de uma vista de tabela.

Listas de ver as propriedades de um objeto ou um valor de bloco de script numa ou mais colunas de tabela. Cada coluna representa uma única propriedade do objeto ou um valor de script. Pode definir uma vista de tabela que apresenta todas as propriedades de um objeto, um subconjunto das propriedades de um objeto ou uma combinação de propriedades e valores de script. Cada linha da tabela representa um objeto devolvido. Criar uma vista de tabela é muito semelhante a quando encaminhar um objeto para o `Format-Table` cmdlet. Para obter mais informações sobre esta vista, consulte [vista de tabela](./creating-a-table-view.md).

Lista de vista lista as propriedades de um objeto ou um valor de script numa única coluna. Cada linha da lista apresenta uma etiqueta opcional ou o nome da propriedade seguido o valor da propriedade ou script. Criar uma vista de lista é muito semelhante a canalização de um objeto para o `Format-List` cmdlet. Para obter mais informações sobre esta vista, consulte [vista de lista](./creating-a-list-view.md).

Vista alargada apresenta uma lista de uma única propriedade de um objeto ou um valor de script numa ou mais colunas. Não existe nenhuma etiqueta ou cabeçalho para esta vista. Criar uma vista alargada é muito semelhante a canalização de um objeto para o `Format-Wide` cmdlet. Para obter mais informações sobre esta vista, consulte [vista alargada](./creating-a-wide-view.md).

Exibição personalizada mostra uma vista personalizável de propriedades do objeto ou valores de script que não correspondem à estrutura rígida de exibições de tabela, vistas de lista ou vistas ampla. Pode definir uma vista personalizada autónoma ou pode definir uma vista personalizada que é utilizada por outra vista, como uma vista de tabela ou vista de lista. Criar uma vista personalizada é muito semelhante a canalização de um objeto para o `Format-Custom` cmdlet. Para obter mais informações sobre esta vista, consulte [vista personalizada](./creating-custom-controls.md).

## <a name="components-of-a-view"></a>Componentes de uma vista

Os exemplos XML seguintes mostram os componentes básicos de XML de um modo de exibição. Os elementos XML individuais variam dependendo do que a vista que pretende criar, mas os componentes básicos dos modos de exibição são todos iguais.

Para começar, cada vista tem um `Name` elemento que especifica um nome de utilizador amigável que é utilizado para referenciar o modo de exibição. um `ViewSelectedBy` elemento que define quais os objetos .NET são apresentados pela exibição, e um *controle* elemento que define o modo de exibição.

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

Dentro do elemento de controle, pode definir uma ou mais *entrada* elementos. Se utilizar várias definições, tem de especificar quais os objetos .NET utilizam cada definição. Normalmente, apenas uma entrada, com apenas uma definição, é necessário para cada controle.

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

Dentro de cada elemento de entrada de uma vista, especifique a *item* elementos que definem as propriedades de .NET ou scripts que são apresentados por essa visão.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

Conforme mostrado nos exemplos anteriores, o ficheiro de formatação pode conter várias Exibições, uma exibição pode conter várias definições e cada definição pode conter vários itens.

## <a name="example-of-a-table-view"></a>Exemplo de uma vista de tabela

O exemplo seguinte mostra as marcas XML usadas para definir uma vista de tabela que contém duas colunas. O [ViewDefinitions](./viewdefinitions-element-format.md) elemento é o elemento de contêiner para todas as vistas definidas no ficheiro de formatação. O [vista](./view-element-format.md) elemento define a tabela específica, lista, vista ampla ou personalizada. Dentro de cada [View](./view-element-format.md) elemento, o [nome](./name-element-for-view-format.md) elemento Especifica o nome da vista, o [ViewSelectedBy](./viewselectedby-element-format.md) elemento define os objetos que utilizam o modo de exibição e os diferentes controlar elementos (como o `TableControl` elemento mostrado no exemplo a seguir) definem o tipo da vista.

```xml
<ViewDefinitions>
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

## <a name="see-also"></a>Consulte Também

[Criar uma vista de lista](./creating-a-list-view.md)

[Criar uma vista de tabela](./creating-a-table-view.md)

[Criar uma vista alargada](./creating-a-wide-view.md)

[Criação de controles personalizados](./creating-custom-controls.md)

[Escrever uma formatação de PowerShell e tipos de ficheiro](./writing-a-powershell-formatting-file.md)
