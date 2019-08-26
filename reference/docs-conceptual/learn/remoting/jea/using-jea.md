---
ms.date: 07/10/2019
keywords: Jea, PowerShell, segurança
title: Utilizar a JEA
ms.openlocfilehash: 8f3cc9186c61a2ae5b64eb3dc4f72ca83f1a58c5
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017896"
---
# <a name="using-jea"></a><span data-ttu-id="86c44-103">Utilizar a JEA</span><span class="sxs-lookup"><span data-stu-id="86c44-103">Using JEA</span></span>

<span data-ttu-id="86c44-104">Este artigo descreve as várias maneiras pelas quais você pode se conectar e usar um ponto de extremidade JEA.</span><span class="sxs-lookup"><span data-stu-id="86c44-104">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="86c44-105">Usando o JEA interativamente</span><span class="sxs-lookup"><span data-stu-id="86c44-105">Using JEA interactively</span></span>

<span data-ttu-id="86c44-106">Se você estiver testando a configuração do JEA ou tiver tarefas simples para os usuários, poderá usar o JEA da mesma maneira que faria com uma sessão de comunicação remota do PowerShell normal.</span><span class="sxs-lookup"><span data-stu-id="86c44-106">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="86c44-107">Para tarefas de comunicação remota complexas, é recomendável usar [comunicação remota implícita](#using-jea-with-implicit-remoting).</span><span class="sxs-lookup"><span data-stu-id="86c44-107">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="86c44-108">A comunicação remota implícita permite que os usuários operem com os objetos de dados localmente.</span><span class="sxs-lookup"><span data-stu-id="86c44-108">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="86c44-109">Para usar o JEA interativamente, você precisa:</span><span class="sxs-lookup"><span data-stu-id="86c44-109">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="86c44-110">O nome do computador ao qual você está se conectando (pode ser o computador local)</span><span class="sxs-lookup"><span data-stu-id="86c44-110">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="86c44-111">O nome do ponto de extremidade JEA registrado no computador</span><span class="sxs-lookup"><span data-stu-id="86c44-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="86c44-112">Credenciais que têm acesso ao ponto de extremidade do JEA nesse computador</span><span class="sxs-lookup"><span data-stu-id="86c44-112">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="86c44-113">Dadas essas informações, você pode iniciar uma sessão JEA usando os cmdlets [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) ou [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) .</span><span class="sxs-lookup"><span data-stu-id="86c44-113">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="86c44-114">Se a conta de usuário atual tiver acesso ao ponto de extremidade JEA, você poderá omitir o parâmetro **Credential** .</span><span class="sxs-lookup"><span data-stu-id="86c44-114">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="86c44-115">Quando o prompt do PowerShell for `[localhost]: PS>` alterado para você, você saberá que agora está interagindo com a sessão Jea remota.</span><span class="sxs-lookup"><span data-stu-id="86c44-115">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="86c44-116">Você pode executar `Get-Command` para verificar quais comandos estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="86c44-116">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="86c44-117">Consulte seu administrador para saber se há restrições sobre os parâmetros disponíveis ou os valores de parâmetro permitidos.</span><span class="sxs-lookup"><span data-stu-id="86c44-117">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="86c44-118">Lembre-se de que as sessões JEA operam no modo nolanguage.</span><span class="sxs-lookup"><span data-stu-id="86c44-118">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="86c44-119">Algumas das maneiras que você normalmente usa o PowerShell podem não estar disponíveis.</span><span class="sxs-lookup"><span data-stu-id="86c44-119">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="86c44-120">Por exemplo, você não pode usar variáveis para armazenar dados ou inspecionar as propriedades em objetos retornados de cmdlets.</span><span class="sxs-lookup"><span data-stu-id="86c44-120">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="86c44-121">O exemplo a seguir mostra duas abordagens para obter os mesmos comandos para trabalhar no modo nolanguage.</span><span class="sxs-lookup"><span data-stu-id="86c44-121">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

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

<span data-ttu-id="86c44-122">Para invocações de comando mais complexas que tornam essa abordagem difícil, considere o uso de [comunicação remota implícita](#using-jea-with-implicit-remoting) ou a [criação de funções personalizadas](role-capabilities.md#creating-custom-functions) que encapsulam a funcionalidade necessária.</span><span class="sxs-lookup"><span data-stu-id="86c44-122">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="86c44-123">Usando o JEA com comunicação remota implícita</span><span class="sxs-lookup"><span data-stu-id="86c44-123">Using JEA with implicit remoting</span></span>

<span data-ttu-id="86c44-124">O PowerShell tem um modelo de comunicação remota implícito que permite que você importe cmdlets de proxy de um computador remoto e interaja com eles como se eles fossem comandos locais.</span><span class="sxs-lookup"><span data-stu-id="86c44-124">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="86c44-125">A comunicação remota implícita é explicada neste **Ei, equipe de scripts!**</span><span class="sxs-lookup"><span data-stu-id="86c44-125">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="86c44-126">[postagem no blog](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span><span class="sxs-lookup"><span data-stu-id="86c44-126">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="86c44-127">A comunicação remota implícita é útil ao trabalhar com JEA porque permite que você trabalhe com cmdlets JEA em um modo de linguagem completa.</span><span class="sxs-lookup"><span data-stu-id="86c44-127">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="86c44-128">Você pode usar o preenchimento com Tab, variáveis, manipular objetos e até mesmo usar scripts locais para automatizar tarefas em um ponto de extremidade JEA.</span><span class="sxs-lookup"><span data-stu-id="86c44-128">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="86c44-129">Sempre que você invoca um comando de proxy, os dados são enviados para o ponto de extremidade JEA no computador remoto e executados lá.</span><span class="sxs-lookup"><span data-stu-id="86c44-129">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="86c44-130">A comunicação remota implícita funciona importando cmdlets de uma sessão do PowerShell existente.</span><span class="sxs-lookup"><span data-stu-id="86c44-130">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="86c44-131">Opcionalmente, você pode optar por prefixar os substantivos de cada cmdlet de proxy com uma cadeia de caracteres de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="86c44-131">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="86c44-132">O prefixo permite que você diferencie os comandos que são para o sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="86c44-132">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="86c44-133">Um módulo de script temporário que contém todos os comandos de proxy é criado e importado durante a sua sessão local do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86c44-133">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="86c44-134">Alguns sistemas podem não ser capazes de importar uma sessão JEA inteira devido a restrições nos cmdlets JEA padrão.</span><span class="sxs-lookup"><span data-stu-id="86c44-134">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="86c44-135">Para contornar isso, importe apenas os comandos necessários da sessão Jea fornecendo explicitamente seus nomes para o `-CommandName` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="86c44-135">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="86c44-136">Uma atualização futura resolverá o problema com a importação de sessões inteiras do JEA em sistemas afetados.</span><span class="sxs-lookup"><span data-stu-id="86c44-136">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="86c44-137">Se não for possível importar uma sessão JEA devido a restrições JEA nos parâmetros padrão, siga as etapas abaixo para filtrar os comandos padrão do conjunto importado.</span><span class="sxs-lookup"><span data-stu-id="86c44-137">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="86c44-138">Você pode continuar usando comandos como `Select-Object`, mas você usará apenas a versão local instalada no seu computador em vez de uma importada da sessão Jea remota.</span><span class="sxs-lookup"><span data-stu-id="86c44-138">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

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

<span data-ttu-id="86c44-139">Você também pode persistir os cmdlets de proxy de comunicação remota implícita usando [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span><span class="sxs-lookup"><span data-stu-id="86c44-139">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="86c44-140">Para obter mais informações sobre comunicação remota implícita, consulte a documentação de [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) e [Import-Module](/powershell/microsoft.powershell.core/import-module).</span><span class="sxs-lookup"><span data-stu-id="86c44-140">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="86c44-141">Usando o JEA programaticamente</span><span class="sxs-lookup"><span data-stu-id="86c44-141">Using JEA programmatically</span></span>

<span data-ttu-id="86c44-142">O JEA também pode ser usado em sistemas de automação e em aplicativos de usuário, como aplicativos de assistência técnica interna e sites.</span><span class="sxs-lookup"><span data-stu-id="86c44-142">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="86c44-143">A abordagem é a mesma que a criação de aplicativos que se comunicam com pontos de extremidade do PowerShell sem restrição.</span><span class="sxs-lookup"><span data-stu-id="86c44-143">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="86c44-144">Verifique se o programa foi projetado para funcionar com limitação imposta pelo JEA.</span><span class="sxs-lookup"><span data-stu-id="86c44-144">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="86c44-145">Para tarefas simples e única, você pode usar [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) para executar comandos em uma sessão Jea.</span><span class="sxs-lookup"><span data-stu-id="86c44-145">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="86c44-146">Para verificar quais comandos estão disponíveis para uso quando você se conecta a uma sessão do Jea `Get-Command` , execute e itere nos resultados para verificar os parâmetros permitidos.</span><span class="sxs-lookup"><span data-stu-id="86c44-146">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="86c44-147">Se você estiver criando um C# aplicativo, poderá criar um runspace do PowerShell que se conecta a uma sessão Jea especificando o nome da configuração em um objeto [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) .</span><span class="sxs-lookup"><span data-stu-id="86c44-147">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="86c44-148">Usando o JEA com o PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="86c44-148">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="86c44-149">O Hyper-V no Windows 10 e no Windows Server 2016 oferece o [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), um recurso que permite que os administradores do Hyper-v gerenciem máquinas virtuais com o PowerShell, independentemente da configuração de rede ou das configurações de gerenciamento remoto na máquina virtual Tradução.</span><span class="sxs-lookup"><span data-stu-id="86c44-149">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="86c44-150">Você pode usar o PowerShell Direct com JEA para dar a um administrador do Hyper-V acesso limitado à sua VM.</span><span class="sxs-lookup"><span data-stu-id="86c44-150">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="86c44-151">Isso pode ser útil se você perder a conectividade de rede para sua VM e precisar de um administrador de datacenter para corrigir as configurações de rede.</span><span class="sxs-lookup"><span data-stu-id="86c44-151">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="86c44-152">Nenhuma configuração adicional é necessária para usar o JEA no PowerShell Direct.</span><span class="sxs-lookup"><span data-stu-id="86c44-152">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="86c44-153">No entanto, o sistema operacional convidado em execução dentro da máquina virtual deve ser Windows 10, Windows Server 2016 ou superior.</span><span class="sxs-lookup"><span data-stu-id="86c44-153">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="86c44-154">O administrador do Hyper-V pode se conectar ao ponto de extremidade Jea `-VMName` usando `-VMId` os parâmetros ou nos cmdlets PSRemoting:</span><span class="sxs-lookup"><span data-stu-id="86c44-154">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="86c44-155">É recomendável que você crie uma conta de usuário dedicada com os direitos mínimos necessários para gerenciar o sistema para uso por um administrador do Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="86c44-155">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="86c44-156">Lembre-se, mesmo um usuário sem privilégios pode entrar em um computador Windows por padrão, incluindo o uso do PowerShell irrestrito.</span><span class="sxs-lookup"><span data-stu-id="86c44-156">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="86c44-157">Isso permite que eles procurem o sistema de arquivos e saiba mais sobre o ambiente do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="86c44-157">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="86c44-158">Para bloquear um administrador do Hyper-V e limitá-los a acessar apenas uma VM usando o PowerShell Direct com JEA, você deve negar direitos de logon local à conta JEA do administrador do Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="86c44-158">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
