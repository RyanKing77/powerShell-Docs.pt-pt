---
title: Controla o elemento de configuração (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066877"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="73970-102">Controls Element for Configuration (Format) (Elemento Controls para Configuration [Formatação])</span><span class="sxs-lookup"><span data-stu-id="73970-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="73970-103">Define os controles comuns que podem ser utilizados por todas as vistas do ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="73970-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="73970-104">Elemento de controles de elemento (formato) de configuração da configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="73970-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="73970-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73970-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="73970-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="73970-106">Attributes and Elements</span></span>

<span data-ttu-id="73970-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `Controls` elemento.</span><span class="sxs-lookup"><span data-stu-id="73970-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="73970-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="73970-108">Attributes</span></span>

<span data-ttu-id="73970-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="73970-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="73970-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="73970-110">Child Elements</span></span>

|<span data-ttu-id="73970-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="73970-111">Element</span></span>|<span data-ttu-id="73970-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="73970-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73970-113">Elemento de controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="73970-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="73970-114">Elemento necessário.</span><span class="sxs-lookup"><span data-stu-id="73970-114">Required element.</span></span><br /><br /> <span data-ttu-id="73970-115">Define um controle comum que pode ser utilizado por todas as vistas do ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="73970-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="73970-116">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="73970-116">Parent Elements</span></span>

|<span data-ttu-id="73970-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="73970-117">Element</span></span>|<span data-ttu-id="73970-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="73970-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73970-119">Elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="73970-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="73970-120">Representa o elemento de nível superior de um ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="73970-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="73970-121">Observações</span><span class="sxs-lookup"><span data-stu-id="73970-121">Remarks</span></span>

<span data-ttu-id="73970-122">Pode criar qualquer número de controles comuns.</span><span class="sxs-lookup"><span data-stu-id="73970-122">You can create any number of common controls.</span></span> <span data-ttu-id="73970-123">Para cada controle, tem de especificar o nome que é utilizado para referenciar o controle e os componentes do controle.</span><span class="sxs-lookup"><span data-stu-id="73970-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="73970-124">Veja Também</span><span class="sxs-lookup"><span data-stu-id="73970-124">See Also</span></span>

[<span data-ttu-id="73970-125">Elemento de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="73970-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="73970-126">Elemento de controle para controles de configuração (formato)</span><span class="sxs-lookup"><span data-stu-id="73970-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="73970-127">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="73970-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
