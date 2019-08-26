---
ms.date: 07/10/2019
keywords: Jea, PowerShell, segurança
title: Auditoria e relatórios no JEA
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017924"
---
# <a name="auditing-and-reporting-on-jea"></a>Auditoria e relatórios no JEA

Depois de implantar o JEA, você precisa auditar regularmente a configuração do JEA. A auditoria ajuda a avaliar que as pessoas corretas têm acesso ao ponto de extremidade JEA e suas funções atribuídas ainda são apropriadas.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Localizar sessões de JEA registradas em um computador

Para verificar quais sessões do JEA estão registradas em um computador, use o cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) .

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

Os direitos efetivos para o ponto de extremidade são listados na propriedade **Permission** . Esses usuários têm o direito de se conectar ao ponto de extremidade JEA. No entanto, as funções e os comandos aos quais eles têm acesso são determinados pela propriedade **RoleDefinitions** no [arquivo de configuração de sessão](session-configurations.md) que foi usado para registrar o ponto de extremidade. Expanda a propriedade **RoleDefinitions** para avaliar os mapeamentos de função em um ponto de extremidade Jea registrado.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Localizar recursos de função disponíveis no computador

Jea Obtém os `.psrc` recursos de função dos arquivos armazenados na pasta **RoleCapabilities** dentro de um módulo do PowerShell. A função a seguir localiza todos os recursos de função disponíveis em um computador.

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> A ordem dos resultados dessa função não é necessariamente a ordem na qual os recursos de função serão selecionados se vários recursos de função compartilham o mesmo nome.

## <a name="check-effective-rights-for-a-specific-user"></a>Verificar direitos efetivos de um usuário específico

O cmdlet [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) enumera todos os comandos disponíveis em um ponto de extremidade Jea com base nas associações de grupo de um usuário.
A saída de `Get-PSSessionCapability` é idêntica à do usuário especificado em execução `Get-Command -CommandType All` em uma sessão Jea.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Se os usuários não são membros permanentes de grupos que concedem direitos JEAs adicionais, esse cmdlet pode não refletir essas permissões extras. Isso acontece ao usar sistemas de gerenciamento de acesso privilegiado just-in-time para permitir que os usuários pertençam temporariamente a um grupo de segurança. Avalie cuidadosamente o mapeamento de usuários para funções e recursos para garantir que os usuários obtenham apenas o nível de acesso necessário para realizar seus trabalhos com êxito.

## <a name="powershell-event-logs"></a>Logs de eventos do PowerShell

Se você habilitou o log do módulo ou do bloco de script no sistema, poderá ver os eventos nos logs de eventos do Windows para cada comando executado por um usuário em uma sessão do JEA. Para encontrar esses eventos, abra **Microsoft-Windows-PowerShell/** log de eventos operacional e procure eventos com a ID de evento **4104**.

Cada entrada de log de eventos inclui informações sobre a sessão na qual o comando foi executado. Para sessões JEA, o evento inclui informações sobre o **ConnectedUser** e o **RunAsUser**. O **ConnectedUser** é o usuário real que criou a sessão Jea. **RunAsUser** é a conta Jea usada para executar o comando.

Os logs de eventos do aplicativo mostram as alterações feitas por **RunAsUser**. Portanto, ter o log de módulo e script habilitado é necessário para rastrear uma invocação de comando específica de volta para o **ConnectedUser**.

## <a name="application-event-logs"></a>Logs de eventos do aplicativo

Os comandos executados em uma sessão JEA que interagem com aplicativos ou serviços externos podem registrar eventos em seus próprios logs de eventos. Ao contrário dos logs do PowerShell e das transcrições, outros mecanismos de registro em log não capturam o usuário conectado da sessão JEA. Em vez disso, esses aplicativos registram apenas o usuário virtual executar como.
Para determinar quem executou o comando, você precisa consultar uma [transcrição de sessão](#session-transcripts) ou correlacionar os logs de eventos do PowerShell com a hora e o usuário mostrados no log de eventos do aplicativo.

O log do WinRM também pode ajudá-lo a correlacionar os usuários executar como ao usuário que está se conectando em um log de eventos do aplicativo. A ID do evento **193** no log **Microsoft-Windows-gerenciamento remoto do Windows/Operational** registra o Sid (identificador de segurança) e o nome da conta para o usuário que está se conectando e o usuário executar como para cada nova sessão do Jea.

## <a name="session-transcripts"></a>Transcrições de sessão

Se você tiver configurado o JEA para criar uma transcrição para cada sessão de usuário, uma cópia de texto das ações de cada usuário será armazenada na pasta especificada.

O comando a seguir (como administrador) localiza todos os diretórios de transcrição.

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

Cada transcrição começa com informações sobre a hora em que a sessão foi iniciada, qual usuário se conectou à sessão e qual identidade JEA foi atribuída a elas.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

O corpo da transcrição contém informações sobre cada comando invocado pelo usuário. A sintaxe exata do comando usado não está disponível em sessões JEA devido à maneira como os comandos são transformados para a comunicação remota do PowerShell. No entanto, você ainda pode determinar o comando efetivo que foi executado. Veja abaixo um exemplo de trecho de transcrição de um `Get-Service Dns` usuário em execução em uma sessão Jea:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Uma linha **CommandInvocation** é escrita para cada comando que um usuário executa. **ParameterBindings** registra cada parâmetro e valor fornecido com o comando. No exemplo anterior, você pode ver que o **nome** do parâmetro foi fornecido com o **DNS** com valor para `Get-Service` o cmdlet.

A saída de cada comando também dispara um **CommandInvocation**, geralmente para `Out-Default`. O **InputObject** de `Out-Default` é o objeto do PowerShell retornado do comando. Os detalhes desse objeto são impressos em algumas linhas abaixo, imitando o que o usuário teria visto.

## <a name="see-also"></a>Consulte também

[*PowerShell ♥ a* postagem no blog da equipe azul sobre segurança](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
