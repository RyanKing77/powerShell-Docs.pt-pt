---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Utilizar um servidor de relatório de DSC
ms.openlocfilehash: bcd414e9cc6d3b321676aaab6bbc3ca1b02e80aa
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893142"
---
# <a name="using-a-dsc-report-server"></a><span data-ttu-id="95657-103">Utilizar um servidor de relatório de DSC</span><span class="sxs-lookup"><span data-stu-id="95657-103">Using a DSC report server</span></span>

<span data-ttu-id="95657-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="95657-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="95657-105">O servidor de solicitação (recurso do Windows *DSC-serviço*) é um componente suportado do Windows Server no entanto, não existem planos para oferecer novas funcionalidades ou capacidades.</span><span class="sxs-lookup"><span data-stu-id="95657-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="95657-106">É recomendado para começar a fazer a transição geridos os clientes [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação de mensagens em fila no Windows Server) ou uma das soluções da Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="95657-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>
>
> <span data-ttu-id="95657-107">**Tenha em atenção** o servidor de relatórios descrito neste tópico não está disponível no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="95657-107">**Note** The report server described in this topic is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="95657-108">O Gestor de configuração Local (LCM) de um nó pode ser configurado para enviar relatórios sobre o estado de configuração para um servidor de solicitação, em seguida, pode ser consultado para obter esses dados.</span><span class="sxs-lookup"><span data-stu-id="95657-108">The Local Configuration Manager (LCM) of a node can be configured to send reports about its configuration status to a pull server, which can then be queried to retrieve that data.</span></span> <span data-ttu-id="95657-109">Sempre que o nó verifica e aplica-se de uma configuração, envia um relatório para o servidor de relatórios.</span><span class="sxs-lookup"><span data-stu-id="95657-109">Each time the node checks and applies a configuration, it sends a report to the report server.</span></span> <span data-ttu-id="95657-110">Estes relatórios são armazenados numa base de dados no servidor e podem ser obtidos chamando o serviço web de relatórios.</span><span class="sxs-lookup"><span data-stu-id="95657-110">These reports are stored in a database on the server, and can be retrieved by calling the reporting web service.</span></span> <span data-ttu-id="95657-111">Cada relatório contém informações como que configurações foram aplicadas e se eles foi concluída com êxito, os recursos utilizados, quaisquer erros que foram lançados e iniciar e terminar vezes.</span><span class="sxs-lookup"><span data-stu-id="95657-111">Each report contains information such as what configurations were applied and whether they succeeded, the resources used, any errors that were thrown, and start and finish times.</span></span>

## <a name="configuring-a-node-to-send-reports"></a><span data-ttu-id="95657-112">Configurar um nó para enviar relatórios</span><span class="sxs-lookup"><span data-stu-id="95657-112">Configuring a node to send reports</span></span>

<span data-ttu-id="95657-113">Diz que um nó para enviar relatórios a um servidor com uma **ReportServerWeb** Bloquear configuração de LCM do nó (para obter informações sobre como configurar o LCM, consulte [configurar o Gestor de configuração Local](metaConfig.md) ).</span><span class="sxs-lookup"><span data-stu-id="95657-113">You tell a node to send reports to a server by using a **ReportServerWeb** block in the node's LCM configuration (for information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md)).</span></span> <span data-ttu-id="95657-114">O servidor ao qual o nó envia relatórios tem de ser definido como um servidor de solicitação da web (não é possível enviar relatórios para uma partilha SMB).</span><span class="sxs-lookup"><span data-stu-id="95657-114">The server to which the node sends reports must be set up as a web pull server (you cannot send reports to an SMB share).</span></span> <span data-ttu-id="95657-115">Para obter informações sobre como configurar um servidor de solicitação, consulte [como configurar um servidor de solicitação do DSC web](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="95657-115">For information about setting up a pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span> <span data-ttu-id="95657-116">O servidor de relatórios pode ser o mesmo serviço a partir do qual o nó obtém configurações e obtém os recursos, ou pode ser um serviço diferente.</span><span class="sxs-lookup"><span data-stu-id="95657-116">The report server can be the same service from which the node pulls configurations and gets resources, or it can be a different service.</span></span>

<span data-ttu-id="95657-117">Na **ReportServerWeb** bloco, especifica a URL do serviço pull e uma chave de registo que é conhecida para o servidor.</span><span class="sxs-lookup"><span data-stu-id="95657-117">In the **ReportServerWeb** block, you specify the URL of the pull service and a registration key that is known to the server.</span></span>

