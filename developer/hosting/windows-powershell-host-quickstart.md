---
title: Guia de introdução do Windows PowerShell anfitrião | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: cc014487a680747ad59437052f79d4576154a1cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082554"
---
# <a name="windows-powershell-host-quickstart"></a>Windows PowerShell Host Quickstart (Guia de Início Rápido de Alojamento do Windows PowerShell)

Para alojar o Windows PowerShell na sua aplicação, utilize o [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe. Essa classe fornece métodos que cria um pipeline de comandos e, em seguida, executar esses comandos num espaço de execução. A forma mais simples de criar um aplicativo host é usar o espaço de execução padrão. O espaço de execução predefinido contém todos os comandos do Windows PowerShell core. Se quiser que o aplicativo para expor apenas um subconjunto dos comandos do Windows PowerShell, tem de criar um espaço de execução personalizado.

## <a name="using-the-default-runspace"></a>Usando o espaço de execução padrão

Para começar, vamos utilizar o espaço de execução padrão e usar os métodos do [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe para adicionar os comandos, parâmetros, instruções e scripts para um pipeline.

### <a name="addcommand"></a>AddCommand

Utilizar o [System.Management.Automation.Powershell.AddCommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) método o [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe adicionar comandos para o pipeline. Por exemplo, suponha que deseja obter a lista de processos em execução na máquina. Segue-se a forma de executar este comando.

1. Criar uma [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) objeto.

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

Se chamar o [System.Management.Automation.Powershell.AddCommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) método mais do que uma vez antes de chamar os [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) método, o resultado das primeiro comando é enviado por pipe para o segundo e assim por diante. Se não pretender encaminhar o resultado de um comando anterior para um comando, adicione-o ao chamar o [System.Management.Automation.Powershell.AddStatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) em vez disso.

### <a name="addparameter"></a>AddParameter

O exemplo anterior executa um único comando sem quaisquer parâmetros. Pode adicionar parâmetros ao comando utilizando o [System.Management.Automation.PSCommand.AddParameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) método por exemplo, o código seguinte obtém uma lista de todos os processos chamados `PowerShell` em execução no máquina.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

Pode adicionar parâmetros adicionais ao chamar [System.Management.Automation.PSCommand.AddParameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repetidamente.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

Também pode adicionar um dicionário de valores e nomes de parâmetros ao chamar o [System.Management.Automation.PowerShell.AddParameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) método.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

Pode simular a criação de batches, utilizando o [System.Management.Automation.PowerShell.AddStatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) método, que adiciona uma instrução adicional no final do pipeline, o código a seguir obtém uma lista de processos em execução com o nome `PowerShell`e, em seguida, obtém a lista de serviços em execução.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

Pode executar um script existente ao chamar o [System.Management.Automation.PowerShell.AddScript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) método. O exemplo seguinte adiciona um script para o pipeline e executa-o. Este exemplo assume que já existe um script chamado `MyScript.ps1` numa pasta chamada `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

Também existe uma versão dos [System.Management.Automation.PowerShell.AddScript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) método que usa um parâmetro booleano denominado `useLocalScope`. Se este parâmetro estiver definido como `true`, em seguida, o script é executado no âmbito do local. O código a seguir será executado o script no escopo local.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>Criar um espaço de execução personalizado

Embora o espaço de execução padrão usado nos exemplos anteriores carrega todos os comandos do Windows PowerShell core, pode criar um espaço de execução personalizado que carrega apenas um determinado subconjunto de todos os comandos. Pode querer fazê-lo para melhorar o desempenho (o carregamento de um grande número de comandos é um impacto no desempenho), ou para restringir a capacidade do utilizador para realizar operações. Um espaço de execução que expõe apenas um número limitado de comandos é chamado de um espaço de execução restrito. Para criar um espaço de execução restrito, utilize o [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) e [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.

### <a name="creating-an-initialsessionstate-object"></a>Criação de um objeto de InitialSessionState

Para criar um espaço de execução personalizado, tem primeiro de criar uma [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto. No exemplo a seguir, usamos o [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) para criar um espaço de execução depois de criar um padrão [System.Management.Automation.Runspaces.InitialSessionState ](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto.

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>Restrição de espaço de execução

No exemplo anterior, criámos uma predefinição [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto que carrega todos da principal interno do Windows PowerShell. Podemos também poderia ter chamado a [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) método para criar um objeto de InitialSessionState que carrega apenas os comandos a Microsoft.PowerShell.Core snap-in. Para criar um espaço de execução mais restrito, tem de criar vazio [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto chamando o [ System.Management.Automation.Runspaces.InitialSessionState.Create*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) método e, em seguida, adicionar comandos para o InitialSessionState.

A utilização de um espaço de execução que carrega apenas os comandos que especificar fornece um desempenho significativamente melhorado.

Usar os métodos do [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) classe para definir os cmdlets para o estado da sessão inicial. O exemplo seguinte cria um Estado de sessão inicial vazio, em seguida, define e adiciona a `Get-Command` e `Import-Module` comandos para o estado da sessão inicial. Podemos, em seguida, crie um espaço de execução restringido por esse Estado de sessão inicial e execute os comandos nesse espaço de execução.

Crie o estado da sessão inicial.

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

Definir e adicionar comandos para o estado da sessão inicial.

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

Criar e abrir o espaço de execução.

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

Executar um comando e mostrar o resultado.

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

Quando executada, a saída desse código será a aparência da seguinte forma.

```powershell
Get-Command
Import-Module
```
