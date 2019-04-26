---
title: Criar uma vista alargada | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066724"
---
# <a name="creating-a-wide-view"></a>Creating a Wide View (Criar uma Vista Ampla)

Uma vista alargada apresenta um valor único para cada objeto que é apresentado. O valor apresentado pode ser o valor de uma propriedade de objeto do .NET ou o valor de um script. Por predefinição, não existe o rótulo ou cabeçalho para esta vista.

## <a name="a-wide-view-display"></a>Uma vista alargada de apresentação

O exemplo seguinte mostra como o Windows PowerShell apresenta os [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto devolvido pela [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet quando o respetivo resultado é enviada por pipe para o [ Em todo o formato](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet. (Por predefinição, o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet devolve uma vista de tabela.) Neste exemplo, as duas colunas são usadas para exibir o nome do processo para cada objeto devolvido. O nome da propriedade do objeto não for apresentado, apenas o valor da propriedade.

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a>Definir a vista alargada

O XML a seguir mostra o esquema de vista alargada para o [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

Os seguintes elementos XML são utilizados para definir uma vista alargada:

- O [vista](./view-element-format.md) elemento é o elemento principal da vista ampla. (Este é o mesmo elemento principal para a tabela, lista e modos de exibição do controle personalizado).

- O [nome](./name-element-for-view-format.md) elemento Especifica o nome da vista. Este elemento é necessário para todas as vistas.

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define os objetos que utilizam o modo de exibição. Este elemento é necessário.

- O [GroupBy](./groupby-element-for-view-format.md) elemento define quando é apresentado um novo grupo de objetos. Um novo grupo é iniciado sempre que o valor de uma propriedade específica ou um script é alterado. Este elemento é opcional.

- O [controles](./controls-element-for-view-format.md) elementos define os controles personalizados que são definidos pela vista ampla. Controles dão-lhe uma forma para especificar a forma como os dados são apresentados. Este elemento é opcional. Uma vista pode definir seus próprios controles personalizados, ou ele pode usar controles comuns que podem ser utilizados por qualquer vista no ficheiro de formatação. Para obter mais informações sobre controles personalizados, consulte [criar controles personalizados](./creating-custom-controls.md).

- O [WideControl](./widecontrol-element-format.md) elemento e seus elementos filho definem o que é apresentado na vista. No exemplo anterior, a vista foi projetada para apresentar os [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) propriedade.

Para obter um exemplo de um ficheiro de formatação completado que define uma vista alargada simple, consulte [vista alargada (básico)](./wide-view-basic.md).

## <a name="providing-definitions-for-your-wide-view"></a>Fornecer definições para a sua vista alargada

Vistas ampla podem fornecer uma ou mais definições utilizando os elementos filho do [WideControl](./widecontrol-element-format.md) elemento. Normalmente, uma vista irá ter apenas uma definição. No exemplo a seguir, o modo de exibição fornece uma única definição que exibe o valor do [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) propriedade. Uma vista alargada pode apresentar o valor de uma propriedade ou o valor de um script (não mostrado no exemplo).

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

Os seguintes elementos XML podem ser utilizados para fornecer definições para uma visão ampla:

- O [WideControl](./widecontrol-element-format.md) elemento e seus elementos filho definem o que é apresentado na vista.

- O [AutoSize](./autosize-element-for-widecontrol-format.md) elemento Especifica se o tamanho da coluna e o número de colunas são ajustados com base no tamanho dos dados. Este elemento é opcional.

- O [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) elemento Especifica o número de colunas apresentadas na vista alargada. Este elemento é opcional.

- O [WideEntries](./wideentries-element-for-widecontrol-format.md) elemento fornece as definições da vista. Na maioria dos casos, uma exibição terão apenas uma única definição. Este elemento é necessário.

- O [WideEntry](./wideentry-element-for-widecontrol-format.md) elemento fornece uma definição da vista. Pelo menos um [WideEntry](./wideentry-element-for-widecontrol-format.md) é necessária; no entanto, não há nenhum limite máximo para o número de elementos que podem ser adicionados. Na maioria dos casos, uma exibição terão apenas uma única definição.

- O [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento Especifica os objetos que são apresentados por uma definição específica. Este elemento é opcional e é necessário apenas quando define várias [WideEntry](./wideentry-element-for-widecontrol-format.md) elementos que apresentam diferentes objetos.

- O [WideItem](./wideitem-element-for-widecontrol-format.md) elemento Especifica os dados que são apresentados pela vista. Ao contrário de outros tipos de vistas, um controle amplo pode apresentar apenas um item.

- O [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elemento Especifica a propriedade cujo valor é apresentado pela vista. Tem de especificar uma propriedade ou um script, mas não é possível especificar ambos.

- O [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento Especifica o script cujo valor é apresentado pela vista. Tem de especificar um script ou uma propriedade, mas não é possível especificar ambos.

- O [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elemento Especifica um padrão que é utilizado para apresentar os dados. Este elemento é opcional.

Para obter um exemplo de um ficheiro de formatação completado que define uma definição de vista alargada, consulte [vista alargada (básico)](./wide-view-basic.md).

## <a name="defining-the-objects-that-use-the-wide-view"></a>Definir os objetos que usam a vista alargada

Existem duas formas de definir quais os objetos .NET utilizam a vista alargada. Pode utilizar o [ViewSelectedBy](./viewselectedby-element-format.md) elemento para definir os objetos que podem ser apresentados por todas as definições de vista ou pode usar o [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento para definir quais os objetos são apresentados por um obter definição específica da vista. Na maioria dos casos, um view tem apenas uma definição, para objetos, normalmente, são definidos pelos [ViewSelectedBy](./viewselectedby-element-format.md) elemento.

O exemplo seguinte mostra como definir os objetos que são apresentados, a vista alargada utilizando o [ViewSelectedBy](./viewselectedby-element-format.md) e [TypeName](./typename-element-for-viewselectedby-format.md) elementos. Não há limite para o número de [TypeName](./typename-element-for-viewselectedby-format.md) elementos que pode especificar, e a ordem não é significativa.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Os seguintes elementos XML podem ser utilizados para especificar os objetos que são utilizados pela wide vista:

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais os objetos são apresentados pela exibição ampla.

- O [TypeName](./typename-element-for-viewselectedby-format.md) elemento especifica do .NET que é apresentada pela vista. O nome do tipo .NET completamente qualificado é necessário. Tem de especificar pelo menos um tipo ou seleção definido para a vista, mas existe um número máximo de elementos que podem ser especificados.

Para obter um exemplo de um ficheiro de formatação completado, consulte [vista alargada (básico)](./wide-view-basic.md).

O exemplo seguinte utiliza a [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementos. Utilize conjuntos de seleção em que tem um conjunto de objetos que são apresentados com várias Exibições, como quando define uma vista alargada e uma vista de tabela para os mesmos objetos relacionados. Para obter mais informações sobre como criar um conjunto de seleção, consulte [definir conjuntos de seleção](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Os seguintes elementos XML podem ser utilizados para especificar os objetos que são utilizados pela wide vista:

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais os objetos são apresentados pela exibição ampla.

- O [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento Especifica um conjunto de objetos que podem ser apresentados pela exibição. Tem de especificar, pelo menos, um conjunto de seleção ou tipo para o modo de exibição, mas existe um número máximo de elementos que podem ser especificados.

O exemplo seguinte mostra como definir os objetos apresentados por uma definição específica da vista alargada usando o [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento. Usando esse elemento, pode especificar o nome do tipo .NET de objeto, um conjunto de seleção de objetos ou uma condição de seleção que especifica quando é utilizada a definição. Para obter mais informações sobre como criar uma seleção condições, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

Os seguintes elementos XML podem ser utilizados para especificar os objetos que são utilizados por uma definição específica da vista alargada:

- O [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento define quais os objetos são apresentados pela definição do.

- O [TypeName](./typename-element-for-viewselectedby-format.md) elemento Especifica o que é apresentado pela definição do .NET. Ao utilizar este elemento o nome do tipo .NET completamente qualificado é necessário. Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para a definição, mas existe um número máximo de elementos que podem ser especificados.

- O [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento (não mostrado) Especifica um conjunto de objetos que podem ser apresentados por esta definição. Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para a definição, mas existe um número máximo de elementos que podem ser especificados.

- O [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) elemento (não mostrado) Especifica uma condição que tem de existir para esta definição a utilizar. Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para a definição, mas existe um número máximo de elementos que podem ser especificados. Para obter mais informações sobre como definir condições de seleção, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>Exibição de grupos de objetos numa vista alargada

Pode separar os objetos que são apresentados pela exibição ampla em grupos. Isso não significa que definir um grupo, apenas se o Windows PowerShell é iniciado um novo grupo sempre que o valor de uma propriedade específica ou um script é alterado. No exemplo a seguir, um novo grupo é iniciado sempre que o valor do [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) alterações de propriedade.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Os seguintes elementos XML são utilizados para definir quando um grupo é iniciado:

- O [GroupBy](./groupby-element-for-view-format.md) elemento define a propriedade ou um script que inicia o novo grupo e define como o grupo é exibido.

- O [PropertyName](./propertyname-element-for-groupby-format.md) elemento Especifica a propriedade que inicia um novo grupo sempre que seu valor é alterado. Tem de especificar uma propriedade ou um script para iniciar o grupo, mas não é possível especificar ambos.

- O [ScriptBlock](./scriptblock-element-for-groupby-format.md) elemento Especifica o script que inicia um novo grupo sempre que seu valor é alterado. Tem de especificar um script ou uma propriedade para iniciar o grupo, mas não é possível especificar ambos.

- O [etiqueta](./label-element-for-groupby-format.md) elemento define uma etiqueta que é apresentada no início de cada grupo. Além do texto especificado por este elemento, o Windows PowerShell apresenta o valor que acionou o novo grupo e adiciona uma linha em branco antes e depois a etiqueta. Este elemento é opcional.

- O [CustomControl](./customcontrol-element-for-groupby-format.md) elemento define um controle que é utilizado para apresentar os dados. Este elemento é opcional.

- O [CustomControlName](./customcontrolname-element-for-groupby-format.md) elemento Especifica uma comum ou ver o controle que é utilizado para apresentar os dados. Este elemento é opcional.

Para obter um exemplo de um ficheiro de formatação completado que define os grupos, veja [vista alargada (GroupBy)](./wide-view-groupby.md).

## <a name="using-format-strings"></a>Usar cadeias de caracteres de formato

Cadeias de caracteres de formatação podem ser adicionadas a uma vista alargada para definir melhor a forma como os dados são apresentados. O exemplo seguinte mostra como definir uma cadeia de caracteres de formatação para o valor do `StartTime` propriedade.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

Os seguintes elementos XML podem ser utilizados para especificar um padrão de formato:

- O [WideItem](./wideitem-element-for-widecontrol-format.md) elemento Especifica os dados que são apresentados pela vista.

- O [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elemento Especifica a propriedade cujo valor é apresentado pela vista. Tem de especificar uma propriedade ou um script, mas não é possível especificar ambos.

- O [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elemento Especifica um padrão de formato que define como o valor de propriedade ou um script é apresentado na vista

- O [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento (não mostrado) Especifica o script cujo valor é apresentado pela vista. Tem de especificar um script ou uma propriedade, mas não é possível especificar ambos.

No exemplo a seguir, o `ToString` método é chamado para formatar o valor do script. Scripts podem chamar qualquer método de um objeto. Por conseguinte, se um objeto tem um método, como `ToString`, que tem parâmetros de formatação, o script pode chamar esse método para formatar o valor de saída do script.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

O seguinte elemento XML pode ser utilizados para chamar o `ToString` método:

- O [WideItem](./wideitem-element-for-widecontrol-format.md) elemento Especifica os dados que são apresentados pela vista.

- O [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento (não mostrado) Especifica o script cujo valor é apresentado pela vista. Tem de especificar um script ou uma propriedade, mas não é possível especificar ambos.

## <a name="see-also"></a>Veja Também

[Vista alargada (básico)](./wide-view-basic.md)

[Vista alargada (GroupBy)](./wide-view-groupby.md)

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
