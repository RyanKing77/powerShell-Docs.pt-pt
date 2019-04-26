---
title: Criar uma vista de lista | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066860"
---
# <a name="creating-a-list-view"></a>Creating a List View (Criar uma Vista de Lista)

Uma vista de lista apresenta dados numa única coluna (por ordem sequencial). Os dados apresentados na lista podem ser o valor de uma propriedade .NET ou o valor de um script.

## <a name="a-list-view-display"></a>Uma exibição de vista de lista

O resultado seguinte mostra como o Windows PowerShell apresenta as propriedades de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos que são devolvidos pela [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. Neste exemplo, três objetos foram devolvidos, com cada objeto separado do objeto anterior por uma linha em branco.

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a>Definir o modo de exibição de lista

O XML a seguir mostra o esquema de vista de lista para exibir várias propriedades do [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objeto. Tem de especificar cada propriedade que que pretende apresentar na vista de lista.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

Os seguintes elementos XML são utilizados para definir uma vista de lista:

- O [vista](./view-element-format.md) elemento é o elemento principal da vista de lista. (Este é o mesmo elemento principal para a tabela, vistas de controlo de largura e personalizado.)

- O [nome](./name-element-for-view-format.md) elemento Especifica o nome da vista. Este elemento é necessário para todas as vistas.

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define os objetos que utilizam o modo de exibição. Este elemento é necessário.

- O [GroupBy](./groupby-element-for-view-format.md) elemento define quando é apresentado um novo grupo de objetos. Um novo grupo é iniciado sempre que o valor de uma propriedade específica ou um script é alterado. Este elemento é opcional.

- O [controles](./controls-element-for-view-format.md) elemento define os controles personalizados definidos pela vista de lista. Controles dão-lhe uma forma para especificar a forma como os dados são apresentados. Este elemento é opcional. Uma vista pode definir seus próprios controles personalizados, ou ele pode usar controles comuns que podem ser utilizados por qualquer vista no ficheiro de formatação. Para obter mais informações sobre controles personalizados, consulte [criar controles personalizados](./creating-custom-controls.md).

- O [ListControl](./listcontrol-element-format.md) elemento define o que é apresentado na vista e como é formatado. Assim como todos os outros modos de exibição, uma vista de lista pode apresentar os valores das propriedades do objeto ou valores gerados por script.

Para obter um exemplo de um ficheiro de formatação completado que define uma vista de lista simples, consulte [vista de lista (básico)](./list-view-basic.md).

## <a name="providing-definitions-for-your-list-view"></a>Fornecer definições para a vista de lista

Vistas de lista podem fornecer uma ou mais definições utilizando os elementos filho do [ListControl](./listcontrol-element-format.md) elemento. Normalmente, uma vista irá ter apenas uma definição. No exemplo a seguir, o modo de exibição fornece uma única definição que apresenta várias propriedades do [Diagnostics? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objeto. Uma vista de lista pode apresentar o valor de uma propriedade ou o valor de um script (não mostrado no exemplo).

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

Os seguintes elementos XML podem ser utilizados para fornecer definições para uma vista de lista:

- O [ListControl](./listcontrol-element-format.md) elemento e seus elementos filho definem o que é apresentado na vista.

- O [ListEntries](./listentries-element-for-listcontrol-format.md) elemento fornece as definições da vista. Na maioria dos casos, uma exibição terão apenas uma única definição. Este elemento é necessário.

- O [ListEntry](./listentry-element-for-listcontrol-format.md) elemento fornece uma definição da vista. Pelo menos um [ListEntry](./listentry-element-for-listcontrol-format.md) é necessária; no entanto, não há nenhum limite máximo para o número de elementos que podem ser adicionados. Na maioria dos casos, uma exibição terão apenas uma única definição.

- O [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento Especifica os objetos que são apresentados por uma definição específica. Este elemento é opcional e é necessário apenas quando define várias [ListEntry](./listentry-element-for-listcontrol-format.md) elementos que apresentam diferentes objetos.

- O [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) elemento Especifica as propriedades e os scripts cujos valores são apresentados nas linhas da exibição de lista.

- O [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) elemento Especifica uma propriedade ou um script cujo valor é apresentado numa linha da exibição de lista. Uma vista de lista tem de especificar pelo menos uma propriedade ou script. Não existe nenhum limite máximo para o número de linhas que podem ser especificados.

- O [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento Especifica a propriedade cujo valor é apresentado na linha. Tem de especificar uma propriedade ou um script, mas não é possível especificar ambos.

- O [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento Especifica o script cujo valor é apresentado na linha. Tem de especificar um script ou uma propriedade, mas não é possível especificar ambos.

- O [etiqueta](./label-element-for-listitem-for-listcontrol-format.md) elemento Especifica a etiqueta que é apresentada à esquerda do valor de propriedade ou um script na linha. Este elemento é opcional. Se uma etiqueta não for especificada, é apresentado o nome da propriedade ou o script. Para obter um exemplo completo, consulte [vista de lista (etiquetas)](./list-view-labels.md).

- O [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) elemento Especifica uma condição que tem de existir para a linha a ser exibido. Para obter mais informações sobre como adicionar condições para a vista de lista, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md). Este elemento é opcional.

- O [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) elemento Especifica um padrão que é utilizado para apresentar o valor da propriedade ou script. Este elemento é opcional.

Para obter um exemplo de um ficheiro de formatação completado que define uma vista de lista simples, consulte [vista de lista (básico)](./list-view-basic.md).

## <a name="defining-the-objects-that-use-the-list-view"></a>Definir os objetos que utilizam a vista de lista

Existem duas formas de definir quais os objetos .NET, utilize a vista de lista. Pode utilizar o [ViewSelectedBy](./viewselectedby-element-format.md) elemento para definir os objetos que podem ser apresentados por todas as definições de vista ou pode usar o [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento para definir quais os objetos são apresentados por um obter definição específica da vista. Na maioria dos casos, um view tem apenas uma definição, para objetos, normalmente, são definidos pelos [ViewSelectedBy](./viewselectedby-element-format.md) elemento.

O exemplo seguinte mostra como definir os objetos que são apresentados, a vista de lista utilizando o [ViewSelectedBy](./viewselectedby-element-format.md) e [TypeName](./typename-element-for-viewselectedby-format.md) elementos. Não há limite para o número de [TypeName](./typename-element-for-viewselectedby-format.md) elementos que pode especificar, e a ordem não é significativa.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Os seguintes elementos XML podem ser utilizados para especificar os objetos que são utilizados pela exibição de lista:

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais os objetos são apresentados pela vista de lista.

- O [TypeName](./typename-element-for-viewselectedby-format.md) elemento Especifica o objeto de .NET que é apresentado pela vista. O nome do tipo .NET completamente qualificado é necessário. Tem de especificar pelo menos um tipo ou seleção definido para a vista, mas existe um número máximo de elementos que podem ser especificados.

Para obter um exemplo de um ficheiro de formatação completado, consulte [vista de lista (básico)](./list-view-basic.md).

O exemplo seguinte utiliza a [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementos. Utilize conjuntos de seleção em que tem um conjunto de objetos que são apresentados com várias Exibições, como quando define uma vista de lista e uma vista de tabela para os mesmos objetos relacionados. Para obter mais informações sobre como criar um conjunto de seleção, consulte [definir conjuntos de seleção](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Os seguintes elementos XML podem ser utilizados para especificar os objetos que são utilizados pela exibição de lista:

- O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais os objetos são apresentados pela vista de lista.

- O [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento Especifica um conjunto de objetos que podem ser apresentados pela exibição. Tem de especificar, pelo menos, um conjunto de seleção ou tipo para o modo de exibição, mas existe um número máximo de elementos que podem ser especificados.

O exemplo seguinte mostra como definir os objetos apresentados por uma definição específica do uso de vista de lista a [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento. Usando esse elemento, pode especificar o nome do tipo .NET de objeto, um conjunto de seleção de objetos ou uma condição de seleção que especifica quando é utilizada a definição. Para obter mais informações sobre como criar uma seleção condições, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

Os seguintes elementos XML podem ser utilizados para especificar os objetos que são utilizados por uma definição específica de exibição de lista:

- O [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento define quais os objetos são apresentados pela definição do.

- O [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elemento Especifica o objeto de .NET que é apresentado pela definição. Ao usar esse elemento, o nome do tipo .NET completamente qualificado é necessário. Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para a definição, mas existe um número máximo de elementos que podem ser especificados.

- O [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) elemento (não mostrado) Especifica um conjunto de objetos que podem ser apresentados por esta definição. Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para a definição, mas existe um número máximo de elementos que podem ser especificados.

- O [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) elemento (não mostrado) Especifica uma condição que tem de existir para esta definição a utilizar. Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para a definição, mas existe um número máximo de elementos que podem ser especificados. Para obter mais informações sobre como definir condições de seleção, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-list-view"></a>Exibição de grupos de objetos numa vista de lista

Pode separar os objetos que são apresentados pela vista de lista em grupos. Isso não significa que definir um grupo, apenas se o Windows PowerShell é iniciado um novo grupo sempre que o valor de uma propriedade específica ou um script é alterado. No exemplo a seguir, um novo grupo é iniciado sempre que o valor do [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) alterações de propriedade.

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

Para obter um exemplo de um ficheiro de formatação completado que define os grupos, veja [vista de lista (GroupBy)](./list-view-groupby.md).

## <a name="using-format-strings"></a>Usar cadeias de caracteres de formato

Cadeias de caracteres de formatação podem ser adicionadas a uma vista para definir melhor a forma como os dados são apresentados. O exemplo seguinte mostra como definir uma cadeia de caracteres de formatação para o valor do `StartTime` propriedade.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

Os seguintes elementos XML podem ser utilizados para especificar um padrão de formato:

- O [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento Especifica os dados que são apresentados pela vista.

- O [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento Especifica a propriedade cujo valor é apresentado pela vista. Tem de especificar uma propriedade ou um script, mas não é possível especificar ambos.

- O [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) elemento Especifica um padrão de formato que define como o valor de propriedade ou um script é apresentado na vista.

- O [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento (não mostrado) Especifica o script cujo valor é apresentado pela vista. Tem de especificar um script ou uma propriedade, mas não é possível especificar ambos.

No exemplo a seguir, o `ToString` método é chamado para formatar o valor do script. Scripts podem chamar qualquer método de um objeto. Por conseguinte, se um objeto tem um método, como `ToString`, que tem parâmetros de formatação, o script pode chamar esse método para formatar o valor de saída do script.

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

O seguinte elemento XML pode ser utilizados para chamar o `ToString` método:

- O [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento Especifica os dados que são apresentados pela vista.

- O [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elemento (não mostrado) Especifica o script cujo valor é apresentado pela vista. Tem de especificar um script ou uma propriedade, mas não é possível especificar ambos.

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md)
