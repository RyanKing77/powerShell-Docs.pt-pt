---
ms.date: 07/10/2019
keywords: jea, powershell, segurança
title: Auditoria e relatórios na JEA
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726752"
---
# <a name="auditing-and-reporting-on-jea"></a>Auditoria e relatórios na JEA

Depois de implementar JEA, terá de regularmente fazer auditoria da configuração de JEA. Auditoria ajuda a avaliar o que as pessoas certas tenham acesso ao ponto final JEA e suas funções são ainda adequadas.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Encontre sessões JEA registrados numa máquina

Para verificar quais sessões JEA são registrados num computador, utilize o [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

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

Os direitos em vigor para o ponto final estão listados na **permissão** propriedade. Estes utilizadores têm o direito de ligar para o ponto final da JEA. No entanto, as funções e comandos aos quais têm acesso é determinado pelos **RoleDefinitions** propriedade na [o ficheiro de configuração de sessão](session-configurations.md) que foi utilizada para registar o ponto final. Expanda a **RoleDefinitions** propriedade para avaliar os mapeamentos de função num ponto final da JEA registado.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Localizar funcionalidades de função disponíveis na máquina

JEA obtém capacidades de função a partir do `.psrc` ficheiros armazenados no **RoleCapabilities** pasta dentro de um módulo do PowerShell. A função seguinte localiza todas as funcionalidades de função disponíveis num computador.

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
> A ordem de resultados desta função não é necessariamente a ordem na qual os recursos de função seja selecionados se várias funcionalidades de função partilham o mesmo nome.

## <a name="check-effective-rights-for-a-specific-user"></a>Verificação de direitos em vigor a partir de um utilizador específico

O [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumera todos os comandos disponíveis num ponto final JEA com base em associações de grupo de um utilizador.
A saída de `Get-PSSessionCapability` é idêntico ao que o utilizador especificado em execução `Get-Command -CommandType All` numa sessão JEA.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Se os utilizadores não são membros permanentes dos grupos que concedem os direitos JEA adicionais, este cmdlet pode não refletir essas permissões adicionais. Isto acontece quando utilizar sistemas de gestão para permitir que os utilizadores temporariamente pertencem a um grupo de segurança de acesso privilegiado just-in-time. Avalie cuidadosamente o mapeamento de utilizadores a funções e funcionalidades para garantir que os utilizadores obtenham apenas o nível de acesso necessário para realizar seus trabalhos com êxito.

## <a name="powershell-event-logs"></a>Registos de eventos do PowerShell

Se ativou o registo do sistema de bloco de módulo ou script, pode ver eventos nos logs de eventos do Windows para cada comando que é executado um usuário numa sessão JEA. Para localizar esses eventos, abra **Microsoft-Windows-PowerShell/Operational** registo de eventos e procure eventos com o ID de evento **4104**.

Cada entrada de registo de eventos inclui informações sobre a sessão em que o comando foi executado. Para sessões JEA, o evento inclui informações sobre o **ConnectedUser** e o **RunAsUser**. O **ConnectedUser** é o utilizador real que criou a sessão JEA. O **RunAsUser** é a conta JEA utilizada para executar o comando.

Registos de eventos do aplicativo mostrar as alterações feitas pela **RunAsUser**. Para ter o módulo e o registo de script ativada é necessária para o rastreio de uma invocação de comando específico de volta para o **ConnectedUser**.

## <a name="application-event-logs"></a>Registos de eventos do aplicativo

Comandos executados numa sessão JEA que interagem com aplicações externas ou serviços podem registar eventos em seus próprios registos de eventos. Ao contrário dos registos do PowerShell e transcrições, outros mecanismos de Registro em log não capturam do usuário conectado da sessão JEA. Em vez disso, esses aplicativos apenas iniciar o utilizador Run virtual.
Para determinar que executou o comando, precisar de consultar um [transcrição de sessão](#session-transcripts) ou correlacionar os registos de eventos do PowerShell com o tempo e o utilizador mostrado no log de eventos do aplicativo.

O registo de WinRM também pode ajudar correlacionar os utilizadores executar como para o usuário conectado num log de eventos do aplicativo. ID de evento **193** no **Microsoft-Windows-Windows remoto gestão/Operational** os registros do log o identificador de segurança (SID) e o nome de conta para a ligação de utilizadores e de execução como usuário para cada novo JEA sessão.

## <a name="session-transcripts"></a>Transcrições de sessão

Se tiver configurado a JEA para criar uma transcrição para cada sessão de utilizador, uma cópia de texto de ações de cada usuário são armazenadas na pasta especificada.

O seguinte comando (como administrador) localiza todos os diretórios de transcrição.

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

Cada transcrição começa com informações sobre a sessão iniciada, o tempo que utilizador ligado para a sessão e que identidade JEA foi atribuída a eles.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

O corpo da transcrição contém informações sobre cada comando invocado do utilizador. A sintaxe exata do comando utilizado não está disponível em sessões JEA por conta da forma comandos são transformados para comunicação remota do PowerShell. No entanto, ainda é possível determinar o comando eficaz que foi executado. Segue-se um fragmento de transcrição de exemplo de um utilizador que executa `Get-Service Dns` numa sessão JEA:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

R **CommandInvocation** linha foi escrita para cada comando é executado de um utilizador. **ParameterBindings** gravar cada parâmetro e o valor fornecido com o comando. No exemplo anterior, pode ver que o parâmetro **Name** foi fornecida a com o valor **Dns** para o `Get-Service` cmdlet.

A saída de cada comando também aciona uma **CommandInvocation**normalmente ao `Out-Default`. O **InputObject** de `Out-Default` é o objeto do PowerShell devolvido do comando. Os detalhes desse objeto são impressos algumas linhas abaixo, imitando de perto o que o usuário teria visto.

## <a name="see-also"></a>Consulte também

[*PowerShell ♥ a equipa de azul* mensagem de blogue sobre segurança](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
