---
title: Os utilizadores pedir confirmação | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067226"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="5b024-102">Users Requesting Confirmation (Confirmação Pedida por Utilizadores)</span><span class="sxs-lookup"><span data-stu-id="5b024-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="5b024-103">Quando especificar um valor de `true` para o `SupportsShouldProcess` parâmetro da declaração de atributo do Cmdlet, os utilizadores podem especificar o `Confirm` parâmetro no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="5b024-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="5b024-104">No ambiente predefinido, os utilizadores podem especificar a `Confirm` parâmetro ou `"-Confirm:$true` , de modo a que for solicitada a confirmação quando o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método é chamado.</span><span class="sxs-lookup"><span data-stu-id="5b024-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="5b024-105">Isso ignora [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) pedidos de confirmação, mesmo para operações de alto impacto.</span><span class="sxs-lookup"><span data-stu-id="5b024-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="5b024-106">Se `Confirm` não for especificado, o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamada pede a confirmação se o `$ConfirmPreference` variável de preferência é igual ou maior do que o `ConfirmImpact` definição do cmdlet ou o fornecedor.</span><span class="sxs-lookup"><span data-stu-id="5b024-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="5b024-107">A predefinição de `$ConfirmPreference` é alta.</span><span class="sxs-lookup"><span data-stu-id="5b024-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="5b024-108">Portanto, no ambiente predefinido, apenas cmdlets e fornecedores que especificam uma ação de alto impacto pedir confirmação.</span><span class="sxs-lookup"><span data-stu-id="5b024-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="5b024-109">Se `Confirm` for false ou se `"-Confirm:$false` for especificado, o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) chamada pede a confirmação do usuário e o `$ConfirmPreference` variável de shell é ignorada.</span><span class="sxs-lookup"><span data-stu-id="5b024-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b024-110">Observações</span><span class="sxs-lookup"><span data-stu-id="5b024-110">Remarks</span></span>

- <span data-ttu-id="5b024-111">Para cmdlets e fornecedores que especificam `SupportsShouldProcess`, mas não `ConfirmImpact`, essas ações são processadas como ações de "impacto intermédio", e eles não pedirá por predefinição.</span><span class="sxs-lookup"><span data-stu-id="5b024-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="5b024-112">O nível de impacto é menor do que a predefinição do `$ConfirmPreference` variável de preferência.</span><span class="sxs-lookup"><span data-stu-id="5b024-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="5b024-113">Se o usuário especificar a `Verbose` parâmetro, este serão notificado de que a operação, mesmo que não são pedidas a confirmação.</span><span class="sxs-lookup"><span data-stu-id="5b024-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b024-114">Veja Também</span><span class="sxs-lookup"><span data-stu-id="5b024-114">See Also</span></span>

[<span data-ttu-id="5b024-115">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5b024-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
