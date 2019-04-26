---
title: Os tipos de atributo | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068664"
---
# <a name="attribute-types"></a><span data-ttu-id="ab81b-102">Attribute Types (Tipos de Atributo)</span><span class="sxs-lookup"><span data-stu-id="ab81b-102">Attribute Types</span></span>

<span data-ttu-id="ab81b-103">Atributos de cmdlet podem ser agrupados por funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="ab81b-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="ab81b-104">As secções seguintes descrevem os atributos disponíveis e descrevem o que faz o tempo de execução quando o atributo é invocado.</span><span class="sxs-lookup"><span data-stu-id="ab81b-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="ab81b-105">Cmdlet Attributes (Atributos de Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="ab81b-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="ab81b-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ab81b-106">Cmdlet</span></span>

<span data-ttu-id="ab81b-107">Identifica uma classe do .NET Framework como um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab81b-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="ab81b-108">Este é o atributo base necessário.</span><span class="sxs-lookup"><span data-stu-id="ab81b-108">This is the required base attribute.</span></span>
<span data-ttu-id="ab81b-109">Para obter mais informações, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ab81b-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="ab81b-110">Atributos de parâmetro</span><span class="sxs-lookup"><span data-stu-id="ab81b-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="ab81b-111">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="ab81b-111">Parameter</span></span>

<span data-ttu-id="ab81b-112">Identifica uma propriedade pública na classe cmdlet como um parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab81b-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="ab81b-113">Para obter mais informações, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ab81b-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="ab81b-114">Alias</span><span class="sxs-lookup"><span data-stu-id="ab81b-114">Alias</span></span>

<span data-ttu-id="ab81b-115">Especifica um ou mais aliases para um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ab81b-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="ab81b-116">Para obter mais informações, consulte [declaração de atributo de Alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ab81b-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="ab81b-117">Atributos de validação de argumento</span><span class="sxs-lookup"><span data-stu-id="ab81b-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="ab81b-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="ab81b-118">ValidateCount</span></span>

<span data-ttu-id="ab81b-119">Especifica o número mínimo e máximo de argumentos que são permitidos para um parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab81b-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="ab81b-120">Para obter mais informações, consulte [declaração de atributo ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ab81b-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="ab81b-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="ab81b-121">ValidateLength</span></span>

<span data-ttu-id="ab81b-122">Especifica um número mínimo e máximo de carateres para um argumento do parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab81b-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="ab81b-123">Para obter mais informações, consulte [declaração de atributo ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ab81b-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="ab81b-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="ab81b-124">ValidatePattern</span></span>

<span data-ttu-id="ab81b-125">Especifica um padrão de expressão regular que o argumento do parâmetro de cmdlet tem de corresponder.</span><span class="sxs-lookup"><span data-stu-id="ab81b-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="ab81b-126">Para obter mais informações, consulte [declaração de atributo ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ab81b-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="ab81b-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="ab81b-127">ValidateRange</span></span>

<span data-ttu-id="ab81b-128">Especifica os valores mínimos e máximo para um argumento do parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab81b-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="ab81b-129">Para obter mais informações, consulte [declaração de atributo ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ab81b-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="ab81b-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="ab81b-130">ValidateSet</span></span>

<span data-ttu-id="ab81b-131">Especifica um conjunto de valores válidos para o argumento do parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab81b-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="ab81b-132">Para obter mais informações, consulte [declaração de atributo ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ab81b-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ab81b-133">Veja Também</span><span class="sxs-lookup"><span data-stu-id="ab81b-133">See Also</span></span>

[<span data-ttu-id="ab81b-134">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ab81b-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
