---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Utilizar a JEA
ms.openlocfilehash: 539d280aff0b2656a5e9c710acfa468057753027
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522995"
---
# <a name="using-jea"></a>Utilizar a JEA

> Aplica-se a: Windows PowerShell 5.0

Este tópico descreve as várias formas como pode ligar e utilizar um ponto final JEA.

## <a name="using-jea-interactively"></a>Utilizar a JEA interativamente

Se estiver a testar a configuração de JEA ou tiver tarefas simples para que os usuários realizem, pode usar JEA da mesma forma que faria com uma sessão de comunicação remota do PowerShell regular.
Para tarefas de comunicação remota complexas, é recomendável usar [comunicação remota implícita](#using-jea-with-implicit-remoting) em vez disso, para tornar mais fácil para os seus utilizadores ao permitir que os utilizadores funcionar com os dados localmente objetos.

Para utilizar a JEA interativamente, terá de:
- O nome do computador que está a ligar (pode ser o computador local)
- O nome do ponto final JEA registado nesse computador
- Credenciais para o computador que têm acesso ao ponto final JEA

Com essas informações em mãos, pode iniciar uma sessão JEA usando [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) ou [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Se a conta que tem atualmente sessão iniciada como tem acesso ao ponto final JEA, poderá omitir a `-Credential` parâmetro.

Quando o PowerShell solicitar alterações `[localhost]: PS>` ficará a saber o que estiver a interagir agora com a sessão JEA remota.
Pode executar `Get-Command` para verificar quais comandos estão disponíveis.
Precisará consultar com o seu administrador para saber se existem quaisquer restrições nos parâmetros disponíveis ou valores de parâmetro permitidos.

Como lembrete, sessões JEA funcionam num modo de NoLanguage, pelo que algumas das formas de que utilizar o PowerShell, normalmente, podem não estar disponíveis.
Por exemplo, é possível utilizar variáveis para armazenar os dados ou Inspecione as propriedades em objetos devolvidos por cmdlets.
A seguir o exemplo mostra um exemplo de como pode estar a utilizar PowerShell hoje mesmo e duas abordagens para obter o mesmo comando trabalhar no modo de NoLanguage.

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

Para invocações de comando mais complexas que dificultam essa abordagem, considere a utilização [comunicação remota implícita](#using-jea-with-implicit-remoting) ou [criar funções personalizadas](role-capabilities.md#creating-custom-functions) que encapsule a funcionalidade desejado.

## <a name="using-jea-with-implicit-remoting"></a>Utilizar a JEA com comunicação remota implícita

PowerShell suporta um modelo de comunicação remota alternativo onde pode importar os cmdlets do proxy de um computador remoto no seu computador local e interagir com eles, como se estivessem comandos locais.
Isso é chamado de comunicação remota implícita e é explicado no [isso *Hey, Scripting Guy!* mensagem do blogue](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).
Comunicação remota implícita é particularmente útil ao trabalhar com JEA porque ela permite que trabalhe com os cmdlets JEA num modo de linguagem completa.
Isso significa que pode utilizar a conclusão de tabulação, variáveis, manipular os objetos e até mesmo usar scripts locais para automatizar mais facilmente em relação a um ponto final JEA.
Sempre que invocar um comando de proxy, os dados serão enviados para o ponto final JEA na máquina remota e executados lá.

Comunicação remota implícita funciona através da importação cmdlets a partir de uma sessão do PowerShell existente.
Opcionalmente, pode optar por prefixo os nomes de cada cmdlet de proxy com uma cadeia de caracteres de sua escolha para distinguir quais comandos estão do sistema remoto.
Um módulo de script temporário que contém todos os comandos de proxy será criado e pode ser utilizado para a duração de sessão local do PowerShell.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Alguns sistemas talvez não consiga importar uma sessão completa de JEA devido a restrições nos cmdlets JEA padrão.
> Para contornar esse problema, só importar os comandos de que precisa da sessão JEA fornecendo explicitamente os respetivos nomes para o `-CommandName` parâmetro.
> Uma atualização futura irá resolver o problema com a importação de sessões JEA todos em sistemas afetados.

Se não é possível importar uma sessão JEA devido a restrições em parâmetros JEA predefinidos, pode seguir os passos abaixo para filtrar os comandos padrão do conjunto de importados.
Ainda poderá usar comandos como `Select-Object` – usará a versão local instalada no seu computador em vez da remoto na sessão JEA.

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

Também pode manter os cmdlets transmitidas por proxy de comunicação remota implícita usando [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).
Para obter mais informações sobre a comunicação remota implícita, consulte a documentação de ajuda para [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) e [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).

## <a name="using-jea-programatically"></a>Utilizar a JEA programaticamente

JEA também pode ser utilizado em sistemas de automatização e nos aplicativos de usuário, como web sites e aplicações de suporte técnico interno.
A abordagem é o mesmo que para criar aplicações que comunique com os pontos finais irrestrita do PowerShell, tendo em mente que o programa deve conhecer JEA esteja a limitar os comandos que podem ser executados na sessão remota.

Para tarefas simples e unitárias, pode usar [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) para executar um conjunto de comandos utilizando JEA.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Para verificar quais comandos estão disponíveis para utilização quando se liga a uma sessão JEA, execute `Get-Command` e iterar os resultados para verificar os parâmetros permitidos.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Se estiver a criar uma aplicação c#, pode criar um espaço de execução do PowerShell que se liga a uma sessão JEA, especificando o nome de configuração num [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) objeto.

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

## <a name="using-jea-with-powershell-direct"></a>Utilizar a JEA com o PowerShell Direct

Hyper-V no Windows 10 e Windows Server 2016 oferece [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), uma funcionalidade que permite aos administradores de Hyper-V gerir máquinas virtuais com o PowerShell, independentemente da configuração de rede ou a gestão remota definições da máquina virtual.

Pode utilizar o PowerShell Direct com JEA para dar um acesso de administrador limitado de Hyper-V para a VM, que pode ser útil se perder a conectividade de rede para a VM e precisar de um administrador do datacenter para corrigir as definições de rede.

Nenhuma configuração adicional é necessária para utilizar a JEA através do PowerShell Direct, o sistema operativo em execução dentro da máquina virtual tem de ser Windows 10 ou Windows Server 2016.
O administrador do Hyper-V, pode ligar ao ponto final JEA utilizando o `-VMName` ou `-VMId` parâmetros PSRemoting cmdlets:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

É vivamente recomendado que crie um utilizador local dedicado com nenhum outro direito para gerir o sistema para os administradores de Hyper-V para utilizar.
Lembre-se de que até mesmo um utilizador sem privilégios pode ainda iniciar sessão numa máquina Windows por padrão, incluindo com o PowerShell irrestrita.
Que irão permitir-lhe procurar (alguns dos) no sistema de arquivos e saiba mais sobre o ambiente do sistema operacional.
Bloquear um administrador do Hyper-V apenas para acessar uma VM com o PowerShell Direct com JEA, terá de negar direitos de início de sessão local para a conta JEA do administrador do Hyper-V.