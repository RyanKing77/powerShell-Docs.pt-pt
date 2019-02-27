---
title: O elemento de DefaultSettings (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: 59cc0514087cc52438e0d1271b8b77a7799eb32c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846579"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="10c87-102">DefaultSettings Element (Format) (Elemento DefaultSettings [Formatação])</span><span class="sxs-lookup"><span data-stu-id="10c87-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="10c87-103">Define configurações comuns que se aplicam a todas as vistas do ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="10c87-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="10c87-104">Definições comuns incluem a exibição de erros, quebra de texto em tabelas, definir a forma como as coleções são expandidas e muito mais.</span><span class="sxs-lookup"><span data-stu-id="10c87-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="10c87-105">Elemento de DefaultSettings de elemento (formato) de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="10c87-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="10c87-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10c87-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="10c87-107">Atributos e Elementos</span><span class="sxs-lookup"><span data-stu-id="10c87-107">Attributes and Elements</span></span>

<span data-ttu-id="10c87-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `DefaultSettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="10c87-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="10c87-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="10c87-109">Attributes</span></span>

<span data-ttu-id="10c87-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="10c87-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="10c87-111">Elementos Subordinados</span><span class="sxs-lookup"><span data-stu-id="10c87-111">Child Elements</span></span>

|<span data-ttu-id="10c87-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="10c87-112">Element</span></span>|<span data-ttu-id="10c87-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="10c87-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="10c87-114">Elemento de DisplayError (Frmat)</span><span class="sxs-lookup"><span data-stu-id="10c87-114">DisplayError Element (Frmat)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="10c87-115">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="10c87-115">Optional element.</span></span><br /><br /> <span data-ttu-id="10c87-116">Especifica que a cadeia de caracteres #ERR é apresentada quando ocorre um erro ao apresentar um conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="10c87-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="10c87-117">Elemento de EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="10c87-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="10c87-118">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="10c87-118">Optional element.</span></span><br /><br /> <span data-ttu-id="10c87-119">Define as diferentes formas em que os objetos do .NET são expandidos quando são apresentados numa vista.</span><span class="sxs-lookup"><span data-stu-id="10c87-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="10c87-120">PropertyCountForTable (formato)</span><span class="sxs-lookup"><span data-stu-id="10c87-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="10c87-121">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="10c87-121">Optional element.</span></span><br /><br /> <span data-ttu-id="10c87-122">Especifica o número mínimo de propriedades que têm de ter um objeto para exibir o objeto numa exibição de tabela.</span><span class="sxs-lookup"><span data-stu-id="10c87-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="10c87-123">Elemento de ShowError (formato)</span><span class="sxs-lookup"><span data-stu-id="10c87-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="10c87-124">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="10c87-124">Optional element.</span></span><br /><br /> <span data-ttu-id="10c87-125">Especifica que o registo de erro completa é apresentado quando ocorre um erro ao apresentar um conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="10c87-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="10c87-126">Elemento de WrapTables (formato)</span><span class="sxs-lookup"><span data-stu-id="10c87-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="10c87-127">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="10c87-127">Optional element.</span></span><br /><br /> <span data-ttu-id="10c87-128">Especifica que os dados numa tabela são movidos para a próxima linha se ele não se adequarão a largura da coluna.</span><span class="sxs-lookup"><span data-stu-id="10c87-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="10c87-129">Elementos Principais</span><span class="sxs-lookup"><span data-stu-id="10c87-129">Parent Elements</span></span>

|<span data-ttu-id="10c87-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="10c87-130">Element</span></span>|<span data-ttu-id="10c87-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="10c87-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="10c87-132">Elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="10c87-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="10c87-133">Representa o elemento de nível superior de um ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="10c87-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="10c87-134">Observações</span><span class="sxs-lookup"><span data-stu-id="10c87-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="10c87-135">Veja Também</span><span class="sxs-lookup"><span data-stu-id="10c87-135">See Also</span></span>

[<span data-ttu-id="10c87-136">Elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="10c87-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="10c87-137">Elemento de DisplayError (Frmat)</span><span class="sxs-lookup"><span data-stu-id="10c87-137">DisplayError Element (Frmat)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="10c87-138">Elemento de EnumerableExpansions (formato)</span><span class="sxs-lookup"><span data-stu-id="10c87-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="10c87-139">PropertyCountForTable (formato)</span><span class="sxs-lookup"><span data-stu-id="10c87-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="10c87-140">Elemento de ShowError (formato)</span><span class="sxs-lookup"><span data-stu-id="10c87-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="10c87-141">Elemento de WrapTables (formato)</span><span class="sxs-lookup"><span data-stu-id="10c87-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="10c87-142">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="10c87-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
