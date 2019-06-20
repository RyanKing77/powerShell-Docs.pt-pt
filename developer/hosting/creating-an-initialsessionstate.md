---
title: Criar um InitialSessionState | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: 9140d03e046def2fbbcc2a842b9ea1b9e1fa2985
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263844"
---
# <a name="creating-an-initialsessionstate"></a>Creating an InitialSessionState (Criar um espaço de execução InitialSessionState)

Executam comandos do PowerShell num espaço de execução.
Para hospedar o PowerShell na sua aplicação, tem de criar uma [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) objeto.
Cada espaço de execução tem um [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto associado ao mesmo.
O InitialSessionState Especifica características do espaço de execução, tais como que comandos, variáveis e módulos estão disponíveis para esse espaço de execução.

## <a name="create-a-default-initialsessionstate"></a>Criar um padrão InitialSessionState

O [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) e [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) métodos para o **InitialSessionState** classe pode ser usada para criar um **InitialSessionState**objeto.
O **CreateDefault** método cria uma **InitialSessionState** com todos os comandos internos carregados, ao mesmo tempo o **CreateDefault2** método carrega apenas os comandos necessário para hospedar o PowerShell (os comandos do módulo Microsoft.PowerShell.Core).

Se pretender limitar ainda mais os comandos disponíveis na sua aplicação anfitriã terá de criar um espaço de execução restrito.
Para obter informações, consulte [criar um espaço de execução restrito](creating-a-constrained-runspace.md).

O código seguinte mostra como criar uma **InitialSessionState**, atribuí-lo a um espaço de execução, adicionar comandos para o pipeline, esse espaço de execução e invocar os comandos.
Para obter mais informações sobre como adicionar e invocar comandos, consulte [adicionar e invocar comandos](adding-and-invoking-commands.md).

```csharp
namespace SampleHost
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  class HostP4b
  {
    static void Main(string[] args)
    {
      // Call the InitialSessionState.CreateDefault method to create
      // an empty InitialSessionState object, and then add the
      // elements that will be available when the runspace is opened.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      SessionStateVariableEntry var1 = new
          SessionStateVariableEntry("test1",
                                    "MyVar1",
                                    "Initial session state MyVar1 test");
      iss.Variables.Add(var1);

      SessionStateVariableEntry var2 = new
          SessionStateVariableEntry("test2",
                                    "MyVar2",
                                    "Initial session state MyVar2 test");
      iss.Variables.Add(var2);

      // Call the RunspaceFactory.CreateRunspace(InitialSessionState)
      // method to create the runspace where the pipeline is run.
      Runspace rs = RunspaceFactory.CreateRunspace(iss);
      rs.Open();

      // Call the PowerShell.Create() method to create the PowerShell object,
      // and then specify the runspace and commands to the pipeline.
      // and create the command pipeline.
      PowerShell ps = PowerShell.Create();
      ps.Runspace = rs;
      ps.AddCommand("Get-Variable");
      ps.AddArgument("test*");

      Console.WriteLine("Variable             Value");
      Console.WriteLine("--------------------------");

      // Call the PowerShell.Invoke() method to run
      // the pipeline synchronously.
      foreach (PSObject result in ps.Invoke())
      {
        Console.WriteLine("{0,-20}{1}",
            result.Members["Name"].Value,
            result.Members["Value"].Value);
      } // End foreach.

      // Close the runspace to free resources.
      rs.Close();

    } // End Main.
  } // End SampleHost.
}
```

## <a name="see-also"></a>Veja Também

[Criar um espaço de execução restrito](creating-a-constrained-runspace.md)

[Adicionar e invocar comandos](adding-and-invoking-commands.md)
