---
title: Como solicitar confirmações | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 8cfbcacf93733667ffba63a252c86518c0919b57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851997"
---
# <a name="how-to-request-confirmations"></a>How to Request Confirmations (Como Pedir Confirmações)

Este exemplo mostra como chamar o [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos para pedir confirmações das utilizador antes de uma ação está a ser utilizada.

> [!IMPORTANT]
> Para obter mais informações sobre como o Windows PowerShell manipula estes pedidos, consulte [pedir confirmação](./requesting-confirmation-from-cmdlets.md).

## <a name="to-request-confirmation"></a>Para pedir a confirmação

1. Certifique-se de que o `SupportsShouldProcess` parâmetro do Cmdlet atributo estiver definido como `true`. (Para as funções é um parâmetro do atributo CmdletBinding.)

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. Adicionar um `Force` parâmetro ao seu cmdlet para que o utilizador pode ignorar um pedido de confirmação.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. Adicionar uma `if` instrução que utiliza o valor de retorno a [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método para determinar se o [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método é chamado.

4. Adicione um segundo `if` instrução que utiliza o valor de retorno a [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método e o valor da `Force` parâmetro para determinar se a operação deve ser efetuar.

## <a name="example"></a>Exemplo

No exemplo de código a seguir, o [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos são chamados de dentro do substituição do [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método. No entanto, também pode chamar esses métodos de entrada outra métodos de processamento.

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
