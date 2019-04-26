---
title: Elemento de CustomEntry para CustomControl para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066478"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="c0035-102">CustomEntry Element for CustomControl for Controls for Configuration (Format) (Elemento CustomEntry para CustomControl para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="c0035-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="c0035-103">Fornece uma definição do controle comum.</span><span class="sxs-lookup"><span data-stu-id="c0035-103">Provides a definition of the common control.</span></span> <span data-ttu-id="c0035-104">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="c0035-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="c0035-105">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Elemento de CustomEntry de formato) para CustomControl para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="c0035-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c0035-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0035-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c0035-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c0035-107">Attributes and Elements</span></span>

<span data-ttu-id="c0035-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="c0035-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="c0035-109">Tem de especificar os itens exibidos pela definição.</span><span class="sxs-lookup"><span data-stu-id="c0035-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="c0035-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c0035-110">Attributes</span></span>

<span data-ttu-id="c0035-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c0035-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c0035-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="c0035-112">Child Elements</span></span>

|<span data-ttu-id="c0035-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="c0035-113">Element</span></span>|<span data-ttu-id="c0035-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0035-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0035-115">Elemento de EntrySelectedBy para CustomEntry para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="c0035-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="c0035-116">Elemento opcional.</span><span class="sxs-lookup"><span data-stu-id="c0035-116">Optional element.</span></span><br /><br /> <span data-ttu-id="c0035-117">Define os tipos do .NET que utilizam a definição de controle comum ou a condição que tem de existir para este controlo a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="c0035-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="c0035-118">Elemento de CustomItem para CustomEntry para controles de configuração</span><span class="sxs-lookup"><span data-stu-id="c0035-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="c0035-119">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="c0035-119">Required element.</span></span><br /><br /> <span data-ttu-id="c0035-120">Define os dados que são apresentados pelo controle e como ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="c0035-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c0035-121">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="c0035-121">Parent Elements</span></span>

|<span data-ttu-id="c0035-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="c0035-122">Element</span></span>|<span data-ttu-id="c0035-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0035-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0035-124">Elemento de CustomEntries para CustomControl para a configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="c0035-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="c0035-125">Fornece as definições do controle comum.</span><span class="sxs-lookup"><span data-stu-id="c0035-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c0035-126">Observações</span><span class="sxs-lookup"><span data-stu-id="c0035-126">Remarks</span></span>

<span data-ttu-id="c0035-127">Na maioria dos casos, apenas uma definição é necessária para cada controlo personalizado comuns, mas é possível ter várias definições, se pretender utilizar o mesmo controlo para apresentar diferentes objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="c0035-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="c0035-128">Nesses casos, pode fornecer uma definição de separado para cada objeto ou conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="c0035-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0035-129">Veja Também</span><span class="sxs-lookup"><span data-stu-id="c0035-129">See Also</span></span>

[<span data-ttu-id="c0035-130">Elemento de CustomEntries para CustomControl para a configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="c0035-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="c0035-131">Elemento de CustomItem para CustomEntry para controles de configuração</span><span class="sxs-lookup"><span data-stu-id="c0035-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="c0035-132">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0035-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
