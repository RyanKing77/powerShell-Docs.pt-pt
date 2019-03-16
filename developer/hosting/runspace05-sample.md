---
title: Exemplo de Runspace05 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1685cfc4-b32c-4bed-b221-e0c4482db955
caps.latest.revision: 9
ms.openlocfilehash: eb227b5fa5e91f59b6fc99981ff5affca1cf63fd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056452"
---
# <a name="runspace05-sample"></a><span data-ttu-id="e5a9d-102">Runspace05 Sample (Exemplo Runspace05)</span><span class="sxs-lookup"><span data-stu-id="e5a9d-102">Runspace05 Sample</span></span>

<span data-ttu-id="e5a9d-103">Este exemplo mostra como adicionar um snap-in para uma [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) de objeto para que o cmdlet do snap-in está disponível quando o espaço de execução é aberto.</span><span class="sxs-lookup"><span data-stu-id="e5a9d-103">This sample shows how to add a snap-in to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span> <span data-ttu-id="e5a9d-104">O snap-in fornece um cmdlet de Get-Proc (definido pela [exemplo de GetProcessSample01](../cmdlet/getprocesssample01-sample.md)) que é executado de forma síncrona ao utilizar um [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.</span><span class="sxs-lookup"><span data-stu-id="e5a9d-104">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](../cmdlet/getprocesssample01-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5a9d-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e5a9d-105">Requirements</span></span>

<span data-ttu-id="e5a9d-106">Este exemplo requer o Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="e5a9d-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e5a9d-107">Demonstra</span><span class="sxs-lookup"><span data-stu-id="e5a9d-107">Demonstrates</span></span>

<span data-ttu-id="e5a9d-108">Este exemplo demonstra o seguinte.</span><span class="sxs-lookup"><span data-stu-id="e5a9d-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="e5a9d-109">Criar uma [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto.</span><span class="sxs-lookup"><span data-stu-id="e5a9d-109">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="e5a9d-110">Adicionar o snap-in para o [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto.</span><span class="sxs-lookup"><span data-stu-id="e5a9d-110">Adding the snap-in to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="e5a9d-111">Criar uma [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) objeto que usa o [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto.</span><span class="sxs-lookup"><span data-stu-id="e5a9d-111">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="e5a9d-112">Criar uma [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto que utiliza o espaço de execução.</span><span class="sxs-lookup"><span data-stu-id="e5a9d-112">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="e5a9d-113">Adicionar o snap-in do cmdlet de get-proc para o pipeline do [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.</span><span class="sxs-lookup"><span data-stu-id="e5a9d-113">Adding the snap-in's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="e5a9d-114">Executar o comando de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="e5a9d-114">Running the command synchronously.</span></span>

- <span data-ttu-id="e5a9d-115">Extração de propriedades a partir da [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objetos devolvidos pelo comando.</span><span class="sxs-lookup"><span data-stu-id="e5a9d-115">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="e5a9d-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e5a9d-116">Example</span></span>

<span data-ttu-id="e5a9d-117">Este exemplo cria um espaço de execução que utiliza um [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto para definir os elementos que estão disponíveis quando o espaço de execução é aberto.</span><span class="sxs-lookup"><span data-stu-id="e5a9d-117">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="e5a9d-118">Neste exemplo, um snap-in que define um cmdlet de Get-Proc, é adicionado para o estado de sessão inicial.</span><span class="sxs-lookup"><span data-stu-id="e5a9d-118">In this sample, a snap-in that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace05
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a Windows PowerShell snap-in that is present in the console file.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample01.dll
    /// that is produced by the GetProcessSample01 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a snap-in to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the snap-in's get-proc cmdlet to the PowerShell object.
    /// 6. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create the default initial session state. The default initial
      // session state contains all the elements provided by Windows
      // PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      PSSnapInException warning;
      iss.ImportPSSnapIn("GetProcPSSnapIn01", out warning);

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the snap-in cmdlet and specify the runspace.
          powershell.AddCommand("GetProcPSSnapIn01\\get-proc");
          powershell.Runspace = myRunSpace;

          // Run the cmdlet synchronously.
          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the results.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                              "{0,-20} {1}",
                              result.Members["ProcessName"].Value,
                              result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release any resources.
        myRunSpace.Close();
      }
      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="e5a9d-119">Veja Também</span><span class="sxs-lookup"><span data-stu-id="e5a9d-119">See Also</span></span>

[<span data-ttu-id="e5a9d-120">Escrever um aplicativo de Host de PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="e5a9d-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)