---
title: Mensagens de confirmação | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 75214a3fe4bc019836f75db19fb873bd081f200f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850604"
---
# <a name="confirmation-messages"></a><span data-ttu-id="7230e-102">Confirmation Messages (Mensagens de Confirmação)</span><span class="sxs-lookup"><span data-stu-id="7230e-102">Confirmation Messages</span></span>

<span data-ttu-id="7230e-103">Seguem-se as mensagens de confirmação diferentes que podem ser apresentadas consoante as variantes do [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [ System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos que são chamados.</span><span class="sxs-lookup"><span data-stu-id="7230e-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7230e-104">Para o código de exemplo que mostra como pedir confirmações, consulte [como pedido confirmações](./how-to-request-confirmations.md).</span><span class="sxs-lookup"><span data-stu-id="7230e-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="7230e-105">Especificar o recurso</span><span class="sxs-lookup"><span data-stu-id="7230e-105">Specifying the Resource</span></span>

<span data-ttu-id="7230e-106">Pode especificar o recurso que está prestes a ser alterado ao chamar o [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) método.</span><span class="sxs-lookup"><span data-stu-id="7230e-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="7230e-107">Neste caso, fornecer o recurso utilizando o `target` adicionado o parâmetro do método e a operação pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7230e-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="7230e-108">A seguinte mensagem, o texto "MyResource" é o recurso analisado e a operação é o nome do comando que faz a chamada.</span><span class="sxs-lookup"><span data-stu-id="7230e-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="7230e-109">Se o utilizador seleciona **Sim** ou **Sim para todos** para a confirmação do pedido (conforme mostrado no exemplo a seguir), uma chamada para o [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método é feito, o que faz com que uma mensagem de confirmação segundo a serem exibidos.</span><span class="sxs-lookup"><span data-stu-id="7230e-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="7230e-110">Especificar a operação e recursos</span><span class="sxs-lookup"><span data-stu-id="7230e-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="7230e-111">Pode especificar o recurso que está prestes a ser alterado e a operação que o comando está prestes a efetuar ao chamar o [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) método.</span><span class="sxs-lookup"><span data-stu-id="7230e-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="7230e-112">Neste caso, fornecer o recurso utilizando o `target` parâmetro e a operação utilizando o `target` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7230e-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="7230e-113">A seguinte mensagem, o texto "MyResource" é o recurso acionado e "MyAction" é a operação a ser executada.</span><span class="sxs-lookup"><span data-stu-id="7230e-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="7230e-114">Se o utilizador seleciona **Sim** ou **Sim para todos** para a mensagem anterior, uma chamada para o [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método é feita, que faz com que um segunda mensagem de confirmação a apresentar.</span><span class="sxs-lookup"><span data-stu-id="7230e-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="7230e-115">Veja Também</span><span class="sxs-lookup"><span data-stu-id="7230e-115">See Also</span></span>

[<span data-ttu-id="7230e-116">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7230e-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
