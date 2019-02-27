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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848560"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="72481-102">Creating a Wide View (Criar uma Vista Ampla)</span><span class="sxs-lookup"><span data-stu-id="72481-102">Creating a Wide View</span></span>

<span data-ttu-id="72481-103">Uma vista alargada apresenta um valor único para cada objeto que é apresentado.</span><span class="sxs-lookup"><span data-stu-id="72481-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="72481-104">O valor apresentado pode ser o valor de uma propriedade de objeto do .NET ou o valor de um script.</span><span class="sxs-lookup"><span data-stu-id="72481-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="72481-105">Por predefinição, não existe o rótulo ou cabeçalho para esta vista.</span><span class="sxs-lookup"><span data-stu-id="72481-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="72481-106">Uma vista alargada de apresentação</span><span class="sxs-lookup"><span data-stu-id="72481-106">A Wide View Display</span></span>

<span data-ttu-id="72481-107">O exemplo seguinte mostra como o Windows PowerShell apresenta os [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto devolvido pela [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet quando o respetivo resultado é enviada por pipe para o [ Em todo o formato](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72481-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="72481-108">(Por predefinição, o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet devolve uma vista de tabela.) Neste exemplo, as duas colunas são usadas para exibir o nome do processo para cada objeto devolvido.</span><span class="sxs-lookup"><span data-stu-id="72481-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="72481-109">O nome da propriedade do objeto não for apresentado, apenas o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="72481-109">The name of the object's property is not displayed, only the value of the property.</span></span>

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

## <a name="defining-the-wide-view"></a><span data-ttu-id="72481-110">Definir a vista alargada</span><span class="sxs-lookup"><span data-stu-id="72481-110">Defining the Wide View</span></span>

<span data-ttu-id="72481-111">O XML a seguir mostra o esquema de vista alargada para o [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto.</span><span class="sxs-lookup"><span data-stu-id="72481-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="72481-112">Os seguintes elementos XML são utilizados para definir uma vista alargada:</span><span class="sxs-lookup"><span data-stu-id="72481-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="72481-113">O [vista](./view-element-format.md) elemento é o elemento principal da vista ampla.</span><span class="sxs-lookup"><span data-stu-id="72481-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="72481-114">(Este é o mesmo elemento principal para a tabela, lista e modos de exibição do controle personalizado).</span><span class="sxs-lookup"><span data-stu-id="72481-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="72481-115">O [nome](./name-element-for-view-format.md) elemento Especifica o nome da vista.</span><span class="sxs-lookup"><span data-stu-id="72481-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="72481-116">Este elemento é necessário para todas as vistas.</span><span class="sxs-lookup"><span data-stu-id="72481-116">This element is required for all views.</span></span>

- <span data-ttu-id="72481-117">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define os objetos que utilizam o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="72481-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="72481-118">Este elemento é necessário.</span><span class="sxs-lookup"><span data-stu-id="72481-118">This element is required.</span></span>

- <span data-ttu-id="72481-119">O [GroupBy](./groupby-element-for-view-format.md) elemento define quando é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="72481-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="72481-120">Um novo grupo é iniciado sempre que o valor de uma propriedade específica ou um script é alterado.</span><span class="sxs-lookup"><span data-stu-id="72481-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="72481-121">Este elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="72481-121">This element is optional.</span></span>

- <span data-ttu-id="72481-122">O [controles](./controls-element-for-view-format.md) elementos define os controles personalizados que são definidos pela vista ampla.</span><span class="sxs-lookup"><span data-stu-id="72481-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="72481-123">Controles dão-lhe uma forma para especificar a forma como os dados são apresentados.</span><span class="sxs-lookup"><span data-stu-id="72481-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="72481-124">Este elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="72481-124">This element is optional.</span></span> <span data-ttu-id="72481-125">Uma vista pode definir seus próprios controles personalizados, ou ele pode usar controles comuns que podem ser utilizados por qualquer vista no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="72481-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="72481-126">Para obter mais informações sobre controles personalizados, consulte [criar controles personalizados](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="72481-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="72481-127">O [WideControl](./widecontrol-element-format.md) elemento e seus elementos filho definem o que é apresentado na vista.</span><span class="sxs-lookup"><span data-stu-id="72481-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="72481-128">No exemplo anterior, a vista foi projetada para apresentar os [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) propriedade.</span><span class="sxs-lookup"><span data-stu-id="72481-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="72481-129">Para obter um exemplo de um ficheiro de formatação completado que define uma vista alargada simple, consulte [vista alargada (básico)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="72481-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="72481-130">Fornecer definições para a sua vista alargada</span><span class="sxs-lookup"><span data-stu-id="72481-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="72481-131">Vistas ampla podem fornecer uma ou mais definições utilizando os elementos filho do [WideControl](./widecontrol-element-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="72481-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="72481-132">Normalmente, uma vista irá ter apenas uma definição.</span><span class="sxs-lookup"><span data-stu-id="72481-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="72481-133">No exemplo a seguir, o modo de exibição fornece uma única definição que exibe o valor do [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) propriedade.</span><span class="sxs-lookup"><span data-stu-id="72481-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="72481-134">Uma vista alargada pode apresentar o valor de uma propriedade ou o valor de um script (não mostrado no exemplo).</span><span class="sxs-lookup"><span data-stu-id="72481-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="72481-135">Os seguintes elementos XML podem ser utilizados para fornecer definições para uma visão ampla:</span><span class="sxs-lookup"><span data-stu-id="72481-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="72481-136">O [WideControl](./widecontrol-element-format.md) elemento e seus elementos filho definem o que é apresentado na vista.</span><span class="sxs-lookup"><span data-stu-id="72481-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="72481-137">O [AutoSize](./autosize-element-for-widecontrol-format.md) elemento Especifica se o tamanho da coluna e o número de colunas são ajustados com base no tamanho dos dados.</span><span class="sxs-lookup"><span data-stu-id="72481-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="72481-138">Este elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="72481-138">This element is optional.</span></span>

- <span data-ttu-id="72481-139">O [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) elemento Especifica o número de colunas apresentadas na vista alargada.</span><span class="sxs-lookup"><span data-stu-id="72481-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="72481-140">Este elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="72481-140">This element is optional.</span></span>

- <span data-ttu-id="72481-141">O [WideEntries](./wideentries-element-for-widecontrol-format.md) elemento fornece as definições da vista.</span><span class="sxs-lookup"><span data-stu-id="72481-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="72481-142">Na maioria dos casos, uma exibição terão apenas uma única definição.</span><span class="sxs-lookup"><span data-stu-id="72481-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="72481-143">Este elemento é necessário.</span><span class="sxs-lookup"><span data-stu-id="72481-143">This element is required.</span></span>

- <span data-ttu-id="72481-144">O [WideEntry](./wideentry-element-for-widecontrol-format.md) elemento fornece uma definição da vista.</span><span class="sxs-lookup"><span data-stu-id="72481-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="72481-145">Pelo menos um [WideEntry](./wideentry-element-for-widecontrol-format.md) é necessária; no entanto, não há nenhum limite máximo para o número de elementos que podem ser adicionados.</span><span class="sxs-lookup"><span data-stu-id="72481-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="72481-146">Na maioria dos casos, uma exibição terão apenas uma única definição.</span><span class="sxs-lookup"><span data-stu-id="72481-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="72481-147">O [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento Especifica os objetos que são apresentados por uma definição específica.</span><span class="sxs-lookup"><span data-stu-id="72481-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="72481-148">Este elemento é opcional e é necessário apenas quando define várias [WideEntry](./wideentry-element-for-widecontrol-format.md) elementos que apresentam diferentes objetos.</span><span class="sxs-lookup"><span data-stu-id="72481-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="72481-149">O [WideItem](./wideitem-element-for-widecontrol-format.md) elemento Especifica os dados que são apresentados pela vista.</span><span class="sxs-lookup"><span data-stu-id="72481-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="72481-150">Ao contrário de outros tipos de vistas, um controle amplo pode apresentar apenas um item.</span><span class="sxs-lookup"><span data-stu-id="72481-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="72481-151">O [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elemento Especifica a propriedade cujo valor é apresentado pela vista.</span><span class="sxs-lookup"><span data-stu-id="72481-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="72481-152">Tem de especificar uma propriedade ou um script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="72481-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="72481-153">O [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento Especifica o script cujo valor é apresentado pela vista.</span><span class="sxs-lookup"><span data-stu-id="72481-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="72481-154">Tem de especificar um script ou uma propriedade, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="72481-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="72481-155">O [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elemento Especifica um padrão que é utilizado para apresentar os dados.</span><span class="sxs-lookup"><span data-stu-id="72481-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="72481-156">Este elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="72481-156">This element is optional.</span></span>

<span data-ttu-id="72481-157">Para obter um exemplo de um ficheiro de formatação completado que define uma definição de vista alargada, consulte [vista alargada (básico)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="72481-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="72481-158">Definir os objetos que usam a vista alargada</span><span class="sxs-lookup"><span data-stu-id="72481-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="72481-159">Existem duas formas de definir quais os objetos .NET utilizam a vista alargada.</span><span class="sxs-lookup"><span data-stu-id="72481-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="72481-160">Pode utilizar o [ViewSelectedBy](./viewselectedby-element-format.md) elemento para definir os objetos que podem ser apresentados por todas as definições de vista ou pode usar o [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento para definir quais os objetos são apresentados por um obter definição específica da vista.</span><span class="sxs-lookup"><span data-stu-id="72481-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="72481-161">Na maioria dos casos, um view tem apenas uma definição, para objetos, normalmente, são definidos pelos [ViewSelectedBy](./viewselectedby-element-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="72481-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="72481-162">O exemplo seguinte mostra como definir os objetos que são apresentados, a vista alargada utilizando o [ViewSelectedBy](./viewselectedby-element-format.md) e [TypeName](./typename-element-for-viewselectedby-format.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="72481-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="72481-163">Não há limite para o número de [TypeName](./typename-element-for-viewselectedby-format.md) elementos que pode especificar, e a ordem não é significativa.</span><span class="sxs-lookup"><span data-stu-id="72481-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="72481-164">Os seguintes elementos XML podem ser utilizados para especificar os objetos que são utilizados pela wide vista:</span><span class="sxs-lookup"><span data-stu-id="72481-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="72481-165">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais os objetos são apresentados pela exibição ampla.</span><span class="sxs-lookup"><span data-stu-id="72481-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="72481-166">O [TypeName](./typename-element-for-viewselectedby-format.md) elemento especifica do .NET que é apresentada pela vista.</span><span class="sxs-lookup"><span data-stu-id="72481-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="72481-167">O nome do tipo .NET completamente qualificado é necessário.</span><span class="sxs-lookup"><span data-stu-id="72481-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="72481-168">Tem de especificar pelo menos um tipo ou seleção definido para a vista, mas existe um número máximo de elementos que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="72481-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="72481-169">Para obter um exemplo de um ficheiro de formatação completado, consulte [vista alargada (básico)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="72481-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="72481-170">O exemplo seguinte utiliza a [ViewSelectedBy](./viewselectedby-element-format.md) e [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="72481-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="72481-171">Utilize conjuntos de seleção em que tem um conjunto de objetos que são apresentados com várias Exibições, como quando define uma vista alargada e uma vista de tabela para os mesmos objetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="72481-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="72481-172">Para obter mais informações sobre como criar um conjunto de seleção, consulte [definir conjuntos de seleção](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="72481-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="72481-173">Os seguintes elementos XML podem ser utilizados para especificar os objetos que são utilizados pela wide vista:</span><span class="sxs-lookup"><span data-stu-id="72481-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="72481-174">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento define quais os objetos são apresentados pela exibição ampla.</span><span class="sxs-lookup"><span data-stu-id="72481-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="72481-175">O [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento Especifica um conjunto de objetos que podem ser apresentados pela exibição.</span><span class="sxs-lookup"><span data-stu-id="72481-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="72481-176">Tem de especificar, pelo menos, um conjunto de seleção ou tipo para o modo de exibição, mas existe um número máximo de elementos que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="72481-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="72481-177">O exemplo seguinte mostra como definir os objetos apresentados por uma definição específica da vista alargada usando o [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="72481-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="72481-178">Usando esse elemento, pode especificar o nome do tipo .NET de objeto, um conjunto de seleção de objetos ou uma condição de seleção que especifica quando é utilizada a definição.</span><span class="sxs-lookup"><span data-stu-id="72481-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="72481-179">Para obter mais informações sobre como criar uma seleção condições, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="72481-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="72481-180">Os seguintes elementos XML podem ser utilizados para especificar os objetos que são utilizados por uma definição específica da vista alargada:</span><span class="sxs-lookup"><span data-stu-id="72481-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="72481-181">O [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elemento define quais os objetos são apresentados pela definição do.</span><span class="sxs-lookup"><span data-stu-id="72481-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="72481-182">O [TypeName](./typename-element-for-viewselectedby-format.md) elemento Especifica o que é apresentado pela definição do .NET.</span><span class="sxs-lookup"><span data-stu-id="72481-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="72481-183">Ao utilizar este elemento o nome do tipo .NET completamente qualificado é necessário.</span><span class="sxs-lookup"><span data-stu-id="72481-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="72481-184">Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para a definição, mas existe um número máximo de elementos que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="72481-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="72481-185">O [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elemento (não mostrado) Especifica um conjunto de objetos que podem ser apresentados por esta definição.</span><span class="sxs-lookup"><span data-stu-id="72481-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="72481-186">Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para a definição, mas existe um número máximo de elementos que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="72481-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="72481-187">O [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) elemento (não mostrado) Especifica uma condição que tem de existir para esta definição a utilizar.</span><span class="sxs-lookup"><span data-stu-id="72481-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="72481-188">Tem de especificar pelo menos um tipo, o conjunto de seleção ou condição de seleção para a definição, mas existe um número máximo de elementos que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="72481-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="72481-189">Para obter mais informações sobre como definir condições de seleção, consulte [definir condições para exibir dados](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="72481-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="72481-190">Exibição de grupos de objetos numa vista alargada</span><span class="sxs-lookup"><span data-stu-id="72481-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="72481-191">Pode separar os objetos que são apresentados pela exibição ampla em grupos.</span><span class="sxs-lookup"><span data-stu-id="72481-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="72481-192">Isso não significa que definir um grupo, apenas se o Windows PowerShell é iniciado um novo grupo sempre que o valor de uma propriedade específica ou um script é alterado.</span><span class="sxs-lookup"><span data-stu-id="72481-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="72481-193">No exemplo a seguir, um novo grupo é iniciado sempre que o valor do [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) alterações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="72481-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="72481-194">Os seguintes elementos XML são utilizados para definir quando um grupo é iniciado:</span><span class="sxs-lookup"><span data-stu-id="72481-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="72481-195">O [GroupBy](./groupby-element-for-view-format.md) elemento define a propriedade ou um script que inicia o novo grupo e define como o grupo é exibido.</span><span class="sxs-lookup"><span data-stu-id="72481-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="72481-196">O [PropertyName](./propertyname-element-for-groupby-format.md) elemento Especifica a propriedade que inicia um novo grupo sempre que seu valor é alterado.</span><span class="sxs-lookup"><span data-stu-id="72481-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="72481-197">Tem de especificar uma propriedade ou um script para iniciar o grupo, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="72481-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="72481-198">O [ScriptBlock](./scriptblock-element-for-groupby-format.md) elemento Especifica o script que inicia um novo grupo sempre que seu valor é alterado.</span><span class="sxs-lookup"><span data-stu-id="72481-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="72481-199">Tem de especificar um script ou uma propriedade para iniciar o grupo, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="72481-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="72481-200">O [etiqueta](./label-element-for-groupby-format.md) elemento define uma etiqueta que é apresentada no início de cada grupo.</span><span class="sxs-lookup"><span data-stu-id="72481-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="72481-201">Além do texto especificado por este elemento, o Windows PowerShell apresenta o valor que acionou o novo grupo e adiciona uma linha em branco antes e depois a etiqueta.</span><span class="sxs-lookup"><span data-stu-id="72481-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="72481-202">Este elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="72481-202">This element is optional.</span></span>

- <span data-ttu-id="72481-203">O [CustomControl](./customcontrol-element-for-groupby-format.md) elemento define um controle que é utilizado para apresentar os dados.</span><span class="sxs-lookup"><span data-stu-id="72481-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="72481-204">Este elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="72481-204">This element is optional.</span></span>

- <span data-ttu-id="72481-205">O [CustomControlName](./customcontrolname-element-for-groupby-format.md) elemento Especifica uma comum ou ver o controle que é utilizado para apresentar os dados.</span><span class="sxs-lookup"><span data-stu-id="72481-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="72481-206">Este elemento é opcional.</span><span class="sxs-lookup"><span data-stu-id="72481-206">This element is optional.</span></span>

<span data-ttu-id="72481-207">Para obter um exemplo de um ficheiro de formatação completado que define os grupos, veja [vista alargada (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="72481-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="72481-208">Usar cadeias de caracteres de formato</span><span class="sxs-lookup"><span data-stu-id="72481-208">Using Format Strings</span></span>

<span data-ttu-id="72481-209">Cadeias de caracteres de formatação podem ser adicionadas a uma vista alargada para definir melhor a forma como os dados são apresentados.</span><span class="sxs-lookup"><span data-stu-id="72481-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="72481-210">O exemplo seguinte mostra como definir uma cadeia de caracteres de formatação para o valor do `StartTime` propriedade.</span><span class="sxs-lookup"><span data-stu-id="72481-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="72481-211">Os seguintes elementos XML podem ser utilizados para especificar um padrão de formato:</span><span class="sxs-lookup"><span data-stu-id="72481-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="72481-212">O [WideItem](./wideitem-element-for-widecontrol-format.md) elemento Especifica os dados que são apresentados pela vista.</span><span class="sxs-lookup"><span data-stu-id="72481-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="72481-213">O [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elemento Especifica a propriedade cujo valor é apresentado pela vista.</span><span class="sxs-lookup"><span data-stu-id="72481-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="72481-214">Tem de especificar uma propriedade ou um script, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="72481-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="72481-215">O [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elemento Especifica um padrão de formato que define como o valor de propriedade ou um script é apresentado na vista</span><span class="sxs-lookup"><span data-stu-id="72481-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="72481-216">O [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento (não mostrado) Especifica o script cujo valor é apresentado pela vista.</span><span class="sxs-lookup"><span data-stu-id="72481-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="72481-217">Tem de especificar um script ou uma propriedade, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="72481-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="72481-218">No exemplo a seguir, o `ToString` método é chamado para formatar o valor do script.</span><span class="sxs-lookup"><span data-stu-id="72481-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="72481-219">Scripts podem chamar qualquer método de um objeto.</span><span class="sxs-lookup"><span data-stu-id="72481-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="72481-220">Por conseguinte, se um objeto tem um método, como `ToString`, que tem parâmetros de formatação, o script pode chamar esse método para formatar o valor de saída do script.</span><span class="sxs-lookup"><span data-stu-id="72481-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="72481-221">O seguinte elemento XML pode ser utilizados para chamar o `ToString` método:</span><span class="sxs-lookup"><span data-stu-id="72481-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="72481-222">O [WideItem](./wideitem-element-for-widecontrol-format.md) elemento Especifica os dados que são apresentados pela vista.</span><span class="sxs-lookup"><span data-stu-id="72481-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="72481-223">O [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elemento (não mostrado) Especifica o script cujo valor é apresentado pela vista.</span><span class="sxs-lookup"><span data-stu-id="72481-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="72481-224">Tem de especificar um script ou uma propriedade, mas não é possível especificar ambos.</span><span class="sxs-lookup"><span data-stu-id="72481-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="72481-225">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="72481-225">See Also</span></span>

[<span data-ttu-id="72481-226">Vista alargada (básico)</span><span class="sxs-lookup"><span data-stu-id="72481-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="72481-227">Vista alargada (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="72481-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="72481-228">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="72481-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
