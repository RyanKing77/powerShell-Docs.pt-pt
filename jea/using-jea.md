---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Utilizar a JEA
ms.openlocfilehash: 891e4be4c3fadceeff5ede7ac5cab04a5f80e5c1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190082"
---
# <a name="using-jea"></a>Utilizar a JEA

> Aplica-se a: Windows PowerShell 5.0

Este tópico descreve as várias formas de poder ligar ao e utilizar um ponto final JEA.

## <a name="using-jea-interactively"></a>Utilizar o JEA interativamente

Se estiver a testar a configuração de JEA ou têm tarefas simples para que os utilizadores efetuem, pode utilizar JEA da mesma forma que faria com uma sessão de comunicação remota do PowerShell regular.
Para tarefas de comunicação remota complexa, é recomendado utilizar [comunicação remota implícita](#using-jea-with-implicit-remoting) em vez disso, para tornar mais fácil para os seus utilizadores, permitindo que os utilizadores funcionar com os dados de objetos de localmente.

Para utilizar o JEA interativamente, necessitará de:
- O nome do computador que está a ligar (pode ser o computador local)
- O nome do ponto final JEA registado nesse computador
- Credenciais do computador que tem acesso ao ponto final do JEA

Com essa informação em mão, pode iniciar uma sessão JEA utilizando [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) ou [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Se a conta que está atualmente sessão iniciada como tem acesso ao ponto final do JEA, pode omitir o `-Credential` parâmetro.

Quando o PowerShell solicitar as alterações à `[localhost]: PS>` ficará a saber que agora interage com a sessão JEA remota.
Pode executar `Get-Command` para verificar quais os comandos estão disponíveis.
Terá de Consulte com o seu administrador para saber se existem quaisquer restrições para os parâmetros disponíveis ou valores de parâmetro permitido.

Como um lembrete sessões JEA operam em modo de NoLanguage, pelo que algumas das formas que é, normalmente, utilizar o PowerShell poderão não estar disponíveis.
Por exemplo, não é possível utilizar variáveis para armazenar dados ou Inspecione as propriedades de objetos devolvidos de cmdlets.
O abaixo exemplo mostra um exemplo de como pode utilizar o PowerShell hoje em dia, e duas abordagens para obter o mesmo comando funcionar no modo de NoLanguage.

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

Para mais complexas invocações de comando que esta abordagem difícil, considere a utilização [comunicação remota implícita](#using-jea-with-implicit-remoting) ou [criar funções personalizadas](role-capabilities.md#creating-custom-functions) que encapsular a funcionalidade pretendidos ao nível.

## <a name="using-jea-with-implicit-remoting"></a>Utilizar JEA com comunicação remota implícita

PowerShell suporta um modelo de sistema de interação remota alternativo onde pode importar os cmdlets do proxy de um computador remoto no computador local e interagir com os mesmos, como se estivessem comandos locais.
Isto é denominado sistema de interação remota implícito e é explicado no bem [isto *Hey, Scripting Guy!* blogue](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).
Comunicação remota implícita é particularmente útil ao trabalhar com JEA porque permite-lhe trabalhar com os cmdlets JEA num modo completo de linguagem.
Isto significa que pode utilizar conclusão de separador, variáveis, manipular objetos e mesmo utilize scripts de locais para automatizar mais facilmente em relação a um ponto final JEA.
Em qualquer altura invocar um comando de proxy, os dados serão enviados para o ponto final JEA no computador remoto e executados não existe.

Comunicação remota implícita funciona através da importação de cmdlets do PowerShell sessão existente.
Opcionalmente, pode optar por prefixo os substantivos de cada cmdlet de proxy com uma cadeia à sua escolha distinguir os comandos são para o sistema remoto.
Um módulo de script temporária que contém todos os comandos proxy será criado e pode ser utilizado para a duração da sessão do PowerShell local.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Alguns sistemas poderão não conseguir importar uma sessão completa de JEA devido a restrições de cmdlets JEA predefinido.
> Para contornar este problema, apenas importar os comandos que precisa da sessão JEA fornecendo explicitamente os respetivos nomes para o `-CommandName` parâmetro.
> Atualização futura irá resolver o problema com a importação completos JEA sessões no sistemas afetados.

Se não for possível importar uma sessão JEA devido a restrições de parâmetros predefinidos de JEA, pode seguir os passos abaixo para filtrar os comandos predefinida do conjunto de importado.
Ainda poderá utilizar comandos como `Select-Object` – apenas utilizará a versão local instalada no seu computador em vez dos remoto na sessão JEA.

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

Também pode manter os cmdlets efetuados da utilização do sistema de interação remota implícito [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).
Para obter mais informações sobre a gestão remota implícita, consulte a documentação de ajuda para [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) e [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).

## <a name="using-jea-programatically"></a>Utilizar o JEA x509securitytokenparameters

JEA também pode ser utilizado em sistemas de automatização e nas aplicações do utilizador, tais como aplicações de suporte técnico internas e web sites.
A abordagem é o mesmo que para a criação de aplicações que comunique com os pontos finais do PowerShell, com a advertência de que o programa deve estar ciente de que o JEA é limitar os comandos que podem ser executados na sessão remota.

Para tarefas simples, pontuais, pode utilizar [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) para executar um conjunto de comandos utilizando JEA.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Para verificar quais os comandos estão disponíveis para utilização quando se liga a uma sessão JEA, execute `Get-Command` e iterar percorrer os resultados para verificar se os parâmetros permitidos.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Se está a criar uma aplicação c#, pode criar um espaço de execução do PowerShell que estabelece ligação a uma sessão JEA, especificando o nome da configuração num [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) objeto.

```csharp

// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/en-us/library/system.management.automation.pscredential(v=vs.85).aspx)

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

## <a name="using-jea-with-powershell-direct"></a>Utilizar o JEA com o PowerShell direta

Hyper-V no Windows 10 e Windows Server 2016 oferece [PowerShell direta](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession), uma funcionalidade que permite aos administradores de Hyper-V gerir máquinas virtuais com o PowerShell, independentemente da configuração de rede ou a gestão remota definições da máquina virtual.

Pode utilizar o PowerShell direta com JEA para conceder um acesso de administrador limitado de Hyper-V à sua VM, que pode ser útil se perder a conectividade de rede para a VM e precisar de um administrador de datacenter para corrigir as definições de rede.

Nenhuma configuração adicional é necessária utilizar JEA através do PowerShell direta, no entanto, o sistema operativo em execução dentro da máquina virtual tem de ser Windows 10 ou Windows Server 2016.
O administrador do Hyper-V pode ligar ao ponto final do JEA utilizando o `-VMName` ou `-VMId` parâmetros PSRemoting cmdlets:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

É vivamente recomendado que crie um utilizador local dedicado com outros direitos de gerir o sistema para os administradores de Hyper-V para utilizar.
Lembre-se de que, mesmo um utilizador sem privilégios pode ainda iniciar sessão numa máquina Windows por predefinição, incluindo a utilização do PowerShell.
Que irão permitir-lhe procurar (alguns dos) do sistema de ficheiros e obter mais informações sobre o ambiente de SO.
Para bloquear um administrador do Hyper-V para aceder apenas uma VM com o PowerShell direta JEA, terá de negar direitos de início de sessão local para a conta JEA do administrador do Hyper-V.