---
title: Elemento de CustomEntries para CustomControl para controles de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066605"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="58594-102">CustomEntries Element for CustomControl for Controls for Configuration (Format) (Elemento CustomEntries para CustomControl para Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="58594-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="58594-103">Fornece definições de um controle comum.</span><span class="sxs-lookup"><span data-stu-id="58594-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="58594-104">Este elemento é utilizado ao definir um controlo comuns que pode ser utilizado por todas as vistas no ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="58594-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="58594-105">Elemento de controles de elemento (formato) de configuração do elemento de controle de configuração (formato) para controles para o elemento de CustomControl de configuração (formato) para controlo de configuração (formato) CustomEntries elemento para CustomControl para configuração ( Formato)</span><span class="sxs-lookup"><span data-stu-id="58594-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="58594-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58594-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="58594-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="58594-107">Attributes and Elements</span></span>

<span data-ttu-id="58594-108">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `CustomEntries` elemento.</span><span class="sxs-lookup"><span data-stu-id="58594-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="58594-109">Tem de especificar um ou mais elementos subordinados.</span><span class="sxs-lookup"><span data-stu-id="58594-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="58594-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="58594-110">Attributes</span></span>

<span data-ttu-id="58594-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="58594-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="58594-112">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="58594-112">Child Elements</span></span>

|<span data-ttu-id="58594-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="58594-113">Element</span></span>|<span data-ttu-id="58594-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="58594-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="58594-115">Elemento de CustomEntry para CustomControl para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="58594-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="58594-116">Fornece uma definição do controle comum.</span><span class="sxs-lookup"><span data-stu-id="58594-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="58594-117">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="58594-117">Parent Elements</span></span>

|<span data-ttu-id="58594-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="58594-118">Element</span></span>|<span data-ttu-id="58594-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="58594-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="58594-120">Elemento de CustomControl para controlo de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="58594-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="58594-121">Define um controle comum.</span><span class="sxs-lookup"><span data-stu-id="58594-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="58594-122">Observações</span><span class="sxs-lookup"><span data-stu-id="58594-122">Remarks</span></span>

<span data-ttu-id="58594-123">Na maioria dos casos, um controle tiver apenas uma definição, o que é definida num único `CustomEntry` elemento.</span><span class="sxs-lookup"><span data-stu-id="58594-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="58594-124">No entanto, é possível ter várias definições de se pretender utilizar o mesmo controlo para apresentar diferentes objetos do .NET.</span><span class="sxs-lookup"><span data-stu-id="58594-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="58594-125">Nesses casos, pode definir um `CustomEntry` elemento para cada objeto ou conjunto de objetos.</span><span class="sxs-lookup"><span data-stu-id="58594-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="58594-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="58594-126">See Also</span></span>

[<span data-ttu-id="58594-127">Elemento de CustomControl para controlo de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="58594-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="58594-128">Elemento de CustomEntry para CustomControl para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="58594-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="58594-129">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="58594-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
