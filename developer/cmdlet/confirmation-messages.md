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
ms.openlocfilehash: 229725b5b9f1f0082592dcebe11564fd2f630ce1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059478"
---
# <a name="confirmation-messages"></a><span data-ttu-id="9d33f-102">Confirmation Messages (Mensagens de Confirmação)</span><span class="sxs-lookup"><span data-stu-id="9d33f-102">Confirmation Messages</span></span>

<span data-ttu-id="9d33f-103">Seguem-se as mensagens de confirmação diferentes que podem ser apresentadas consoante as variantes do [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue ](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos que são chamados.</span><span class="sxs-lookup"><span data-stu-id="9d33f-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9d33f-104">Para o código de exemplo que mostra como pedir confirmações, consulte [como pedido confirmações](./how-to-request-confirmations.md).</span><span class="sxs-lookup"><span data-stu-id="9d33f-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="9d33f-105">Especificar o recurso</span><span class="sxs-lookup"><span data-stu-id="9d33f-105">Specifying the Resource</span></span>

<span data-ttu-id="9d33f-106">Pode especificar o recurso que está prestes a ser alterado ao chamar o [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) método.</span><span class="sxs-lookup"><span data-stu-id="9d33f-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="9d33f-107">Neste caso, fornecer o recurso utilizando o `target` adicionado o parâmetro do método e a operação pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d33f-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="9d33f-108">A seguinte mensagem, o texto "MyResource" é o recurso analisado e a operação é o nome do comando que faz a chamada.</span><span class="sxs-lookup"><span data-stu-id="9d33f-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="9d33f-109">Se o utilizador seleciona **Sim** ou **Sim para todos** para a confirmação do pedido (conforme mostrado no exemplo a seguir), uma chamada para o [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)método é feito, o que faz com que uma mensagem de confirmação segundo a serem exibidos.</span><span class="sxs-lookup"><span data-stu-id="9d33f-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="9d33f-110">Especificar a operação e recursos</span><span class="sxs-lookup"><span data-stu-id="9d33f-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="9d33f-111">Pode especificar o recurso que está prestes a ser alterado e a operação que o comando está prestes a efetuar ao chamar o [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) método.</span><span class="sxs-lookup"><span data-stu-id="9d33f-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="9d33f-112">Neste caso, fornecer o recurso utilizando o `target` parâmetro e a operação utilizando o `target` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9d33f-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="9d33f-113">A seguinte mensagem, o texto "MyResource" é o recurso acionado e "MyAction" é a operação a ser executada.</span><span class="sxs-lookup"><span data-stu-id="9d33f-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="9d33f-114">Se o utilizador seleciona **Sim** ou **Sim para todos** para a mensagem anterior, uma chamada para o [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método é feita, que faz com que um segunda mensagem de confirmação a apresentar.</span><span class="sxs-lookup"><span data-stu-id="9d33f-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="9d33f-115">Veja Também</span><span class="sxs-lookup"><span data-stu-id="9d33f-115">See Also</span></span>

[<span data-ttu-id="9d33f-116">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d33f-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
