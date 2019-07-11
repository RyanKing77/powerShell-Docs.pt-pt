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
# <a name="using-jea"></a>Utilizar a JEA

Este artigo descreve as várias formas como pode ligar e utilizar um ponto final JEA.

## <a name="using-jea-interactively"></a>Utilizar a JEA interativamente

Se estiver a testar a configuração de JEA ou tiver tarefas simples para os utilizadores, pode utilizar JEA da mesma forma que faria com uma sessão de comunicação remota do PowerShell regular. Para tarefas de comunicação remota complexas, é recomendado que utilize [comunicação remota implícita](#using-jea-with-implicit-remoting). Comunicação remota implícita permite aos utilizadores funcionar com os objetos de dados localmente.

Para utilizar a JEA interativamente, terá de:

- O nome do computador que está a ligar (pode ser o computador local)
- O nome do ponto final JEA registado nesse computador
- Credenciais que têm acesso ao ponto final JEA nesse computador

Tendo em conta essas informações, pode iniciar uma sessão JEA utilizando o [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) ou [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Se a conta de utilizador atual tem acesso para o ponto final da JEA, poderá omitir a **credencial** parâmetro.

Quando o PowerShell solicitar alterações `[localhost]: PS>` sabe o que agora está interagindo com a sessão JEA remota. Pode executar `Get-Command` para verificar quais comandos estão disponíveis. Consulte o seu administrador para saber se existem quaisquer restrições nos parâmetros disponíveis ou valores de parâmetro permitidos.

Lembre-se de que as sessões JEA operam no modo de NoLanguage. Algumas das formas de que utilizar o PowerShell, normalmente, poderão não estar disponíveis. Por exemplo, é possível utilizar variáveis para armazenar os dados ou Inspecione as propriedades em objetos devolvidos por cmdlets. O exemplo seguinte mostra as duas abordagens para obter os mesmos comandos para funcionar no modo de NoLanguage.

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

Para invocações de comando mais complexas que dificultam essa abordagem, considere a utilização [comunicação remota implícita](#using-jea-with-implicit-remoting) ou [criar funções personalizadas](role-capabilities.md#creating-custom-functions) que encapsule a funcionalidade necessária.

## <a name="using-jea-with-implicit-remoting"></a>Utilizar a JEA com comunicação remota implícita

PowerShell possui um modelo de comunicação remota implícita que lhe permite importar os cmdlets do proxy de um computador remoto e interagir com eles, como se estivessem comandos locais. Comunicação remota implícita é explicada neste **ei, equipe de scripts!** [mensagem de blogue](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).
Comunicação remota implícita é útil ao trabalhar com JEA porque ela permite que trabalhe com os cmdlets JEA num modo de linguagem completa. Pode utilizar a conclusão de tabulação, variáveis, manipular os objetos e até mesmo usar scripts locais para automatizar tarefas relativamente de um ponto final JEA. Sempre que invocar um comando de proxy, os dados são enviados para o ponto final JEA na máquina remota e executados lá.

Comunicação remota implícita funciona através da importação cmdlets a partir de uma sessão do PowerShell existente. Opcionalmente, pode optar por prefixo os nomes de cada cmdlet de proxy com uma cadeia de caracteres de sua escolha. O prefixo permite-lhe distinguir os comandos do sistema remoto. Um módulo de script temporário que contém todos os comandos de proxy é criado e importado para a duração de sessão local do PowerShell.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Alguns sistemas talvez não consiga importar uma sessão completa de JEA devido a restrições nos cmdlets JEA padrão. Para contornar esse problema, só importar os comandos de que precisa da sessão JEA fornecendo explicitamente os respetivos nomes para o `-CommandName` parâmetro. Uma atualização futura irá resolver o problema com a importação de sessões JEA todos em sistemas afetados.

Se não é possível importar uma sessão JEA por causa de restrições JEA nos parâmetros predefinidos, siga os passos abaixo para filtrar os comandos padrão do conjunto de importados. Pode continuar a utilizar comandos como `Select-Object`, mas usará a versão local instalada no seu computador em vez da importados a partir da sessão JEA remota.

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

Também pode manter os cmdlets transmitidas por proxy de comunicação remota implícita usando [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).
Para obter mais informações sobre a comunicação remota implícita, consulte a documentação para [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) e [Import-Module](/powershell/microsoft.powershell.core/import-module).

## <a name="using-jea-programmatically"></a>Utilizar a JEA por meio de programação

JEA também pode ser utilizado em sistemas de automatização e nos aplicativos de usuário, como aplicações de suporte técnico internos e Web sites. A abordagem é o mesmo que para criar aplicações que comunicam com pontos finais de PowerShell irrestrita. Certifique-se de que o programa foi concebido para trabalhar com limitação imposta pela JEA.

Para tarefas simples e unitárias, pode usar [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) para executar comandos numa sessão JEA.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Para verificar quais comandos estão disponíveis para utilização quando se liga a uma sessão JEA, execute `Get-Command` e iterar os resultados para verificar os parâmetros permitidos.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Se estiver criando um C# aplicação, pode criar um espaço de execução do PowerShell que se liga a uma sessão JEA, especificando o nome de configuração num [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) objeto.

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

## <a name="using-jea-with-powershell-direct"></a>Utilizar a JEA com o PowerShell Direct

Hyper-V no Windows 10 e Windows Server 2016 oferece [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), uma funcionalidade que permite aos administradores de Hyper-V gerir máquinas virtuais com o PowerShell, independentemente da configuração de rede ou a gestão remota definições da máquina virtual.

Pode utilizar o PowerShell Direct com JEA para dar um acesso de administrador limitado do Hyper-V para a VM.
Isso pode ser útil se perder a conectividade de rede para a VM e precisar de um administrador do datacenter para corrigir as definições de rede.

Nenhuma configuração adicional é necessário para utilizar a JEA através do PowerShell Direct. No entanto, o sistema operativo convidado em execução dentro da máquina virtual tem de ser Windows 10, Windows Server 2016 ou superior. O administrador do Hyper-V, pode ligar ao ponto final JEA utilizando o `-VMName` ou `-VMId` parâmetros PSRemoting cmdlets:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Recomenda-se que criar uma conta de utilizador dedicado com os direitos mínimos necessários para gerir o sistema para utilização por um administrador do Hyper-V. Lembre-se de que, até mesmo um utilizador sem privilégios pode iniciar sessão numa máquina Windows por padrão, incluindo com o PowerShell irrestrita. Isso permite que os mesmos para procurar o sistema de ficheiros e saiba mais sobre o ambiente do sistema operacional. Para bloquear um administrador do Hyper-V e limitá-las apenas para acessar uma VM com o PowerShell Direct com JEA, tem de negar direitos de início de sessão local para a conta JEA do administrador do Hyper-V.
