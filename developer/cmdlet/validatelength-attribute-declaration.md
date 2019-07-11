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
ms.openlocfilehash: a25fa2410fcc6803563573596af1bc99052c3ffa
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735104"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="9d2b7-102">ValidateLength Attribute Declaration (Declaração do Atributo ValidateLength)</span><span class="sxs-lookup"><span data-stu-id="9d2b7-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="9d2b7-103">O atributo de ValidateLength Especifica o número mínimo e máximo de carateres para um argumento do parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9d2b7-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="9d2b7-104">Este atributo também pode ser utilizado por funções do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d2b7-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="9d2b7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d2b7-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="9d2b7-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9d2b7-106">Parameters</span></span>

<span data-ttu-id="9d2b7-107">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span><span class="sxs-lookup"><span data-stu-id="9d2b7-107">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="9d2b7-108">Especifica o número mínimo de carateres permitidos.</span><span class="sxs-lookup"><span data-stu-id="9d2b7-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="9d2b7-109">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span><span class="sxs-lookup"><span data-stu-id="9d2b7-109">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="9d2b7-110">Especifica o número máximo de carateres permitidos.</span><span class="sxs-lookup"><span data-stu-id="9d2b7-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d2b7-111">Observações</span><span class="sxs-lookup"><span data-stu-id="9d2b7-111">Remarks</span></span>

- <span data-ttu-id="9d2b7-112">Para obter mais informações sobre como declarar este atributo, consulte [como as regras de validação de entrada declarar](./how-to-validate-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="9d2b7-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="9d2b7-113">Quando esse atributo não for utilizado, o argumento do parâmetro correspondente pode ter qualquer comprimento.</span><span class="sxs-lookup"><span data-stu-id="9d2b7-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="9d2b7-114">O tempo de execução do Windows PowerShell emite um erro nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="9d2b7-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="9d2b7-115">Quando o valor do `MaxLength` parametr atributu é inferior ao valor da `MinLength` atributo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9d2b7-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="9d2b7-116">Quando o `MaxLength` parâmetro de atributo é definido como 0.</span><span class="sxs-lookup"><span data-stu-id="9d2b7-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="9d2b7-117">Quando o argumento não é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9d2b7-117">When the argument is not a string.</span></span>

- <span data-ttu-id="9d2b7-118">O atributo ValidateLength é definido pela [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="9d2b7-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d2b7-119">Veja Também</span><span class="sxs-lookup"><span data-stu-id="9d2b7-119">See Also</span></span>

[<span data-ttu-id="9d2b7-120">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="9d2b7-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="9d2b7-121">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d2b7-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