<span data-ttu-id="95657-118">A seguinte configuração configura um nó para as configurações de solicitação de um serviço e enviar relatórios para um serviço num servidor diferente.</span><span class="sxs-lookup"><span data-stu-id="95657-118">The following configuration configures a node to pull configurations from one service, and send reports to a service on a different server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration ReportClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PULL:8080/PSDSCPullServer.svc'
            RegistrationKey    = 'bbb9778f-43f2-47de-b61e-a0daff474c6d'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCReportServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}

ReportClientConfig
```

<span data-ttu-id="95657-119">A seguinte configuração configura um nó para utilizar um único servidor para configurações, recursos e geração de relatórios.</span><span class="sxs-lookup"><span data-stu-id="95657-119">The following configuration configures a node to use a single server for configurations, resources, and reporting.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }



        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfig
```

> [!NOTE]
> <span data-ttu-id="95657-120">Pode nomear o serviço web que quiser ao configurar um servidor de solicitação, mas a **ServerURL** propriedade tem de corresponder ao nome do serviço.</span><span class="sxs-lookup"><span data-stu-id="95657-120">You can name the web service whatever you want when you set up a pull server, but the **ServerURL** property must match the service name.</span></span>

## <a name="getting-report-data"></a><span data-ttu-id="95657-121">Obter dados de relatório</span><span class="sxs-lookup"><span data-stu-id="95657-121">Getting report data</span></span>

<span data-ttu-id="95657-122">Relatórios enviados para o servidor de solicitação são inseridos num banco de dados no servidor.</span><span class="sxs-lookup"><span data-stu-id="95657-122">Reports sent to the pull server are entered into a database on the server.</span></span> <span data-ttu-id="95657-123">Os relatórios estão disponíveis por meio de chamadas para o serviço web.</span><span class="sxs-lookup"><span data-stu-id="95657-123">The reports are available through calls to the web service.</span></span> <span data-ttu-id="95657-124">Para obter relatórios para um nó específico, enviar um pedido HTTP para o serviço da web de relatório no seguinte formato: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports` onde `MyNodeAgentId` é AgentId do nó para o qual pretende obter relatórios.</span><span class="sxs-lookup"><span data-stu-id="95657-124">To retrieve reports for a specific node, send an HTTP request to the report web service in the following form: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports` where `MyNodeAgentId` is the AgentId of the node for which you want to get reports.</span></span> <span data-ttu-id="95657-125">Pode obter o AgentID para um nó chamando [Get-dsclocalconfigurationmanager para](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) nesse nó.</span><span class="sxs-lookup"><span data-stu-id="95657-125">You can get the AgentID for a node by calling [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) on that node.</span></span>

<span data-ttu-id="95657-126">Os relatórios são retornados como uma matriz de objetos JSON.</span><span class="sxs-lookup"><span data-stu-id="95657-126">The reports are returned as an array of JSON objects.</span></span>

<span data-ttu-id="95657-127">O script a seguir devolve os relatórios para o nó no qual é executado:</span><span class="sxs-lookup"><span data-stu-id="95657-127">The following script returns the reports for the node on which it is run:</span></span>

```powershell
function GetReport
{
    param
    (
        $AgentId = "$((glcm).AgentId)", 
        $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCPullServer.svc"
    )

    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```

## <a name="viewing-report-data"></a><span data-ttu-id="95657-128">Ver os dados de relatório</span><span class="sxs-lookup"><span data-stu-id="95657-128">Viewing report data</span></span>

<span data-ttu-id="95657-129">Se definir uma variável para o resultado do **GetReport** função, pode ver os campos individuais num elemento da matriz que é devolvido:</span><span class="sxs-lookup"><span data-stu-id="95657-129">If you set a variable to the result of the **GetReport** function, you can view the individual fields in an element of the array that is returned:</span></span>

```powershell
$reports = GetReport
$reports[1]
```

