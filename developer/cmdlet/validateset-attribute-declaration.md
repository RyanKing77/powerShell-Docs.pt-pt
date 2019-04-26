---
title: Declaração de atributo ValidateSet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067077"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="920e8-102">ValidateSet Attribute Declaration (Declaração do Atributo ValidateSet)</span><span class="sxs-lookup"><span data-stu-id="920e8-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="920e8-103">O atributo de ValidateSetAttribute Especifica um conjunto de valores possíveis para um argumento do parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="920e8-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="920e8-104">Este atributo também pode ser utilizado por funções do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="920e8-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="920e8-105">Quando esse atributo é especificado, o tempo de execução do Windows PowerShell determina se o argumento fornecido para o parâmetro de cmdlet corresponde a um elemento no conjunto de elemento fornecido.</span><span class="sxs-lookup"><span data-stu-id="920e8-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="920e8-106">O cmdlet é executado apenas se o argumento do parâmetro corresponde a um elemento no conjunto.</span><span class="sxs-lookup"><span data-stu-id="920e8-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="920e8-107">Se nenhuma correspondência for encontrada, é gerado um erro ao tempo de execução do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="920e8-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="920e8-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="920e8-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="920e8-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="920e8-109">Parameters</span></span>

<span data-ttu-id="920e8-110">`ValidValues` ([System. String](/dotnet/api/System.String)) necessária.</span><span class="sxs-lookup"><span data-stu-id="920e8-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="920e8-111">Especifica os valores de elemento de parâmetro válido.</span><span class="sxs-lookup"><span data-stu-id="920e8-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="920e8-112">O exemplo a seguir mostra como especificar um elemento ou em vários elementos.</span><span class="sxs-lookup"><span data-stu-id="920e8-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="920e8-113">`IgnoreCase` ([Boolean](/dotnet/api/System.Boolean)) opcional chamado de parameter.</span><span class="sxs-lookup"><span data-stu-id="920e8-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="920e8-114">O valor predefinido de `true` indica que o caso é ignorado.</span><span class="sxs-lookup"><span data-stu-id="920e8-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="920e8-115">Um valor de `false` faz com que o cmdlet diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="920e8-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="920e8-116">Observações</span><span class="sxs-lookup"><span data-stu-id="920e8-116">Remarks</span></span>

- <span data-ttu-id="920e8-117">Este atributo pode ser utilizado apenas uma vez por parâmetro.</span><span class="sxs-lookup"><span data-stu-id="920e8-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="920e8-118">Se o valor do parâmetro é uma matriz, cada elemento da matriz deve coincidir com um elemento do conjunto de atributo.</span><span class="sxs-lookup"><span data-stu-id="920e8-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="920e8-119">O atributo ValidateSetAttribute é definido pela [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="920e8-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="920e8-120">Veja Também</span><span class="sxs-lookup"><span data-stu-id="920e8-120">See Also</span></span>

[<span data-ttu-id="920e8-121">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="920e8-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="920e8-122">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="920e8-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
