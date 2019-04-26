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
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="21918-102">Windows PowerShell Host Quickstart (Guia de Início Rápido de Alojamento do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="21918-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="21918-103">Para alojar o Windows PowerShell na sua aplicação, utilize o [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe.</span><span class="sxs-lookup"><span data-stu-id="21918-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span> <span data-ttu-id="21918-104">Essa classe fornece métodos que cria um pipeline de comandos e, em seguida, executar esses comandos num espaço de execução.</span><span class="sxs-lookup"><span data-stu-id="21918-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span> <span data-ttu-id="21918-105">A forma mais simples de criar um aplicativo host é usar o espaço de execução padrão.</span><span class="sxs-lookup"><span data-stu-id="21918-105">The simplest way to create a host application is to use the default runspace.</span></span> <span data-ttu-id="21918-106">O espaço de execução predefinido contém todos os comandos do Windows PowerShell core.</span><span class="sxs-lookup"><span data-stu-id="21918-106">The default runspace contains all of the core Windows PowerShell commands.</span></span> <span data-ttu-id="21918-107">Se quiser que o aplicativo para expor apenas um subconjunto dos comandos do Windows PowerShell, tem de criar um espaço de execução personalizado.</span><span class="sxs-lookup"><span data-stu-id="21918-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="21918-108">Usando o espaço de execução padrão</span><span class="sxs-lookup"><span data-stu-id="21918-108">Using the default runspace</span></span>

<span data-ttu-id="21918-109">Para começar, vamos utilizar o espaço de execução padrão e usar os métodos do [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe para adicionar os comandos, parâmetros, instruções e scripts para um pipeline.</span><span class="sxs-lookup"><span data-stu-id="21918-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="21918-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="21918-110">AddCommand</span></span>

<span data-ttu-id="21918-111">Utilizar o [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) método o [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe adicionar comandos para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="21918-111">You use the [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands to the pipeline.</span></span> <span data-ttu-id="21918-112">Por exemplo, suponha que deseja obter a lista de processos em execução na máquina.</span><span class="sxs-lookup"><span data-stu-id="21918-112">For example, suppose you want to get the list of running processes on the machine.</span></span> <span data-ttu-id="21918-113">Segue-se a forma de executar este comando.</span><span class="sxs-lookup"><span data-stu-id="21918-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="21918-114">Criar uma [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) objeto.</span><span class="sxs-lookup"><span data-stu-id="21918-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="21918-115">Adicione o comando que pretende executar.</span><span class="sxs-lookup"><span data-stu-id="21918-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="21918-116">Invoca o comando.</span><span class="sxs-lookup"><span data-stu-id="21918-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="21918-117">Se chamar o [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) método mais do que uma vez antes de chamar os [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) método, o resultado das primeiro comando é enviado por pipe para o segundo e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="21918-117">If you call the [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="21918-118">Se não pretender encaminhar o resultado de um comando anterior para um comando, adicione-o ao chamar o [System.Management.Automation.Powershell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="21918-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="21918-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="21918-119">AddParameter</span></span>

<span data-ttu-id="21918-120">O exemplo anterior executa um único comando sem quaisquer parâmetros.</span><span class="sxs-lookup"><span data-stu-id="21918-120">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="21918-121">Pode adicionar parâmetros ao comando utilizando o [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) método por exemplo, o código seguinte obtém uma lista de todos os processos chamados `PowerShell` em execução no máquina.</span><span class="sxs-lookup"><span data-stu-id="21918-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="21918-122">Pode adicionar parâmetros adicionais ao chamar [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repetidamente.</span><span class="sxs-lookup"><span data-stu-id="21918-122">You can add additional parameters by calling [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

<span data-ttu-id="21918-123">Também pode adicionar um dicionário de valores e nomes de parâmetros ao chamar o [System.Management.Automation.PowerShell.AddParameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) método.</span><span class="sxs-lookup"><span data-stu-id="21918-123">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="21918-124">AddStatement</span><span class="sxs-lookup"><span data-stu-id="21918-124">AddStatement</span></span>

<span data-ttu-id="21918-125">Pode simular a criação de batches, utilizando o [System.Management.Automation.PowerShell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) método, que adiciona uma instrução adicional no final do pipeline, o código a seguir obtém uma lista de processos em execução com o nome `PowerShell`e, em seguida, obtém a lista de serviços em execução.</span><span class="sxs-lookup"><span data-stu-id="21918-125">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="21918-126">AddScript</span><span class="sxs-lookup"><span data-stu-id="21918-126">AddScript</span></span>

<span data-ttu-id="21918-127">Pode executar um script existente ao chamar o [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) método.</span><span class="sxs-lookup"><span data-stu-id="21918-127">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="21918-128">O exemplo seguinte adiciona um script para o pipeline e executa-o.</span><span class="sxs-lookup"><span data-stu-id="21918-128">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="21918-129">Este exemplo assume que já existe um script chamado `MyScript.ps1` numa pasta chamada `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="21918-129">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="21918-130">Também existe uma versão dos [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) método que usa um parâmetro booleano denominado `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="21918-130">There is also a version of the [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="21918-131">Se este parâmetro estiver definido como `true`, em seguida, o script é executado no âmbito do local.</span><span class="sxs-lookup"><span data-stu-id="21918-131">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="21918-132">O código a seguir será executado o script no escopo local.</span><span class="sxs-lookup"><span data-stu-id="21918-132">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="21918-133">Criar um espaço de execução personalizado</span><span class="sxs-lookup"><span data-stu-id="21918-133">Creating a custom runspace</span></span>

<span data-ttu-id="21918-134">Embora o espaço de execução padrão usado nos exemplos anteriores carrega todos os comandos do Windows PowerShell core, pode criar um espaço de execução personalizado que carrega apenas um determinado subconjunto de todos os comandos.</span><span class="sxs-lookup"><span data-stu-id="21918-134">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span> <span data-ttu-id="21918-135">Pode querer fazê-lo para melhorar o desempenho (o carregamento de um grande número de comandos é um impacto no desempenho), ou para restringir a capacidade do utilizador para realizar operações.</span><span class="sxs-lookup"><span data-stu-id="21918-135">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span> <span data-ttu-id="21918-136">Um espaço de execução que expõe apenas um número limitado de comandos é chamado de um espaço de execução restrito.</span><span class="sxs-lookup"><span data-stu-id="21918-136">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span> <span data-ttu-id="21918-137">Para criar um espaço de execução restrito, utilize o [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) e [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span><span class="sxs-lookup"><span data-stu-id="21918-137">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="21918-138">Criação de um objeto de InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="21918-138">Creating an InitialSessionState object</span></span>

<span data-ttu-id="21918-139">Para criar um espaço de execução personalizado, tem primeiro de criar uma [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto.</span><span class="sxs-lookup"><span data-stu-id="21918-139">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span> <span data-ttu-id="21918-140">No exemplo a seguir, usamos o [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) para criar um espaço de execução depois de criar um padrão [System.Management.Automation.Runspaces.InitialSessionState ](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto.</span><span class="sxs-lookup"><span data-stu-id="21918-140">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="21918-141">Restrição de espaço de execução</span><span class="sxs-lookup"><span data-stu-id="21918-141">Constraining the runspace</span></span>

<span data-ttu-id="21918-142">No exemplo anterior, criámos uma predefinição [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto que carrega todos da principal interno do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21918-142">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span> <span data-ttu-id="21918-143">Podemos também poderia ter chamado a [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) método para criar um objeto de InitialSessionState que carrega apenas os comandos a Microsoft.PowerShell.Core snap-in.</span><span class="sxs-lookup"><span data-stu-id="21918-143">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span> <span data-ttu-id="21918-144">Para criar um espaço de execução mais restrito, tem de criar vazio [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto chamando o [ System.Management.Automation.Runspaces.InitialSessionState.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) método e, em seguida, adicionar comandos para o InitialSessionState.</span><span class="sxs-lookup"><span data-stu-id="21918-144">To create a more constrained runspace, you must create an empty [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="21918-145">A utilização de um espaço de execução que carrega apenas os comandos que especificar fornece um desempenho significativamente melhorado.</span><span class="sxs-lookup"><span data-stu-id="21918-145">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="21918-146">Usar os métodos do [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) classe para definir os cmdlets para o estado da sessão inicial.</span><span class="sxs-lookup"><span data-stu-id="21918-146">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span> <span data-ttu-id="21918-147">O exemplo seguinte cria um Estado de sessão inicial vazio, em seguida, define e adiciona a `Get-Command` e `Import-Module` comandos para o estado da sessão inicial.</span><span class="sxs-lookup"><span data-stu-id="21918-147">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span> <span data-ttu-id="21918-148">Podemos, em seguida, crie um espaço de execução restringido por esse Estado de sessão inicial e execute os comandos nesse espaço de execução.</span><span class="sxs-lookup"><span data-stu-id="21918-148">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="21918-149">Crie o estado da sessão inicial.</span><span class="sxs-lookup"><span data-stu-id="21918-149">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="21918-150">Definir e adicionar comandos para o estado da sessão inicial.</span><span class="sxs-lookup"><span data-stu-id="21918-150">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="21918-151">Criar e abrir o espaço de execução.</span><span class="sxs-lookup"><span data-stu-id="21918-151">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="21918-152">Executar um comando e mostrar o resultado.</span><span class="sxs-lookup"><span data-stu-id="21918-152">Execute a command and show the result.</span></span>

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

<span data-ttu-id="21918-153">Quando executada, a saída desse código será a aparência da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="21918-153">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
