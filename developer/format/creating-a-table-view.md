---
title: Criar uma vista de tabela | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066843"
---
# <a name="creating-a-table-view"></a>Creating a Table View (Criar uma Vista de Tabela)

Uma vista de tabela apresenta os dados numa ou mais colunas. Cada linha na tabela representa um objeto .NET, e cada coluna da tabela representa uma propriedade de objeto ou um valor de script. Pode definir uma vista de tabela que apresenta todas as propriedades de um objeto ou um subconjunto das propriedades de um objeto.

## <a name="a-table-view-display"></a>Uma exibição de exibição de tabela

O exemplo seguinte mostra como o Windows PowerShell apresenta os [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto devolvido pela [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. Para este objeto, o Windows PowerShell definiu uma vista de tabela que apresenta os `Status` propriedade, o `Name` propriedade (esta propriedade é uma propriedade de alias para o `ServiceName` propriedade) e o `DisplayName` propriedade. Cada linha na tabela representa um objeto devolvido pelo cmdlet.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>Definir a exibição de tabela

O XML a seguir mostra o esquema de vista de tabela para exibir o [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objeto. Tem de especificar cada propriedade que que pretende apresentar na vista de tabela.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

Os seguintes elementos XML são utilizados para definir uma vista de lista:

- O [vista](./view-element-format.md) elemento é o elemento principal da vista de tabela. (Este é o mesmo elemento principal para a lista, vistas de controlo de largura e personalizado.)

- O [nome](./name-element-for-view-format.md) elemento Especifica o nome da vista. Este elemento é necessário para todas as vistas.

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define os objetos que utilizam o modo de exibição. Este elemento é necessário.

- O [GroupBy](./groupby-element-for-view-format.md) elemento (não mostrado neste exemplo) define quando é apresentado um novo grupo de objetos. Um novo grupo é iniciado sempre que o valor de uma propriedade específica ou um script é alterado. Este elemento é opcional.

- O [controles](./controls-element-for-view-format.md) elemento (não mostrado neste exemplo) define os controles personalizados definidos pela exibição de tabela. Controles dão-lhe uma forma para especificar a forma como os dados são apresentados. Este elemento é opcional. Uma vista pode definir seus próprios controles personalizados, ou ele pode usar controles comuns que podem ser utilizados por qualquer vista no ficheiro de formatação. Para obter mais informações sobre controles personalizados, consulte [criar controles personalizados](./creating-custom-controls.md).

- O [HideTableHeaders](./hidetableheaders-element-format.md) elemento (não mostrar neste exemplo) Especifica que a tabela não apresentará quaisquer etiquetas na parte superior da tabela. Este elemento é opcional.

- O [TableControl](./tablecontrol-element-format.md) elemento que define as informações de cabeçalho e de linha da tabela. Assim como todos os outros modos de exibição, uma vista de tabela pode apresentar os valores das propriedades do objeto ou valores gerados por scripts.

## <a name="defining-column-headers"></a>Definir cabeçalhos de coluna

1. O [TableHeaders](./tableheaders-element-format.md) elemento e seus elementos filho definem o que é apresentado na parte superior da tabela.

2. O [TableColumnHeader](./tablecolumnheader-element-format.md) elemento define o que é apresentado na parte superior de uma coluna da tabela. Especifique esses elementos na ordem em que pretende que os cabeçalhos apresentados.

   Não há limite para o número destes elemento que pode utilizar, mas o número de [TableColumnHeader](./tablecolumnheader-element-format.md) elementos na vista de tabela devem ser igual ao número de [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elementos que utilizar.

3. O [etiqueta](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento Especifica o texto que é apresentado. Este elemento é opcional.

4. O [largura](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento Especifica a largura (em carateres) da coluna. Este elemento é opcional.

5. O [alinhamento](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento Especifica como a etiqueta é apresentada. A etiqueta pode ser alinhada à esquerda, à direita, ou centralizada. Este elemento é opcional.

## <a name="defining-the-table-rows"></a>Definindo as linhas de tabela

Exibições de tabela podem fornecer uma ou mais definições que especifique os dados que são apresentados nas linhas da tabela, utilizando os elementos filho do [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elemento. Tenha em atenção que pode especificar várias definições para as linhas da tabela, mas os cabeçalhos das linhas permanece o mesmo, independentemente da definição de linha que é utilizada. Normalmente, uma tabela irá ter apenas uma definição.

No exemplo a seguir, o modo de exibição fornece uma única definição que exibe os valores de várias propriedades do [Diagnostics? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objeto. Uma vista de tabela pode apresentar o valor de uma propriedade ou o valor de um script (não mostrado no exemplo) em suas linhas.

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

Os seguintes elementos XML podem ser utilizados para fornecer definições para uma linha:

- O [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elemento e seus elementos filho definem o que é apresentado nas linhas da tabela.

- O [TableRowEntry](./listentry-element-for-listcontrol-format.md) elemento fornece uma definição da linha. Pelo menos um [TableRowEntry](./listentry-element-for-listcontrol-format.md) é necessária; no entanto, não há nenhum limite máximo para o número de elementos que podem ser adicionados. Na maioria dos casos, uma exibição terão apenas uma única definição.

- O [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento Especifica os objetos que são apresentados por uma definição específica. Este elemento é opcional e é necessário apenas quando define várias [TableRowEntry](./listentry-element-for-listcontrol-format.md) elementos que apresentam diferentes objetos.

- O [encapsular](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) elemento Especifica que o texto que excede a largura da coluna é apresentado na próxima linha. Por predefinição, o texto que excede a largura da coluna é truncado.

- O [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) elemento define as propriedades ou scripts cujos valores são apresentados na linha.

- O [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define a propriedade ou um script cujo valor é apresentado na coluna da linha. R [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento é necessário para cada coluna da linha. A primeira entrada é apresentada na primeira coluna, a segunda entrada na segunda coluna e assim por diante.

- O [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica a propriedade cujo valor é apresentado na linha. Tem de especificar uma propriedade ou um script, mas não é possível especificar ambos.

- O [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica o script cujo valor é apresentado na linha. Tem de especificar um script ou uma propriedade, mas não é possível especificar ambos.

- O [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elemento Especifica um padrão de formato que define como o valor de propriedade ou um script é apresentado. Este elemento é opcional.

- O [alinhamento](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica como o valor da propriedade ou script é apresentado. O valor pode ser alinhado à esquerda, à direita, ou centralizado. Este elemento é opcional.

## <a name="defining-the-objects-that-use-the-table-view"></a>Definir os objetos que utilizam a vista de tabela

Existem duas formas de definir quais os objetos .NET, utilize a vista de tabela. Pode utilizar o [ViewSelectedBy](./viewselectedby-element-format.md) elemento para definir os objetos que podem ser apresentados por todas as definições de vista ou pode usar o [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento para definir quais os objetos são apresentados por um obter definição específica da vista. Na maioria dos casos, um view tem apenas uma definição, para objetos, normalmente, são definidos pelos [ViewSelectedBy](./viewselectedby-element-format.md) elemento.

O exemplo seguinte mostra como definir os objetos que são apresentados pelo modo de exibição de tabela com o [ViewSelectedBy](./viewselectedby-element-format.md) e [TypeName](./typename-element-for-viewselectedby-format.md) elementos. Não há limite para o número de [TypeName](./typename-element-for-viewselectedby-format.md) elementos que pode especificar, e a ordem não é significativa.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Os seguintes elementos XML podem ser utilizados para especificar os objetos que são utilizados pela exibição de tabela:

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais os objetos são apresentados pela vista de lista.

- O [TypeName](./typename-element-for-viewselectedby-format.md) elemento Especifica o objeto de .NET que é apresentado pela vista. O nome do tipo .NET completamente qualificado é necessário. Tem de especificar pelo menos um tipo ou seleção definido para a vista, mas existe um número máximo de elementos que podem ser especificados.

O exemplo seguinte utiliza a [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementos. Utilize conjuntos de seleção em que tem um conjunto de objetos que são apresentados com várias Exibições, como quando define uma vista de lista e uma vista de tabela para os mesmos objetos relacionados. Para obter mais informações sobre como criar um conjunto de seleção, consulte [definir conjuntos de seleção](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Os seguintes elementos XML podem ser utilizados para especificar os objetos que são utilizados pela exibição de lista:

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais os objetos são apresentados pela vista de lista.

- O [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento Especifica um conjunto de objetos que podem ser apresentados pela exibição. Tem de especificar, pelo menos, um conjunto de seleção ou tipo para o modo de exibição, mas existe um número máximo de elementos que podem ser especificados.

O exemplo seguinte mostra como definir os objetos apresentados por uma definição específica do modo de exibição de tabela com o [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento. Usando esse elemento, pode especificar o nome do tipo .NET de objeto, um conjunto de seleção de objetos ou uma condição de seleção que especifica quando é utilizada a definição. Para obter mais informações sobre como criar uma seleção condições, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).

> [!NOTE]
> Ao criar várias definições de vista de tabela que não é possível especificar cabeçalhos de coluna diferente. Pode especificar apenas o que é apresentado nas linhas da tabela, como os objetos que são apresentados.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

Os seguintes elementos XML podem ser utilizados para especificar os objetos que são utilizados por uma definição específica de exibição de lista:

- O [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento define quais os objetos são apresentados pela definição do.

- O [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elemento Especifica o objeto de .NET que é apresentado pela definição. Ao usar esse elemento, o nome do tipo .NET completamente qualificado é necessário. Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para a definição, mas existe um número máximo de elementos que podem ser especificados.

- O [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) elemento (não mostrado) Especifica um conjunto de objetos que podem ser apresentados por esta definição. Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para a definição, mas existe um número máximo de elementos que podem ser especificados.

- O [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) elemento (não mostrado) Especifica uma condição que tem de existir para esta definição a utilizar. Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para a definição, mas existe um número máximo de elementos que podem ser especificados. Para obter mais informações sobre como definir condições de seleção, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).

## <a name="using-format-strings"></a>Usar cadeias de caracteres de formato

Cadeias de caracteres de formatação podem ser adicionadas a uma vista para definir melhor a forma como os dados são apresentados. O exemplo seguinte mostra como definir uma cadeia de caracteres de formatação para o valor do `StartTime` propriedade.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

Os seguintes elementos XML podem ser utilizados para especificar um padrão de formato:

- O [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define a propriedade ou um script cujo valor é apresentado na coluna da linha. R [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento é necessário para cada coluna da linha. A primeira entrada é apresentada na primeira coluna, a segunda entrada na segunda coluna e assim por diante.

- O [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica a propriedade cujo valor é apresentado na linha. Tem de especificar uma propriedade ou um script, mas não é possível especificar ambos.

- O [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elemento Especifica um padrão de formato que define como o valor de propriedade ou um script é apresentado.

No exemplo a seguir, o `ToString` método é chamado para formatar o valor do script. Scripts podem chamar qualquer método de um objeto. Por conseguinte, se um objeto tem um método, como `ToString`, que tem parâmetros de formatação, o script pode chamar esse método para formatar o valor de saída do script.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

O seguinte elemento XML pode ser utilizados para chamar o `ToString` método:

- O [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define a propriedade ou um script cujo valor é apresentado na coluna da linha. R [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento é necessário para cada coluna da linha. A primeira entrada é apresentada na primeira coluna, a segunda entrada na segunda coluna e assim por diante.

- O [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica o script cujo valor é apresentado na linha. Tem de especificar um script ou uma propriedade, mas não é possível especificar ambos.

## <a name="see-also"></a>Veja Também

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
