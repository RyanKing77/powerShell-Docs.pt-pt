---
ms.date: 07/10/2019
keywords: jea, powershell, segurança
title: Utilizar a JEA
ms.openlocfilehash: 8f3cc9186c61a2ae5b64eb3dc4f72ca83f1a58c5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734212"
---
# <a name="using-jea"></a><span data-ttu-id="b5c96-103">Utilizar a JEA</span><span class="sxs-lookup"><span data-stu-id="b5c96-103">Using JEA</span></span>

<span data-ttu-id="b5c96-104">Este artigo descreve as várias formas como pode ligar e utilizar um ponto final JEA.</span><span class="sxs-lookup"><span data-stu-id="b5c96-104">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="b5c96-105">Utilizar a JEA interativamente</span><span class="sxs-lookup"><span data-stu-id="b5c96-105">Using JEA interactively</span></span>

<span data-ttu-id="b5c96-106">Se estiver a testar a configuração de JEA ou tiver tarefas simples para os utilizadores, pode utilizar JEA da mesma forma que faria com uma sessão de comunicação remota do PowerShell regular.</span><span class="sxs-lookup"><span data-stu-id="b5c96-106">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="b5c96-107">Para tarefas de comunicação remota complexas, é recomendado que utilize [comunicação remota implícita](#using-jea-with-implicit-remoting).</span><span class="sxs-lookup"><span data-stu-id="b5c96-107">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="b5c96-108">Comunicação remota implícita permite aos utilizadores funcionar com os objetos de dados localmente.</span><span class="sxs-lookup"><span data-stu-id="b5c96-108">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="b5c96-109">Para utilizar a JEA interativamente, terá de:</span><span class="sxs-lookup"><span data-stu-id="b5c96-109">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="b5c96-110">O nome do computador que está a ligar (pode ser o computador local)</span><span class="sxs-lookup"><span data-stu-id="b5c96-110">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="b5c96-111">O nome do ponto final JEA registado nesse computador</span><span class="sxs-lookup"><span data-stu-id="b5c96-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="b5c96-112">Credenciais que têm acesso ao ponto final JEA nesse computador</span><span class="sxs-lookup"><span data-stu-id="b5c96-112">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="b5c96-113">Tendo em conta essas informações, pode iniciar uma sessão JEA utilizando o [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) ou [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b5c96-113">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="b5c96-114">Se a conta de utilizador atual tem acesso para o ponto final da JEA, poderá omitir a **credencial** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b5c96-114">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="b5c96-115">Quando o PowerShell solicitar alterações `[localhost]: PS>` sabe o que agora está interagindo com a sessão JEA remota.</span><span class="sxs-lookup"><span data-stu-id="b5c96-115">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="b5c96-116">Pode executar `Get-Command` para verificar quais comandos estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="b5c96-116">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="b5c96-117">Consulte o seu administrador para saber se existem quaisquer restrições nos parâmetros disponíveis ou valores de parâmetro permitidos.</span><span class="sxs-lookup"><span data-stu-id="b5c96-117">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="b5c96-118">Lembre-se de que as sessões JEA operam no modo de NoLanguage.</span><span class="sxs-lookup"><span data-stu-id="b5c96-118">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="b5c96-119">Algumas das formas de que utilizar o PowerShell, normalmente, poderão não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="b5c96-119">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="b5c96-120">Por exemplo, é possível utilizar variáveis para armazenar os dados ou Inspecione as propriedades em objetos devolvidos por cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b5c96-120">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="b5c96-121">O exemplo seguinte mostra as duas abordagens para obter os mesmos comandos para funcionar no modo de NoLanguage.</span><span class="sxs-lookup"><span data-stu-id="b5c96-121">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

```powershell
# Using variables is prohibited in NoLanguage mode. The following will not work:
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# You can also use parameter sets that don't require extra data to be passed in
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="b5c96-122">Para invocações de comando mais complexas que dificultam essa abordagem, considere a utilização [comunicação remota implícita](#using-jea-with-implicit-remoting) ou [criar funções personalizadas](role-capabilities.md#creating-custom-functions) que encapsule a funcionalidade necessária.</span><span class="sxs-lookup"><span data-stu-id="b5c96-122">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="b5c96-123">Utilizar a JEA com comunicação remota implícita</span><span class="sxs-lookup"><span data-stu-id="b5c96-123">Using JEA with implicit remoting</span></span>

<span data-ttu-id="b5c96-124">PowerShell possui um modelo de comunicação remota implícita que lhe permite importar os cmdlets do proxy de um computador remoto e interagir com eles, como se estivessem comandos locais.</span><span class="sxs-lookup"><span data-stu-id="b5c96-124">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="b5c96-125">Comunicação remota implícita é explicada neste **ei, equipe de scripts!**</span><span class="sxs-lookup"><span data-stu-id="b5c96-125">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="b5c96-126">[mensagem de blogue](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="b5c96-126">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="b5c96-127">Comunicação remota implícita é útil ao trabalhar com JEA porque ela permite que trabalhe com os cmdlets JEA num modo de linguagem completa.</span><span class="sxs-lookup"><span data-stu-id="b5c96-127">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="b5c96-128">Pode utilizar a conclusão de tabulação, variáveis, manipular os objetos e até mesmo usar scripts locais para automatizar tarefas relativamente de um ponto final JEA.</span><span class="sxs-lookup"><span data-stu-id="b5c96-128">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="b5c96-129">Sempre que invocar um comando de proxy, os dados são enviados para o ponto final JEA na máquina remota e executados lá.</span><span class="sxs-lookup"><span data-stu-id="b5c96-129">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="b5c96-130">Comunicação remota implícita funciona através da importação cmdlets a partir de uma sessão do PowerShell existente.</span><span class="sxs-lookup"><span data-stu-id="b5c96-130">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="b5c96-131">Opcionalmente, pode optar por prefixo os nomes de cada cmdlet de proxy com uma cadeia de caracteres de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="b5c96-131">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="b5c96-132">O prefixo permite-lhe distinguir os comandos do sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="b5c96-132">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="b5c96-133">Um módulo de script temporário que contém todos os comandos de proxy é criado e importado para a duração de sessão local do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b5c96-133">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="b5c96-134">Alguns sistemas talvez não consiga importar uma sessão completa de JEA devido a restrições nos cmdlets JEA padrão.</span><span class="sxs-lookup"><span data-stu-id="b5c96-134">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="b5c96-135">Para contornar esse problema, só importar os comandos de que precisa da sessão JEA fornecendo explicitamente os respetivos nomes para o `-CommandName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b5c96-135">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="b5c96-136">Uma atualização futura irá resolver o problema com a importação de sessões JEA todos em sistemas afetados.</span><span class="sxs-lookup"><span data-stu-id="b5c96-136">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="b5c96-137">Se não é possível importar uma sessão JEA por causa de restrições JEA nos parâmetros predefinidos, siga os passos abaixo para filtrar os comandos padrão do conjunto de importados.</span><span class="sxs-lookup"><span data-stu-id="b5c96-137">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="b5c96-138">Pode continuar a utilizar comandos como `Select-Object`, mas usará a versão local instalada no seu computador em vez da importados a partir da sessão JEA remota.</span><span class="sxs-lookup"><span data-stu-id="b5c96-138">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Get a list of all the commands on the JEA endpoint
$commands = Invoke-Command -Session $jeasession -ScriptBlock { Get-Command }

# Filter out the default cmdlets
$jeaDefaultCmdlets = 'Clear-Host', 'Exit-PSSession', 'Get-Command', 'Get-FormatData', 'Get-Help', 'Measure-Object', 'Out-Default', 'Select-Object'
$filteredCommands = $commands.Name | Where-Object { $jeaDefaultCmdlets -notcontains $_ }

# Import only commands explicitly added in role capabilities and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA' -CommandName $filteredCommands
```

<span data-ttu-id="b5c96-139">Também pode manter os cmdlets transmitidas por proxy de comunicação remota implícita usando [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="b5c96-139">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="b5c96-140">Para obter mais informações sobre a comunicação remota implícita, consulte a documentação para [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) e [Import-Module](/powershell/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="b5c96-140">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="b5c96-141">Utilizar a JEA por meio de programação</span><span class="sxs-lookup"><span data-stu-id="b5c96-141">Using JEA programmatically</span></span>

<span data-ttu-id="b5c96-142">JEA também pode ser utilizado em sistemas de automatização e nos aplicativos de usuário, como aplicações de suporte técnico internos e Web sites.</span><span class="sxs-lookup"><span data-stu-id="b5c96-142">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="b5c96-143">A abordagem é o mesmo que para criar aplicações que comunicam com pontos finais de PowerShell irrestrita.</span><span class="sxs-lookup"><span data-stu-id="b5c96-143">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="b5c96-144">Certifique-se de que o programa foi concebido para trabalhar com limitação imposta pela JEA.</span><span class="sxs-lookup"><span data-stu-id="b5c96-144">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="b5c96-145">Para tarefas simples e unitárias, pode usar [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) para executar comandos numa sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="b5c96-145">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="b5c96-146">Para verificar quais comandos estão disponíveis para utilização quando se liga a uma sessão JEA, execute `Get-Command` e iterar os resultados para verificar os parâmetros permitidos.</span><span class="sxs-lookup"><span data-stu-id="b5c96-146">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="b5c96-147">Se estiver criando um C# aplicação, pode criar um espaço de execução do PowerShell que se liga a uma sessão JEA, especificando o nome de configuração num [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) objeto.</span><span class="sxs-lookup"><span data-stu-id="b5c96-147">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
// See https://docs.microsoft.com/dotnet/api/system.management.automation.pscredential
var creds        = // create a PSCredential object here

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
    false,                 // Use SSL
    computerName,          // Computer name
    5985,                  // WSMan Port
    "/wsman",              // WSMan Path
                           // Connection URI with config name
    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),
    creds);                // Credentials

// Now, use the connection info to create a runspace where you can run the commands
using (Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo))
{
    // Open the runspace
    runspace.Open();

    using (PowerShell ps = PowerShell.Create())
    {
        // Set the PowerShell object to use the JEA runspace
        ps.Runspace = runspace;

        // Now you can add and invoke commands
        ps.AddCommand("Get-Command");
        foreach (var result in ps.Invoke())
        {
            Console.WriteLine(result);
        }
    }

    // Close the runspace
    runspace.Close();
}
```

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="b5c96-148">Utilizar a JEA com o PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="b5c96-148">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="b5c96-149">Hyper-V no Windows 10 e Windows Server 2016 oferece [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), uma funcionalidade que permite aos administradores de Hyper-V gerir máquinas virtuais com o PowerShell, independentemente da configuração de rede ou a gestão remota definições da máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="b5c96-149">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="b5c96-150">Pode utilizar o PowerShell Direct com JEA para dar um acesso de administrador limitado do Hyper-V para a VM.</span><span class="sxs-lookup"><span data-stu-id="b5c96-150">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="b5c96-151">Isso pode ser útil se perder a conectividade de rede para a VM e precisar de um administrador do datacenter para corrigir as definições de rede.</span><span class="sxs-lookup"><span data-stu-id="b5c96-151">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="b5c96-152">Nenhuma configuração adicional é necessário para utilizar a JEA através do PowerShell Direct.</span><span class="sxs-lookup"><span data-stu-id="b5c96-152">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="b5c96-153">No entanto, o sistema operativo convidado em execução dentro da máquina virtual tem de ser Windows 10, Windows Server 2016 ou superior.</span><span class="sxs-lookup"><span data-stu-id="b5c96-153">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="b5c96-154">O administrador do Hyper-V, pode ligar ao ponto final JEA utilizando o `-VMName` ou `-VMId` parâmetros PSRemoting cmdlets:</span><span class="sxs-lookup"><span data-stu-id="b5c96-154">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="b5c96-155">Recomenda-se que criar uma conta de utilizador dedicado com os direitos mínimos necessários para gerir o sistema para utilização por um administrador do Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="b5c96-155">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="b5c96-156">Lembre-se de que, até mesmo um utilizador sem privilégios pode iniciar sessão numa máquina Windows por padrão, incluindo com o PowerShell irrestrita.</span><span class="sxs-lookup"><span data-stu-id="b5c96-156">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="b5c96-157">Isso permite que os mesmos para procurar o sistema de ficheiros e saiba mais sobre o ambiente do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="b5c96-157">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="b5c96-158">Para bloquear um administrador do Hyper-V e limitá-las apenas para acessar uma VM com o PowerShell Direct com JEA, tem de negar direitos de início de sessão local para a conta JEA do administrador do Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="b5c96-158">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
