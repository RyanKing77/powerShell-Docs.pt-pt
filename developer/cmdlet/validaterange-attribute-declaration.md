---
title: Declaração de atributo ValidateRange | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847538"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="0b63c-102">ValidateRange Attribute Declaration (Declaração do Atributo ValidateRange)</span><span class="sxs-lookup"><span data-stu-id="0b63c-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="0b63c-103">O atributo de ValidateRange Especifica os valores mínimos e máximo (o intervalo) para o argumento do parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b63c-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="0b63c-104">Este atributo também pode ser utilizado por funções do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0b63c-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="0b63c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b63c-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="0b63c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b63c-106">Parameters</span></span>

<span data-ttu-id="0b63c-107">`MinRange` ([System. Object](/dotnet/api/system.object)) necessária.</span><span class="sxs-lookup"><span data-stu-id="0b63c-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="0b63c-108">Especifica o valor mínimo permitido.</span><span class="sxs-lookup"><span data-stu-id="0b63c-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="0b63c-109">`MaxRange` ([System. Object](/dotnet/api/system.object)) necessária.</span><span class="sxs-lookup"><span data-stu-id="0b63c-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="0b63c-110">Especifica o valor máximo permitido.</span><span class="sxs-lookup"><span data-stu-id="0b63c-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="0b63c-111">Observações</span><span class="sxs-lookup"><span data-stu-id="0b63c-111">Remarks</span></span>

- <span data-ttu-id="0b63c-112">O tempo de execução do Windows PowerShell gera um erro de construção quando o valor do `MinRange` parâmetro é superior ao valor da `MaxRange` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0b63c-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="0b63c-113">O tempo de execução do Windows PowerShell gera um erro de validação nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="0b63c-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="0b63c-114">Quando o valor do argumento é menos do que o `MinRange` limite ou maior do que o `MaxRange` limite.</span><span class="sxs-lookup"><span data-stu-id="0b63c-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="0b63c-115">Quando o argumento não é do mesmo tipo como o `MinRange` e o `MaxRange` parâmetros.</span><span class="sxs-lookup"><span data-stu-id="0b63c-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="0b63c-116">O atributo ValidateRange é definido pela [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="0b63c-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b63c-117">Veja Também</span><span class="sxs-lookup"><span data-stu-id="0b63c-117">See Also</span></span>

[<span data-ttu-id="0b63c-118">System.Management.Automation.Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="0b63c-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="0b63c-119">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b63c-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
