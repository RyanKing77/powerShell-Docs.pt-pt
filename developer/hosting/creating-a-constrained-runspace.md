---
title: Criar um espaço de execução restrito | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59125e65-7030-40bb-9926-756120b2d952
caps.latest.revision: 5
ms.openlocfilehash: 20ac1e2af8e047b8b572d86a55439676aa8df25c
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301383"
---
# <a name="creating-a-constrained-runspace"></a>Creating a constrained runspace (Criar um espaço de execução restrito)

Por motivos de segurança ou de desempenho, pode querer restringir os comandos do Windows PowerShell disponíveis para seu aplicativo host. Para fazer isso é criar vazio [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) chamando o [System.Management.Automation.Runspaces.Initialsessionstate.Create*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) método, e, em seguida, adicione apenas os comandos que quer estão disponíveis.

 A utilização de um espaço de execução que carrega apenas os comandos que especificar fornece um desempenho significativamente melhorado.

 Usar os métodos do [System.Management.Automation.Runspaces.Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) classe para definir os cmdlets para o estado da sessão inicial.

 Também pode tornar comandos privado. Comandos privados podem ser utilizados pelo aplicativo host, mas não por usuários do aplicativo.

## <a name="adding-commands-to-an-empty-runspace"></a>Adicionar os comandos para um espaço de execução vazio

 O exemplo seguinte demonstra como criar um InitialSessionState vazio e adicionar os comandos a ele.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using Microsoft.PowerShell.Commands;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class Runspace10b
  {
    /// <summary>
    /// This sample shows how to create an empty initial session state,
    /// how to add commands to the session state, and then how to create a
    /// runspace that has only those two commands. A PowerShell object
    /// is used to run the Get-Command cmdlet to show that only two commands
    /// are available.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create an empty InitialSessionState and then add two commands.
      InitialSessionState iss = InitialSessionState.Create();

      // Add the Get-Process and Get-Command cmdlets to the session state.
      SessionStateCmdletEntry ssce1 = new SessionStateCmdletEntry(
                                                            "get-process",
                                                            typeof(GetProcessCommand),
                                                            null);
      iss.Commands.Add(ssce1);

      SessionStateCmdletEntry ssce2 = new SessionStateCmdletEntry(
                                                            "get-command",
                                                            typeof(GetCommandCommand),
                                                            null);
      iss.Commands.Add(ssce2);

      // Create a runspace.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Create a pipeline with the Get-Command command.
          powershell.AddCommand("get-command");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Verb                 Noun");
          Console.WriteLine("----------------------------");

          // Display each result object.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                             "{0,-20} {1}",
                             result.Members["verb"].Value,
                             result.Members["Noun"].Value);
          }
        }

        // Close the runspace and release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="making-commands-private"></a>Tornando os comandos privada

 Também pode tornar um comando privada, ao defini-la da [System.Management.Automation.Commandinfo.Visibility](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) propriedade [System.Management.Automation.SessionStateEntryVisibility](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility) **Privada**. O aplicativo de host e outros comandos que podem chamar esse comando, mas o utilizador da aplicação não é possível. No exemplo a seguir, o [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) comando é privado.

```csharp
defaultSessionState = InitialSessionState.CreateDefault();
commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;

this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
this.runspace.Open();
```

## <a name="see-also"></a>Veja Também

 [Criar um InitialSessionState](./creating-an-initialsessionstate.md)
