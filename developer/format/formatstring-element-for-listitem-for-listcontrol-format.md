---
title: Elemento de FormatString para ListItem para ListControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065625"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="e8385-102">FormatString Element for ListItem for ListControl (Format) (Elemento FormatString para ListItem para ListControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="e8385-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="e8385-103">Especifica um padrão de formato que define como o valor de propriedade ou um script é apresentado.</span><span class="sxs-lookup"><span data-stu-id="e8385-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="e8385-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) ListControl elemento (formato) ListEntries elemento de configuração para o elemento de ListEntry ListControl (formato) para o elemento de ListItems ListControl (formato) para ListControl (formato) Elemento de ListItem para o elemento de FormatString ListControl (formato) para ListItem para ListControl (formato)</span><span class="sxs-lookup"><span data-stu-id="e8385-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e8385-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8385-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e8385-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e8385-106">Attributes and Elements</span></span>

<span data-ttu-id="e8385-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `FormatString` elemento.</span><span class="sxs-lookup"><span data-stu-id="e8385-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e8385-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="e8385-108">Attributes</span></span>

<span data-ttu-id="e8385-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e8385-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e8385-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="e8385-110">Child Elements</span></span>

<span data-ttu-id="e8385-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e8385-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e8385-112">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="e8385-112">Parent Elements</span></span>

|<span data-ttu-id="e8385-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="e8385-113">Element</span></span>|<span data-ttu-id="e8385-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8385-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e8385-115">Elemento de ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="e8385-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="e8385-116">Define a propriedade ou um script cujo valor é apresentado numa linha da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="e8385-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e8385-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="e8385-117">Text Value</span></span>

<span data-ttu-id="e8385-118">Especifique o padrão que é utilizado para formatar os dados.</span><span class="sxs-lookup"><span data-stu-id="e8385-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="e8385-119">Por exemplo, pode utilizar este padrão para formatar o valor de qualquer propriedade que é do tipo [TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: dd} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="e8385-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8385-120">Observações</span><span class="sxs-lookup"><span data-stu-id="e8385-120">Remarks</span></span>

<span data-ttu-id="e8385-121">Cadeias de caracteres de formato podem ser utilizadas ao criar exibições de tabela, vistas de lista, modos de exibição amplo ou vistas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="e8385-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="e8385-122">Para obter mais informações sobre a formatação de um valor apresentado numa vista, consulte [formatação de dados apresentada](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="e8385-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="e8385-123">Para obter mais informações sobre como utilizar cadeias de caracteres de formato nas vistas de lista, consulte [Criar vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="e8385-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e8385-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e8385-124">Example</span></span>

<span data-ttu-id="e8385-125">O exemplo seguinte mostra como definir uma cadeia de caracteres de formatação para o valor do `StartTime` propriedade.</span><span class="sxs-lookup"><span data-stu-id="e8385-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="e8385-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="e8385-126">See Also</span></span>

[<span data-ttu-id="e8385-127">Criar uma vista de lista</span><span class="sxs-lookup"><span data-stu-id="e8385-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e8385-128">Elemento de ListItem (formato)</span><span class="sxs-lookup"><span data-stu-id="e8385-128">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="e8385-129">Escrever do Windows PowerShell, formatação e os tipos de ficheiro</span><span class="sxs-lookup"><span data-stu-id="e8385-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
