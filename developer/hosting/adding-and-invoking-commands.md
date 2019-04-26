---
title: Adicionar e invocar comandos | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: 9a01f948c5b474b4f9068030907601543e13cc7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083030"
---
# <a name="adding-and-invoking-commands"></a>Adding and invoking commands (Adicionar comandos de invocação)

Depois de criar um espaço de execução, pode adicionar scripts e PowerShellcommands do Windows para um pipeline e, em seguida, invocar o pipeline de forma síncrona ou assíncrona.

## <a name="creating-a-pipeline"></a>Criar um pipeline

 O [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) classe fornece vários métodos para adicionar os comandos, parâmetros e scripts para o pipeline. É possível invocar o pipeline de forma síncrona chamando uma sobrecarga do [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) método, ou de forma assíncrona chamando uma sobrecarga do [ System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) e, em seguida, o [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) método.

### <a name="addcommand"></a>AddCommand

1. Criar uma [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objeto.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Adicione o comando que pretende executar.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Invoca o comando.

   ```csharp
   ps.Invoke();
   ```

 Se chamar o [System.Management.Automation.Powershell.Addcommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) método mais do que uma vez antes de chamar os [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) método, o resultado das primeiro comando é enviado por pipe para o segundo e assim por diante. Se não pretender encaminhar o resultado de um comando anterior para um comando, adicione-o ao chamar o [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) em vez disso.

### <a name="addparameter"></a>AddParameter

 O exemplo anterior executa um único comando sem quaisquer parâmetros. Pode adicionar parâmetros ao comando utilizando o [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) método por exemplo, o código seguinte obtém uma lista de todos os processos chamados `PowerShell` em execução no máquina.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 Pode adicionar parâmetros adicionais ao chamar [System.Management.Automation.Pscommand.Addparameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repetidamente.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 Também pode adicionar um dicionário de valores e nomes de parâmetros ao chamar o [System.Management.Automation.Powershell.Addparameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) método.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

 Pode simular a criação de batches, utilizando o [System.Management.Automation.Powershell.Addstatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) método, que adiciona uma instrução adicional no final do pipeline, o código a seguir obtém uma lista de processos em execução com o nome `PowerShell`e, em seguida, obtém a lista de serviços em execução.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

 Pode executar um script existente ao chamar o [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) método. O exemplo seguinte adiciona um script para o pipeline e executa-o. Este exemplo assume que já existe um script chamado `MyScript.ps1` numa pasta chamada `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 Também existe uma versão dos [System.Management.Automation.Powershell.Addscript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) método que usa um parâmetro booleano denominado `useLocalScope`. Se este parâmetro estiver definido como `true`, em seguida, o script é executado no âmbito do local. O código a seguir será executado o script no escopo local.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a>Invocar um pipeline de forma síncrona

 Depois de adicionar elementos ao pipeline, invocá-lo. Para invocar o pipeline de forma síncrona, chame uma sobrecarga do [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) método. O exemplo seguinte mostra como sincronicamente invocar um pipeline.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a>Invocar um pipeline de forma assíncrona

 Invocar um pipeline de forma assíncrona chamando uma sobrecarga do [System.Management.Automation.Powershell.Begininvoke*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) para criar um [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) objeto e, em seguida, chamar o [ System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) método.

 O exemplo seguinte mostra como invocar um pipeline de forma assíncrona.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediately
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a>Veja Também

 [Criar um InitialSessionState](./creating-an-initialsessionstate.md)

 [Criar um espaço de execução restrito](./creating-a-constrained-runspace.md)
