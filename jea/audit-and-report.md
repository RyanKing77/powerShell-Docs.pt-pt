---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Auditoria e relatórios na JEA
ms.openlocfilehash: 2388c735840d8d3683aa8bc9869b9fb0371e5902
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851225"
---
# <a name="auditing-and-reporting-on-jea"></a>Auditoria e relatórios na JEA

> Aplica-se a: Windows PowerShell 5.0

Depois de implementar JEA, convém regularmente fazer auditoria da configuração de JEA.
Isto ajudará a avaliar se as pessoas certas tenham acesso ao ponto final JEA e suas funções são ainda adequadas.

Este tópico descreve as várias formas que pode fazer uma auditoria um ponto final JEA.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Encontre sessões JEA registrados numa máquina

Para verificar quais sessões JEA são registrados num computador, utilize o [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

Os direitos em vigor para o ponto final estão listados na propriedade "Permissão".
Estes utilizadores têm o direito de ligar para o ponto final JEA mas quais funções (e, por extensão, comandos) aos quais têm acesso é determinado pelo campo "RoleDefinitions" no [o ficheiro de configuração de sessão](session-configurations.md) que foi utilizada para registar o ponto final.

Pode avaliar os mapeamentos de função num ponto final da JEA registado ao expandir os dados na propriedade "RoleDefinitions".

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Localizar funcionalidades de função disponíveis na máquina

Arquivos de recurso de função só serão utilizados pelo JEA se eles são armazenados numa pasta "RoleCapabilities" dentro de um módulo do PowerShell válida.
Pode encontrar todas as funcionalidades de função disponíveis num computador ao pesquisar a lista de módulos disponíveis.

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
> A ordem de resultados desta função não é necessariamente a ordem na qual os recursos de função seja selecionados se várias funcionalidades de função partilham o mesmo nome.

## <a name="check-effective-rights-for-a-specific-user"></a>Verificação de direitos em vigor a partir de um utilizador específico

Assim que tiver configurado um ponto final JEA, convém verificar quais comandos estão disponíveis para um utilizador específico numa sessão JEA.
Pode usar [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) para enumerar todos os comandos aplicáveis a um utilizador se estivessem iniciar uma sessão JEA com suas associações de grupo atual.
A saída de `Get-PSSessionCapability` é idêntico ao que o utilizador especificado em execução `Get-Command -CommandType All` numa sessão JEA.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Se os utilizadores não são membros permanentes de grupos que concedem os direitos JEA adicionais, este cmdlet pode não refletir essas permissões adicionais.
Isso é normalmente o caso quando utilizar sistemas de gestão de acesso privilegiado just-in-time para permitir que os utilizadores temporariamente pertencem a um grupo de segurança.
Avalie sempre cuidadosamente o mapeamento de utilizadores às funções e o conteúdo de cada função para garantir que os utilizadores é apenas obtendo acesso para a quantidade de comandos necessários para realizar seus trabalhos com êxito.

## <a name="powershell-event-logs"></a>Registos de eventos do PowerShell

Se ativou o módulo de e/ou script bloco de registo do sistema, será capaz de encontrar eventos nos logs de eventos Windows para cada comando que foi executado um usuário em suas sessões JEA.
Para localizar estes eventos, abra o Visualizador de eventos do Windows, navegue para o **Microsoft-Windows-PowerShell/Operational** registo de eventos e procure eventos com o ID de evento **4104**.

Cada entrada de registo de eventos irá incluir informações sobre a sessão em que o comando foi executado.
Para sessões JEA, isso inclui informações importantes sobre o **ConnectedUser**, que é o utilizador real que criou a sessão JEA, bem como os **RunAsUser** que identifica a conta JEA utilizada para Execute o comando.
Registos de eventos da aplicação mostrará as alterações feitas por RunAsUser, então, ter transcrições ou registo de módulo/script ativado é crucial para poder rastrear uma invocação de comando específico para um utilizador.

## <a name="application-event-logs"></a>Registos de eventos do aplicativo

Quando executa um comando numa sessão JEA que interage com um serviço ou aplicação externa, esses aplicativos podem registar eventos em seus próprios registos de eventos.
Ao contrário dos registos do PowerShell e transcrições, outros mecanismos de Registro em log não capturará o usuário conectado da sessão JEA e, em vez disso, serão apenas iniciar o utilizador de início de executar como virtual ou a conta de serviço geridas de grupo.
Para determinar que executou o comando, terá de consultar um [transcrição de sessão](#session-transcripts) ou correlacionar os registos de eventos do PowerShell com o tempo e o utilizador mostrado no log de eventos do aplicativo.

O WinRM registo pode também ajudar a correlacionar são executados como usuários num log de eventos do aplicativo com o usuário conectado.
ID de evento **193** no **Microsoft-Windows-Windows remoto gestão/Operational** registos o identificador de segurança (SID) e a conta dê um nome para o utilizador ao ligar e executem como utilizador sempre que um JEA a sessão é criada.

## <a name="session-transcripts"></a>Transcrições de sessão

Se tiver configurado a JEA para criar uma transcrição para cada sessão de utilizador, uma cópia de texto de ações de todos os usuários será armazenada na pasta especificada.

Para localizar todos os diretórios de transcrição, execute o seguinte comando como administrador no computador configurado com JEA:

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
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

No corpo da transcrição, as informações são registradas sobre cada comando invocado do utilizador.
A sintaxe exata do comando executado o utilizador não está disponível em sessões JEA a forma como os comandos são transformados para comunicação remota do PowerShell, no entanto, ainda poderá determinar que o comando eficaz que foi executado.
Segue-se um fragmento de transcrição de exemplo de um utilizador que executa `Get-Service Dns` numa sessão JEA:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Para cada comando que é executado de um utilizador, uma linha de "CommandInvocation" será escrita, descrevendo o cmdlet ou função de utilizador invocado.
ParameterBindings siga cada CommandInvocation para falar sobre cada parâmetro e o valor fornecido com o comando.
No exemplo acima, pode ver que o parâmetro "Nome" foi fornecido o valor "Dns" para o cmdlet "Get-Service".

A saída de cada comando também irá acionar um CommandInvocation, geralmente como out-predefinido.
O InputObject Out-Default é o objeto de PowerShell devolvido do comando.
Os detalhes desse objeto são impressos algumas linhas abaixo, imitando de perto o que o usuário teria visto.

## <a name="see-also"></a>Consulte também

- [*PowerShell ♥ a equipa de azul* mensagem de blogue sobre segurança](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)
