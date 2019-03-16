---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Utilizar a JEA
ms.openlocfilehash: fa3d3a3c8bc0090ec9ad788585ec5df933134173
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054684"
---
# <a name="using-jea"></a><span data-ttu-id="6ccac-103">Utilizar a JEA</span><span class="sxs-lookup"><span data-stu-id="6ccac-103">Using JEA</span></span>

> <span data-ttu-id="6ccac-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6ccac-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="6ccac-105">Este tópico descreve as várias formas como pode ligar e utilizar um ponto final JEA.</span><span class="sxs-lookup"><span data-stu-id="6ccac-105">This topic describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="6ccac-106">Utilizar a JEA interativamente</span><span class="sxs-lookup"><span data-stu-id="6ccac-106">Using JEA interactively</span></span>

<span data-ttu-id="6ccac-107">Se estiver a testar a configuração de JEA ou tiver tarefas simples para que os usuários realizem, pode usar JEA da mesma forma que faria com uma sessão de comunicação remota do PowerShell regular.</span><span class="sxs-lookup"><span data-stu-id="6ccac-107">If you are testing your JEA configuration or have simple tasks for users to perform, you can use JEA the same way you would a regular PowerShell remoting session.</span></span>
<span data-ttu-id="6ccac-108">Para tarefas de comunicação remota complexas, é recomendável usar [comunicação remota implícita](#using-jea-with-implicit-remoting) em vez disso, para tornar mais fácil para os seus utilizadores ao permitir que os utilizadores funcionar com os dados localmente objetos.</span><span class="sxs-lookup"><span data-stu-id="6ccac-108">For complex remoting tasks, it is recommended to use [implicit remoting](#using-jea-with-implicit-remoting) instead to make it easier for your users by allowing users to operate with the data objects locally.</span></span>

<span data-ttu-id="6ccac-109">Para utilizar a JEA interativamente, terá de:</span><span class="sxs-lookup"><span data-stu-id="6ccac-109">To use JEA interactively, you will need:</span></span>
- <span data-ttu-id="6ccac-110">O nome do computador que está a ligar (pode ser o computador local)</span><span class="sxs-lookup"><span data-stu-id="6ccac-110">The name of the computer you are connecting to (can be the local machine)</span></span>
- <span data-ttu-id="6ccac-111">O nome do ponto final JEA registado nesse computador</span><span class="sxs-lookup"><span data-stu-id="6ccac-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="6ccac-112">Credenciais para o computador que têm acesso ao ponto final JEA</span><span class="sxs-lookup"><span data-stu-id="6ccac-112">Credentials for the computer that have access to the JEA endpoint</span></span>

<span data-ttu-id="6ccac-113">Com essas informações em mãos, pode iniciar uma sessão JEA usando [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) ou [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="6ccac-113">With that information in hand, you can start a JEA session using [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="6ccac-114">Se a conta que tem atualmente sessão iniciada como tem acesso ao ponto final JEA, poderá omitir a `-Credential` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6ccac-114">If the account you're currently logged in as has access to the JEA endpoint, you can omit the `-Credential` parameter.</span></span>

<span data-ttu-id="6ccac-115">Quando o PowerShell solicitar alterações `[localhost]: PS>` ficará a saber o que estiver a interagir agora com a sessão JEA remota.</span><span class="sxs-lookup"><span data-stu-id="6ccac-115">When the PowerShell prompt changes to `[localhost]: PS>` you will know that you are now interacting with the remote JEA session.</span></span>
<span data-ttu-id="6ccac-116">Pode executar `Get-Command` para verificar quais comandos estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6ccac-116">You can run `Get-Command` to check which commands are available.</span></span>
<span data-ttu-id="6ccac-117">Precisará consultar com o seu administrador para saber se existem quaisquer restrições nos parâmetros disponíveis ou valores de parâmetro permitidos.</span><span class="sxs-lookup"><span data-stu-id="6ccac-117">You will need to consult with your administrator to learn if there are any restrictions on the available parameters or allowable parameter values.</span></span>

<span data-ttu-id="6ccac-118">Como lembrete, sessões JEA funcionam num modo de NoLanguage, pelo que algumas das formas de que utilizar o PowerShell, normalmente, podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6ccac-118">As a reminder, JEA sessions operate in NoLanguage mode, so some of the ways you typically use PowerShell may not be available.</span></span>
<span data-ttu-id="6ccac-119">Por exemplo, é possível utilizar variáveis para armazenar os dados ou Inspecione as propriedades em objetos devolvidos por cmdlets.</span><span class="sxs-lookup"><span data-stu-id="6ccac-119">For instance, you cannot use variables to store data or inspect the properties on objects returned from cmdlets.</span></span>
<span data-ttu-id="6ccac-120">A seguir o exemplo mostra um exemplo de como pode estar a utilizar PowerShell hoje mesmo e duas abordagens para obter o mesmo comando trabalhar no modo de NoLanguage.</span><span class="sxs-lookup"><span data-stu-id="6ccac-120">The below example shows an example of how you may be using PowerShell today, and two approaches to get the same command working in NoLanguage mode.</span></span>

```powershell
# Using variables in NoLanguage mode is disallowed, so the following will not work
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# Better yet, use parameter sets that don't require extra data to be passed in when possible
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="6ccac-121">Para invocações de comando mais complexas que dificultam essa abordagem, considere a utilização [comunicação remota implícita](#using-jea-with-implicit-remoting) ou [criar funções personalizadas](role-capabilities.md#creating-custom-functions) que encapsule a funcionalidade desejado.</span><span class="sxs-lookup"><span data-stu-id="6ccac-121">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you desire.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="6ccac-122">Utilizar a JEA com comunicação remota implícita</span><span class="sxs-lookup"><span data-stu-id="6ccac-122">Using JEA with implicit remoting</span></span>

<span data-ttu-id="6ccac-123">PowerShell suporta um modelo de comunicação remota alternativo onde pode importar os cmdlets do proxy de um computador remoto no seu computador local e interagir com eles, como se estivessem comandos locais.</span><span class="sxs-lookup"><span data-stu-id="6ccac-123">PowerShell supports an alternative remoting model where you can import proxy cmdlets from a remote machine on your local computer and interact with them as if they were local commands.</span></span>
<span data-ttu-id="6ccac-124">Isso é chamado de comunicação remota implícita e é explicado no [isso *Hey, Scripting Guy!* mensagem do blogue](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="6ccac-124">This is called implicit remoting, and is explained well in [this *Hey, Scripting Guy!* blog post](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="6ccac-125">Comunicação remota implícita é particularmente útil ao trabalhar com JEA porque ela permite que trabalhe com os cmdlets JEA num modo de linguagem completa.</span><span class="sxs-lookup"><span data-stu-id="6ccac-125">Implicit remoting is particularly useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span>
<span data-ttu-id="6ccac-126">Isso significa que pode utilizar a conclusão de tabulação, variáveis, manipular os objetos e até mesmo usar scripts locais para automatizar mais facilmente em relação a um ponto final JEA.</span><span class="sxs-lookup"><span data-stu-id="6ccac-126">This means you can use tab completion, variables, manipulate objects, and even use local scripts to more easily automate against a JEA endpoint.</span></span>
<span data-ttu-id="6ccac-127">Sempre que invocar um comando de proxy, os dados serão enviados para o ponto final JEA na máquina remota e executados lá.</span><span class="sxs-lookup"><span data-stu-id="6ccac-127">Anytime you invoke a proxy command, the data will be sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="6ccac-128">Comunicação remota implícita funciona através da importação cmdlets a partir de uma sessão do PowerShell existente.</span><span class="sxs-lookup"><span data-stu-id="6ccac-128">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span>
<span data-ttu-id="6ccac-129">Opcionalmente, pode optar por prefixo os nomes de cada cmdlet de proxy com uma cadeia de caracteres de sua escolha para distinguir quais comandos estão do sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="6ccac-129">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing to distinguish which commands are for the remote system.</span></span>
<span data-ttu-id="6ccac-130">Um módulo de script temporário que contém todos os comandos de proxy será criado e pode ser utilizado para a duração de sessão local do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6ccac-130">A temporary script module containing all of the proxy commands will be created and can be used for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="6ccac-131">Alguns sistemas talvez não consiga importar uma sessão completa de JEA devido a restrições nos cmdlets JEA padrão.</span><span class="sxs-lookup"><span data-stu-id="6ccac-131">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span>
> <span data-ttu-id="6ccac-132">Para contornar esse problema, só importar os comandos de que precisa da sessão JEA fornecendo explicitamente os respetivos nomes para o `-CommandName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6ccac-132">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span>
> <span data-ttu-id="6ccac-133">Uma atualização futura irá resolver o problema com a importação de sessões JEA todos em sistemas afetados.</span><span class="sxs-lookup"><span data-stu-id="6ccac-133">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="6ccac-134">Se não é possível importar uma sessão JEA devido a restrições em parâmetros JEA predefinidos, pode seguir os passos abaixo para filtrar os comandos padrão do conjunto de importados.</span><span class="sxs-lookup"><span data-stu-id="6ccac-134">If you are unable to import a JEA session due to constraints on the default JEA parameters, you can follow the steps below to filter out the default commands from the imported set.</span></span>
<span data-ttu-id="6ccac-135">Ainda poderá usar comandos como `Select-Object` – usará a versão local instalada no seu computador em vez da remoto na sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="6ccac-135">You will still be able to use commands like `Select-Object` -- you'll just use the local version installed on your computer instead of the remote one in the JEA session.</span></span>

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

<span data-ttu-id="6ccac-136">Também pode manter os cmdlets transmitidas por proxy de comunicação remota implícita usando [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="6ccac-136">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="6ccac-137">Para obter mais informações sobre a comunicação remota implícita, consulte a documentação de ajuda para [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) e [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="6ccac-137">For more information about implicit remoting, check out the help documentation for [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) and [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="6ccac-138">Utilizar a JEA por meio de programação</span><span class="sxs-lookup"><span data-stu-id="6ccac-138">Using JEA programmatically</span></span>

<span data-ttu-id="6ccac-139">JEA também pode ser utilizado em sistemas de automatização e nos aplicativos de usuário, como web sites e aplicações de suporte técnico interno.</span><span class="sxs-lookup"><span data-stu-id="6ccac-139">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and web sites.</span></span>
<span data-ttu-id="6ccac-140">A abordagem é o mesmo que para criar aplicações que comunique com os pontos finais irrestrita do PowerShell, tendo em mente que o programa deve conhecer JEA esteja a limitar os comandos que podem ser executados na sessão remota.</span><span class="sxs-lookup"><span data-stu-id="6ccac-140">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints, with the caveat that the program should be aware that JEA is limiting the commands that can be run in the remote session.</span></span>

<span data-ttu-id="6ccac-141">Para tarefas simples e unitárias, pode usar [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) para executar um conjunto de comandos utilizando JEA.</span><span class="sxs-lookup"><span data-stu-id="6ccac-141">For simple, one-off tasks, you can use [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) to run a set of commands using JEA.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="6ccac-142">Para verificar quais comandos estão disponíveis para utilização quando se liga a uma sessão JEA, execute `Get-Command` e iterar os resultados para verificar os parâmetros permitidos.</span><span class="sxs-lookup"><span data-stu-id="6ccac-142">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="6ccac-143">Se estiver a criar um C# aplicação, pode criar um espaço de execução do PowerShell que se liga a uma sessão JEA, especificando o nome de configuração num [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) objeto.</span><span class="sxs-lookup"><span data-stu-id="6ccac-143">If you are building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) object.</span></span>

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/library/system.management.automation.pscredential(v=vs.85).aspx)

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
                    false,                 // Use SSL
                    computerName,          // Computer name
                    5985,                  // WSMan Port
                    "/wsman",              // WSMan Path
                    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),  // Connection URI with config name
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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="6ccac-144">Utilizar a JEA com o PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="6ccac-144">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="6ccac-145">Hyper-V no Windows 10 e Windows Server 2016 oferece [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), uma funcionalidade que permite aos administradores de Hyper-V gerir máquinas virtuais com o PowerShell, independentemente da configuração de rede ou a gestão remota definições da máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="6ccac-145">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), a feature which allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="6ccac-146">Pode utilizar o PowerShell Direct com JEA para dar um acesso de administrador limitado de Hyper-V para a VM, que pode ser útil se perder a conectividade de rede para a VM e precisar de um administrador do datacenter para corrigir as definições de rede.</span><span class="sxs-lookup"><span data-stu-id="6ccac-146">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM, which can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="6ccac-147">Nenhuma configuração adicional é necessária para utilizar a JEA através do PowerShell Direct, o sistema operativo em execução dentro da máquina virtual tem de ser Windows 10 ou Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="6ccac-147">No additional configuration is required to use JEA over PowerShell Direct, however the operating system running inside the virtual machine must be Windows 10 or Windows Server 2016.</span></span>
<span data-ttu-id="6ccac-148">O administrador do Hyper-V, pode ligar ao ponto final JEA utilizando o `-VMName` ou `-VMId` parâmetros PSRemoting cmdlets:</span><span class="sxs-lookup"><span data-stu-id="6ccac-148">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="6ccac-149">É vivamente recomendado que crie um utilizador local dedicado com nenhum outro direito para gerir o sistema para os administradores de Hyper-V para utilizar.</span><span class="sxs-lookup"><span data-stu-id="6ccac-149">It is strongly recommended that you create a dedicated local user with no other rights to manage the system for your Hyper-V administrators to use.</span></span>
<span data-ttu-id="6ccac-150">Lembre-se de que até mesmo um utilizador sem privilégios pode ainda iniciar sessão numa máquina Windows por padrão, incluindo com o PowerShell irrestrita.</span><span class="sxs-lookup"><span data-stu-id="6ccac-150">Remember that even an unprivileged user can still log into a Windows machine by default, including using unconstrained PowerShell.</span></span>
<span data-ttu-id="6ccac-151">Que irão permitir-lhe procurar (alguns dos) no sistema de arquivos e saiba mais sobre o ambiente do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="6ccac-151">That will allow them to browse (some of) the file system and learn more about your OS environment.</span></span>
<span data-ttu-id="6ccac-152">Bloquear um administrador do Hyper-V apenas para acessar uma VM com o PowerShell Direct com JEA, terá de negar direitos de início de sessão local para a conta JEA do administrador do Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="6ccac-152">To lock down a Hyper-V administrator to only access a VM using PowerShell Direct with JEA, you will need to deny local logon rights to the Hyper-V admin's JEA account.</span></span>
