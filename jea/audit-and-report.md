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
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="1d258-103">Auditoria e relatórios na JEA</span><span class="sxs-lookup"><span data-stu-id="1d258-103">Auditing and Reporting on JEA</span></span>

<span data-ttu-id="1d258-104">Depois de implementar JEA, terá de regularmente fazer auditoria da configuração de JEA.</span><span class="sxs-lookup"><span data-stu-id="1d258-104">After you've deployed JEA, you need to regularly audit the JEA configuration.</span></span> <span data-ttu-id="1d258-105">Auditoria ajuda a avaliar o que as pessoas certas tenham acesso ao ponto final JEA e suas funções são ainda adequadas.</span><span class="sxs-lookup"><span data-stu-id="1d258-105">Auditing helps you assess that the correct people have access to the JEA endpoint and their assigned roles are still appropriate.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="1d258-106">Encontre sessões JEA registrados numa máquina</span><span class="sxs-lookup"><span data-stu-id="1d258-106">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="1d258-107">Para verificar quais sessões JEA são registrados num computador, utilize o [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1d258-107">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

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

<span data-ttu-id="1d258-108">Os direitos em vigor para o ponto final estão listados na **permissão** propriedade.</span><span class="sxs-lookup"><span data-stu-id="1d258-108">The effective rights for the endpoint are listed in the **Permission** property.</span></span> <span data-ttu-id="1d258-109">Estes utilizadores têm o direito de ligar para o ponto final da JEA.</span><span class="sxs-lookup"><span data-stu-id="1d258-109">These users have the right to connect to the JEA endpoint.</span></span> <span data-ttu-id="1d258-110">No entanto, as funções e comandos aos quais têm acesso é determinado pelos **RoleDefinitions** propriedade na [o ficheiro de configuração de sessão](session-configurations.md) que foi utilizada para registar o ponto final.</span><span class="sxs-lookup"><span data-stu-id="1d258-110">However, the roles and commands they have access to is determined by the **RoleDefinitions** property in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span> <span data-ttu-id="1d258-111">Expanda a **RoleDefinitions** propriedade para avaliar os mapeamentos de função num ponto final da JEA registado.</span><span class="sxs-lookup"><span data-stu-id="1d258-111">Expand the **RoleDefinitions** property to evaluate the role mappings in a registered JEA endpoint.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="1d258-112">Localizar funcionalidades de função disponíveis na máquina</span><span class="sxs-lookup"><span data-stu-id="1d258-112">Find available role capabilities on the machine</span></span>

<span data-ttu-id="1d258-113">JEA obtém capacidades de função a partir do `.psrc` ficheiros armazenados no **RoleCapabilities** pasta dentro de um módulo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d258-113">JEA gets role capabilities from the `.psrc` files stored in the **RoleCapabilities** folder inside a PowerShell module.</span></span> <span data-ttu-id="1d258-114">A função seguinte localiza todas as funcionalidades de função disponíveis num computador.</span><span class="sxs-lookup"><span data-stu-id="1d258-114">The following function finds all role capabilities available on a computer.</span></span>

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
> <span data-ttu-id="1d258-115">A ordem de resultados desta função não é necessariamente a ordem na qual os recursos de função seja selecionados se várias funcionalidades de função partilham o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="1d258-115">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="1d258-116">Verificação de direitos em vigor a partir de um utilizador específico</span><span class="sxs-lookup"><span data-stu-id="1d258-116">Check effective rights for a specific user</span></span>

