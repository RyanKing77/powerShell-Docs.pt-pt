---
title: Como invocar um Cmdlet a partir de um Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: d4564b51b74422cdaec3878b227ffc6be7c97949
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846733"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="97a6c-102">How to Invoke a Cmdlet from Within a Cmdlet (Como Invocar um Cmdlet num Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="97a6c-102">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="97a6c-103">Este exemplo mostra como invocar um cmdlet a partir de outro cmdlet, o que permite-lhe adicionar a funcionalidade do cmdlet invocado para o cmdlet que está a desenvolver.</span><span class="sxs-lookup"><span data-stu-id="97a6c-103">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="97a6c-104">Neste exemplo, o `Get-Process` cmdlet é invocado para obter os processos que estão em execução no computador local.</span><span class="sxs-lookup"><span data-stu-id="97a6c-104">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="97a6c-105">A chamada para o `Get-Process` cmdlet equivale a ter o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="97a6c-105">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="97a6c-106">Este comando obtém todos os processos cujos nomes começam com os carateres "a" através de "t".</span><span class="sxs-lookup"><span data-stu-id="97a6c-106">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="97a6c-107">Pode invocar apenas esses cmdlets que derivam diretamente a partir da [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe.</span><span class="sxs-lookup"><span data-stu-id="97a6c-107">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="97a6c-108">Não é possível invocar um cmdlet que deriva de [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.</span><span class="sxs-lookup"><span data-stu-id="97a6c-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="97a6c-109">Para invocar um cmdlet a partir de um cmdlet</span><span class="sxs-lookup"><span data-stu-id="97a6c-109">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="97a6c-110">Certifique-se de que o assembly que define o cmdlet a ser invocado é referenciado e que o adequado `using` instrução é adicionada.</span><span class="sxs-lookup"><span data-stu-id="97a6c-110">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="97a6c-111">Neste exemplo, os espaços de nomes seguintes são adicionados.</span><span class="sxs-lookup"><span data-stu-id="97a6c-111">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="97a6c-112">A entrada a processar o método do cmdlet, crie uma nova instância do cmdlet para ser invocada.</span><span class="sxs-lookup"><span data-stu-id="97a6c-112">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="97a6c-113">Neste exemplo, um objeto do tipo [Microsoft.Powershell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) é criado, juntamente com a cadeia de caracteres que contém os argumentos que são utilizados quando o cmdlet é invocado.</span><span class="sxs-lookup"><span data-stu-id="97a6c-113">In this example, an object of type [Microsoft.Powershell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="97a6c-114">Chamar o [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método para invocar o `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="97a6c-114">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="97a6c-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="97a6c-115">Example</span></span>

<span data-ttu-id="97a6c-116">Neste exemplo, o `Get-Process` cmdlet é invocado a partir de [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método de um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="97a6c-116">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;   // Windows PowerShell assembly.
using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify an
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "GreetingInvoke")]
  public class SendGreetingInvokeCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the BeginProcessing method to invoke
    // the Get-Process cmdlet.
    protected override void BeginProcessing()
    {
      GetProcessCommand gp = new GetProcessCommand();
      gp.Name = new string[] { "[a-t]*" };
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="97a6c-117">Veja Também</span><span class="sxs-lookup"><span data-stu-id="97a6c-117">See Also</span></span>

[<span data-ttu-id="97a6c-118">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="97a6c-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
