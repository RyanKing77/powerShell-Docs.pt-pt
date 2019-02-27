---
title: Elemento de FormatString para TableColumnItem para TableControl (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845641"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="50f11-102">FormatString Element for TableColumnItem for TableControl (Format) (Elemento FormatString para TableColumnItem para TableControl [Formatação])</span><span class="sxs-lookup"><span data-stu-id="50f11-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="50f11-103">Especifica um padrão de formato que define como o valor de propriedade ou do script da tabela é exibido.</span><span class="sxs-lookup"><span data-stu-id="50f11-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="50f11-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) TableControl elemento (formato) TableRowEntries elemento (formato) TableRowEntry elemento (formato) TableColumnItems elemento (formato) TableColumnItem elemento de configuração (formato) Elemento de FormatString para TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="50f11-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="50f11-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="50f11-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="50f11-106">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="50f11-106">Attributes and Elements</span></span>

<span data-ttu-id="50f11-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `FormatString` elemento.</span><span class="sxs-lookup"><span data-stu-id="50f11-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="50f11-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="50f11-108">Attributes</span></span>

<span data-ttu-id="50f11-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="50f11-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="50f11-110">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="50f11-110">Child Elements</span></span>

<span data-ttu-id="50f11-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="50f11-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="50f11-112">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="50f11-112">Parent Elements</span></span>

|<span data-ttu-id="50f11-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="50f11-113">Element</span></span>|<span data-ttu-id="50f11-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="50f11-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50f11-115">Elemento de TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="50f11-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="50f11-116">Define a propriedade ou um script cujo valor é apresentado na coluna da linha.</span><span class="sxs-lookup"><span data-stu-id="50f11-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="50f11-117">Valor do Texto</span><span class="sxs-lookup"><span data-stu-id="50f11-117">Text Value</span></span>

<span data-ttu-id="50f11-118">Especifique o padrão que é utilizado para formatar os dados.</span><span class="sxs-lookup"><span data-stu-id="50f11-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="50f11-119">Por exemplo, este padrão pode ser utilizado para formatar o valor de qualquer propriedade que é do tipo [TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: dd} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="50f11-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="50f11-120">Observações</span><span class="sxs-lookup"><span data-stu-id="50f11-120">Remarks</span></span>

<span data-ttu-id="50f11-121">Cadeias de caracteres de formato podem ser utilizadas ao criar exibições de tabela, vistas de lista, modos de exibição amplo ou vistas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="50f11-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="50f11-122">Para obter mais informações sobre a formatação de um valor apresentado numa vista, consulte [formatação de dados apresentada](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="50f11-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="50f11-123">Para obter mais informações sobre os componentes de uma vista de tabela, consulte [vista de tabela](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="50f11-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="50f11-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="50f11-124">Example</span></span>

<span data-ttu-id="50f11-125">O exemplo seguinte mostra como definir uma cadeia de caracteres de formatação para o valor do `StartTime` propriedade.</span><span class="sxs-lookup"><span data-stu-id="50f11-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="50f11-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="50f11-126">See Also</span></span>

[<span data-ttu-id="50f11-127">Criar uma vista de tabela</span><span class="sxs-lookup"><span data-stu-id="50f11-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="50f11-128">Formatação apresentados dados</span><span class="sxs-lookup"><span data-stu-id="50f11-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="50f11-129">Elemento de TableColumnItem (formato)</span><span class="sxs-lookup"><span data-stu-id="50f11-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="50f11-130">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="50f11-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
