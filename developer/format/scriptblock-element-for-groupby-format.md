---
title: Elemento de ScriptBlock para GroupBy (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: f2f6b9af7740b1231881294c2f32bf97b5a1568b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064514"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="8f77d-102">ScriptBlock Element for GroupBy (Format) (Elemento ScriptBlock para GroupBy [Formatação])</span><span class="sxs-lookup"><span data-stu-id="8f77d-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="8f77d-103">Especifica o script que inicia um novo grupo sempre que seu valor é alterado.</span><span class="sxs-lookup"><span data-stu-id="8f77d-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="8f77d-104">O elemento (formato) ViewDefinitions elemento (formato) vista elemento (formato) GroupBy elemento de configuração para o modo de exibição (formato) ScriptBlock elemento para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8f77d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8f77d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f77d-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8f77d-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8f77d-106">Attributes and Elements</span></span>

<span data-ttu-id="8f77d-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `ScriptBlock` elemento.</span><span class="sxs-lookup"><span data-stu-id="8f77d-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8f77d-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="8f77d-108">Attributes</span></span>

<span data-ttu-id="8f77d-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8f77d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8f77d-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="8f77d-110">Child Elements</span></span>

<span data-ttu-id="8f77d-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8f77d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8f77d-112">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="8f77d-112">Parent Elements</span></span>

|<span data-ttu-id="8f77d-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="8f77d-113">Element</span></span>|<span data-ttu-id="8f77d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f77d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f77d-115">GroupBy elemento para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="8f77d-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="8f77d-116">Define como um grupo de objetos do .NET é exibido.</span><span class="sxs-lookup"><span data-stu-id="8f77d-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8f77d-117">Valor de texto</span><span class="sxs-lookup"><span data-stu-id="8f77d-117">Text Value</span></span>

<span data-ttu-id="8f77d-118">Especifique o script que é avaliado.</span><span class="sxs-lookup"><span data-stu-id="8f77d-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="8f77d-119">Observações</span><span class="sxs-lookup"><span data-stu-id="8f77d-119">Remarks</span></span>

<span data-ttu-id="8f77d-120">É iniciado um novo grupo do Windows PowerShell sempre que o valor desse script é alterado.</span><span class="sxs-lookup"><span data-stu-id="8f77d-120">Windows PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="8f77d-121">Quando este elemento é especificado, não é possível especificar a [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) elemento para iniciar um novo grupo.</span><span class="sxs-lookup"><span data-stu-id="8f77d-121">When this element is specified, you cannot specify the [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f77d-122">Veja Também</span><span class="sxs-lookup"><span data-stu-id="8f77d-122">See Also</span></span>

[<span data-ttu-id="8f77d-123">Elemento de PropertyName para GroupBy (formato)</span><span class="sxs-lookup"><span data-stu-id="8f77d-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="8f77d-124">GroupBy elemento para a exibição (formato)</span><span class="sxs-lookup"><span data-stu-id="8f77d-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="8f77d-125">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f77d-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
