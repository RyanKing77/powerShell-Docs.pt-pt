---
title: Validação de entrada do parâmetro | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848805"
---
# <a name="validating-parameter-input"></a><span data-ttu-id="47ca8-102">Validating Parameter Input (Validar a Entrada de Parâmetros)</span><span class="sxs-lookup"><span data-stu-id="47ca8-102">Validating Parameter Input</span></span>

<span data-ttu-id="47ca8-103">Windows PowerShell pode validar os argumentos passados para os parâmetros de cmdlet de várias formas.</span><span class="sxs-lookup"><span data-stu-id="47ca8-103">Windows PowerShell can validate the arguments passed to cmdlet parameters in several ways.</span></span> <span data-ttu-id="47ca8-104">Windows PowerShell pode validar o comprimento, o intervalo e o padrão de caracteres do argumento.</span><span class="sxs-lookup"><span data-stu-id="47ca8-104">Windows PowerShell can validate the length, the range, and the pattern of the characters of the argument.</span></span> <span data-ttu-id="47ca8-105">Pode validar o número de argumentos disponíveis (a contagem).</span><span class="sxs-lookup"><span data-stu-id="47ca8-105">It can validate the number of arguments available (the count).</span></span> <span data-ttu-id="47ca8-106">Estas regras de validação são definidas por atributos de validação que são declarados com o atributo de parâmetro em propriedades públicas da classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="47ca8-106">These validation rules are defined by validation attributes that are declared with the Parameter attribute on public properties of the cmdlet class.</span></span>

<span data-ttu-id="47ca8-107">Para validar um argumento do parâmetro, o tempo de execução do Windows PowerShell usa as informações fornecidas pelos atributos de validação para confirmar o valor do parâmetro antes do cmdlet é executado.</span><span class="sxs-lookup"><span data-stu-id="47ca8-107">To validate a parameter argument, the Windows PowerShell runtime uses the information provided by the validation attributes to confirm the value of the parameter before the cmdlet is run.</span></span> <span data-ttu-id="47ca8-108">Se a entrada de parâmetro não for válida, o utilizador recebe uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="47ca8-108">If the parameter input is not valid, the user receives an error message.</span></span> <span data-ttu-id="47ca8-109">Cada parâmetro de validação define uma regra de validação que é imposta pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47ca8-109">Each validation parameter defines a validation rule that is enforced by Windows PowerShell.</span></span>

<span data-ttu-id="47ca8-110">Windows PowerShell impõe as regras de validação com base nos seguintes atributos.</span><span class="sxs-lookup"><span data-stu-id="47ca8-110">Windows PowerShell enforces the validation rules based on the following attributes.</span></span>

<span data-ttu-id="47ca8-111">ValidateCount Especifica o número mínimo e máximo de argumentos que pode aceitar um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="47ca8-111">ValidateCount Specifies the minimum and maximum number of arguments that a parameter can accept.</span></span> <span data-ttu-id="47ca8-112">Para obter mais informações sobre a sintaxe usada para declarar este atributo, consulte [declaração de atributo ValidateCount](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="47ca8-112">For more information about the syntax used to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

<span data-ttu-id="47ca8-113">ValidateLength Especifica o número mínimo e máximo de carateres no argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="47ca8-113">ValidateLength Specifies the minimum and maximum number of characters in the parameter argument.</span></span> <span data-ttu-id="47ca8-114">Para obter mais informações sobre a sintaxe usada para declarar este atributo, consulte [declaração de atributo ValidateLength](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="47ca8-114">For more information about the syntax used to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

<span data-ttu-id="47ca8-115">ValidatePattern Especifica uma expressão regular que valida o argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="47ca8-115">ValidatePattern Specifies a regular expression that validates the parameter argument.</span></span> <span data-ttu-id="47ca8-116">Para obter mais informações sobre a sintaxe usada para declarar este atributo, consulte [declaração de atributo ValidatePattern](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="47ca8-116">For more information about the syntax used to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

<span data-ttu-id="47ca8-117">ValidateRange Especifica os valores mínimos e máximo do argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="47ca8-117">ValidateRange Specifies the minimum and maximum values of the parameter argument.</span></span> <span data-ttu-id="47ca8-118">Para obter mais informações sobre a sintaxe usada para declarar este atributo, consulte [declaração de atributo ValidateRange](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="47ca8-118">For more information about the syntax used to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

<span data-ttu-id="47ca8-119">ValidateSet Especifica os valores válidos para o argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="47ca8-119">ValidateSet Specifies the valid values for the parameter argument.</span></span> <span data-ttu-id="47ca8-120">Para obter mais informações sobre a sintaxe usada para declarar este atributo, consulte [declaração de atributo ValidateSet](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="47ca8-120">For more information about the syntax used to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="47ca8-121">Veja Também</span><span class="sxs-lookup"><span data-stu-id="47ca8-121">See Also</span></span>

[<span data-ttu-id="47ca8-122">Como validar a entrada de parâmetro</span><span class="sxs-lookup"><span data-stu-id="47ca8-122">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

[<span data-ttu-id="47ca8-123">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="47ca8-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
