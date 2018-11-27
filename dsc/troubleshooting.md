---
ms.date: 10/30/2018
keywords: DSC, powershell, configuração, a configuração
title: Resolução de Problemas de DSC
ms.openlocfilehash: 844512e390200ed14df2b811dd5997b102a18dd1
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2018
ms.locfileid: "52321099"
---
# <a name="troubleshooting-dsc"></a><span data-ttu-id="27236-103">Resolução de Problemas de DSC</span><span class="sxs-lookup"><span data-stu-id="27236-103">Troubleshooting DSC</span></span>

<span data-ttu-id="27236-104">_Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="27236-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="27236-105">Este tópico descreve formas de resolver problemas de DSC quando surgem problemas.</span><span class="sxs-lookup"><span data-stu-id="27236-105">This topic describes ways to troubleshoot DSC when problems arise.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="27236-106">Dependência de WinRM</span><span class="sxs-lookup"><span data-stu-id="27236-106">WinRM Dependency</span></span>

<span data-ttu-id="27236-107">Windows PowerShell Desired State Configuration (DSC) depende de WinRM.</span><span class="sxs-lookup"><span data-stu-id="27236-107">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="27236-108">WinRM não está ativado por padrão no Windows Server 2008 R2 e Windows 7.</span><span class="sxs-lookup"><span data-stu-id="27236-108">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="27236-109">Executar `Set-WSManQuickConfig`, no Windows PowerShell elevados sessão, para ativar o WinRM.</span><span class="sxs-lookup"><span data-stu-id="27236-109">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="27236-110">Usando Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="27236-110">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="27236-111">O [Get-DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) cmdlet obtém informações sobre o estado da configuração a partir de um nó de destino.</span><span class="sxs-lookup"><span data-stu-id="27236-111">The [Get-DscConfigurationStatus](https://technet.microsoft.com/library/mt517868.aspx) cmdlet gets information about configuration status from a target node.</span></span> <span data-ttu-id="27236-112">Um objeto avançado for retornado com informações de alto nível sobre se é ou não a execução de configuração foi concluída com êxito ou não.</span><span class="sxs-lookup"><span data-stu-id="27236-112">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="27236-113">Pode examinar o objeto para detetar informações sobre a configuração executar como:</span><span class="sxs-lookup"><span data-stu-id="27236-113">You can dig into the object to discover details about the configuration run such as:</span></span>

- <span data-ttu-id="27236-114">Todos os recursos que falharam</span><span class="sxs-lookup"><span data-stu-id="27236-114">All of the resources that failed</span></span>
- <span data-ttu-id="27236-115">Qualquer recurso que solicitou uma reinicialização</span><span class="sxs-lookup"><span data-stu-id="27236-115">Any resource that requested a reboot</span></span>
- <span data-ttu-id="27236-116">Executam definições de configuração de meta no momento da configuração</span><span class="sxs-lookup"><span data-stu-id="27236-116">Meta-Configuration settings at time of configuration run</span></span>
- <span data-ttu-id="27236-117">Etc.</span><span class="sxs-lookup"><span data-stu-id="27236-117">Etc.</span></span>

<span data-ttu-id="27236-118">O conjunto de parâmetros seguintes devolve as informações de estado para a última configuração executar:</span><span class="sxs-lookup"><span data-stu-id="27236-118">The following parameter set returns the status information for the last configuration run:</span></span>

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```
<span data-ttu-id="27236-119">O conjunto de parâmetros seguintes devolve as informações de estado para execuções de configuração de todas as anteriores:</span><span class="sxs-lookup"><span data-stu-id="27236-119">The following parameter set returns the status information for all previous configuration runs:</span></span>

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="27236-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="27236-120">Example</span></span>

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status         StartDate                Type            Mode    RebootRequested        NumberOfResources
------        ---------                ----            ----    ---------------        -----------------
Failure        11/24/2015  3:44:56     Consistency        Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName     :    MyService
DependsOn             :
ModuleName            :    PSDesiredStateConfiguration
ModuleVersion         :    1.1
PsDscRunAsCredential  :
ResourceID            :    [File]ServiceDll
SourceInfo            :    c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds     :    0.19
Error                 :    SourcePath must be accessible for current configuration. The related file/directory is:
                           \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState            :
InDesiredState        :    False
InitialState          :
InstanceName          :    ServiceDll
RebootRequested       :    False
ReosurceName          :    File
StartDate             :    11/24/2015  3:44:56
PSComputerName        :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="27236-121">Meu script não será executado: utilizar o DSC registos para diagnosticar erros de script</span><span class="sxs-lookup"><span data-stu-id="27236-121">My script won't run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="27236-122">Como todos os Windows software, DSC registra os erros e eventos no [registos](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) que podem ser visualizados a partir do [Visualizador de eventos](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer).</span><span class="sxs-lookup"><span data-stu-id="27236-122">Like all Windows software, DSC records errors and events in [logs](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx) that can be viewed from the [Event Viewer](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer).</span></span>
<span data-ttu-id="27236-123">Examinar estes registos pode ajudar a compreender por que motivo uma determinada operação falha e como impedir a falha no futuro.</span><span class="sxs-lookup"><span data-stu-id="27236-123">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span> <span data-ttu-id="27236-124">Escrita de scripts de configuração pode ser complicada, por isso facilitar o controlo de erros como autor de, use o recurso de Log de DSC para controlar o progresso da sua configuração no registo de eventos analíticos de DSC.</span><span class="sxs-lookup"><span data-stu-id="27236-124">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="27236-125">Onde estão os registos de eventos de DSC?</span><span class="sxs-lookup"><span data-stu-id="27236-125">Where are DSC event logs?</span></span>

<span data-ttu-id="27236-126">No Visualizador de eventos, os eventos de DSC são em: **aplicativos e serviços registos/Microsoft/Windows/Desired State Configuration**</span><span class="sxs-lookup"><span data-stu-id="27236-126">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="27236-127">O cmdlet do PowerShell correspondente [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), também pode ser executado para ver os registos de eventos:</span><span class="sxs-lookup"><span data-stu-id="27236-127">The corresponding PowerShell cmdlet, [Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

<span data-ttu-id="27236-128">Conforme mostrado acima, o nome do registo principal do DSC está **Microsoft -> Windows -> DSC** (outros nomes de registo no Windows não são mostrados aqui por questões de brevidade).</span><span class="sxs-lookup"><span data-stu-id="27236-128">As shown above, DSC's primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="27236-129">O nome principal é acrescentado ao nome do canal para criar o nome do registo concluída.</span><span class="sxs-lookup"><span data-stu-id="27236-129">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="27236-130">O motor de DSC escreve principalmente em três tipos de registos: [registos operacional, analítico e depuração](https://technet.microsoft.com/library/cc722404.aspx).</span><span class="sxs-lookup"><span data-stu-id="27236-130">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](https://technet.microsoft.com/library/cc722404.aspx).</span></span> <span data-ttu-id="27236-131">Desde a análise e os registos de depuração estão desativados por predefinição, deve ativá-los no Visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="27236-131">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span> <span data-ttu-id="27236-132">Para tal, abra o Visualizador de eventos ao escrever Show-registo de eventos do Windows PowerShell; ou, clique nas **começar** botão, clique em **painel de controlo**, clique em **ferramentas administrativas**e, em seguida, clique em **Visualizador de eventos**.</span><span class="sxs-lookup"><span data-stu-id="27236-132">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel**, click **Administrative Tools**, and then click **Event Viewer**.</span></span>
<span data-ttu-id="27236-133">Sobre o **View** menu no Visualizador de eventos, clique em **Mostrar depurar registos analíticos e**.</span><span class="sxs-lookup"><span data-stu-id="27236-133">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="27236-134">É o nome do registo para o canal analítico **Microsoft-Windows-Dsc/analítico**, e o canal de depuração é **Microsoft-Windows-Dsc/Debug**.</span><span class="sxs-lookup"><span data-stu-id="27236-134">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic**, and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="27236-135">Também pode utilizar o [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) utilitário para ativar os registos, conforme mostrado no exemplo seguinte.</span><span class="sxs-lookup"><span data-stu-id="27236-135">You could also use the [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="27236-136">O que contêm os registos de DSC?</span><span class="sxs-lookup"><span data-stu-id="27236-136">What do DSC logs contain?</span></span>

<span data-ttu-id="27236-137">Registos de DSC são divididos ao longo de três canais de registo com base na importância da mensagem.</span><span class="sxs-lookup"><span data-stu-id="27236-137">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="27236-138">O registo operacional no DSC contém todas as mensagens de erro e pode ser utilizado para identificar um problema.</span><span class="sxs-lookup"><span data-stu-id="27236-138">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="27236-139">O registo de análise tem um volume maior de eventos e pode identificar em que ocorreu o erro (s).</span><span class="sxs-lookup"><span data-stu-id="27236-139">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="27236-140">Este canal também contém as mensagens verbosas (se houver).</span><span class="sxs-lookup"><span data-stu-id="27236-140">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="27236-141">O registo de depuração contém registos que podem ajudar a compreender como os erros ocorreram.</span><span class="sxs-lookup"><span data-stu-id="27236-141">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="27236-142">Mensagens de eventos de DSC são estruturadas, de modo a que todas as mensagens de evento começa com um ID de tarefa que representa exclusivamente uma operação de DSC.</span><span class="sxs-lookup"><span data-stu-id="27236-142">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="27236-143">O exemplo abaixo tenta obter a mensagem do primeiro evento registado para o registo DSC operacional.</span><span class="sxs-lookup"><span data-stu-id="27236-143">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

<span data-ttu-id="27236-144">Eventos de DSC são registados numa estrutura específica que permite ao usuário para agregar eventos a partir de uma tarefa de DSC.</span><span class="sxs-lookup"><span data-stu-id="27236-144">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="27236-145">A estrutura é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="27236-145">The structure is as follows:</span></span>

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="27236-146">Recolha de eventos de uma única operação de DSC</span><span class="sxs-lookup"><span data-stu-id="27236-146">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="27236-147">Registos de eventos de DSC conter eventos gerados pelo várias operações de DSC.</span><span class="sxs-lookup"><span data-stu-id="27236-147">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="27236-148">No entanto, normalmente será preocupados com apenas uma determinada operação com os detalhes.</span><span class="sxs-lookup"><span data-stu-id="27236-148">However, you'll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="27236-149">Todos os registos de DSC podem ser agrupados pela propriedade de ID de tarefa que é exclusiva para cada operação de DSC.</span><span class="sxs-lookup"><span data-stu-id="27236-149">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="27236-150">O ID da tarefa é apresentado como o primeiro valor de propriedade em todos os eventos de DSC.</span><span class="sxs-lookup"><span data-stu-id="27236-150">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="27236-151">Os seguintes passos explicam como a acumular todos os eventos numa estrutura de matriz agrupados.</span><span class="sxs-lookup"><span data-stu-id="27236-151">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
wevtutil.exe set-log "Microsoft-Windows-Dsc/Debug" /q:True /e:true

<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>

Get-DscLocalConfigurationManager

<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>

$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)


<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}
```

<span data-ttu-id="27236-152">Aqui, a variável `$SeparateDscOperations` com registos agrupados pela tarefa de IDs.</span><span class="sxs-lookup"><span data-stu-id="27236-152">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="27236-153">Cada elemento de matriz desta variável representa um grupo de eventos registados por uma operação de DSC diferente, permitindo o acesso para obter mais informações sobre os registos.</span><span class="sxs-lookup"><span data-stu-id="27236-153">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

```
PS C:\> $SeparateDscOperations

Count Name                      Group
----- ----                      -----
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....

PS C:\> $SeparateDscOperations[0].Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
```

<span data-ttu-id="27236-154">Pode extrair os dados na variável `$SeparateDscOperations` usando [Where-Object](https://technet.microsoft.com/library/ee177028.aspx).</span><span class="sxs-lookup"><span data-stu-id="27236-154">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](https://technet.microsoft.com/library/ee177028.aspx).</span></span> <span data-ttu-id="27236-155">Seguem-se cinco cenários em que pode querer extrair dados para resolução de problemas de DSC:</span><span class="sxs-lookup"><span data-stu-id="27236-155">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="27236-156">1: falhas de operações</span><span class="sxs-lookup"><span data-stu-id="27236-156">1: Operations failures</span></span>

<span data-ttu-id="27236-157">Todos os eventos possuem [níveis de gravidade](https://msdn.microsoft.com/library/dd996917(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="27236-157">All events have [severity levels](https://msdn.microsoft.com/library/dd996917(v=vs.85)).</span></span> <span data-ttu-id="27236-158">Estas informações podem ser utilizadas para identificar os eventos de erro:</span><span class="sxs-lookup"><span data-stu-id="27236-158">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="27236-159">2: detalhes das operações executada na última meia hora</span><span class="sxs-lookup"><span data-stu-id="27236-159">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="27236-160">`TimeCreated`, uma propriedade de todos os eventos do Windows, indica o tempo que o evento foi criado.</span><span class="sxs-lookup"><span data-stu-id="27236-160">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="27236-161">Comparar essa propriedade com um objeto de data/hora específico pode ser utilizado para filtrar todos os eventos:</span><span class="sxs-lookup"><span data-stu-id="27236-161">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="27236-162">3: mensagens da operação de mais recente</span><span class="sxs-lookup"><span data-stu-id="27236-162">3: Messages from the latest operation</span></span>

<span data-ttu-id="27236-163">A operação mais recente é armazenada no primeiro índice do grupo de matriz `$SeparateDscOperations`.</span><span class="sxs-lookup"><span data-stu-id="27236-163">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span>
<span data-ttu-id="27236-164">Consultas de mensagens do grupo para o índice 0 retorna todas as mensagens para a operação mais recente:</span><span class="sxs-lookup"><span data-stu-id="27236-164">Querying the group's messages for index 0 returns all messages for the latest operation:</span></span>

```powershell
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Consistency check completed.
```

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="27236-165">4: mensagens de erro registadas para operações com falhas recentes</span><span class="sxs-lookup"><span data-stu-id="27236-165">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="27236-166">`$SeparateDscOperations[0].Group` contém um conjunto de eventos para a operação mais recente.</span><span class="sxs-lookup"><span data-stu-id="27236-166">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="27236-167">Execute o `Where-Object` cmdlet para filtrar os eventos com base nos respetivos nomes a apresentar de nível.</span><span class="sxs-lookup"><span data-stu-id="27236-167">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="27236-168">Os resultados são armazenados no `$myFailedEvent` variável, que podem ser ainda mais examinadas para obter a mensagem de evento:</span><span class="sxs-lookup"><span data-stu-id="27236-168">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="27236-169">5: todos os eventos gerados para um ID de tarefa específica.</span><span class="sxs-lookup"><span data-stu-id="27236-169">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="27236-170">`$SeparateDscOperations` é uma matriz de grupos, cada um com o nome como o ID exclusivo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="27236-170">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="27236-171">Ao executar o `Where-Object` cmdlet, pode extrair esses grupos de eventos que tem um ID de tarefa específica:</span><span class="sxs-lookup"><span data-stu-id="27236-171">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
```

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="27236-172">Registos de utilização xDscDiagnostics para analisar o DSC</span><span class="sxs-lookup"><span data-stu-id="27236-172">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="27236-173">**xDscDiagnostics** é um módulo do PowerShell que consiste em várias funções que podem ajudar a analisar falhas de DSC no seu computador.</span><span class="sxs-lookup"><span data-stu-id="27236-173">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="27236-174">Estas funções podem ajudar a identificar todos os eventos locais de últimos de DSC de operações ou eventos de DSC em computadores remotos (com credenciais válidas).</span><span class="sxs-lookup"><span data-stu-id="27236-174">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="27236-175">Aqui, o termo operação DSC é usado para definir uma execução DSC exclusiva única desde seu início para o respetivo fim.</span><span class="sxs-lookup"><span data-stu-id="27236-175">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="27236-176">Por exemplo, `Test-DscConfiguration` seria uma operação de DSC separada.</span><span class="sxs-lookup"><span data-stu-id="27236-176">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="27236-177">Da mesma forma, todos os outro cmdlet no DSC (como `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) cada identificado como operações de DSC separadas.</span><span class="sxs-lookup"><span data-stu-id="27236-177">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="27236-178">As funções são explicadas em [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span><span class="sxs-lookup"><span data-stu-id="27236-178">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span> <span data-ttu-id="27236-179">A ajuda está disponível através da execução `Get-Help <cmdlet name>`.</span><span class="sxs-lookup"><span data-stu-id="27236-179">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="27236-180">A obter os detalhes das operações de DSC</span><span class="sxs-lookup"><span data-stu-id="27236-180">Getting details of DSC operations</span></span>

<span data-ttu-id="27236-181">O `Get-xDscOperation` função permite-lhe encontrar os resultados das operações de DSC que são executados num ou vários computadores e retorna um objeto que contém a coleção de eventos produzido por cada operação de DSC.</span><span class="sxs-lookup"><span data-stu-id="27236-181">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span> <span data-ttu-id="27236-182">Por exemplo, na seguinte saída, três comandos foram executados.</span><span class="sxs-lookup"><span data-stu-id="27236-182">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="27236-183">Primeiro transmitido e a outra dois falhou.</span><span class="sxs-lookup"><span data-stu-id="27236-183">The first one passed, and the other two failed.</span></span> <span data-ttu-id="27236-184">Esses resultados estão resumidos na saída do `Get-xDscOperation`.</span><span class="sxs-lookup"><span data-stu-id="27236-184">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

<span data-ttu-id="27236-185">Também pode especificar que pretende que apenas os resultados para as operações mais recentes, utilizando o `Newest` parâmetro:</span><span class="sxs-lookup"><span data-stu-id="27236-185">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="27236-186">A obter os detalhes de eventos de DSC</span><span class="sxs-lookup"><span data-stu-id="27236-186">Getting details of DSC events</span></span>

<span data-ttu-id="27236-187">O `Trace-xDscOperation` cmdlet devolve um objeto que contém uma coleção de eventos, seus tipos de evento, e a mensagem de saída gerados a partir de uma determinada operação de DSC.</span><span class="sxs-lookup"><span data-stu-id="27236-187">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="27236-188">Normalmente, quando encontrar uma falha em qualquer uma das operações usando `Get-xDscOperation`, teria de rastreio essa operação para descobrir qual dos eventos provocou uma falha.</span><span class="sxs-lookup"><span data-stu-id="27236-188">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="27236-189">Utilize o `SequenceID` parâmetro para obter os eventos para uma operação específica de um computador específico.</span><span class="sxs-lookup"><span data-stu-id="27236-189">Use the `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span>
<span data-ttu-id="27236-190">Por exemplo, se especificar uma `SequenceID` 9, `Trace-xDscOperaion` obter o rastreio para a operação de DSC que foi 9th da última operação:</span><span class="sxs-lookup"><span data-stu-id="27236-190">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully.
```

<span data-ttu-id="27236-191">Passar o **GUID** atribuído a uma operação específica do DSC (conforme devolvido pelo `Get-xDscOperation` cmdlet) para obter os detalhes do evento para essa operação de DSC:</span><span class="sxs-lookup"><span data-stu-id="27236-191">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmdlet) to get the event details for that DSC operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

<span data-ttu-id="27236-192">Tenha em atenção que, uma vez que `Trace-xDscOperation` agrega eventos de análise, depuração e operacional registos, que irá solicitar-lhe ativar estes registos, conforme descrito acima.</span><span class="sxs-lookup"><span data-stu-id="27236-192">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="27236-193">Em alternativa, pode recolher informações sobre os eventos ao guardar a saída de `Trace-xDscOperation` numa variável.</span><span class="sxs-lookup"><span data-stu-id="27236-193">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="27236-194">Pode utilizar os seguintes comandos para apresentar todos os eventos para uma determinada operação de DSC.</span><span class="sxs-lookup"><span data-stu-id="27236-194">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="27236-195">Esta ação apresenta os mesmos resultados como o `Get-WinEvent` cmdlet, como no resultado abaixo:</span><span class="sxs-lookup"><span data-stu-id="27236-195">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

```output
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

<span data-ttu-id="27236-196">O ideal é que, primeiro deve ser usada `Get-xDscOperation` para listar o último DSC alguns configuração é executado nas suas máquinas.</span><span class="sxs-lookup"><span data-stu-id="27236-196">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="27236-197">Ao seguir esta, é possível examinar qualquer operação única (com seu SequenceID ou JobID) com `Trace-xDscOperation` para descobrir o que fiz em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="27236-197">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="27236-198">Obter eventos para um computador remoto</span><span class="sxs-lookup"><span data-stu-id="27236-198">Getting events for a remote computer</span></span>

<span data-ttu-id="27236-199">Utilize o `ComputerName` parâmetro do `Trace-xDscOperation` cmdlet para obter os detalhes do evento num computador remoto.</span><span class="sxs-lookup"><span data-stu-id="27236-199">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="27236-200">Antes de poder fazer isto, terá de criar uma regra de firewall para permitir a administração remota no computador remoto:</span><span class="sxs-lookup"><span data-stu-id="27236-200">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

<span data-ttu-id="27236-201">Agora pode especificar esse computador na sua chamada a `Trace-xDscOperation`:</span><span class="sxs-lookup"><span data-stu-id="27236-201">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="27236-202">Não atualizar os meus recursos: como repor a cache</span><span class="sxs-lookup"><span data-stu-id="27236-202">My resources won't update: How to reset the cache</span></span>

<span data-ttu-id="27236-203">O motor de DSC armazena em cache recursos implementados como um módulo do PowerShell para fins de eficiência.</span><span class="sxs-lookup"><span data-stu-id="27236-203">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span>
<span data-ttu-id="27236-204">No entanto, isso pode causar problemas quando estiver a criação de um recurso e testá-lo em simultâneo porque DSC irá carregar a versão em cache até que o processo seja reiniciado.</span><span class="sxs-lookup"><span data-stu-id="27236-204">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="27236-205">A única forma de tornar o DSC carregar a versão mais recente é explicitamente interromper o processo que hospeda o mecanismo de DSC.</span><span class="sxs-lookup"><span data-stu-id="27236-205">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="27236-206">Da mesma forma, quando executa `Start-DscConfiguration`, depois de adicionar e modificar um recurso personalizado, a modificação pode não ser executado, a menos que ou até que, o computador é reiniciado.</span><span class="sxs-lookup"><span data-stu-id="27236-206">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="27236-207">Isto acontece porque o DSC é executado no processo de anfitrião do fornecedor de WMI (WmiPrvSE) e, normalmente, existem muitas instâncias de WmiPrvSE em execução ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="27236-207">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="27236-208">Quando reiniciar, o processo de host é reiniciado e a cache está desmarcada.</span><span class="sxs-lookup"><span data-stu-id="27236-208">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="27236-209">Para reciclar a configuração e limpar o cache sem reiniciar com êxito, tem de parar e, em seguida, reinicie o processo de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="27236-209">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="27236-210">Isso pode ser feito numa base por instância, na qual identifique o processo de pará-la e reiniciá-lo.</span><span class="sxs-lookup"><span data-stu-id="27236-210">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="27236-211">Em alternativa, pode utilizar `DebugMode`, como demonstrado abaixo, para recarregar o recurso de DSC do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="27236-211">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="27236-212">Para identificar o processo que está a alojar o motor de DSC e pará-la numa base por instância, pode listar o ID de processo do WmiPrvSE que está a alojar o motor de DSC.</span><span class="sxs-lookup"><span data-stu-id="27236-212">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="27236-213">Em seguida, para atualizar o fornecedor, pare o processo de WmiPrvSE utilizando os comandos abaixo e execute **Start-dscconfiguration para** novamente.</span><span class="sxs-lookup"><span data-stu-id="27236-213">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers |
Where-Object {$_.provider -like 'dsccore'} |
Select-Object -ExpandProperty HostProcessIdentifier

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## <a name="using-debugmode"></a><span data-ttu-id="27236-214">Usando DebugMode</span><span class="sxs-lookup"><span data-stu-id="27236-214">Using DebugMode</span></span>

<span data-ttu-id="27236-215">Pode configurar o DSC Local Configuration Manager (LCM) para utilizar `DebugMode` sempre limpar a cache quando o processo de host é reiniciado.</span><span class="sxs-lookup"><span data-stu-id="27236-215">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="27236-216">Quando definido como **TRUE**, ele faz com que o mecanismo sempre recarregar o recurso de DSC do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="27236-216">When set to **TRUE**, it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="27236-217">Depois de concluída a escrever o seu recurso, pode configurá-lo para **FALSE** e o mecanismo irá reverter para o seu comportamento de colocação em cache os módulos.</span><span class="sxs-lookup"><span data-stu-id="27236-217">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="27236-218">Segue-se uma demonstração para mostrar como `DebugMode` automaticamente pode atualizar a cache.</span><span class="sxs-lookup"><span data-stu-id="27236-218">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="27236-219">Em primeiro lugar, vamos examinar a configuração predefinida:</span><span class="sxs-lookup"><span data-stu-id="27236-219">First, let's look at the default configuration:</span></span>

```powershell
PS C:\> Get-DscLocalConfigurationManager
```

```output
AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : {None}
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

<span data-ttu-id="27236-220">Pode ver que `DebugMode` está definido como **"None"**.</span><span class="sxs-lookup"><span data-stu-id="27236-220">You can see that `DebugMode` is set to **"None"**.</span></span>

<span data-ttu-id="27236-221">Para configurar o `DebugMode` demonstração, utilize o seguinte recurso do PowerShell:</span><span class="sxs-lookup"><span data-stu-id="27236-221">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
}
```

<span data-ttu-id="27236-222">Agora, criar uma configuração usando o recurso acima, chamado `TestProviderDebugMode`:</span><span class="sxs-lookup"><span data-stu-id="27236-222">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

<span data-ttu-id="27236-223">Verá que o conteúdo do ficheiro: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` é **1**.</span><span class="sxs-lookup"><span data-stu-id="27236-223">You will see that the contents of file: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` is **1**.</span></span>

<span data-ttu-id="27236-224">Agora, atualize o código do provedor usando o seguinte script:</span><span class="sxs-lookup"><span data-stu-id="27236-224">Now, update the provider code using the following script:</span></span>

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

<span data-ttu-id="27236-225">Este script gera um número aleatório e atualiza o código do provedor em conformidade.</span><span class="sxs-lookup"><span data-stu-id="27236-225">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="27236-226">Com o `DebugMode` definido como FALSO, o conteúdo do ficheiro "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" nunca são alterados.</span><span class="sxs-lookup"><span data-stu-id="27236-226">With `DebugMode` set to false, the contents of the file "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" are never changed.</span></span>

<span data-ttu-id="27236-227">Agora, defina `DebugMode` para **"ForceModuleImport"** no seu script de configuração:</span><span class="sxs-lookup"><span data-stu-id="27236-227">Now, set `DebugMode` to **"ForceModuleImport"** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

<span data-ttu-id="27236-228">Ao executar novamente o script acima, verá que o conteúdo do ficheiro é diferente cada vez.</span><span class="sxs-lookup"><span data-stu-id="27236-228">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="27236-229">(Pode executar `Get-DscConfiguration` registá-lo).</span><span class="sxs-lookup"><span data-stu-id="27236-229">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="27236-230">Segue-se o resultado das duas execuções adicionais (os resultados podem ser diferentes quando executar o script):</span><span class="sxs-lookup"><span data-stu-id="27236-230">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
20                                      localhost

PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
14                                      localhost
```

## <a name="see-also"></a><span data-ttu-id="27236-231">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="27236-231">See Also</span></span>

### <a name="reference"></a><span data-ttu-id="27236-232">Referência</span><span class="sxs-lookup"><span data-stu-id="27236-232">Reference</span></span>

- [<span data-ttu-id="27236-233">Recurso Log de DSC</span><span class="sxs-lookup"><span data-stu-id="27236-233">DSC Log Resource</span></span>](logResource.md)

### <a name="concepts"></a><span data-ttu-id="27236-234">Conceitos</span><span class="sxs-lookup"><span data-stu-id="27236-234">Concepts</span></span>

- [<span data-ttu-id="27236-235">Criar recursos do Windows personalizados do PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="27236-235">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="27236-236">Outros Recursos</span><span class="sxs-lookup"><span data-stu-id="27236-236">Other Resources</span></span>

- <span data-ttu-id="27236-237">[Windows PowerShell Desired State Configuration Cmdlets](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="27236-237">[Windows PowerShell Desired State Configuration Cmdlets](https://technet.microsoft.com/library/dn521624(v=wps.630).aspx)</span></span>
