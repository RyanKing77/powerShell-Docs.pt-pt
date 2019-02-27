---
title: Declaração de atributo ValidateLength | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: 1e8364c78abba5272007019550ffcb2cedaf9fd0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848819"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="ea1f3-102">ValidateLength Attribute Declaration (Declaração do Atributo ValidateLength)</span><span class="sxs-lookup"><span data-stu-id="ea1f3-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="ea1f3-103">O atributo de ValidateLength Especifica o número mínimo e máximo de carateres para um argumento do parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ea1f3-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="ea1f3-104">Este atributo também pode ser utilizado por funções do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea1f3-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="ea1f3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea1f3-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="ea1f3-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ea1f3-106">Parameters</span></span>

<span data-ttu-id="ea1f3-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span><span class="sxs-lookup"><span data-stu-id="ea1f3-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="ea1f3-108">Especifica o número mínimo de carateres permitidos.</span><span class="sxs-lookup"><span data-stu-id="ea1f3-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="ea1f3-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span><span class="sxs-lookup"><span data-stu-id="ea1f3-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="ea1f3-110">Especifica o número máximo de carateres permitidos.</span><span class="sxs-lookup"><span data-stu-id="ea1f3-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea1f3-111">Observações</span><span class="sxs-lookup"><span data-stu-id="ea1f3-111">Remarks</span></span>

- <span data-ttu-id="ea1f3-112">Para obter mais informações sobre como declarar este atributo, consulte [como as regras de validação de entrada declarar](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="ea1f3-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>
- <span data-ttu-id="ea1f3-113">Para obter mais informações sobre como declarar este atributo, consulte [como as regras de validação de entrada declarar](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="ea1f3-113">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="ea1f3-114">Quando esse atributo não for utilizado, o argumento do parâmetro correspondente pode ter qualquer comprimento.</span><span class="sxs-lookup"><span data-stu-id="ea1f3-114">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="ea1f3-115">O tempo de execução do Windows PowerShell emite um erro nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="ea1f3-115">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="ea1f3-116">Quando o valor do `MaxLength` parametr atributu é inferior ao valor da `MinLength` atributo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ea1f3-116">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="ea1f3-117">Quando o `MaxLength` parâmetro de atributo é definido como 0.</span><span class="sxs-lookup"><span data-stu-id="ea1f3-117">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="ea1f3-118">Quando o argumento não é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ea1f3-118">When the argument is not a string.</span></span>

- <span data-ttu-id="ea1f3-119">O atributo ValidateLength é definido pela [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="ea1f3-119">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea1f3-120">Veja Também</span><span class="sxs-lookup"><span data-stu-id="ea1f3-120">See Also</span></span>

[<span data-ttu-id="ea1f3-121">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="ea1f3-121">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="ea1f3-122">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea1f3-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
