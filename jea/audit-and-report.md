---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Auditoria e de relatórios no JEA
ms.openlocfilehash: e68206cd6fe94c51507f42ae2c3e6702f6fd4e0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188857"
---
# <a name="auditing-and-reporting-on-jea"></a>Auditoria e de relatórios no JEA

> Aplica-se a: Windows PowerShell 5.0

Após implementar JEA, irá querer regularmente a configuração de JEA de auditoria.
Isto irá ajudar a avaliar se as pessoas corretas tem acesso ao ponto final do JEA e as respetivas funções atribuídas são ainda adequadas.

Este tópico descreve as várias formas, pode auditar um ponto final JEA.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Localizar sessões JEA registadas num computador

Para verificar quais sessões JEA estão registadas num computador, utilize o [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

Os direitos eficazes para o ponto final estão listados na propriedade "Permissão".
Estes utilizadores tem permissão para ligar ao ponto de final JEA, mas que funções (e, por extensão, comandos) têm acesso aos é determinado pelo campo "RoleDefinitions" no [ficheiro de configuração de sessão](session-configurations.md) que foi utilizada para registar o ponto final.

Pode avaliar os mapeamentos de funções num ponto final JEA registado, expandindo os dados na propriedade "RoleDefinitions".

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Localizar as capacidades de função disponível na máquina

Ficheiros de capacidade de função só serão utilizados pelo JEA se são armazenados numa pasta "RoleCapabilities" dentro de um módulo do PowerShell válida.
Pode encontrar todas as capacidades de função disponíveis num computador ao pesquisar a lista de módulos disponíveis.

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
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> A ordem dos resultados desta função não é necessariamente a ordem em que as capacidades de função serão selecionadas se várias capacidades de função partilham o mesmo nome.

## <a name="check-effective-rights-for-a-specific-user"></a>Selecione efetivos direitos para um utilizador específico

Assim que tiver configurado um ponto final JEA, poderá pretender verificar quais os comandos estão disponíveis para um utilizador específico numa sessão JEA.
Pode utilizar [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) enumerar todos os comandos aplicáveis a um utilizador se estivessem iniciar uma sessão JEA com as respetivas associações a atual.
A saída do `Get-PSSessionCapability` é idêntico ao que o utilizador especificado em execução `Get-Command -CommandType All` numa sessão JEA.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Se os utilizadores não são membros permanentes do grupos que podem conceder direitos JEA adicionais, este cmdlet pode não refletir essas permissões adicionais.
Isto é normalmente o caso quando utilizar sistemas de gestão de acesso privilegiado just-in-time para permitir que os utilizadores temporariamente pertence a um grupo de segurança.
Avaliar sempre cuidadosamente o mapeamento de utilizadores a funções e o conteúdo de cada função para garantir que os utilizadores só é obter acesso para o mínimo de comandos necessários para as respetivas tarefas com êxito.

## <a name="powershell-event-logs"></a>Registos de eventos do PowerShell

Se tiver ativado o bloco de módulo e/ou de script de início de sessão no sistema, poderá encontrar eventos nos registos de eventos do Windows para cada comando que foi executado um utilizador nas respetivas sessões JEA.
Para obter estes eventos, abra o Visualizador de eventos do Windows, navegue para o **Microsoft-Windows-PowerShell/Operational** registo de eventos e procure eventos com o ID de evento **4104**.

Cada entrada de registo de eventos irá incluir informações sobre a sessão no qual o comando foi executado.
Para sessões JEA, isto inclui informações importantes sobre o **ConnectedUser**, que é o utilizador real que criou a sessão JEA, bem como o **RunAsUser** que identifica a conta JEA utilizada para Execute o comando.
Os registos de eventos de aplicações irá mostrar as alterações que está a ser efetuadas pelo RunAsUser, por isso, ter transcrições ou o registo de módulo/script ativado é fundamental para conseguir uma invocação de comando específico para um utilizador de rastreio.

## <a name="application-event-logs"></a>Registos de eventos de aplicações

Quando executar um comando numa sessão JEA que interage com uma aplicação externa ou um serviço, as aplicações podem registar eventos para os seus próprios registos de eventos.
Ao contrário dos registos do PowerShell e transcrições, outros mecanismos de registo não capturará o utilizador da sessão JEA ligado e, em vez disso, apenas registará o utilizador executar como virtual ou a conta de serviço geridas de grupo.
Para determinar que executou o comando, é necessário consultar um [transcript sessão](#session-transcripts) ou correlacionar os registos de eventos do PowerShell com a hora e o utilizador apresentado no registo de eventos de aplicações.

O WinRM registo também pode ajudar a correlacionar run utilizadores um registo de eventos de aplicações com o utilizador ao ligar.
ID de evento **193** no **Microsoft-Windows-Windows remoto gestão/Operational** registos a conta do identificador de segurança (SID) e o nome do utilizador ao ligar e executar como utilizador sempre que um JEA a sessão é criada.

## <a name="session-transcripts"></a>Transcrições de sessão

Se tiver configurado o JEA para criar um transcript para cada sessão de utilizador, uma cópia de texto de ações de cada utilizador será armazenada na pasta especificada.

Para localizar todos os diretórios de transcript, execute o seguinte comando como administrador no computador configurado com JEA:

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

Cada transcript começa com informações sobre a hora de início de sessão, que utilizador ligado para a sessão e que identidade JEA foi atribuída.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

No corpo do transcript, as informações são registadas sobre cada comando invocado o utilizador.
A sintaxe exata do comando que foi executado o utilizador não está disponível em sessões JEA devido a forma como os comandos são transformados para comunicação remota do PowerShell, no entanto, ainda pode determinar o comando Efetivo que foi executado.
Segue-se um fragmento de transcript de exemplo de um utilizador que executa `Get-Service Dns` numa sessão JEA:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Para cada comando que executa um utilizador, uma linha de "CommandInvocation" será escrita, que descreve o cmdlet ou função de utilizador invocado.
ParameterBindings siga cada CommandInvocation para lhe indicar sobre cada parâmetro e valor que foi fornecido com o comando.
No exemplo acima, pode ver que o parâmetro "Nome" foi fornecido o valor "Dns" para o cmdlet ""Get-serviço.

O resultado de cada comando também aciona um CommandInvocation, normalmente para out-predefinido.
O InputObject Out-Default é o objeto do PowerShell devolvido do comando.
Os detalhes desse objeto são indicados algumas linhas abaixo, rigorosamente mimicking que o utilizador deverá ter visto.

## <a name="see-also"></a>Consulte também

- [Ações de utilizador de auditoria numa sessão JEA](audit-and-report.md)
- [*PowerShell ♥ a equipa azul* blogue de segurança](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)