---
title: Exemplo de Runspace06 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 471c85f3-9287-45c2-b4bc-833caa1b7634
caps.latest.revision: 8
ms.openlocfilehash: 3850aec88bc800718a82f51c91fbd0cb3c705089
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082656"
---
# <a name="runspace06-sample"></a><span data-ttu-id="87dd9-102">Runspace06 Sample (Exemplo Runspace06)</span><span class="sxs-lookup"><span data-stu-id="87dd9-102">Runspace06 Sample</span></span>

<span data-ttu-id="87dd9-103">Este exemplo mostra como adicionar um módulo para uma [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) de objeto para que o módulo é carregado quando o espaço de execução é aberto.</span><span class="sxs-lookup"><span data-stu-id="87dd9-103">This sample shows how to add a module to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the module is loaded when the runspace is opened.</span></span> <span data-ttu-id="87dd9-104">O módulo fornece um cmdlet de Get-Proc (definido pela [exemplo de GetProcessSample02](../cmdlet/getprocesssample02-sample.md)) que é executado de forma síncrona ao utilizar um [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.</span><span class="sxs-lookup"><span data-stu-id="87dd9-104">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](../cmdlet/getprocesssample02-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="87dd9-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="87dd9-105">Requirements</span></span>

<span data-ttu-id="87dd9-106">Este exemplo requer o Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="87dd9-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="87dd9-107">Demonstra</span><span class="sxs-lookup"><span data-stu-id="87dd9-107">Demonstrates</span></span>

<span data-ttu-id="87dd9-108">Este exemplo demonstra o seguinte.</span><span class="sxs-lookup"><span data-stu-id="87dd9-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="87dd9-109">Criar uma [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto.</span><span class="sxs-lookup"><span data-stu-id="87dd9-109">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="87dd9-110">Adicionar o módulo para o [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto.</span><span class="sxs-lookup"><span data-stu-id="87dd9-110">Adding the module to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="87dd9-111">Criar uma [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) objeto que usa o [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto.</span><span class="sxs-lookup"><span data-stu-id="87dd9-111">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="87dd9-112">Criar uma [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto que utiliza o espaço de execução.</span><span class="sxs-lookup"><span data-stu-id="87dd9-112">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="87dd9-113">A adicionar o cmdlet de get-proc do módulo para o pipeline do [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.</span><span class="sxs-lookup"><span data-stu-id="87dd9-113">Adding the module's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="87dd9-114">Executar o comando de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="87dd9-114">Running the command synchronously.</span></span>

- <span data-ttu-id="87dd9-115">Extração de propriedades a partir da [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objetos devolvidos pelo comando.</span><span class="sxs-lookup"><span data-stu-id="87dd9-115">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="87dd9-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87dd9-116">Example</span></span>

<span data-ttu-id="87dd9-117">Este exemplo cria um espaço de execução que utiliza um [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto para definir os elementos que estão disponíveis quando o espaço de execução é aberto.</span><span class="sxs-lookup"><span data-stu-id="87dd9-117">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="87dd9-118">Neste exemplo, um módulo que define um cmdlet de Get-Proc é adicionado para o estado de sessão inicial.</span><span class="sxs-lookup"><span data-stu-id="87dd9-118">In this sample, a module that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

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
  internal class Runspace06
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a binary module that is loaded by the initial session state.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample02.dll
    /// that is produced by the GetProcessSample02 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a module to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the module's get-proc cmdlet to the PowerShell object.
    /// 6. Running the command synchronously.
    /// 7. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
        // Create the default initial session state and add the module.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      iss.ImportPSModule(new string[] { @".\GetProcessSample02.dll" });

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the cmdlet and specify the runspace.
          powershell.AddCommand(@"GetProcessSample02\get-proc");
          powershell.Runspace = myRunSpace;

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

## <a name="see-also"></a><span data-ttu-id="87dd9-119">Veja Também</span><span class="sxs-lookup"><span data-stu-id="87dd9-119">See Also</span></span>

[<span data-ttu-id="87dd9-120">Escrever um aplicativo de Host de PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="87dd9-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)