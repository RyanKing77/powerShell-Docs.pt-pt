---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea, powershell, segurança"
title: "Auditoria e de relatórios no JEA"
ms.openlocfilehash: 60bc7a4213c75735628207bb21078bf90f7b1ca3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="a99aa-103">Auditoria e de relatórios no JEA</span><span class="sxs-lookup"><span data-stu-id="a99aa-103">Auditing and Reporting on JEA</span></span>

> <span data-ttu-id="a99aa-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a99aa-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="a99aa-105">Após implementar JEA, irá querer regularmente a configuração de JEA de auditoria.</span><span class="sxs-lookup"><span data-stu-id="a99aa-105">After you've deployed JEA, you will want to regularly audit the JEA configuration.</span></span>
<span data-ttu-id="a99aa-106">Isto irá ajudar a avaliar se as pessoas corretas tem acesso ao ponto final do JEA e as respetivas funções atribuídas são ainda adequadas.</span><span class="sxs-lookup"><span data-stu-id="a99aa-106">This will help you assess if the correct people have access to the JEA endpoint and if their assigned roles are still appropriate.</span></span>

<span data-ttu-id="a99aa-107">Este tópico descreve as várias formas, pode auditar um ponto final JEA.</span><span class="sxs-lookup"><span data-stu-id="a99aa-107">This topic describes the various ways you can audit a JEA endpoint.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="a99aa-108">Localizar sessões JEA registadas num computador</span><span class="sxs-lookup"><span data-stu-id="a99aa-108">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="a99aa-109">Para verificar quais sessões JEA estão registadas num computador, utilize o [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a99aa-109">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="a99aa-110">Os direitos eficazes para o ponto final estão listados na propriedade "Permissão".</span><span class="sxs-lookup"><span data-stu-id="a99aa-110">The effective rights for the endpoint are listed in the "Permission" property.</span></span>
<span data-ttu-id="a99aa-111">Estes utilizadores tem permissão para ligar ao ponto de final JEA, mas que funções (e, por extensão, comandos) têm acesso aos é determinado pelo campo "RoleDefinitions" no [ficheiro de configuração de sessão](session-configurations.md) que foi utilizada para registar o ponto final.</span><span class="sxs-lookup"><span data-stu-id="a99aa-111">These users have the right to connect to the JEA endpoint, but which roles (and, by extension, commands) they have access to is determined by the "RoleDefinitions" field in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span>

<span data-ttu-id="a99aa-112">Pode avaliar os mapeamentos de funções num ponto final JEA registado, expandindo os dados na propriedade "RoleDefinitions".</span><span class="sxs-lookup"><span data-stu-id="a99aa-112">You can evaluate the role mappings in a registered JEA endpoint by expanding the data in the "RoleDefinitions" property.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="a99aa-113">Localizar as capacidades de função disponível na máquina</span><span class="sxs-lookup"><span data-stu-id="a99aa-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="a99aa-114">Ficheiros de capacidade de função só serão utilizados pelo JEA se são armazenados numa pasta "RoleCapabilities" dentro de um módulo do PowerShell válida.</span><span class="sxs-lookup"><span data-stu-id="a99aa-114">Role capability files will only be used by JEA if they are stored in a "RoleCapabilities" folder inside a valid PowerShell module.</span></span>
<span data-ttu-id="a99aa-115">Pode encontrar todas as capacidades de função disponíveis num computador ao pesquisar a lista de módulos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a99aa-115">You can find all role capabilities available on a computer by searching the list of available modules.</span></span>

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
> <span data-ttu-id="a99aa-116">A ordem dos resultados desta função não é necessariamente a ordem em que as capacidades de função serão selecionadas se várias capacidades de função partilham o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="a99aa-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="a99aa-117">Selecione efetivos direitos para um utilizador específico</span><span class="sxs-lookup"><span data-stu-id="a99aa-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="a99aa-118">Assim que tiver configurado um ponto final JEA, poderá pretender verificar quais os comandos estão disponíveis para um utilizador específico numa sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="a99aa-118">Once you have set up a JEA endpoint, you may want to check which commands are available to a specific user in a JEA session.</span></span>
<span data-ttu-id="a99aa-119">Pode utilizar [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) enumerar todos os comandos aplicáveis a um utilizador se estivessem iniciar uma sessão JEA com as respetivas associações a atual.</span><span class="sxs-lookup"><span data-stu-id="a99aa-119">You can use [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) to enumerate all of the commands applicable to a user if they were to start a JEA session with their current group memberships.</span></span>
<span data-ttu-id="a99aa-120">A saída do `Get-PSSessionCapability` é idêntico ao que o utilizador especificado em execução `Get-Command -CommandType All` numa sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="a99aa-120">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="a99aa-121">Se os utilizadores não são membros permanentes do grupos que podem conceder direitos JEA adicionais, este cmdlet pode não refletir essas permissões adicionais.</span><span class="sxs-lookup"><span data-stu-id="a99aa-121">If your users are not permanent members of groups which would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span>
<span data-ttu-id="a99aa-122">Isto é normalmente o caso quando utilizar sistemas de gestão de acesso privilegiado just-in-time para permitir que os utilizadores temporariamente pertence a um grupo de segurança.</span><span class="sxs-lookup"><span data-stu-id="a99aa-122">This is typically the case when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span>
<span data-ttu-id="a99aa-123">Avaliar sempre cuidadosamente o mapeamento de utilizadores a funções e o conteúdo de cada função para garantir que os utilizadores só é obter acesso para o mínimo de comandos necessários para as respetivas tarefas com êxito.</span><span class="sxs-lookup"><span data-stu-id="a99aa-123">Always carefully evaluate the mapping of users to roles and the contents of each role to ensure users are only getting access to the least amount of commands needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="a99aa-124">Registos de eventos do PowerShell</span><span class="sxs-lookup"><span data-stu-id="a99aa-124">PowerShell event logs</span></span>

<span data-ttu-id="a99aa-125">Se tiver ativado o bloco de módulo e/ou de script de início de sessão no sistema, poderá encontrar eventos nos registos de eventos do Windows para cada comando que foi executado um utilizador nas respetivas sessões JEA.</span><span class="sxs-lookup"><span data-stu-id="a99aa-125">If you enabled module and/or script block logging on the system, you will be able to find events in the Windows event logs for each command a user ran in their JEA sessions.</span></span>
<span data-ttu-id="a99aa-126">Para obter estes eventos, abra o Visualizador de eventos do Windows, navegue para o **Microsoft-Windows-PowerShell/Operational** registo de eventos e procure eventos com o ID de evento **4104**.</span><span class="sxs-lookup"><span data-stu-id="a99aa-126">To find these events, open the Windows Event Viewer, navigate to the **Microsoft-Windows-PowerShell/Operational** event log, and look for events with event ID **4104**.</span></span>

<span data-ttu-id="a99aa-127">Cada entrada de registo de eventos irá incluir informações sobre a sessão no qual o comando foi executado.</span><span class="sxs-lookup"><span data-stu-id="a99aa-127">Each event log entry will include information about the session in which the command was run.</span></span>
<span data-ttu-id="a99aa-128">Para sessões JEA, isto inclui informações importantes sobre o **ConnectedUser**, que é o utilizador real que criou a sessão JEA, bem como o **RunAsUser** que identifica a conta JEA utilizada para Execute o comando.</span><span class="sxs-lookup"><span data-stu-id="a99aa-128">For JEA sessions, this includes important information about the **ConnectedUser**, which is the actual user who created the JEA session, as well as the **RunAsUser** which identifies the account JEA used to execute the command.</span></span>
<span data-ttu-id="a99aa-129">Os registos de eventos de aplicações irá mostrar as alterações que está a ser efetuadas pelo RunAsUser, por isso, ter transcrições ou o registo de módulo/script ativado é fundamental para conseguir uma invocação de comando específico para um utilizador de rastreio.</span><span class="sxs-lookup"><span data-stu-id="a99aa-129">Application event logs will show changes being made by the RunAsUser, so having transcripts or module/script logging enabled is crucial to be able to trace a specific command invocation back to a user.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="a99aa-130">Registos de eventos de aplicações</span><span class="sxs-lookup"><span data-stu-id="a99aa-130">Application event logs</span></span>

<span data-ttu-id="a99aa-131">Quando executar um comando numa sessão JEA que interage com uma aplicação externa ou um serviço, as aplicações podem registar eventos para os seus próprios registos de eventos.</span><span class="sxs-lookup"><span data-stu-id="a99aa-131">When you run a command in a JEA session that interacts with an external application or service, those applications may log events to their own event logs.</span></span>
<span data-ttu-id="a99aa-132">Ao contrário dos registos do PowerShell e transcrições, outros mecanismos de registo não capturará o utilizador da sessão JEA ligado e, em vez disso, apenas registará o utilizador executar como virtual ou a conta de serviço geridas de grupo.</span><span class="sxs-lookup"><span data-stu-id="a99aa-132">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the connected user of the JEA session, and will instead only log the virtual run-as user or group managed service account.</span></span>
<span data-ttu-id="a99aa-133">Para determinar que executou o comando, é necessário consultar um [transcript sessão](#session-transcripts) ou correlacionar os registos de eventos do PowerShell com a hora e o utilizador apresentado no registo de eventos de aplicações.</span><span class="sxs-lookup"><span data-stu-id="a99aa-133">In order to determine who ran the command, you will need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="a99aa-134">O WinRM registo também pode ajudar a correlacionar run utilizadores um registo de eventos de aplicações com o utilizador ao ligar.</span><span class="sxs-lookup"><span data-stu-id="a99aa-134">The WinRM log can also help you correlate run as users in an application event log with the connecting user.</span></span>
<span data-ttu-id="a99aa-135">ID de evento **193** no **Microsoft-Windows-Windows remoto gestão/Operational** registos a conta do identificador de segurança (SID) e o nome do utilizador ao ligar e executar como utilizador sempre que um JEA a sessão é criada.</span><span class="sxs-lookup"><span data-stu-id="a99aa-135">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user every time a JEA session is created.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="a99aa-136">Transcrições de sessão</span><span class="sxs-lookup"><span data-stu-id="a99aa-136">Session transcripts</span></span>

<span data-ttu-id="a99aa-137">Se tiver configurado o JEA para criar um transcript para cada sessão de utilizador, uma cópia de texto de ações de cada utilizador será armazenada na pasta especificada.</span><span class="sxs-lookup"><span data-stu-id="a99aa-137">If you configured JEA to create a transcript for each user session, a text copy of every user's actions will be stored in the specified folder.</span></span>

<span data-ttu-id="a99aa-138">Para localizar todos os diretórios de transcript, execute o seguinte comando como administrador no computador configurado com JEA:</span><span class="sxs-lookup"><span data-stu-id="a99aa-138">To find all transcript directories, run the following command as an administrator on the computer configured with JEA:</span></span>

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="a99aa-139">Cada transcript começa com informações sobre a hora de início de sessão, que utilizador ligado para a sessão e que identidade JEA foi atribuída.</span><span class="sxs-lookup"><span data-stu-id="a99aa-139">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="a99aa-140">No corpo do transcript, as informações são registadas sobre cada comando invocado o utilizador.</span><span class="sxs-lookup"><span data-stu-id="a99aa-140">In the body of the transcript, information is logged about each command the user invoked.</span></span>
<span data-ttu-id="a99aa-141">A sintaxe exata do comando que foi executado o utilizador não está disponível em sessões JEA devido a forma como os comandos são transformados para comunicação remota do PowerShell, no entanto, ainda pode determinar o comando Efetivo que foi executado.</span><span class="sxs-lookup"><span data-stu-id="a99aa-141">The exact syntax of the command the user ran is unavailable in JEA sessions due to the way commands are transformed for PowerShell remoting, however you can still determine the effective command that was executed.</span></span>
<span data-ttu-id="a99aa-142">Segue-se um fragmento de transcript de exemplo de um utilizador que executa `Get-Service Dns` numa sessão JEA:</span><span class="sxs-lookup"><span data-stu-id="a99aa-142">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="a99aa-143">Para cada comando que executa um utilizador, uma linha de "CommandInvocation" será escrita, que descreve o cmdlet ou função de utilizador invocado.</span><span class="sxs-lookup"><span data-stu-id="a99aa-143">For each command a user runs, a "CommandInvocation" line will be written, describing the cmdlet or function the user invoked.</span></span>
<span data-ttu-id="a99aa-144">ParameterBindings siga cada CommandInvocation para lhe indicar sobre cada parâmetro e valor que foi fornecido com o comando.</span><span class="sxs-lookup"><span data-stu-id="a99aa-144">ParameterBindings follow each CommandInvocation to tell you about each parameter and value that was supplied with the command.</span></span>
<span data-ttu-id="a99aa-145">No exemplo acima, pode ver que o parâmetro "Nome" foi fornecido o valor "Dns" para o cmdlet ""Get-serviço.</span><span class="sxs-lookup"><span data-stu-id="a99aa-145">In the above example, you can see that the parameter "Name" was supplied the value "Dns" for the "Get-Service" cmdlet.</span></span>

<span data-ttu-id="a99aa-146">O resultado de cada comando também aciona um CommandInvocation, normalmente para out-predefinido.</span><span class="sxs-lookup"><span data-stu-id="a99aa-146">The output of each command will also trigger a CommandInvocation, usually to Out-Default.</span></span> <span data-ttu-id="a99aa-147">O InputObject Out-Default é o objeto do PowerShell devolvido do comando.</span><span class="sxs-lookup"><span data-stu-id="a99aa-147">The InputObject of Out-Default is the PowerShell object returned from the command.</span></span>
<span data-ttu-id="a99aa-148">Os detalhes desse objeto são indicados algumas linhas abaixo, rigorosamente mimicking que o utilizador deverá ter visto.</span><span class="sxs-lookup"><span data-stu-id="a99aa-148">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="a99aa-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a99aa-149">See also</span></span>

- [<span data-ttu-id="a99aa-150">Ações de utilizador de auditoria numa sessão JEA</span><span class="sxs-lookup"><span data-stu-id="a99aa-150">Audit user actions in a JEA session</span></span>](audit-and-report.md)
- [<span data-ttu-id="a99aa-151">*PowerShell ♥ a equipa azul* blogue de segurança</span><span class="sxs-lookup"><span data-stu-id="a99aa-151">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

