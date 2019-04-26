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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065738"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="8e831-102">Formatting File Overview (Ficheiros de Formatação: Descrição Geral)</span><span class="sxs-lookup"><span data-stu-id="8e831-102">Formatting File Overview</span></span>

<span data-ttu-id="8e831-103">O formato de apresentação para os objetos que são devolvidos pelo comandos (cmdlets, funções e scripts) são definidas usando arquivos de formatação (format.ps1xml ficheiros).</span><span class="sxs-lookup"><span data-stu-id="8e831-103">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="8e831-104">Vários desses arquivos são fornecidos pelo PowerShell para definir o formato de apresentação para esses objetos devolvidos por comandos fornecidos pelo PowerShell, como o [Diagnostics](/dotnet/api/System.Diagnostics.Process) objeto devolvido pelo `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8e831-104">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="8e831-105">No entanto, também pode criar seus próprios arquivos de formatação personalizados para substituir os formatos de exibição padrão ou pode escrever um arquivo personalizado de formatação para definir a apresentação de objetos retornados por seus próprios comandos.</span><span class="sxs-lookup"><span data-stu-id="8e831-105">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8e831-106">Arquivos de formatação não determinar os elementos de um objeto que são devolvidos para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="8e831-106">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="8e831-107">Quando um objeto é devolvido para o pipeline, todos os membros desse objeto estão disponíveis mesmo que alguns não são apresentados.</span><span class="sxs-lookup"><span data-stu-id="8e831-107">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="8e831-108">PowerShell utiliza os dados nesses arquivos de formatação para determinar o que é apresentado e como os dados apresentados são formatados.</span><span class="sxs-lookup"><span data-stu-id="8e831-108">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="8e831-109">Os dados apresentados podem incluir as propriedades de um objeto ou o valor de um script.</span><span class="sxs-lookup"><span data-stu-id="8e831-109">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="8e831-110">Os scripts são utilizados se deseja exibir um valor que não está disponível diretamente a partir das propriedades de um objeto, como o valor de duas propriedades de um objeto a adicionar e, em seguida, exibindo a soma como um conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="8e831-110">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="8e831-111">Formatação dos dados apresentados é feito através da definição de vistas para os objetos que pretende apresentar.</span><span class="sxs-lookup"><span data-stu-id="8e831-111">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="8e831-112">Pode definir uma vista única para cada objeto, pode definir uma única vista para múltiplos objetos ou pode definir vários modos de exibição para o mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="8e831-112">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="8e831-113">Não existe nenhum limite para o número de modos de exibição que pode definir.</span><span class="sxs-lookup"><span data-stu-id="8e831-113">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="8e831-114">Recursos comuns de arquivos de formatação</span><span class="sxs-lookup"><span data-stu-id="8e831-114">Common Features of Formatting Files</span></span>

<span data-ttu-id="8e831-115">Cada arquivo de formatação pode definir os seguintes componentes que podem ser partilhados entre todas as vistas definidas pelo ficheiro:</span><span class="sxs-lookup"><span data-stu-id="8e831-115">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="8e831-116">Definição de configuração, por exemplo, se os dados apresentados nas linhas das tabelas serão apresentados na próxima linha se os dados são maiores do que a largura da coluna como padrão.</span><span class="sxs-lookup"><span data-stu-id="8e831-116">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="8e831-117">Para obter mais informações sobre estas definições, consulte [definir definições de configuração comuns](./defining-common-configuration-features.md).</span><span class="sxs-lookup"><span data-stu-id="8e831-117">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="8e831-118">Conjuntos de objetos que podem ser apresentados por qualquer um dos modos de exibição do arquivo formatação.</span><span class="sxs-lookup"><span data-stu-id="8e831-118">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="8e831-119">Para obter mais informações sobre estes conjuntos de (denominados *conjuntos de seleção*), veja [definir conjuntos de objetos](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="8e831-119">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="8e831-120">Controles comuns que podem ser utilizados por todas as vistas do ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="8e831-120">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="8e831-121">Controles dão-lhe um melhor controle sobre como os dados são apresentados.</span><span class="sxs-lookup"><span data-stu-id="8e831-121">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="8e831-122">Para obter mais informações sobre controles, consulte [definição de controles de personalizado](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8e831-122">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="8e831-123">Vistas de formatação</span><span class="sxs-lookup"><span data-stu-id="8e831-123">Formatting Views</span></span>

<span data-ttu-id="8e831-124">Vistas de formatação podem apresentar os objetos num formato de tabela, o formato de lista, a grande formato e o formato personalizado.</span><span class="sxs-lookup"><span data-stu-id="8e831-124">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="8e831-125">Na maior parte, cada definição de formatação é descrita por um conjunto de marcas XML que descrevem o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="8e831-125">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="8e831-126">Cada vista contém o nome da vista, os objetos que utilizam o modo de exibição e os elementos da exibição, como as informações de coluna e linha de uma vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="8e831-126">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="8e831-127">Listas de ver as propriedades de um objeto ou um valor de bloco de script numa ou mais colunas de tabela.</span><span class="sxs-lookup"><span data-stu-id="8e831-127">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="8e831-128">Cada coluna representa uma única propriedade do objeto ou um valor de script.</span><span class="sxs-lookup"><span data-stu-id="8e831-128">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="8e831-129">Pode definir uma vista de tabela que apresenta todas as propriedades de um objeto, um subconjunto das propriedades de um objeto ou uma combinação de propriedades e valores de script.</span><span class="sxs-lookup"><span data-stu-id="8e831-129">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="8e831-130">Cada linha da tabela representa um objeto devolvido.</span><span class="sxs-lookup"><span data-stu-id="8e831-130">Each row of the table represents a returned object.</span></span> <span data-ttu-id="8e831-131">Criar uma vista de tabela é muito semelhante a quando encaminhar um objeto para o `Format-Table` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8e831-131">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="8e831-132">Para obter mais informações sobre esta vista, consulte [vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="8e831-132">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="8e831-133">Lista de vista lista as propriedades de um objeto ou um valor de script numa única coluna.</span><span class="sxs-lookup"><span data-stu-id="8e831-133">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="8e831-134">Cada linha da lista apresenta uma etiqueta opcional ou o nome da propriedade seguido o valor da propriedade ou script.</span><span class="sxs-lookup"><span data-stu-id="8e831-134">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="8e831-135">Criar uma vista de lista é muito semelhante a canalização de um objeto para o `Format-List` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8e831-135">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="8e831-136">Para obter mais informações sobre esta vista, consulte [vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="8e831-136">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="8e831-137">Vista alargada apresenta uma lista de uma única propriedade de um objeto ou um valor de script numa ou mais colunas.</span><span class="sxs-lookup"><span data-stu-id="8e831-137">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="8e831-138">Não existe nenhuma etiqueta ou cabeçalho para esta vista.</span><span class="sxs-lookup"><span data-stu-id="8e831-138">There is no label or header for this view.</span></span> <span data-ttu-id="8e831-139">Criar uma vista alargada é muito semelhante a canalização de um objeto para o `Format-Wide` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8e831-139">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="8e831-140">Para obter mais informações sobre esta vista, consulte [vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="8e831-140">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="8e831-141">Exibição personalizada mostra uma vista personalizável de propriedades do objeto ou valores de script que não correspondem à estrutura rígida de exibições de tabela, vistas de lista ou vistas ampla.</span><span class="sxs-lookup"><span data-stu-id="8e831-141">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="8e831-142">Pode definir uma vista personalizada autónoma ou pode definir uma vista personalizada que é utilizada por outra vista, como uma vista de tabela ou vista de lista.</span><span class="sxs-lookup"><span data-stu-id="8e831-142">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="8e831-143">Criar uma vista personalizada é muito semelhante a canalização de um objeto para o `Format-Custom` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8e831-143">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="8e831-144">Para obter mais informações sobre esta vista, consulte [vista personalizada](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8e831-144">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="8e831-145">Componentes de uma vista</span><span class="sxs-lookup"><span data-stu-id="8e831-145">Components of a View</span></span>

<span data-ttu-id="8e831-146">Os exemplos XML seguintes mostram os componentes básicos de XML de um modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="8e831-146">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="8e831-147">Os elementos XML individuais variam dependendo do que a vista que pretende criar, mas os componentes básicos dos modos de exibição são todos iguais.</span><span class="sxs-lookup"><span data-stu-id="8e831-147">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="8e831-148">Para começar, cada vista tem um `Name` elemento que especifica um nome de utilizador amigável que é utilizado para referenciar o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="8e831-148">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="8e831-149">um `ViewSelectedBy` elemento que define quais os objetos .NET são apresentados pela exibição, e um *controle* elemento que define o modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="8e831-149">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

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

<span data-ttu-id="8e831-150">Dentro do elemento de controle, pode definir uma ou mais *entrada* elementos.</span><span class="sxs-lookup"><span data-stu-id="8e831-150">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="8e831-151">Se utilizar várias definições, tem de especificar quais os objetos .NET utilizam cada definição.</span><span class="sxs-lookup"><span data-stu-id="8e831-151">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="8e831-152">Normalmente, apenas uma entrada, com apenas uma definição, é necessário para cada controle.</span><span class="sxs-lookup"><span data-stu-id="8e831-152">Typically only one entry, with only one definition, is needed for each control.</span></span>

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

<span data-ttu-id="8e831-153">Dentro de cada elemento de entrada de uma vista, especifique a *item* elementos que definem as propriedades de .NET ou scripts que são apresentados por essa visão.</span><span class="sxs-lookup"><span data-stu-id="8e831-153">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="8e831-154">Conforme mostrado nos exemplos anteriores, o ficheiro de formatação pode conter várias Exibições, uma exibição pode conter várias definições e cada definição pode conter vários itens.</span><span class="sxs-lookup"><span data-stu-id="8e831-154">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="8e831-155">Exemplo de uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="8e831-155">Example of a Table View</span></span>

<span data-ttu-id="8e831-156">O exemplo seguinte mostra as marcas XML usadas para definir uma vista de tabela que contém duas colunas.</span><span class="sxs-lookup"><span data-stu-id="8e831-156">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="8e831-157">O [ViewDefinitions](./viewdefinitions-element-format.md) elemento é o elemento de contêiner para todas as vistas definidas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="8e831-157">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="8e831-158">O [vista](./view-element-format.md) elemento define a tabela específica, lista, vista ampla ou personalizada.</span><span class="sxs-lookup"><span data-stu-id="8e831-158">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="8e831-159">Dentro de cada [View](./view-element-format.md) elemento, o [nome](./name-element-for-view-format.md) elemento Especifica o nome da vista, o [ViewSelectedBy](./viewselectedby-element-format.md) elemento define os objetos que utilizam o modo de exibição e os diferentes controlar elementos (como o `TableControl` elemento mostrado no exemplo a seguir) definem o tipo da vista.</span><span class="sxs-lookup"><span data-stu-id="8e831-159">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8e831-160">Veja Também</span><span class="sxs-lookup"><span data-stu-id="8e831-160">See Also</span></span>

[<span data-ttu-id="8e831-161">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="8e831-161">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8e831-162">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="8e831-162">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8e831-163">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="8e831-163">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="8e831-164">Criação de controles personalizados</span><span class="sxs-lookup"><span data-stu-id="8e831-164">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="8e831-165">Escrever uma formatação de PowerShell e tipos de ficheiro</span><span class="sxs-lookup"><span data-stu-id="8e831-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
