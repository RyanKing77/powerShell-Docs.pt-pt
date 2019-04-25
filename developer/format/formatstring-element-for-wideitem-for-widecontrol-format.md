---
title: Elemento de FormatString para WideItem para WideControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065687"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="35d18-102">FormatString Element for WideItem for WideControl (Format) (Elemento FormatString para WideItem para WideControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="35d18-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="35d18-103">Especifica um padrão de formato que define como o valor de propriedade ou um script é apresentado na vista.</span><span class="sxs-lookup"><span data-stu-id="35d18-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="35d18-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) WideControl elemento (formato) WideEntries elemento (formato) WideEntry elemento de configuração para o elemento de WideItem WideControl (formato) para o elemento de FormatString WideControl (formato) para WideItem para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="35d18-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="35d18-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35d18-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="35d18-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="35d18-106">Attributes and Elements</span></span>

<span data-ttu-id="35d18-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `FormatString` elemento.</span><span class="sxs-lookup"><span data-stu-id="35d18-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="35d18-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="35d18-108">Attributes</span></span>

<span data-ttu-id="35d18-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="35d18-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="35d18-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="35d18-110">Child Elements</span></span>

<span data-ttu-id="35d18-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="35d18-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="35d18-112">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="35d18-112">Parent Elements</span></span>

|<span data-ttu-id="35d18-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="35d18-113">Element</span></span>|<span data-ttu-id="35d18-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="35d18-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="35d18-115">Elemento de WideItem para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="35d18-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="35d18-116">Define a propriedade ou um script cujo valor é apresentado numa linha da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="35d18-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="35d18-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="35d18-117">Text Value</span></span>

<span data-ttu-id="35d18-118">Especifique o padrão que é utilizado para formatar os dados.</span><span class="sxs-lookup"><span data-stu-id="35d18-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="35d18-119">Por exemplo, pode utilizar este padrão para formatar o valor de qualquer propriedade que é do tipo [TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: dd} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="35d18-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="35d18-120">Observações</span><span class="sxs-lookup"><span data-stu-id="35d18-120">Remarks</span></span>

<span data-ttu-id="35d18-121">Cadeias de caracteres de formato podem ser utilizadas ao criar exibições de tabela, vistas de lista, modos de exibição amplo ou vistas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="35d18-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="35d18-122">Para obter mais informações sobre a formatação de um valor apresentado numa vista, consulte [formatação de dados apresentada](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="35d18-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="35d18-123">Para obter mais informações sobre como utilizar cadeias de caracteres de formato em modos de exibição amplo, consulte [criar uma vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="35d18-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="35d18-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35d18-124">Example</span></span>

<span data-ttu-id="35d18-125">O exemplo seguinte mostra como definir uma cadeia de caracteres de formatação para o valor do `StartTime` propriedade.</span><span class="sxs-lookup"><span data-stu-id="35d18-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="35d18-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="35d18-126">See Also</span></span>

[<span data-ttu-id="35d18-127">Criar uma vista alargada</span><span class="sxs-lookup"><span data-stu-id="35d18-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="35d18-128">Elemento de WideItem para WideControl (formato)</span><span class="sxs-lookup"><span data-stu-id="35d18-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="35d18-129">Escrever do Windows PowerShell, formatação e os tipos de ficheiro</span><span class="sxs-lookup"><span data-stu-id="35d18-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
