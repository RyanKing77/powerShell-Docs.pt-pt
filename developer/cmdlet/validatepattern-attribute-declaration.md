---
title: Declaração de atributo ValidatePattern | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848826"
---
# <a name="validatepattern-attribute-declaration"></a><span data-ttu-id="998d9-102">ValidatePattern Attribute Declaration (Declaração do Atributo ValidatePattern)</span><span class="sxs-lookup"><span data-stu-id="998d9-102">ValidatePattern Attribute Declaration</span></span>

<span data-ttu-id="998d9-103">O atributo de ValidatePattern Especifica um padrão de expressão regular que valida o argumento de um parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="998d9-103">The ValidatePattern attribute specifies a regular expression pattern that validates the argument of a cmdlet parameter.</span></span> <span data-ttu-id="998d9-104">Este atributo também pode ser utilizado por funções do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="998d9-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="998d9-105">Quando ValidatePattern é invocado dentro de um cmdlet, o tempo de execução do Windows PowerShell converte o argumento do parâmetro de cmdlet numa cadeia de caracteres e, em seguida, compara essa cadeia de caracteres para o padrão fornecido pelo atributo ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="998d9-105">When ValidatePattern is invoked within a cmdlet, the Windows PowerShell runtime converts the argument of the cmdlet parameter to a string and then compares that string to the pattern supplied by the ValidatePattern attribute.</span></span> <span data-ttu-id="998d9-106">O cmdlet é executado apenas se a representação de cadeia de caracteres convertida do argumento e o padrão fornecido corresponde.</span><span class="sxs-lookup"><span data-stu-id="998d9-106">The cmdlet is run only if the converted string representation of the argument and the supplied pattern match.</span></span> <span data-ttu-id="998d9-107">Se não forem iguais, ocorrerá um erro ao tempo de execução do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="998d9-107">If they do not match, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="998d9-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="998d9-108">Syntax</span></span>

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="998d9-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="998d9-109">Parameters</span></span>

<span data-ttu-id="998d9-110">`RegexString` ([System. String](/dotnet/api/System.String)) necessária.</span><span class="sxs-lookup"><span data-stu-id="998d9-110">`RegexString` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="998d9-111">Especifica uma expressão regular que valida o argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="998d9-111">Specifies a regular expression that validates the parameter argument.</span></span>

<span data-ttu-id="998d9-112">Opções ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) opcional chamado de parameter.</span><span class="sxs-lookup"><span data-stu-id="998d9-112">Options ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) Optional named parameter.</span></span> <span data-ttu-id="998d9-113">Especifica uma combinação de bit a bit de [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) sinalizadores que especificam as opções de expressão regular.</span><span class="sxs-lookup"><span data-stu-id="998d9-113">Specifies a bitwise combination of [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) flags that specify regular expression options.</span></span>

## <a name="remarks"></a><span data-ttu-id="998d9-114">Observações</span><span class="sxs-lookup"><span data-stu-id="998d9-114">Remarks</span></span>

- <span data-ttu-id="998d9-115">Este atributo pode ser utilizado apenas uma vez por parâmetro.</span><span class="sxs-lookup"><span data-stu-id="998d9-115">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="998d9-116">Pode utilizar o `Option` parâmetro do atributo para definir mais aprofundadamente o padrão.</span><span class="sxs-lookup"><span data-stu-id="998d9-116">You can use the `Option` parameter of the attribute to further define the pattern.</span></span> <span data-ttu-id="998d9-117">Por exemplo, pode fazer o padrão de maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="998d9-117">For example, you can make the pattern case sensitive.</span></span>

- <span data-ttu-id="998d9-118">Se este atributo é aplicado a uma coleção, cada elemento na coleção tem de corresponder ao padrão.</span><span class="sxs-lookup"><span data-stu-id="998d9-118">If this attribute is applied to a collection, each element in the collection must match the pattern.</span></span>

- <span data-ttu-id="998d9-119">O atributo ValidatePattern é definido pela [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="998d9-119">The ValidatePattern attribute is defined by the [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="998d9-120">Veja Também</span><span class="sxs-lookup"><span data-stu-id="998d9-120">See Also</span></span>

[<span data-ttu-id="998d9-121">System.Management.Automation.Validatepatternattribute</span><span class="sxs-lookup"><span data-stu-id="998d9-121">System.Management.Automation.Validatepatternattribute</span></span>](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[<span data-ttu-id="998d9-122">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="998d9-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
