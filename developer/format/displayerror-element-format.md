---
title: O elemento de DisplayError (formato) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066265"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="a0480-102">DisplayError Element (Format) (Elemento DisplayError [Formatação])</span><span class="sxs-lookup"><span data-stu-id="a0480-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="a0480-103">Especifica que a cadeia de caracteres #ERR é apresentada quando ocorre um erro de apresentar um conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="a0480-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="a0480-104">Elemento de configuração do DisplayError elemento (formato) DefaultSettings elemento (formato) (formato)</span><span class="sxs-lookup"><span data-stu-id="a0480-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a0480-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0480-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a0480-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a0480-106">Attributes and Elements</span></span>

<span data-ttu-id="a0480-107">As secções seguintes descrevem os atributos e elementos filho e o elemento principal do `DisplayError` elemento.</span><span class="sxs-lookup"><span data-stu-id="a0480-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a0480-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="a0480-108">Attributes</span></span>

<span data-ttu-id="a0480-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a0480-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a0480-110">Elementos subordinados</span><span class="sxs-lookup"><span data-stu-id="a0480-110">Child Elements</span></span>

<span data-ttu-id="a0480-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a0480-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a0480-112">Elementos principais</span><span class="sxs-lookup"><span data-stu-id="a0480-112">Parent Elements</span></span>

|<span data-ttu-id="a0480-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="a0480-113">Element</span></span>|<span data-ttu-id="a0480-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0480-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a0480-115">Elemento de DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="a0480-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="a0480-116">Define configurações comuns que se aplicam a todas as vistas do ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="a0480-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a0480-117">Observações</span><span class="sxs-lookup"><span data-stu-id="a0480-117">Remarks</span></span>

<span data-ttu-id="a0480-118">Por predefinição, quando ocorre um erro ao tentar exibir um conjunto de dados, a localização dos dados é deixada em branco.</span><span class="sxs-lookup"><span data-stu-id="a0480-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="a0480-119">Quando este elemento está definido como true, a cadeia de caracteres #ERR será apresentado.</span><span class="sxs-lookup"><span data-stu-id="a0480-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0480-120">Veja Também</span><span class="sxs-lookup"><span data-stu-id="a0480-120">See Also</span></span>

[<span data-ttu-id="a0480-121">Elemento de DefaultSettings (formato)</span><span class="sxs-lookup"><span data-stu-id="a0480-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="a0480-122">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0480-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
