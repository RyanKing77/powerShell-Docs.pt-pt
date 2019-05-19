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
ms.openlocfilehash: 390eb2d0153c65967d8c0711c852aa6e13fe4660
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855104"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="a1637-102">Windows PowerShell Host Quickstart (Guia de Início Rápido de Alojamento do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="a1637-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="a1637-103">Para alojar o Windows PowerShell na sua aplicação, utilize o [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe.</span><span class="sxs-lookup"><span data-stu-id="a1637-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span>
<span data-ttu-id="a1637-104">Essa classe fornece métodos que cria um pipeline de comandos e, em seguida, executar esses comandos num espaço de execução.</span><span class="sxs-lookup"><span data-stu-id="a1637-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span>
<span data-ttu-id="a1637-105">A forma mais simples de criar um aplicativo host é usar o espaço de execução padrão.</span><span class="sxs-lookup"><span data-stu-id="a1637-105">The simplest way to create a host application is to use the default runspace.</span></span>
<span data-ttu-id="a1637-106">O espaço de execução predefinido contém todos os comandos do Windows PowerShell core.</span><span class="sxs-lookup"><span data-stu-id="a1637-106">The default runspace contains all of the core Windows PowerShell commands.</span></span>
<span data-ttu-id="a1637-107">Se quiser que o aplicativo para expor apenas um subconjunto dos comandos do Windows PowerShell, tem de criar um espaço de execução personalizado.</span><span class="sxs-lookup"><span data-stu-id="a1637-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="a1637-108">Usando o espaço de execução padrão</span><span class="sxs-lookup"><span data-stu-id="a1637-108">Using the default runspace</span></span>

<span data-ttu-id="a1637-109">Para começar, vamos utilizar o espaço de execução padrão e usar os métodos do [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) classe para adicionar os comandos, parâmetros, instruções e scripts para um pipeline.</span><span class="sxs-lookup"><span data-stu-id="a1637-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="a1637-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="a1637-110">AddCommand</span></span>

<span data-ttu-id="a1637-111">Utilizar o [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) método adicionar comandos para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="a1637-111">You use the [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method to add commands to the pipeline.</span></span>
<span data-ttu-id="a1637-112">Por exemplo, suponha que deseja obter a lista de processos em execução na máquina.</span><span class="sxs-lookup"><span data-stu-id="a1637-112">For example, suppose you want to get the list of running processes on the machine.</span></span>
<span data-ttu-id="a1637-113">Segue-se a forma de executar este comando.</span><span class="sxs-lookup"><span data-stu-id="a1637-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="a1637-114">Criar uma [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) objeto.</span><span class="sxs-lookup"><span data-stu-id="a1637-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="a1637-115">Adicione o comando que pretende executar.</span><span class="sxs-lookup"><span data-stu-id="a1637-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="a1637-116">Invoca o comando.</span><span class="sxs-lookup"><span data-stu-id="a1637-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="a1637-117">Se chamar o método AddCommand mais de uma vez antes de chamar o [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) método, o resultado do primeiro comando é enviado por pipe para o segundo e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="a1637-117">If you call the AddCommand method more than once before you call the [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span>
<span data-ttu-id="a1637-118">Se não pretender encaminhar o resultado de um comando anterior para um comando, adicione-o ao chamar o [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="a1637-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="a1637-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="a1637-119">AddParameter</span></span>

<span data-ttu-id="a1637-120">O exemplo anterior executa um único comando sem quaisquer parâmetros.</span><span class="sxs-lookup"><span data-stu-id="a1637-120">The previous example executes a single command without any parameters.</span></span>
<span data-ttu-id="a1637-121">Pode adicionar parâmetros ao comando utilizando o [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) método.</span><span class="sxs-lookup"><span data-stu-id="a1637-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method.</span></span>
<span data-ttu-id="a1637-122">Por exemplo, o código seguinte obtém uma lista de todos os processos chamados `PowerShell` em execução na máquina.</span><span class="sxs-lookup"><span data-stu-id="a1637-122">For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="a1637-123">Pode adicionar parâmetros adicionais, chamando o método de AddParameter repetidamente.</span><span class="sxs-lookup"><span data-stu-id="a1637-123">You can add additional parameters by calling the AddParameter method repeatedly.</span></span>

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

<span data-ttu-id="a1637-124">Também pode adicionar um dicionário de valores e nomes de parâmetros ao chamar o [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) método.</span><span class="sxs-lookup"><span data-stu-id="a1637-124">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="a1637-125">AddStatement</span><span class="sxs-lookup"><span data-stu-id="a1637-125">AddStatement</span></span>

<span data-ttu-id="a1637-126">Pode simular a criação de batches, utilizando o [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) método, que adiciona uma instrução adicional no final do pipeline.</span><span class="sxs-lookup"><span data-stu-id="a1637-126">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline.</span></span>
<span data-ttu-id="a1637-127">O código a seguir obtém uma lista de processos em execução com o nome `PowerShell`e, em seguida, obtém a lista de serviços em execução.</span><span class="sxs-lookup"><span data-stu-id="a1637-127">The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="a1637-128">AddScript</span><span class="sxs-lookup"><span data-stu-id="a1637-128">AddScript</span></span>

<span data-ttu-id="a1637-129">Pode executar um script existente ao chamar o [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) método.</span><span class="sxs-lookup"><span data-stu-id="a1637-129">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span>
<span data-ttu-id="a1637-130">O exemplo seguinte adiciona um script para o pipeline e executa-o.</span><span class="sxs-lookup"><span data-stu-id="a1637-130">The following example adds a script to the pipeline and runs it.</span></span>
<span data-ttu-id="a1637-131">Este exemplo assume que já existe um script chamado `MyScript.ps1` numa pasta chamada `D:\PSScripts`.</span><span class="sxs-lookup"><span data-stu-id="a1637-131">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="a1637-132">Também existe uma versão do método AddScript que assume um parâmetro booleano denominado `useLocalScope`.</span><span class="sxs-lookup"><span data-stu-id="a1637-132">There is also a version of the AddScript method that takes a boolean parameter named `useLocalScope`.</span></span>
<span data-ttu-id="a1637-133">Se este parâmetro estiver definido como `true`, em seguida, o script é executado no âmbito do local.</span><span class="sxs-lookup"><span data-stu-id="a1637-133">If this parameter is set to `true`, then the script is run in the local scope.</span></span>
<span data-ttu-id="a1637-134">O código a seguir será executado o script no escopo local.</span><span class="sxs-lookup"><span data-stu-id="a1637-134">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="a1637-135">Criar um espaço de execução personalizado</span><span class="sxs-lookup"><span data-stu-id="a1637-135">Creating a custom runspace</span></span>

<span data-ttu-id="a1637-136">Embora o espaço de execução padrão usado nos exemplos anteriores carrega todos os comandos do Windows PowerShell core, pode criar um espaço de execução personalizado que carrega apenas um determinado subconjunto de todos os comandos.</span><span class="sxs-lookup"><span data-stu-id="a1637-136">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span>
<span data-ttu-id="a1637-137">Pode querer fazê-lo para melhorar o desempenho (o carregamento de um grande número de comandos é um impacto no desempenho), ou para restringir a capacidade do utilizador para realizar operações.</span><span class="sxs-lookup"><span data-stu-id="a1637-137">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span>
<span data-ttu-id="a1637-138">Um espaço de execução que expõe apenas um número limitado de comandos é chamado de um espaço de execução restrito.</span><span class="sxs-lookup"><span data-stu-id="a1637-138">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span>
<span data-ttu-id="a1637-139">Para criar um espaço de execução restrito, utilize o [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) e [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span><span class="sxs-lookup"><span data-stu-id="a1637-139">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="a1637-140">Criação de um objeto de InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="a1637-140">Creating an InitialSessionState object</span></span>

<span data-ttu-id="a1637-141">Para criar um espaço de execução personalizado, tem primeiro de criar uma [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto.</span><span class="sxs-lookup"><span data-stu-id="a1637-141">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>
<span data-ttu-id="a1637-142">No exemplo a seguir, usamos o [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) para criar um espaço de execução depois de criar um objeto de InitialSessionState padrão.</span><span class="sxs-lookup"><span data-stu-id="a1637-142">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default InitialSessionState object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="a1637-143">Restrição de espaço de execução</span><span class="sxs-lookup"><span data-stu-id="a1637-143">Constraining the runspace</span></span>

<span data-ttu-id="a1637-144">No exemplo anterior, criámos uma predefinição [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objeto que carrega todos da principal interno do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a1637-144">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span>
<span data-ttu-id="a1637-145">Podemos também poderia ter chamado a [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) método para criar um objeto de InitialSessionState que carrega apenas os comandos a Microsoft.PowerShell.Core snap-in.</span><span class="sxs-lookup"><span data-stu-id="a1637-145">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span>
<span data-ttu-id="a1637-146">Para criar um espaço de execução mais restrito, tem de criar um objeto de InitialSessionState vazio ao chamar o [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) método e, em seguida, adicionar comandos para o InitialSessionState.</span><span class="sxs-lookup"><span data-stu-id="a1637-146">To create a more constrained runspace, you must create an empty InitialSessionState object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="a1637-147">A utilização de um espaço de execução que carrega apenas os comandos que especificar fornece um desempenho significativamente melhorado.</span><span class="sxs-lookup"><span data-stu-id="a1637-147">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="a1637-148">Usar os métodos do [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) classe para definir os cmdlets para o estado da sessão inicial.</span><span class="sxs-lookup"><span data-stu-id="a1637-148">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>
<span data-ttu-id="a1637-149">O exemplo seguinte cria um Estado de sessão inicial vazio, em seguida, define e adiciona a `Get-Command` e `Import-Module` comandos para o estado da sessão inicial.</span><span class="sxs-lookup"><span data-stu-id="a1637-149">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span>
<span data-ttu-id="a1637-150">Podemos, em seguida, crie um espaço de execução restringido por esse Estado de sessão inicial e execute os comandos nesse espaço de execução.</span><span class="sxs-lookup"><span data-stu-id="a1637-150">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="a1637-151">Crie o estado da sessão inicial.</span><span class="sxs-lookup"><span data-stu-id="a1637-151">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="a1637-152">Definir e adicionar comandos para o estado da sessão inicial.</span><span class="sxs-lookup"><span data-stu-id="a1637-152">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="a1637-153">Criar e abrir o espaço de execução.</span><span class="sxs-lookup"><span data-stu-id="a1637-153">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="a1637-154">Executar um comando e mostrar o resultado.</span><span class="sxs-lookup"><span data-stu-id="a1637-154">Execute a command and show the result.</span></span>

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

<span data-ttu-id="a1637-155">Quando executada, a saída desse código será a aparência da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="a1637-155">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
