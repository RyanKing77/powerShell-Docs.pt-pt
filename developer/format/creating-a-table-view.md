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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057370"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="10480-102">Creating a Table View (Criar uma Vista de Tabela)</span><span class="sxs-lookup"><span data-stu-id="10480-102">Creating a Table View</span></span>

<span data-ttu-id="10480-103">Uma vista de tabela apresenta os dados numa ou mais colunas.</span><span class="sxs-lookup"><span data-stu-id="10480-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="10480-104">Cada linha na tabela representa um objeto .NET, e cada coluna da tabela representa uma propriedade de objeto ou um valor de script.</span><span class="sxs-lookup"><span data-stu-id="10480-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="10480-105">Pode definir uma vista de tabela que apresenta todas as propriedades de um objeto ou um subconjunto das propriedades de um objeto.</span><span class="sxs-lookup"><span data-stu-id="10480-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="10480-106">Uma exibição de exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="10480-106">A Table View Display</span></span>

<span data-ttu-id="10480-107">O exemplo seguinte mostra como o Windows PowerShell apresenta os [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objeto devolvido pela [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="10480-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="10480-108">Para este objeto, o Windows PowerShell definiu uma vista de tabela que apresenta os `Status` propriedade, o `Name` propriedade (esta propriedade é uma propriedade de alias para o `ServiceName` propriedade) e o `DisplayName` propriedade.</span><span class="sxs-lookup"><span data-stu-id="10480-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="10480-109">Cada linha na tabela representa um objeto devolvido pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="10480-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="10480-110">Definir a exibição de tabela</span><span class="sxs-lookup"><span data-stu-id="10480-110">Defining the Table View</span></span>

<span data-ttu-id="10480-111">O XML a seguir mostra o esquema de vista de tabela para exibir o [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="10480-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="10480-112">Tem de especificar cada propriedade que que pretende apresentar na vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="10480-112">You must specify each property that you want displayed in the table view.</span></span>

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

<span data-ttu-id="10480-113">Os seguintes elementos XML são utilizados para definir uma vista de lista:</span><span class="sxs-lookup"><span data-stu-id="10480-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="10480-114">O [vista](./view-element-format.md) elemento é o elemento principal da vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="10480-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="10480-115">(Este é o mesmo elemento principal para a lista, vistas de controlo de largura e personalizado.)</span><span class="sxs-lookup"><span data-stu-id="10480-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="10480-116">O [nome](./name-element-for-view-format.md) elemento Especifica o nome da vista.</span><span class="sxs-lookup"><span data-stu-id="10480-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="10480-117">Este elemento é necessário para todas as vistas.</span><span class="sxs-lookup"><span data-stu-id="10480-117">This element is required for all views.</span></span>

- <span data-ttu-id="10480-118">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define os objetos que utilizam o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="10480-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="10480-119">Este elemento é necessário.</span><span class="sxs-lookup"><span data-stu-id="10480-119">This element is required.</span></span>

- <span data-ttu-id="10480-120">O [GroupBy](./groupby-element-for-view-format.md) elemento (não mostrado neste exemplo) define quando é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="10480-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="10480-121">Um novo grupo é iniciado sempre que o valor de uma propriedade específica ou um script é alterado.</span><span class="sxs-lookup"><span data-stu-id="10480-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="10480-122">Este elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="10480-122">This element is optional.</span></span>

- <span data-ttu-id="10480-123">O [controles](./controls-element-for-view-format.md) elemento (não mostrado neste exemplo) define os controles personalizados definidos pela exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="10480-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="10480-124">Controles dão-lhe uma forma para especificar a forma como os dados são apresentados.</span><span class="sxs-lookup"><span data-stu-id="10480-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="10480-125">Este elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="10480-125">This element is optional.</span></span> <span data-ttu-id="10480-126">Uma vista pode definir seus próprios controles personalizados, ou ele pode usar controles comuns que podem ser utilizados por qualquer vista no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="10480-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="10480-127">Para obter mais informações sobre controles personalizados, consulte [criar controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="10480-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="10480-128">O [HideTableHeaders](./hidetableheaders-element-format.md) elemento (não mostrar neste exemplo) Especifica que a tabela não apresentará quaisquer etiquetas na parte superior da tabela.</span><span class="sxs-lookup"><span data-stu-id="10480-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="10480-129">Este elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="10480-129">This element is optional.</span></span>

- <span data-ttu-id="10480-130">O [TableControl](./tablecontrol-element-format.md) elemento que define as informações de cabeçalho e de linha da tabela.</span><span class="sxs-lookup"><span data-stu-id="10480-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="10480-131">Assim como todos os outros modos de exibição, uma vista de tabela pode apresentar os valores das propriedades do objeto ou valores gerados por scripts.</span><span class="sxs-lookup"><span data-stu-id="10480-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="10480-132">Definir cabeçalhos de coluna</span><span class="sxs-lookup"><span data-stu-id="10480-132">Defining Column Headers</span></span>

1. <span data-ttu-id="10480-133">O [TableHeaders](./tableheaders-element-format.md) elemento e seus elementos filho definem o que é apresentado na parte superior da tabela.</span><span class="sxs-lookup"><span data-stu-id="10480-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="10480-134">O [TableColumnHeader](./tablecolumnheader-element-format.md) elemento define o que é apresentado na parte superior de uma coluna da tabela.</span><span class="sxs-lookup"><span data-stu-id="10480-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="10480-135">Especifique esses elementos na ordem em que pretende que os cabeçalhos apresentados.</span><span class="sxs-lookup"><span data-stu-id="10480-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="10480-136">Não há limite para o número destes elemento que pode utilizar, mas o número de [TableColumnHeader](./tablecolumnheader-element-format.md) elementos na vista de tabela devem ser igual ao número de [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elementos que utilizar.</span><span class="sxs-lookup"><span data-stu-id="10480-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="10480-137">O [etiqueta](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento Especifica o texto que é apresentado.</span><span class="sxs-lookup"><span data-stu-id="10480-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="10480-138">Este elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="10480-138">This element is optional.</span></span>

4. <span data-ttu-id="10480-139">O [largura](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento Especifica a largura (em carateres) da coluna.</span><span class="sxs-lookup"><span data-stu-id="10480-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="10480-140">Este elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="10480-140">This element is optional.</span></span>

5. <span data-ttu-id="10480-141">O [alinhamento](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) elemento Especifica como a etiqueta é apresentada.</span><span class="sxs-lookup"><span data-stu-id="10480-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="10480-142">A etiqueta pode ser alinhada à esquerda, à direita, ou centralizada.</span><span class="sxs-lookup"><span data-stu-id="10480-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="10480-143">Este elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="10480-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="10480-144">Definindo as linhas de tabela</span><span class="sxs-lookup"><span data-stu-id="10480-144">Defining the Table Rows</span></span>

<span data-ttu-id="10480-145">Exibições de tabela podem fornecer uma ou mais definições que especifique os dados que são apresentados nas linhas da tabela, utilizando os elementos filho do [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="10480-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="10480-146">Tenha em atenção que pode especificar várias definições para as linhas da tabela, mas os cabeçalhos das linhas permanece o mesmo, independentemente da definição de linha que é utilizada.</span><span class="sxs-lookup"><span data-stu-id="10480-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="10480-147">Normalmente, uma tabela irá ter apenas uma definição.</span><span class="sxs-lookup"><span data-stu-id="10480-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="10480-148">No exemplo a seguir, o modo de exibição fornece uma única definição que exibe os valores de várias propriedades do [Diagnostics? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="10480-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="10480-149">Uma vista de tabela pode apresentar o valor de uma propriedade ou o valor de um script (não mostrado no exemplo) em suas linhas.</span><span class="sxs-lookup"><span data-stu-id="10480-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

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

<span data-ttu-id="10480-150">Os seguintes elementos XML podem ser utilizados para fornecer definições para uma linha:</span><span class="sxs-lookup"><span data-stu-id="10480-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="10480-151">O [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elemento e seus elementos filho definem o que é apresentado nas linhas da tabela.</span><span class="sxs-lookup"><span data-stu-id="10480-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="10480-152">O [TableRowEntry](./listentry-element-for-listcontrol-format.md) elemento fornece uma definição da linha.</span><span class="sxs-lookup"><span data-stu-id="10480-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="10480-153">Pelo menos um [TableRowEntry](./listentry-element-for-listcontrol-format.md) é necessária; no entanto, não há nenhum limite máximo para o número de elementos que podem ser adicionados.</span><span class="sxs-lookup"><span data-stu-id="10480-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="10480-154">Na maioria dos casos, uma exibição terão apenas uma única definição.</span><span class="sxs-lookup"><span data-stu-id="10480-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="10480-155">O [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento Especifica os objetos que são apresentados por uma definição específica.</span><span class="sxs-lookup"><span data-stu-id="10480-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="10480-156">Este elemento é opcional e é necessário apenas quando define várias [TableRowEntry](./listentry-element-for-listcontrol-format.md) elementos que apresentam diferentes objetos.</span><span class="sxs-lookup"><span data-stu-id="10480-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="10480-157">O [encapsular](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) elemento Especifica que o texto que excede a largura da coluna é apresentado na próxima linha.</span><span class="sxs-lookup"><span data-stu-id="10480-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="10480-158">Por predefinição, o texto que excede a largura da coluna é truncado.</span><span class="sxs-lookup"><span data-stu-id="10480-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="10480-159">O [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) elemento define as propriedades ou scripts cujos valores são apresentados na linha.</span><span class="sxs-lookup"><span data-stu-id="10480-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="10480-160">O [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define a propriedade ou um script cujo valor é apresentado na coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="10480-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="10480-161">R [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento é necessário para cada coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="10480-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="10480-162">A primeira entrada é apresentada na primeira coluna, a segunda entrada na segunda coluna e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="10480-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="10480-163">O [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica a propriedade cujo valor é apresentado na linha.</span><span class="sxs-lookup"><span data-stu-id="10480-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="10480-164">Tem de especificar uma propriedade ou um script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="10480-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="10480-165">O [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica o script cujo valor é apresentado na linha.</span><span class="sxs-lookup"><span data-stu-id="10480-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="10480-166">Tem de especificar um script ou uma propriedade, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="10480-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="10480-167">O [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elemento Especifica um padrão de formato que define como o valor de propriedade ou um script é apresentado.</span><span class="sxs-lookup"><span data-stu-id="10480-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="10480-168">Este elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="10480-168">This element is optional.</span></span>

- <span data-ttu-id="10480-169">O [alinhamento](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica como o valor da propriedade ou script é apresentado.</span><span class="sxs-lookup"><span data-stu-id="10480-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="10480-170">O valor pode ser alinhado à esquerda, à direita, ou centralizado.</span><span class="sxs-lookup"><span data-stu-id="10480-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="10480-171">Este elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="10480-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="10480-172">Definir os objetos que utilizam a vista de tabela</span><span class="sxs-lookup"><span data-stu-id="10480-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="10480-173">Existem duas formas de definir quais os objetos .NET, utilize a vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="10480-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="10480-174">Pode utilizar o [ViewSelectedBy](./viewselectedby-element-format.md) elemento para definir os objetos que podem ser apresentados por todas as definições de vista ou pode usar o [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elemento para definir quais os objetos são apresentados por um obter definição específica da vista.</span><span class="sxs-lookup"><span data-stu-id="10480-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="10480-175">Na maioria dos casos, um view tem apenas uma definição, para objetos, normalmente, são definidos pelos [ViewSelectedBy](./viewselectedby-element-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="10480-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="10480-176">O exemplo seguinte mostra como definir os objetos que são apresentados pelo modo de exibição de tabela com o [ViewSelectedBy](./viewselectedby-element-format.md) e [TypeName](./typename-element-for-viewselectedby-format.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="10480-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="10480-177">Não há limite para o número de [TypeName](./typename-element-for-viewselectedby-format.md) elementos que pode especificar, e a ordem não é significativa.</span><span class="sxs-lookup"><span data-stu-id="10480-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="10480-178">Os seguintes elementos XML podem ser utilizados para especificar os objetos que são utilizados pela exibição de tabela:</span><span class="sxs-lookup"><span data-stu-id="10480-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="10480-179">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais os objetos são apresentados pela vista de lista.</span><span class="sxs-lookup"><span data-stu-id="10480-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="10480-180">O [TypeName](./typename-element-for-viewselectedby-format.md) elemento Especifica o objeto de .NET que é apresentado pela vista.</span><span class="sxs-lookup"><span data-stu-id="10480-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="10480-181">O nome do tipo .NET completamente qualificado é necessário.</span><span class="sxs-lookup"><span data-stu-id="10480-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="10480-182">Tem de especificar pelo menos um tipo ou seleção definido para a vista, mas existe um número máximo de elementos que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="10480-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="10480-183">O exemplo seguinte utiliza a [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="10480-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="10480-184">Utilize conjuntos de seleção em que tem um conjunto de objetos que são apresentados com várias Exibições, como quando define uma vista de lista e uma vista de tabela para os mesmos objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="10480-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="10480-185">Para obter mais informações sobre como criar um conjunto de seleção, consulte [definir conjuntos de seleção](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="10480-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="10480-186">Os seguintes elementos XML podem ser utilizados para especificar os objetos que são utilizados pela exibição de lista:</span><span class="sxs-lookup"><span data-stu-id="10480-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="10480-187">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais os objetos são apresentados pela vista de lista.</span><span class="sxs-lookup"><span data-stu-id="10480-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="10480-188">O [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento Especifica um conjunto de objetos que podem ser apresentados pela exibição.</span><span class="sxs-lookup"><span data-stu-id="10480-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="10480-189">Tem de especificar, pelo menos, um conjunto de seleção ou tipo para o modo de exibição, mas existe um número máximo de elementos que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="10480-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="10480-190">O exemplo seguinte mostra como definir os objetos apresentados por uma definição específica do modo de exibição de tabela com o [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="10480-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="10480-191">Usando esse elemento, pode especificar o nome do tipo .NET de objeto, um conjunto de seleção de objetos ou uma condição de seleção que especifica quando é utilizada a definição.</span><span class="sxs-lookup"><span data-stu-id="10480-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="10480-192">Para obter mais informações sobre como criar uma seleção condições, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="10480-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="10480-193">Ao criar várias definições de vista de tabela que não é possível especificar cabeçalhos de coluna diferente.</span><span class="sxs-lookup"><span data-stu-id="10480-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="10480-194">Pode especificar apenas o que é apresentado nas linhas da tabela, como os objetos que são apresentados.</span><span class="sxs-lookup"><span data-stu-id="10480-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="10480-195">Os seguintes elementos XML podem ser utilizados para especificar os objetos que são utilizados por uma definição específica de exibição de lista:</span><span class="sxs-lookup"><span data-stu-id="10480-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="10480-196">O [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elemento define quais os objetos são apresentados pela definição do.</span><span class="sxs-lookup"><span data-stu-id="10480-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="10480-197">O [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elemento Especifica o objeto de .NET que é apresentado pela definição.</span><span class="sxs-lookup"><span data-stu-id="10480-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="10480-198">Ao usar esse elemento, o nome do tipo .NET completamente qualificado é necessário.</span><span class="sxs-lookup"><span data-stu-id="10480-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="10480-199">Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para a definição, mas existe um número máximo de elementos que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="10480-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="10480-200">O [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) elemento (não mostrado) Especifica um conjunto de objetos que podem ser apresentados por esta definição.</span><span class="sxs-lookup"><span data-stu-id="10480-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="10480-201">Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para a definição, mas existe um número máximo de elementos que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="10480-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="10480-202">O [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) elemento (não mostrado) Especifica uma condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="10480-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="10480-203">Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para a definição, mas existe um número máximo de elementos que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="10480-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="10480-204">Para obter mais informações sobre como definir condições de seleção, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="10480-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="10480-205">Usar cadeias de caracteres de formato</span><span class="sxs-lookup"><span data-stu-id="10480-205">Using Format Strings</span></span>

<span data-ttu-id="10480-206">Cadeias de caracteres de formatação podem ser adicionadas a uma vista para definir melhor a forma como os dados são apresentados.</span><span class="sxs-lookup"><span data-stu-id="10480-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="10480-207">O exemplo seguinte mostra como definir uma cadeia de caracteres de formatação para o valor do `StartTime` propriedade.</span><span class="sxs-lookup"><span data-stu-id="10480-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="10480-208">Os seguintes elementos XML podem ser utilizados para especificar um padrão de formato:</span><span class="sxs-lookup"><span data-stu-id="10480-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="10480-209">O [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define a propriedade ou um script cujo valor é apresentado na coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="10480-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="10480-210">R [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento é necessário para cada coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="10480-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="10480-211">A primeira entrada é apresentada na primeira coluna, a segunda entrada na segunda coluna e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="10480-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="10480-212">O [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica a propriedade cujo valor é apresentado na linha.</span><span class="sxs-lookup"><span data-stu-id="10480-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="10480-213">Tem de especificar uma propriedade ou um script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="10480-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="10480-214">O [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elemento Especifica um padrão de formato que define como o valor de propriedade ou um script é apresentado.</span><span class="sxs-lookup"><span data-stu-id="10480-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="10480-215">No exemplo a seguir, o `ToString` método é chamado para formatar o valor do script.</span><span class="sxs-lookup"><span data-stu-id="10480-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="10480-216">Scripts podem chamar qualquer método de um objeto.</span><span class="sxs-lookup"><span data-stu-id="10480-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="10480-217">Por conseguinte, se um objeto tem um método, como `ToString`, que tem parâmetros de formatação, o script pode chamar esse método para formatar o valor de saída do script.</span><span class="sxs-lookup"><span data-stu-id="10480-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="10480-218">O seguinte elemento XML pode ser utilizados para chamar o `ToString` método:</span><span class="sxs-lookup"><span data-stu-id="10480-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="10480-219">O [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento define a propriedade ou um script cujo valor é apresentado na coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="10480-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="10480-220">R [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elemento é necessário para cada coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="10480-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="10480-221">A primeira entrada é apresentada na primeira coluna, a segunda entrada na segunda coluna e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="10480-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="10480-222">O [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elemento Especifica o script cujo valor é apresentado na linha.</span><span class="sxs-lookup"><span data-stu-id="10480-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="10480-223">Tem de especificar um script ou uma propriedade, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="10480-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="10480-224">Veja Também</span><span class="sxs-lookup"><span data-stu-id="10480-224">See Also</span></span>

[<span data-ttu-id="10480-225">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="10480-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
