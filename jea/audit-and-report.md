---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Auditoria e relatórios na JEA
ms.openlocfilehash: 2388c735840d8d3683aa8bc9869b9fb0371e5902
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084084"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="9a958-103">Auditoria e relatórios na JEA</span><span class="sxs-lookup"><span data-stu-id="9a958-103">Auditing and Reporting on JEA</span></span>

> <span data-ttu-id="9a958-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9a958-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="9a958-105">Depois de implementar JEA, convém regularmente fazer auditoria da configuração de JEA.</span><span class="sxs-lookup"><span data-stu-id="9a958-105">After you've deployed JEA, you will want to regularly audit the JEA configuration.</span></span>
<span data-ttu-id="9a958-106">Isto ajudará a avaliar se as pessoas certas tenham acesso ao ponto final JEA e suas funções são ainda adequadas.</span><span class="sxs-lookup"><span data-stu-id="9a958-106">This will help you assess if the correct people have access to the JEA endpoint and if their assigned roles are still appropriate.</span></span>

<span data-ttu-id="9a958-107">Este tópico descreve as várias formas que pode fazer uma auditoria um ponto final JEA.</span><span class="sxs-lookup"><span data-stu-id="9a958-107">This topic describes the various ways you can audit a JEA endpoint.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="9a958-108">Encontre sessões JEA registrados numa máquina</span><span class="sxs-lookup"><span data-stu-id="9a958-108">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="9a958-109">Para verificar quais sessões JEA são registrados num computador, utilize o [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9a958-109">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="9a958-110">Os direitos em vigor para o ponto final estão listados na propriedade "Permissão".</span><span class="sxs-lookup"><span data-stu-id="9a958-110">The effective rights for the endpoint are listed in the "Permission" property.</span></span>
<span data-ttu-id="9a958-111">Estes utilizadores têm o direito de ligar para o ponto final JEA mas quais funções (e, por extensão, comandos) aos quais têm acesso é determinado pelo campo "RoleDefinitions" no [o ficheiro de configuração de sessão](session-configurations.md) que foi utilizada para registar o ponto final.</span><span class="sxs-lookup"><span data-stu-id="9a958-111">These users have the right to connect to the JEA endpoint, but which roles (and, by extension, commands) they have access to is determined by the "RoleDefinitions" field in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span>

<span data-ttu-id="9a958-112">Pode avaliar os mapeamentos de função num ponto final da JEA registado ao expandir os dados na propriedade "RoleDefinitions".</span><span class="sxs-lookup"><span data-stu-id="9a958-112">You can evaluate the role mappings in a registered JEA endpoint by expanding the data in the "RoleDefinitions" property.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="9a958-113">Localizar funcionalidades de função disponíveis na máquina</span><span class="sxs-lookup"><span data-stu-id="9a958-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="9a958-114">Arquivos de recurso de função só serão utilizados pelo JEA se eles são armazenados numa pasta "RoleCapabilities" dentro de um módulo do PowerShell válida.</span><span class="sxs-lookup"><span data-stu-id="9a958-114">Role capability files will only be used by JEA if they are stored in a "RoleCapabilities" folder inside a valid PowerShell module.</span></span>
<span data-ttu-id="9a958-115">Pode encontrar todas as funcionalidades de função disponíveis num computador ao pesquisar a lista de módulos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9a958-115">You can find all role capabilities available on a computer by searching the list of available modules.</span></span>

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
> <span data-ttu-id="9a958-116">A ordem de resultados desta função não é necessariamente a ordem na qual os recursos de função seja selecionados se várias funcionalidades de função partilham o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="9a958-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="9a958-117">Verificação de direitos em vigor a partir de um utilizador específico</span><span class="sxs-lookup"><span data-stu-id="9a958-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="9a958-118">Assim que tiver configurado um ponto final JEA, convém verificar quais comandos estão disponíveis para um utilizador específico numa sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="9a958-118">Once you have set up a JEA endpoint, you may want to check which commands are available to a specific user in a JEA session.</span></span>
<span data-ttu-id="9a958-119">Pode usar [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) para enumerar todos os comandos aplicáveis a um utilizador se estivessem iniciar uma sessão JEA com suas associações de grupo atual.</span><span class="sxs-lookup"><span data-stu-id="9a958-119">You can use [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) to enumerate all of the commands applicable to a user if they were to start a JEA session with their current group memberships.</span></span>
<span data-ttu-id="9a958-120">A saída de `Get-PSSessionCapability` é idêntico ao que o utilizador especificado em execução `Get-Command -CommandType All` numa sessão JEA.</span><span class="sxs-lookup"><span data-stu-id="9a958-120">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="9a958-121">Se os utilizadores não são membros permanentes de grupos que concedem os direitos JEA adicionais, este cmdlet pode não refletir essas permissões adicionais.</span><span class="sxs-lookup"><span data-stu-id="9a958-121">If your users are not permanent members of groups which would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span>
<span data-ttu-id="9a958-122">Isso é normalmente o caso quando utilizar sistemas de gestão de acesso privilegiado just-in-time para permitir que os utilizadores temporariamente pertencem a um grupo de segurança.</span><span class="sxs-lookup"><span data-stu-id="9a958-122">This is typically the case when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span>
<span data-ttu-id="9a958-123">Avalie sempre cuidadosamente o mapeamento de utilizadores às funções e o conteúdo de cada função para garantir que os utilizadores é apenas obtendo acesso para a quantidade de comandos necessários para realizar seus trabalhos com êxito.</span><span class="sxs-lookup"><span data-stu-id="9a958-123">Always carefully evaluate the mapping of users to roles and the contents of each role to ensure users are only getting access to the least amount of commands needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="9a958-124">Registos de eventos do PowerShell</span><span class="sxs-lookup"><span data-stu-id="9a958-124">PowerShell event logs</span></span>

<span data-ttu-id="9a958-125">Se ativou o módulo de e/ou script bloco de registo do sistema, será capaz de encontrar eventos nos logs de eventos Windows para cada comando que foi executado um usuário em suas sessões JEA.</span><span class="sxs-lookup"><span data-stu-id="9a958-125">If you enabled module and/or script block logging on the system, you will be able to find events in the Windows event logs for each command a user ran in their JEA sessions.</span></span>
<span data-ttu-id="9a958-126">Para localizar estes eventos, abra o Visualizador de eventos do Windows, navegue para o **Microsoft-Windows-PowerShell/Operational** registo de eventos e procure eventos com o ID de evento **4104**.</span><span class="sxs-lookup"><span data-stu-id="9a958-126">To find these events, open the Windows Event Viewer, navigate to the **Microsoft-Windows-PowerShell/Operational** event log, and look for events with event ID **4104**.</span></span>

<span data-ttu-id="9a958-127">Cada entrada de registo de eventos irá incluir informações sobre a sessão em que o comando foi executado.</span><span class="sxs-lookup"><span data-stu-id="9a958-127">Each event log entry will include information about the session in which the command was run.</span></span>
<span data-ttu-id="9a958-128">Para sessões JEA, isso inclui informações importantes sobre o **ConnectedUser**, que é o utilizador real que criou a sessão JEA, bem como os **RunAsUser** que identifica a conta JEA utilizada para Execute o comando.</span><span class="sxs-lookup"><span data-stu-id="9a958-128">For JEA sessions, this includes important information about the **ConnectedUser**, which is the actual user who created the JEA session, as well as the **RunAsUser** which identifies the account JEA used to execute the command.</span></span>
<span data-ttu-id="9a958-129">Registos de eventos da aplicação mostrará as alterações feitas por RunAsUser, então, ter transcrições ou registo de módulo/script ativado é crucial para poder rastrear uma invocação de comando específico para um utilizador.</span><span class="sxs-lookup"><span data-stu-id="9a958-129">Application event logs will show changes being made by the RunAsUser, so having transcripts or module/script logging enabled is crucial to be able to trace a specific command invocation back to a user.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="9a958-130">Registos de eventos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="9a958-130">Application event logs</span></span>

<span data-ttu-id="9a958-131">Quando executa um comando numa sessão JEA que interage com um serviço ou aplicação externa, esses aplicativos podem registar eventos em seus próprios registos de eventos.</span><span class="sxs-lookup"><span data-stu-id="9a958-131">When you run a command in a JEA session that interacts with an external application or service, those applications may log events to their own event logs.</span></span>
<span data-ttu-id="9a958-132">Ao contrário dos registos do PowerShell e transcrições, outros mecanismos de Registro em log não capturará o usuário conectado da sessão JEA e, em vez disso, serão apenas iniciar o utilizador de início de executar como virtual ou a conta de serviço geridas de grupo.</span><span class="sxs-lookup"><span data-stu-id="9a958-132">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the connected user of the JEA session, and will instead only log the virtual run-as user or group managed service account.</span></span>
<span data-ttu-id="9a958-133">Para determinar que executou o comando, terá de consultar um [transcrição de sessão](#session-transcripts) ou correlacionar os registos de eventos do PowerShell com o tempo e o utilizador mostrado no log de eventos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9a958-133">In order to determine who ran the command, you will need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="9a958-134">O WinRM registo pode também ajudar a correlacionar são executados como usuários num log de eventos do aplicativo com o usuário conectado.</span><span class="sxs-lookup"><span data-stu-id="9a958-134">The WinRM log can also help you correlate run as users in an application event log with the connecting user.</span></span>
<span data-ttu-id="9a958-135">ID de evento **193** no **Microsoft-Windows-Windows remoto gestão/Operational** registos o identificador de segurança (SID) e a conta dê um nome para o utilizador ao ligar e executem como utilizador sempre que um JEA a sessão é criada.</span><span class="sxs-lookup"><span data-stu-id="9a958-135">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user every time a JEA session is created.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="9a958-136">Transcrições de sessão</span><span class="sxs-lookup"><span data-stu-id="9a958-136">Session transcripts</span></span>

<span data-ttu-id="9a958-137">Se tiver configurado a JEA para criar uma transcrição para cada sessão de utilizador, uma cópia de texto de ações de todos os usuários será armazenada na pasta especificada.</span><span class="sxs-lookup"><span data-stu-id="9a958-137">If you configured JEA to create a transcript for each user session, a text copy of every user's actions will be stored in the specified folder.</span></span>

<span data-ttu-id="9a958-138">Para localizar todos os diretórios de transcrição, execute o seguinte comando como administrador no computador configurado com JEA:</span><span class="sxs-lookup"><span data-stu-id="9a958-138">To find all transcript directories, run the following command as an administrator on the computer configured with JEA:</span></span>

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="9a958-139">Cada transcrição começa com informações sobre a sessão iniciada, o tempo que utilizador ligado para a sessão e que identidade JEA foi atribuída a eles.</span><span class="sxs-lookup"><span data-stu-id="9a958-139">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="9a958-140">No corpo da transcrição, as informações são registradas sobre cada comando invocado do utilizador.</span><span class="sxs-lookup"><span data-stu-id="9a958-140">In the body of the transcript, information is logged about each command the user invoked.</span></span>
<span data-ttu-id="9a958-141">A sintaxe exata do comando executado o utilizador não está disponível em sessões JEA a forma como os comandos são transformados para comunicação remota do PowerShell, no entanto, ainda poderá determinar que o comando eficaz que foi executado.</span><span class="sxs-lookup"><span data-stu-id="9a958-141">The exact syntax of the command the user ran is unavailable in JEA sessions due to the way commands are transformed for PowerShell remoting, however you can still determine the effective command that was executed.</span></span>
<span data-ttu-id="9a958-142">Segue-se um fragmento de transcrição de exemplo de um utilizador que executa `Get-Service Dns` numa sessão JEA:</span><span class="sxs-lookup"><span data-stu-id="9a958-142">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="9a958-143">Para cada comando que é executado de um utilizador, uma linha de "CommandInvocation" será escrita, descrevendo o cmdlet ou função de utilizador invocado.</span><span class="sxs-lookup"><span data-stu-id="9a958-143">For each command a user runs, a "CommandInvocation" line will be written, describing the cmdlet or function the user invoked.</span></span>
<span data-ttu-id="9a958-144">ParameterBindings siga cada CommandInvocation para falar sobre cada parâmetro e o valor fornecido com o comando.</span><span class="sxs-lookup"><span data-stu-id="9a958-144">ParameterBindings follow each CommandInvocation to tell you about each parameter and value that was supplied with the command.</span></span>
<span data-ttu-id="9a958-145">No exemplo acima, pode ver que o parâmetro "Nome" foi fornecido o valor "Dns" para o cmdlet "Get-Service".</span><span class="sxs-lookup"><span data-stu-id="9a958-145">In the above example, you can see that the parameter "Name" was supplied the value "Dns" for the "Get-Service" cmdlet.</span></span>

<span data-ttu-id="9a958-146">A saída de cada comando também irá acionar um CommandInvocation, geralmente como out-predefinido.</span><span class="sxs-lookup"><span data-stu-id="9a958-146">The output of each command will also trigger a CommandInvocation, usually to Out-Default.</span></span>
<span data-ttu-id="9a958-147">O InputObject Out-Default é o objeto de PowerShell devolvido do comando.</span><span class="sxs-lookup"><span data-stu-id="9a958-147">The InputObject of Out-Default is the PowerShell object returned from the command.</span></span>
<span data-ttu-id="9a958-148">Os detalhes desse objeto são impressos algumas linhas abaixo, imitando de perto o que o usuário teria visto.</span><span class="sxs-lookup"><span data-stu-id="9a958-148">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a958-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a958-149">See also</span></span>

- [<span data-ttu-id="9a958-150">*PowerShell ♥ a equipa de azul* mensagem de blogue sobre segurança</span><span class="sxs-lookup"><span data-stu-id="9a958-150">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)
