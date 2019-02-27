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
# <a name="confirmation-messages"></a>Confirmation Messages (Mensagens de Confirmação)

Seguem-se as mensagens de confirmação diferentes que podem ser apresentadas consoante as variantes do [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [ System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos que são chamados.

> [!IMPORTANT]
> Para o código de exemplo que mostra como pedir confirmações, consulte [como pedido confirmações](./how-to-request-confirmations.md).

## <a name="specifying-the-resource"></a>Especificar o recurso

Pode especificar o recurso que está prestes a ser alterado ao chamar o [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) método. Neste caso, fornecer o recurso utilizando o `target` adicionado o parâmetro do método e a operação pelo Windows PowerShell. A seguinte mensagem, o texto "MyResource" é o recurso analisado e a operação é o nome do comando que faz a chamada.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Se o utilizador seleciona **Sim** ou **Sim para todos** para a confirmação do pedido (conforme mostrado no exemplo a seguir), uma chamada para o [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método é feito, o que faz com que uma mensagem de confirmação segundo a serem exibidos.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>Especificar a operação e recursos

Pode especificar o recurso que está prestes a ser alterado e a operação que o comando está prestes a efetuar ao chamar o [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) método. Neste caso, fornecer o recurso utilizando o `target` parâmetro e a operação utilizando o `target` parâmetro. A seguinte mensagem, o texto "MyResource" é o recurso acionado e "MyAction" é a operação a ser executada.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Se o utilizador seleciona **Sim** ou **Sim para todos** para a mensagem anterior, uma chamada para o [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método é feita, que faz com que um segunda mensagem de confirmação a apresentar.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