```output
JobId                : 019dfbe5-f99f-11e5-80c6-001dd8b8065c
OperationType        : Consistency
RefreshMode          : Pull
Status               : Success
ReportFormatVersion  : 2.0
ConfigurationVersion : 2.0.0
StartTime            : 04/03/2016 06:21:43
EndTime              : 04/03/2016 06:22:04
RebootRequested      : False
Errors               : {}
StatusData           : {{"StartDate":"2016-04-03T06:21:43.7220000-07:00","IPV6Addresses":["2001:4898:d8:f2f2:852b:b255:b071:283b","fe80::852b:b255:b071
                       :283b%12","::2000:0:0:0","::1","::2000:0:0:0"],"DurationInSeconds":"21","JobID":"{019DFBE5-F99F-11E5-80C6-001DD8B8065C}","Curren
                       tChecksum":"A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F","MetaData":"Author: configAuthor; Name:
                       Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost: CONTOSO-PullSrv;","RebootRequested":"False
                       ","Status":"Success","IPV4Addresses":["10.240.179.151","127.0.0.1"],"LCMVersion":"2.0","ResourcesNotInDesiredState":[{"SourceInf
                       o":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall","ModuleName":"xNetworking","DurationInSeconds":"8.785",
                       "InstanceName":"Firewall","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"xFirewall","ModuleVersion":"2.7.0.0","
                       RebootRequested":"False","ResourceId":"[xFirewall]Firewall","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"False
                       "}],"NumberOfResources":"2","Type":"Consistency","HostName":"CONTOSO-PULLCLI","ResourcesInDesiredState":[{"SourceInfo":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive","ModuleName":"PSDesiredStateConfiguration","DurationInSeconds":"1.848",
                       "InstanceName":"ArchiveExample","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"Archive","ModuleVersion":"1.1","
                       RebootRequested":"False","ResourceId":"[Archive]ArchiveExample","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"T
                       rue"}],"MACAddresses":["00-1D-D8-B8-06-5C","00-00-00-00-00-00-00-E0"],"MetaConfiguration":{"AgentId":"52DA826D-00DE-4166-8ACB-73F2B46A7E00",
                       "ConfigurationDownloadManagers":[{"SourceInfo":"C:\\ReportTest\\LCMConfig.ps1::14::9::ConfigurationRepositoryWeb","A
                       llowUnsecureConnection":"True","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","RegistrationKey":"","ResourceId":"[Config
                       urationRepositoryWeb]CONTOSO-PullSrv","ConfigurationNames":["ClientConfig"]}],"ActionAfterReboot":"ContinueConfiguration","LCMCo
                       mpatibleVersions":["1.0","2.0"],"LCMState":"Idle","ResourceModuleManagers":[],"ReportManagers":[{"AllowUnsecureConnection":"True
                       ","RegistrationKey":"","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","ResourceId":"[ReportServerWeb]CONTOSO-PullSrv","S
                       ourceInfo":"C:\\ReportTest\\LCMConfig.ps1::24::9::ReportServerWeb"}],"StatusRetentionTimeInDays":"10","LCMVersion":"2.0","Config
                       urationMode":"ApplyAndMonitor","RefreshFrequencyMins":"30","RebootNodeIfNeeded":"True","RefreshMode":"Pull","DebugMode":["NONE"]
                       ,"LCMStateDetail":"","AllowModuleOverwrite":"False","ConfigurationModeFrequencyMins":"15"},"Locale":"en-US","Mode":"Pull"}}
AdditionalData       : {}
```

<span data-ttu-id="95657-130">Por predefinição, os relatórios são ordenados pelo **JobID**.</span><span class="sxs-lookup"><span data-stu-id="95657-130">By default, the reports are sorted by **JobID**.</span></span> <span data-ttu-id="95657-131">Para obter o relatório mais recente, pode ordenar os relatórios por descendentes **StartTime** propriedade e, em seguida, obter o primeiro elemento da matriz:</span><span class="sxs-lookup"><span data-stu-id="95657-131">To get the most recent report, you can sort the reports by descending **StartTime** property, and then get the first element of the array:</span></span>

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

<span data-ttu-id="95657-132">Tenha em atenção que o **StatusData** propriedade é um objeto com várias propriedades.</span><span class="sxs-lookup"><span data-stu-id="95657-132">Notice that the **StatusData** property is an object with a number of properties.</span></span> <span data-ttu-id="95657-133">Esta é onde muito do que os dados de relatório.</span><span class="sxs-lookup"><span data-stu-id="95657-133">This is where much of the reporting data is.</span></span> <span data-ttu-id="95657-134">Vamos examinar os campos individuais do **StatusData** propriedade para o relatório mais recente:</span><span class="sxs-lookup"><span data-stu-id="95657-134">Let's look at the individual fields of the **StatusData** property for the most recent report:</span></span>

```powershell
$statusData = $reportMostRecent.StatusData | ConvertFrom-Json
$statusData
```

