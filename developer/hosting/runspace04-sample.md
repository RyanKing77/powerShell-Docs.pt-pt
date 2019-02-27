---
title: Exemplo de Runspace04 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6a04f15-b5d8-475b-ac9c-e75c58ec8933
caps.latest.revision: 8
ms.openlocfilehash: 9e8123e9b1068e0fd6efec8508eacf594ff22301
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845935"
---
# <a name="runspace04-sample"></a><span data-ttu-id="61609-102">Runspace04 Sample (Exemplo Runspace04)</span><span class="sxs-lookup"><span data-stu-id="61609-102">Runspace04 Sample</span></span>

<span data-ttu-id="61609-103">Este exemplo mostra como utilizar o [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe para executar comandos e como erros de terminação de catch que forem lançadas. quando executar os comandos.</span><span class="sxs-lookup"><span data-stu-id="61609-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span> <span data-ttu-id="61609-104">Dois comandos são executados, e o último comando é passado um argumento de parâmetro que não é válido.</span><span class="sxs-lookup"><span data-stu-id="61609-104">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span> <span data-ttu-id="61609-105">Como resultado, não existem objetos são devolvidos e um erro de terminação é lançado.</span><span class="sxs-lookup"><span data-stu-id="61609-105">As a result, no objects are returned and a terminating error is thrown.</span></span>

## <a name="requirements"></a><span data-ttu-id="61609-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61609-106">Requirements</span></span>

<span data-ttu-id="61609-107">Este exemplo requer o Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="61609-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="61609-108">Demonstra</span><span class="sxs-lookup"><span data-stu-id="61609-108">Demonstrates</span></span>

<span data-ttu-id="61609-109">Este exemplo demonstra o seguinte.</span><span class="sxs-lookup"><span data-stu-id="61609-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="61609-110">Criar uma [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.</span><span class="sxs-lookup"><span data-stu-id="61609-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="61609-111">Adicionar os comandos para o pipeline do [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.</span><span class="sxs-lookup"><span data-stu-id="61609-111">Adding commands to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="61609-112">Adição de argumentos de parâmetro no pipeline.</span><span class="sxs-lookup"><span data-stu-id="61609-112">Adding parameter arguments to the pipeline.</span></span>

- <span data-ttu-id="61609-113">Invocar os comandos de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="61609-113">Invoking the commands synchronously.</span></span>

- <span data-ttu-id="61609-114">Usando [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objetos para extrair e apresentar as propriedades dos objetos devolvidos pelos comandos.</span><span class="sxs-lookup"><span data-stu-id="61609-114">Using [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects to extract and display properties from the objects returned by the commands.</span></span>

- <span data-ttu-id="61609-115">A obter e apresentar os registos de erro que foram gerados durante a execução dos comandos.</span><span class="sxs-lookup"><span data-stu-id="61609-115">Retrieving and displaying error records that were generated during the running of the commands.</span></span>

- <span data-ttu-id="61609-116">Capturando e exibindo a terminação exceções acionadas pelos comandos.</span><span class="sxs-lookup"><span data-stu-id="61609-116">Catching and displaying terminating exceptions thrown by the commands.</span></span>

## <a name="example"></a><span data-ttu-id="61609-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="61609-117">Example</span></span>

<span data-ttu-id="61609-118">Este exemplo executa os comandos de forma síncrona de espaço de execução padrão fornecido pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="61609-118">This sample runs commands synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="61609-119">O último comando gera um erro de terminação, uma vez que um argumento de parâmetro que não é válido é passado para o comando.</span><span class="sxs-lookup"><span data-stu-id="61609-119">The last command throws a terminating error because a parameter argument that is not valid is passed to the command.</span></span> <span data-ttu-id="61609-120">O erro de terminação é interceptado e apresentado.</span><span class="sxs-lookup"><span data-stu-id="61609-120">The terminating error is trapped and displayed.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace04
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run commands.
    /// The commands generate a terminating exception that the caller
    /// should catch and process.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run commands.
    /// 2. Adding commands to the pipeline of  the PowerShell object.
    /// 3. Passing input objects to the commands from the calling program.
    /// 4. Using PSObject objects to extract and display properties from the
    ///    objects returned by the commands.
    /// 5. Retrieving and displaying error records that were generated
    ///    while running the commands.
    /// 6. Catching and displaying terminating exceptions generated
    ///    while running the commands.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object.
      using (PowerShell powershell = PowerShell.Create())
      {
        // Add the commands to the PowerShell object.
        powershell.AddCommand("Get-ChildItem").AddCommand("Select-String").AddArgument("*");

        // Run the commands synchronously. Because of the bad regular expression,
        // no objects will be returned. Instead, an exception will be thrown.
        try
        {
          foreach (PSObject result in powershell.Invoke())
          {
            Console.WriteLine("'{0}'", result.ToString());
          }

          // Process any error records that were generated while running the commands.
          Console.WriteLine("\nThe following non-terminating errors occurred:\n");
          PSDataCollection<ErrorRecord> errors = powershell.Streams.Error;
          if (errors != null && errors.Count > 0)
          {
            foreach (ErrorRecord err in errors)
            {
              System.Console.WriteLine("    error: {0}", err.ToString());
            }
          }
        }
        catch (RuntimeException runtimeException)
        {
          // Trap any exception generated by the commands. These exceptions
          // will all be derived from the RuntimeException exception.
          System.Console.WriteLine(
                        "Runtime exception: {0}: {1}\n{2}",
                        runtimeException.ErrorRecord.InvocationInfo.InvocationName,
                        runtimeException.Message,
                        runtimeException.ErrorRecord.InvocationInfo.PositionMessage);
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="61609-121">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="61609-121">See Also</span></span>

[<span data-ttu-id="61609-122">Escrever um aplicativo de Host de PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="61609-122">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)