<span data-ttu-id="1d258-117">O [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumera todos os comandos disponíveis num ponto final JEA com base em associações de grupo de um utilizador.</span><span class="sxs-lookup"><span data-stu-id="1d258-117">The [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumerates all the commands available on a JEA endpoint based on a user's group memberships.</span></span>
<span data-ttu-id="1d258-118">A saída de `Get-PSSessionCapability` é idêntico ao que o utilizador especificado em execução `Get-Command -CommandType All` numa sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="1d258-118">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="1d258-119">Se os utilizadores não são membros permanentes dos grupos que concedem os direitos JEA adicionais, este cmdlet pode não refletir essas permissões adicionais.</span><span class="sxs-lookup"><span data-stu-id="1d258-119">If your users aren't permanent members of groups that would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span> <span data-ttu-id="1d258-120">Isto acontece quando utilizar sistemas de gestão para permitir que os utilizadores temporariamente pertencem a um grupo de segurança de acesso privilegiado just-in-time.</span><span class="sxs-lookup"><span data-stu-id="1d258-120">This happens when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span> <span data-ttu-id="1d258-121">Avalie cuidadosamente o mapeamento de utilizadores a funções e funcionalidades para garantir que os utilizadores obtenham apenas o nível de acesso necessário para realizar seus trabalhos com êxito.</span><span class="sxs-lookup"><span data-stu-id="1d258-121">Carefully evaluate the mapping of users to roles and capabilities to ensure that users only get the level of access needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="1d258-122">Registos de eventos do PowerShell</span><span class="sxs-lookup"><span data-stu-id="1d258-122">PowerShell event logs</span></span>

<span data-ttu-id="1d258-123">Se ativou o registo do sistema de bloco de módulo ou script, pode ver eventos nos logs de eventos do Windows para cada comando que é executado um usuário numa sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="1d258-123">If you enabled module or script block logging on the system, you can see events in the Windows event logs for each command a user runs in a JEA session.</span></span> <span data-ttu-id="1d258-124">Para localizar esses eventos, abra **Microsoft-Windows-PowerShell/Operational** registo de eventos e procure eventos com o ID de evento **4104**.</span><span class="sxs-lookup"><span data-stu-id="1d258-124">To find these events, open **Microsoft-Windows-PowerShell/Operational** event log and look for events with event ID **4104**.</span></span>

<span data-ttu-id="1d258-125">Cada entrada de registo de eventos inclui informações sobre a sessão em que o comando foi executado.</span><span class="sxs-lookup"><span data-stu-id="1d258-125">Each event log entry includes information about the session in which the command was run.</span></span> <span data-ttu-id="1d258-126">Para sessões JEA, o evento inclui informações sobre o **ConnectedUser** e o **RunAsUser**.</span><span class="sxs-lookup"><span data-stu-id="1d258-126">For JEA sessions, the event includes information about the **ConnectedUser** and the **RunAsUser**.</span></span> <span data-ttu-id="1d258-127">O **ConnectedUser** é o utilizador real que criou a sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="1d258-127">The **ConnectedUser** is the actual user who created the JEA session.</span></span> <span data-ttu-id="1d258-128">O **RunAsUser** é a conta JEA utilizada para executar o comando.</span><span class="sxs-lookup"><span data-stu-id="1d258-128">The **RunAsUser** is the account JEA used to execute the command.</span></span>

<span data-ttu-id="1d258-129">Registos de eventos do aplicativo mostrar as alterações feitas pela **RunAsUser**.</span><span class="sxs-lookup"><span data-stu-id="1d258-129">Application event logs show changes being made by the **RunAsUser**.</span></span> <span data-ttu-id="1d258-130">Para ter o módulo e o registo de script ativada é necessária para o rastreio de uma invocação de comando específico de volta para o **ConnectedUser**.</span><span class="sxs-lookup"><span data-stu-id="1d258-130">So having module and script logging enabled is required to trace a specific command invocation back to the **ConnectedUser**.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="1d258-131">Registos de eventos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="1d258-131">Application event logs</span></span>

<span data-ttu-id="1d258-132">Comandos executados numa sessão JEA que interagem com aplicações externas ou serviços podem registar eventos em seus próprios registos de eventos.</span><span class="sxs-lookup"><span data-stu-id="1d258-132">Commands run in a JEA session that interact with external applications or services may log events to their own event logs.</span></span> <span data-ttu-id="1d258-133">Ao contrário dos registos do PowerShell e transcrições, outros mecanismos de Registro em log não capturam do usuário conectado da sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="1d258-133">Unlike PowerShell logs and transcripts, other logging mechanisms don't capture the connected user of the JEA session.</span></span> <span data-ttu-id="1d258-134">Em vez disso, esses aplicativos apenas iniciar o utilizador Run virtual.</span><span class="sxs-lookup"><span data-stu-id="1d258-134">Instead, those applications only log the virtual run-as user.</span></span>
<span data-ttu-id="1d258-135">Para determinar que executou o comando, precisar de consultar um [transcrição de sessão](#session-transcripts) ou correlacionar os registos de eventos do PowerShell com o tempo e o utilizador mostrado no log de eventos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1d258-135">To determine who ran the command, you need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="1d258-136">O registo de WinRM também pode ajudar correlacionar os utilizadores executar como para o usuário conectado num log de eventos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1d258-136">The WinRM log can also help you correlate run-as users to the connecting user in an application event log.</span></span> <span data-ttu-id="1d258-137">ID de evento **193** no **Microsoft-Windows-Windows remoto gestão/Operational** os registros do log o identificador de segurança (SID) e o nome de conta para a ligação de utilizadores e de execução como usuário para cada novo JEA sessão.</span><span class="sxs-lookup"><span data-stu-id="1d258-137">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user for every new JEA session.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="1d258-138">Transcrições de sessão</span><span class="sxs-lookup"><span data-stu-id="1d258-138">Session transcripts</span></span>

<span data-ttu-id="1d258-139">Se tiver configurado a JEA para criar uma transcrição para cada sessão de utilizador, uma cópia de texto de ações de cada usuário são armazenadas na pasta especificada.</span><span class="sxs-lookup"><span data-stu-id="1d258-139">If you configured JEA to create a transcript for each user session, a text copy of every user's actions are stored in the specified folder.</span></span>

<span data-ttu-id="1d258-140">O seguinte comando (como administrador) localiza todos os diretórios de transcrição.</span><span class="sxs-lookup"><span data-stu-id="1d258-140">The following command (as an administrator) finds all transcript directories.</span></span>

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="1d258-141">Cada transcrição começa com informações sobre a sessão iniciada, o tempo que utilizador ligado para a sessão e que identidade JEA foi atribuída a eles.</span><span class="sxs-lookup"><span data-stu-id="1d258-141">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="1d258-142">O corpo da transcrição contém informações sobre cada comando invocado do utilizador.</span><span class="sxs-lookup"><span data-stu-id="1d258-142">The body of the transcript contains information about each command the user invoked.</span></span> <span data-ttu-id="1d258-143">A sintaxe exata do comando utilizado não está disponível em sessões JEA por conta da forma comandos são transformados para comunicação remota do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d258-143">The exact syntax of the command used is unavailable in JEA sessions because of the way commands are transformed for PowerShell remoting.</span></span> <span data-ttu-id="1d258-144">No entanto, ainda é possível determinar o comando eficaz que foi executado.</span><span class="sxs-lookup"><span data-stu-id="1d258-144">However, you can still determine the effective command that was executed.</span></span> <span data-ttu-id="1d258-145">Segue-se um fragmento de transcrição de exemplo de um utilizador que executa `Get-Service Dns` numa sessão JEA:</span><span class="sxs-lookup"><span data-stu-id="1d258-145">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="1d258-146">R **CommandInvocation** linha foi escrita para cada comando é executado de um utilizador.</span><span class="sxs-lookup"><span data-stu-id="1d258-146">A **CommandInvocation** line is written for each command a user runs.</span></span> <span data-ttu-id="1d258-147">**ParameterBindings** gravar cada parâmetro e o valor fornecido com o comando.</span><span class="sxs-lookup"><span data-stu-id="1d258-147">**ParameterBindings** record each parameter and value supplied with the command.</span></span> <span data-ttu-id="1d258-148">No exemplo anterior, pode ver que o parâmetro **Name** foi fornecida a com o valor **Dns** para o `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1d258-148">In the previous example, you can see that the parameter **Name** was supplied the with value **Dns** for the `Get-Service` cmdlet.</span></span>

<span data-ttu-id="1d258-149">A saída de cada comando também aciona uma **CommandInvocation**normalmente ao `Out-Default`.</span><span class="sxs-lookup"><span data-stu-id="1d258-149">The output of each command also triggers a **CommandInvocation**, usually to `Out-Default`.</span></span> <span data-ttu-id="1d258-150">O **InputObject** de `Out-Default` é o objeto do PowerShell devolvido do comando.</span><span class="sxs-lookup"><span data-stu-id="1d258-150">The **InputObject** of `Out-Default` is the PowerShell object returned from the command.</span></span> <span data-ttu-id="1d258-151">Os detalhes desse objeto são impressos algumas linhas abaixo, imitando de perto o que o usuário teria visto.</span><span class="sxs-lookup"><span data-stu-id="1d258-151">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d258-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d258-152">See also</span></span>

[<span data-ttu-id="1d258-153">*PowerShell ♥ a equipa de azul* mensagem de blogue sobre segurança</span><span class="sxs-lookup"><span data-stu-id="1d258-153">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