```output
StartDate                  : 2016-04-04T11:21:41.2990000-07:00
IPV6Addresses              : {2001:4898:d8:f2f2:852b:b255:b071:283b, fe80::852b:b255:b071:283b%12, ::2000:0:0:0, ::1...}
DurationInSeconds          : 25
JobID                      : {135D230E-FA92-11E5-80C6-001DD8B8065C}
CurrentChecksum            : A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F
MetaData                   : Author: configAuthor; Name: Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost:
                             CONTOSO-PullSrv;
RebootRequested            : False
Status                     : Success
IPV4Addresses              : {10.240.179.151, 127.0.0.1}
LCMVersion                 : 2.0
ResourcesNotInDesiredState : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall; ModuleName=xNetworking;
                             DurationInSeconds=10.725; InstanceName=Firewall; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=xFirewall;
                             ModuleVersion=2.7.0.0; RebootRequested=False; ResourceId=[xFirewall]Firewall; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=False}}
NumberOfResources          : 2
Type                       : Consistency
HostName                   : CONTOSO-PULLCLI
ResourcesInDesiredState    : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive; ModuleName=PSDesiredStateConfiguration;
                             DurationInSeconds=2.672; InstanceName=ArchiveExample; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=Archive;
                             ModuleVersion=1.1; RebootRequested=False; ResourceId=[Archive]ArchiveExample; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=True}}
MACAddresses               : {00-1D-D8-B8-06-5C, 00-00-00-00-00-00-00-E0}
MetaConfiguration          : @{AgentId=52DA826D-00DE-4166-8ACB-73F2B46A7E00; ConfigurationDownloadManagers=System.Object[];
                             ActionAfterReboot=ContinueConfiguration; LCMCompatibleVersions=System.Object[]; LCMState=Idle;
                             ResourceModuleManagers=System.Object[]; ReportManagers=System.Object[]; StatusRetentionTimeInDays=10; LCMVersion=2.0;
                             ConfigurationMode=ApplyAndMonitor; RefreshFrequencyMins=30; RebootNodeIfNeeded=True; RefreshMode=Pull;
                             DebugMode=System.Object[]; LCMStateDetail=; AllowModuleOverwrite=False; ConfigurationModeFrequencyMins=15}
Locale                     : en-US
Mode                       : Pull
```

<span data-ttu-id="95657-135">Entre outras coisas, isso mostra que a configuração mais recente chamado dois recursos e que um deles estava no estado pretendido e uma delas não era.</span><span class="sxs-lookup"><span data-stu-id="95657-135">Among other things, this shows that the most recent configuration called two resources, and that one of them was in the desired state, and one of them was not.</span></span> <span data-ttu-id="95657-136">Pode obter uma saída mais legível de apenas o **ResourcesNotInDesiredState** propriedade:</span><span class="sxs-lookup"><span data-stu-id="95657-136">You can get a more readable output of just the **ResourcesNotInDesiredState** property:</span></span>

```powershell
$statusData.ResourcesInDesiredState
```

```output
SourceInfo        : C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive
ModuleName        : PSDesiredStateConfiguration
DurationInSeconds : 2.672
InstanceName      : ArchiveExample
StartDate         : 2016-04-04T11:21:55.7200000-07:00
ResourceName      : Archive
ModuleVersion     : 1.1
RebootRequested   : False
ResourceId        : [Archive]ArchiveExample
ConfigurationName : Sample_ArchiveFirewall
InDesiredState    : True
```

<span data-ttu-id="95657-137">Tenha em atenção que estes exemplos destinam-se para dar uma idéia do que pode fazer com dados de relatório.</span><span class="sxs-lookup"><span data-stu-id="95657-137">Note that these examples are meant to give you an idea of what you can do with report data.</span></span> <span data-ttu-id="95657-138">Para obter uma introdução sobre como trabalhar com JSON no PowerShell, consulte [Brincando com o JSON e o PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="95657-138">For an introduction on working with JSON in PowerShell, see [Playing with JSON and PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span></span>

## <a name="see-also"></a><span data-ttu-id="95657-139">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="95657-139">See Also</span></span>

[<span data-ttu-id="95657-140">Configurar o Gestor de configuração Local</span><span class="sxs-lookup"><span data-stu-id="95657-140">Configuring the Local Configuration Manager</span></span>](metaConfig.md)

[<span data-ttu-id="95657-141">Como configurar um servidor de solicitação da web de DSC</span><span class="sxs-lookup"><span data-stu-id="95657-141">Setting up a DSC web pull server</span></span>](pullServer.md)

[<span data-ttu-id="95657-142">Configurar um cliente de solicitação através de nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="95657-142">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)