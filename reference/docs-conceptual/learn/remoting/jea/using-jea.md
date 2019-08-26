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
# <a name="using-jea"></a>Utilizar a JEA

Este artigo descreve as várias maneiras pelas quais você pode se conectar e usar um ponto de extremidade JEA.

## <a name="using-jea-interactively"></a>Usando o JEA interativamente

Se você estiver testando a configuração do JEA ou tiver tarefas simples para os usuários, poderá usar o JEA da mesma maneira que faria com uma sessão de comunicação remota do PowerShell normal. Para tarefas de comunicação remota complexas, é recomendável usar [comunicação remota implícita](#using-jea-with-implicit-remoting). A comunicação remota implícita permite que os usuários operem com os objetos de dados localmente.

Para usar o JEA interativamente, você precisa:

- O nome do computador ao qual você está se conectando (pode ser o computador local)
- O nome do ponto de extremidade JEA registrado no computador
- Credenciais que têm acesso ao ponto de extremidade do JEA nesse computador

Dadas essas informações, você pode iniciar uma sessão JEA usando os cmdlets [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) ou [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) .

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Se a conta de usuário atual tiver acesso ao ponto de extremidade JEA, você poderá omitir o parâmetro **Credential** .

Quando o prompt do PowerShell for `[localhost]: PS>` alterado para você, você saberá que agora está interagindo com a sessão Jea remota. Você pode executar `Get-Command` para verificar quais comandos estão disponíveis. Consulte seu administrador para saber se há restrições sobre os parâmetros disponíveis ou os valores de parâmetro permitidos.

Lembre-se de que as sessões JEA operam no modo nolanguage. Algumas das maneiras que você normalmente usa o PowerShell podem não estar disponíveis. Por exemplo, você não pode usar variáveis para armazenar dados ou inspecionar as propriedades em objetos retornados de cmdlets. O exemplo a seguir mostra duas abordagens para obter os mesmos comandos para trabalhar no modo nolanguage.

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

Para invocações de comando mais complexas que tornam essa abordagem difícil, considere o uso de [comunicação remota implícita](#using-jea-with-implicit-remoting) ou a [criação de funções personalizadas](role-capabilities.md#creating-custom-functions) que encapsulam a funcionalidade necessária.

## <a name="using-jea-with-implicit-remoting"></a>Usando o JEA com comunicação remota implícita

O PowerShell tem um modelo de comunicação remota implícito que permite que você importe cmdlets de proxy de um computador remoto e interaja com eles como se eles fossem comandos locais. A comunicação remota implícita é explicada neste **Ei, equipe de scripts!** [postagem no blog](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).
A comunicação remota implícita é útil ao trabalhar com JEA porque permite que você trabalhe com cmdlets JEA em um modo de linguagem completa. Você pode usar o preenchimento com Tab, variáveis, manipular objetos e até mesmo usar scripts locais para automatizar tarefas em um ponto de extremidade JEA. Sempre que você invoca um comando de proxy, os dados são enviados para o ponto de extremidade JEA no computador remoto e executados lá.

A comunicação remota implícita funciona importando cmdlets de uma sessão do PowerShell existente. Opcionalmente, você pode optar por prefixar os substantivos de cada cmdlet de proxy com uma cadeia de caracteres de sua escolha. O prefixo permite que você diferencie os comandos que são para o sistema remoto. Um módulo de script temporário que contém todos os comandos de proxy é criado e importado durante a sua sessão local do PowerShell.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Alguns sistemas podem não ser capazes de importar uma sessão JEA inteira devido a restrições nos cmdlets JEA padrão. Para contornar isso, importe apenas os comandos necessários da sessão Jea fornecendo explicitamente seus nomes para o `-CommandName` parâmetro. Uma atualização futura resolverá o problema com a importação de sessões inteiras do JEA em sistemas afetados.

Se não for possível importar uma sessão JEA devido a restrições JEA nos parâmetros padrão, siga as etapas abaixo para filtrar os comandos padrão do conjunto importado. Você pode continuar usando comandos como `Select-Object`, mas você usará apenas a versão local instalada no seu computador em vez de uma importada da sessão Jea remota.

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

Você também pode persistir os cmdlets de proxy de comunicação remota implícita usando [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).
Para obter mais informações sobre comunicação remota implícita, consulte a documentação de [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) e [Import-Module](/powershell/microsoft.powershell.core/import-module).

## <a name="using-jea-programmatically"></a>Usando o JEA programaticamente

O JEA também pode ser usado em sistemas de automação e em aplicativos de usuário, como aplicativos de assistência técnica interna e sites. A abordagem é a mesma que a criação de aplicativos que se comunicam com pontos de extremidade do PowerShell sem restrição. Verifique se o programa foi projetado para funcionar com limitação imposta pelo JEA.

Para tarefas simples e única, você pode usar [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) para executar comandos em uma sessão Jea.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Para verificar quais comandos estão disponíveis para uso quando você se conecta a uma sessão do Jea `Get-Command` , execute e itere nos resultados para verificar os parâmetros permitidos.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Se você estiver criando um C# aplicativo, poderá criar um runspace do PowerShell que se conecta a uma sessão Jea especificando o nome da configuração em um objeto [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) .

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

## <a name="using-jea-with-powershell-direct"></a>Usando o JEA com o PowerShell Direct

O Hyper-V no Windows 10 e no Windows Server 2016 oferece o [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), um recurso que permite que os administradores do Hyper-v gerenciem máquinas virtuais com o PowerShell, independentemente da configuração de rede ou das configurações de gerenciamento remoto na máquina virtual Tradução.

Você pode usar o PowerShell Direct com JEA para dar a um administrador do Hyper-V acesso limitado à sua VM.
Isso pode ser útil se você perder a conectividade de rede para sua VM e precisar de um administrador de datacenter para corrigir as configurações de rede.

Nenhuma configuração adicional é necessária para usar o JEA no PowerShell Direct. No entanto, o sistema operacional convidado em execução dentro da máquina virtual deve ser Windows 10, Windows Server 2016 ou superior. O administrador do Hyper-V pode se conectar ao ponto de extremidade Jea `-VMName` usando `-VMId` os parâmetros ou nos cmdlets PSRemoting:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

É recomendável que você crie uma conta de usuário dedicada com os direitos mínimos necessários para gerenciar o sistema para uso por um administrador do Hyper-V. Lembre-se, mesmo um usuário sem privilégios pode entrar em um computador Windows por padrão, incluindo o uso do PowerShell irrestrito. Isso permite que eles procurem o sistema de arquivos e saiba mais sobre o ambiente do sistema operacional. Para bloquear um administrador do Hyper-V e limitá-los a acessar apenas uma VM usando o PowerShell Direct com JEA, você deve negar direitos de logon local à conta JEA do administrador do Hyper-V.
