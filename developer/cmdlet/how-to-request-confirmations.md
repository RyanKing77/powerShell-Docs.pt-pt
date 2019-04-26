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
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067846"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="d5dd8-102">How to Request Confirmations (Como Pedir Confirmações)</span><span class="sxs-lookup"><span data-stu-id="d5dd8-102">How to Request Confirmations</span></span>

<span data-ttu-id="d5dd8-103">Este exemplo mostra como chamar o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos para pedir confirmações das utilizador antes de uma ação está a ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="d5dd8-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d5dd8-104">Para obter mais informações sobre como o Windows PowerShell manipula estes pedidos, consulte [pedir confirmação](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="d5dd8-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="d5dd8-105">Para pedir a confirmação</span><span class="sxs-lookup"><span data-stu-id="d5dd8-105">To request confirmation</span></span>

1. <span data-ttu-id="d5dd8-106">Certifique-se de que o `SupportsShouldProcess` parâmetro do Cmdlet atributo estiver definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="d5dd8-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="d5dd8-107">(Para as funções é um parâmetro do atributo CmdletBinding.)</span><span class="sxs-lookup"><span data-stu-id="d5dd8-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="d5dd8-108">Adicionar um `Force` parâmetro ao seu cmdlet para que o utilizador pode ignorar um pedido de confirmação.</span><span class="sxs-lookup"><span data-stu-id="d5dd8-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="d5dd8-109">Adicionar uma `if` instrução que utiliza o valor de retorno a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método para determinar se o [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método é chamado.</span><span class="sxs-lookup"><span data-stu-id="d5dd8-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="d5dd8-110">Adicione um segundo `if` instrução que utiliza o valor de retorno a [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método e o valor da `Force` parâmetro para determinar se a operação deve ser efetuar.</span><span class="sxs-lookup"><span data-stu-id="d5dd8-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="d5dd8-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5dd8-111">Example</span></span>

<span data-ttu-id="d5dd8-112">No exemplo de código a seguir, o [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) e [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos são chamados a partir de substituição do [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="d5dd8-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="d5dd8-113">No entanto, também pode chamar esses métodos de entrada outra métodos de processamento.</span><span class="sxs-lookup"><span data-stu-id="d5dd8-113">However, you can also call these methods from the other input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d5dd8-114">Veja Também</span><span class="sxs-lookup"><span data-stu-id="d5dd8-114">See Also</span></span>

[<span data-ttu-id="d5dd8-115">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5dd8-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
