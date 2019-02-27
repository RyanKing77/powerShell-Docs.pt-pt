---
title: Elemento de ListItem para ListItems para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846222"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="8786e-102">ListItem Element for ListItems for ListControl (Format) (Elemento ListItem para ListItems para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="8786e-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="8786e-103">Define a propriedade ou um script cujo valor é apresentado numa linha da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="8786e-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="8786e-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry ListControl (formato) para o elemento de ListItems ListControl (formato) para ListControl (formato) ListItem ListControl elemento (formato)</span><span class="sxs-lookup"><span data-stu-id="8786e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8786e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8786e-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8786e-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="8786e-106">Attributes and Elements</span></span>

<span data-ttu-id="8786e-107">As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `ListItem` elemento.</span><span class="sxs-lookup"><span data-stu-id="8786e-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="8786e-108">Pode ser especificado apenas uma propriedade ou script.</span><span class="sxs-lookup"><span data-stu-id="8786e-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="8786e-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="8786e-109">Attributes</span></span>

<span data-ttu-id="8786e-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8786e-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="8786e-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="8786e-111">Child Elements</span></span>

|<span data-ttu-id="8786e-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="8786e-112">Element</span></span>|<span data-ttu-id="8786e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="8786e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8786e-114">Elemento de FormatString para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8786e-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="8786e-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8786e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8786e-116">Especifica uma cadeia de caracteres de formato que define como o valor de propriedade ou um script é apresentado.</span><span class="sxs-lookup"><span data-stu-id="8786e-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="8786e-117">Elemento de ItemSelectionCondition para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8786e-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="8786e-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8786e-118">Optional element.</span></span><br /><br /> <span data-ttu-id="8786e-119">Define a condição de que tem de existir para este item de lista a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="8786e-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="8786e-120">Elemento da etiqueta para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8786e-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="8786e-121">Elemento opcional</span><span class="sxs-lookup"><span data-stu-id="8786e-121">Optional element</span></span><br /><br /> <span data-ttu-id="8786e-122">Especifica a etiqueta que é apresentada à esquerda do valor de propriedade ou um script na linha.</span><span class="sxs-lookup"><span data-stu-id="8786e-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="8786e-123">Elemento de PropertyName para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8786e-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="8786e-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8786e-124">Optional element.</span></span><br /><br /> <span data-ttu-id="8786e-125">Especifica a propriedade de .NET cujo valor é apresentado na linha.</span><span class="sxs-lookup"><span data-stu-id="8786e-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="8786e-126">Elemento de ScriptBlock para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="8786e-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="8786e-127">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="8786e-127">Optional element.</span></span><br /><br /> <span data-ttu-id="8786e-128">Especifica o script cujo valor é apresentado na linha.</span><span class="sxs-lookup"><span data-stu-id="8786e-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8786e-129">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="8786e-129">Parent Elements</span></span>

|<span data-ttu-id="8786e-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="8786e-130">Element</span></span>|<span data-ttu-id="8786e-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="8786e-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8786e-132">Elemento de ListItems para controle de lista (formato)</span><span class="sxs-lookup"><span data-stu-id="8786e-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="8786e-133">Define as propriedades e os scripts cujos valores são apresentados na vista de lista.</span><span class="sxs-lookup"><span data-stu-id="8786e-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8786e-134">Observações</span><span class="sxs-lookup"><span data-stu-id="8786e-134">Remarks</span></span>

<span data-ttu-id="8786e-135">Para obter mais informações sobre os componentes de uma vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="8786e-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8786e-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8786e-136">Example</span></span>

<span data-ttu-id="8786e-137">Este exemplo mostra os elementos XML que definem três linhas da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="8786e-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="8786e-138">As primeiras duas linhas apresentam o valor de uma propriedade de .NET e a última linha apresenta um valor gerado por um script.</span><span class="sxs-lookup"><span data-stu-id="8786e-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a><span data-ttu-id="8786e-139">Veja Também</span><span class="sxs-lookup"><span data-stu-id="8786e-139">See Also</span></span>

[<span data-ttu-id="8786e-140">Elemento de ListItems (formato)</span><span class="sxs-lookup"><span data-stu-id="8786e-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="8786e-141">Elemento de FormatString para ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="8786e-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="8786e-142">Elemento da etiqueta para ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="8786e-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="8786e-143">Elemento de PropertyName para ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="8786e-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="8786e-144">Elemento de ScriptBlock para ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="8786e-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="8786e-145">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="8786e-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8786e-146">Escrever do Windows PowerShell, formatação e os tipos de ficheiro</span><span class="sxs-lookup"><span data-stu-id="8786e-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
