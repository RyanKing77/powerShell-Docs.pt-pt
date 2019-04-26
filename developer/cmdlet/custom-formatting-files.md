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
# <a name="custom-formatting-files"></a><span data-ttu-id="9140f-102">Custom Formatting Files (Personalizar Ficheiros de Formatação)</span><span class="sxs-lookup"><span data-stu-id="9140f-102">Custom Formatting Files</span></span>

<span data-ttu-id="9140f-103">O formato de apresentação para os objetos devolvidos por cmdlets, funções e scripts são definidos usando arquivos de formatação (format.ps1xml ficheiros).</span><span class="sxs-lookup"><span data-stu-id="9140f-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="9140f-104">Vários desses arquivos são fornecidos pelo Windows PowerShell para definir o formato de exibição padrão para esses objetos devolvidos por cmdlets do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9140f-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="9140f-105">No entanto, também pode criar seus próprios arquivos de formatação personalizados para substituir os formatos de apresentação predefinido ou para definir a apresentação de objetos retornados por seus próprios comandos.</span><span class="sxs-lookup"><span data-stu-id="9140f-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="9140f-106">Windows PowerShell usa os dados nesses arquivos de formatação para determinar o que é apresentado e como os dados são formatados.</span><span class="sxs-lookup"><span data-stu-id="9140f-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="9140f-107">Os dados apresentados podem incluir as propriedades de um objeto ou o valor de um bloco de script.</span><span class="sxs-lookup"><span data-stu-id="9140f-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="9140f-108">Blocos de script são usados se deseja exibir um valor que não está disponível diretamente a partir das propriedades de um objeto.</span><span class="sxs-lookup"><span data-stu-id="9140f-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="9140f-109">Por exemplo, pode querer adicionar o valor de duas propriedades de um objeto e apresentar a soma como um conjunto separado de dados.</span><span class="sxs-lookup"><span data-stu-id="9140f-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="9140f-110">Quando escreve o seu próprio formatação ficheiro, terá de definir *vistas* para os objetos que pretende apresentar.</span><span class="sxs-lookup"><span data-stu-id="9140f-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="9140f-111">Pode definir uma vista única para cada objeto, pode definir uma única vista para múltiplos objetos ou pode definir vários modos de exibição para o mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="9140f-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="9140f-112">Não existe nenhum limite para o número de modos de exibição que pode definir.</span><span class="sxs-lookup"><span data-stu-id="9140f-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9140f-113">Arquivos de formatação não determinar os elementos de um objeto que são devolvidos para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="9140f-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="9140f-114">Quando um objeto é devolvido para o pipeline, todos os membros desse objeto estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9140f-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="9140f-115">Vistas de formato</span><span class="sxs-lookup"><span data-stu-id="9140f-115">Format Views</span></span>

<span data-ttu-id="9140f-116">Vistas de formatação podem apresentar os objetos no formato de tabela, um formato de lista, um formato de grande e um formato personalizado.</span><span class="sxs-lookup"><span data-stu-id="9140f-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="9140f-117">Na maior parte, cada definição de formatação é descrita por um conjunto de marcas XML que descrevem um modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="9140f-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="9140f-118">Cada vista contém o nome da vista, os objetos que utilizam o modo de exibição e os elementos da exibição, como as informações de coluna e linha de uma vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="9140f-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="9140f-119">As vistas seguintes estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9140f-119">The following views are available.</span></span>

<span data-ttu-id="9140f-120">Vista de tabela lista as propriedades de um objeto ou um valor de bloco de script numa ou mais colunas.</span><span class="sxs-lookup"><span data-stu-id="9140f-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="9140f-121">Cada coluna representa uma propriedade de objeto ou um valor de bloco de script.</span><span class="sxs-lookup"><span data-stu-id="9140f-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="9140f-122">Pode definir uma vista de tabela que apresenta todas as propriedades de um objeto, um subconjunto das propriedades de um objeto ou uma combinação de propriedades e valores de bloco de script.</span><span class="sxs-lookup"><span data-stu-id="9140f-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="9140f-123">Cada linha da tabela representa um objeto devolvido.</span><span class="sxs-lookup"><span data-stu-id="9140f-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="9140f-124">Para obter mais informações sobre esta vista, consulte [vista de tabela](../format/creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="9140f-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="9140f-125">Vista de lista lista as propriedades de um objeto ou um valor de bloco de script numa única coluna.</span><span class="sxs-lookup"><span data-stu-id="9140f-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="9140f-126">Cada linha da lista apresenta uma etiqueta opcional ou o nome da propriedade seguido o valor do bloco de script ou de propriedade.</span><span class="sxs-lookup"><span data-stu-id="9140f-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="9140f-127">Para obter mais informações sobre esta vista, consulte [vista de lista](../format/creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="9140f-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="9140f-128">Vista alargada apresenta uma lista de uma única propriedade de um objeto ou um valor de bloco de script numa ou mais colunas.</span><span class="sxs-lookup"><span data-stu-id="9140f-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="9140f-129">Não existe nenhuma etiqueta ou cabeçalho para esta vista.</span><span class="sxs-lookup"><span data-stu-id="9140f-129">There is no label or header for this view.</span></span> <span data-ttu-id="9140f-130">Para obter mais informações sobre esta vista, consulte [vista alargada](../format/creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="9140f-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="9140f-131">Exibição personalizada mostra uma vista personalizável de propriedades do objeto ou valores de bloco de script que não correspondem à estrutura rígida de exibições de tabela, vistas de lista ou vistas ampla.</span><span class="sxs-lookup"><span data-stu-id="9140f-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="9140f-132">Pode definir uma vista personalizada de autónomo ou pode definir uma vista personalizada que é utilizada por outra vista, como uma vista de tabela ou vista de lista.</span><span class="sxs-lookup"><span data-stu-id="9140f-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="9140f-133">Para obter mais informações sobre esta vista, consulte [vista personalizada](../format/creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="9140f-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="9140f-134">Elementos XML do Vista</span><span class="sxs-lookup"><span data-stu-id="9140f-134">View XML Elements</span></span>

<span data-ttu-id="9140f-135">O exemplo seguinte mostra as marcas XML usadas para definir uma vista de tabela que contém duas colunas.</span><span class="sxs-lookup"><span data-stu-id="9140f-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="9140f-136">O [ViewDefinitions](../format/viewdefinitions-element-format.md) elemento é o elemento de contêiner para todas as vistas definidas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="9140f-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="9140f-137">O [vista](../format/view-element-format.md) elemento define a tabela específica, lista, vista ampla ou personalizada.</span><span class="sxs-lookup"><span data-stu-id="9140f-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="9140f-138">Dentro de cada vista, o [Name](../format/name-element-for-view-format.md) elemento Especifica o nome da vista, o [ViewSelectedBy](../format/viewselectedby-element-format.md) elemento define os objetos que utilizam o modo de exibição e os elementos de controle diferentes (como o `TableControl` elemento) definir o formato da vista.</span><span class="sxs-lookup"><span data-stu-id="9140f-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9140f-139">Veja Também</span><span class="sxs-lookup"><span data-stu-id="9140f-139">See Also</span></span>

[<span data-ttu-id="9140f-140">Vista de tabela</span><span class="sxs-lookup"><span data-stu-id="9140f-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="9140f-141">Vista de lista</span><span class="sxs-lookup"><span data-stu-id="9140f-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="9140f-142">Vista alargada</span><span class="sxs-lookup"><span data-stu-id="9140f-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="9140f-143">Vista personalizada</span><span class="sxs-lookup"><span data-stu-id="9140f-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="9140f-144">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9140f-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
