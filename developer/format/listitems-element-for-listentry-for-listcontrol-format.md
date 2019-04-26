---
title: Elemento de ListItems para ListEntry para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065245"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="f8868-102">ListItems Element for ListEntry for ListControl (Format) (Elemento ListItems para ListEntry para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="f8868-102">ListItems Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="f8868-103">Define as propriedades e os scripts cujos valores são apresentados nas linhas da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="f8868-103">Defines the properties and scripts whose values are displayed in the rows of the list view.</span></span>

<span data-ttu-id="f8868-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry de controle (formato) de lista para o elemento de ListItems ListControl (formato) para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f8868-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for List Control (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f8868-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8868-105">Syntax</span></span>

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f8868-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f8868-106">Attributes and Elements</span></span>

<span data-ttu-id="f8868-107">As secções seguintes descrevem os atributos, a elementos filho e o elemento principal do `ListItems` elemento.</span><span class="sxs-lookup"><span data-stu-id="f8868-107">The following sections describe the attributes, child elements, and parent element of the `ListItems` element.</span></span> <span data-ttu-id="f8868-108">Não existe nenhum limite para o número de elementos filho que podem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="f8868-108">There is no limit to the number of child elements that can be specified.</span></span> <span data-ttu-id="f8868-109">A ordem dos elementos subordinados define a ordem em que os valores são apresentados na vista de lista.</span><span class="sxs-lookup"><span data-stu-id="f8868-109">The order of the child elements defines the order that values are displayed in the list view.</span></span>

### <a name="attributes"></a><span data-ttu-id="f8868-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="f8868-110">Attributes</span></span>

<span data-ttu-id="f8868-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f8868-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f8868-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="f8868-112">Child Elements</span></span>

|<span data-ttu-id="f8868-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="f8868-113">Element</span></span>|<span data-ttu-id="f8868-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8868-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8868-115">Elemento de ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f8868-115">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="f8868-116">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="f8868-116">Required element.</span></span><br /><br /> <span data-ttu-id="f8868-117">Define a propriedade ou um script cujo valor é apresentado pelo vista de lista.</span><span class="sxs-lookup"><span data-stu-id="f8868-117">Defines the property or script whose value is displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f8868-118">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="f8868-118">Parent Elements</span></span>

|<span data-ttu-id="f8868-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="f8868-119">Element</span></span>|<span data-ttu-id="f8868-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="f8868-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8868-121">Elemento de ListEntry para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f8868-121">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="f8868-122">Fornece uma definição de vista de lista.</span><span class="sxs-lookup"><span data-stu-id="f8868-122">Provides a definition of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f8868-123">Observações</span><span class="sxs-lookup"><span data-stu-id="f8868-123">Remarks</span></span>

<span data-ttu-id="f8868-124">Para obter mais informações sobre este tipo de vista, consulte [criar uma vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="f8868-124">For more information about this type of view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f8868-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f8868-125">Example</span></span>

<span data-ttu-id="f8868-126">Este exemplo mostra os elementos XML que definem três linhas da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="f8868-126">This example shows the XML elements that define three rows of the list view.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="f8868-127">Veja Também</span><span class="sxs-lookup"><span data-stu-id="f8868-127">See Also</span></span>

[<span data-ttu-id="f8868-128">Elemento de ListEntry para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f8868-128">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="f8868-129">Elemento de ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="f8868-129">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="f8868-130">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="f8868-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f8868-131">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8868-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
