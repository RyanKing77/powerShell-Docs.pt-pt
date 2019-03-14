---
title: Declaração de atributo ValidateCount | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 4e0be34b6f7a56dcf02a4381de4d2a5d08db14df
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794451"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="66891-102">ValidateCount Attribute Declaration (Declaração do Atributo ValidateCount)</span><span class="sxs-lookup"><span data-stu-id="66891-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="66891-103">O atributo de ValidateCount Especifica o número mínimo e máximo de argumentos permitido para um parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="66891-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="66891-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="66891-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="66891-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="66891-105">Parameters</span></span>

<span data-ttu-id="66891-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span><span class="sxs-lookup"><span data-stu-id="66891-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="66891-107">Especifica o número mínimo de argumentos.</span><span class="sxs-lookup"><span data-stu-id="66891-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="66891-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required.</span><span class="sxs-lookup"><span data-stu-id="66891-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="66891-109">Especifica o número máximo de argumentos.</span><span class="sxs-lookup"><span data-stu-id="66891-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="66891-110">Observações</span><span class="sxs-lookup"><span data-stu-id="66891-110">Remarks</span></span>

- <span data-ttu-id="66891-111">Para obter mais informações sobre como declarar este atributo, consulte [como as regras de validação de entrada declarar](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="66891-111">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="66891-112">Quando esse atributo não é invocado, o parâmetro de cmdlet correspondente pode ter qualquer número de argumentos.</span><span class="sxs-lookup"><span data-stu-id="66891-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="66891-113">O tempo de execução do Windows PowerShell emite um erro nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="66891-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="66891-114">O `MinLength` e `MaxLength` parâmetros de atributo não são do tipo [System.Int32](/dotnet/api/System.Int32).</span><span class="sxs-lookup"><span data-stu-id="66891-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32](/dotnet/api/System.Int32).</span></span>

    - <span data-ttu-id="66891-115">O valor do `MaxLength` parametr atributu é inferior ao valor da `MinLength` atributo de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="66891-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="66891-116">O atributo ValidateCount é definido pela [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) classe.</span><span class="sxs-lookup"><span data-stu-id="66891-116">The ValidateCount attribute is defined by the [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="66891-117">Veja Também</span><span class="sxs-lookup"><span data-stu-id="66891-117">See Also</span></span>

[<span data-ttu-id="66891-118">System.Management.Automation.Validatecount</span><span class="sxs-lookup"><span data-stu-id="66891-118">System.Management.Automation.Validatecount</span></span>](/dotnet/api/System.Management.Automation.ValidateCount)

[<span data-ttu-id="66891-119">Como declarar as regras de validação de entrada</span><span class="sxs-lookup"><span data-stu-id="66891-119">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="66891-120">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="66891-120">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
