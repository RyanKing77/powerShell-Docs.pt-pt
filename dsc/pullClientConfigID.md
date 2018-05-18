---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Configurar um cliente de solicitação através de IDs de configuração
ms.openlocfilehash: b4a45c4d014b3c4fc0140ad492f81474b260065a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a><span data-ttu-id="0a8c7-103">Configurar um cliente de solicitação através de IDs de configuração</span><span class="sxs-lookup"><span data-stu-id="0a8c7-103">Setting up a pull client using configuration ID</span></span>

> <span data-ttu-id="0a8c7-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0a8c7-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0a8c7-105">O servidor de solicitação (funcionalidade do Windows *DSC serviço*) é um componente suportado do Windows Server no entanto, são não planos para oferecer novas funcionalidades ou capacidades.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="0a8c7-106">É recomendado para começar a transição geridos os clientes [Automation DSC do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação no Windows Server) ou uma das soluções de Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="0a8c7-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="0a8c7-107">Cada nó de destino tem de ser disse para utilizar o modo de extração e dado o URL onde pode contactar o servidor de solicitação para obter as configurações.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-107">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="0a8c7-108">Para tal, tem de configurar o Gestor de configuração Local (MMC) com as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-108">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="0a8c7-109">Para configurar o MMC, cria um tipo especial de configuração, decorado com o **DSCLocalConfigurationManager** atributo.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-109">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="0a8c7-110">Para obter mais informações sobre como configurar o MMC, consulte [configurar o Gestor de configuração Local](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="0a8c7-110">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="0a8c7-111">**Tenha em atenção**: Este tópico aplica-se ao PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-111">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="0a8c7-112">Para obter informações sobre como configurar um cliente de solicitação no PowerShell 4.0, consulte [configurar um cliente de extração com o ID de configuração no PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="0a8c7-112">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="0a8c7-113">O script seguinte configura o MMC para as configurações de solicitação de um servidor com o nome "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="0a8c7-113">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

<span data-ttu-id="0a8c7-114">O script, o **ConfigurationRepositoryWeb** bloco define o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-114">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="0a8c7-115">O **ServerURL**</span><span class="sxs-lookup"><span data-stu-id="0a8c7-115">The **ServerURL**</span></span>

<span data-ttu-id="0a8c7-116">Depois deste script é executado, cria uma nova pasta de saída com o nome **PullClientConfigID** e coloca não existe um ficheiro MOF de configuração meta.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-116">After this script runs, it creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="0a8c7-117">Neste caso, o ficheiro MOF de configuração meta será designado `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-117">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="0a8c7-118">Para aplicar a configuração, chame o **conjunto DscLocalConfigurationManager** cmdlet, com o **caminho** definido para a localização do ficheiro MOF configuração meta.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-118">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="0a8c7-119">Por exemplo: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span><span class="sxs-lookup"><span data-stu-id="0a8c7-119">For example: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span></span>

## <a name="configuration-id"></a><span data-ttu-id="0a8c7-120">ID de configuração</span><span class="sxs-lookup"><span data-stu-id="0a8c7-120">Configuration ID</span></span>

<span data-ttu-id="0a8c7-121">Os conjuntos de script a **ConfigurationID** propriedade da MMC para um GUID que tinha de ser criado previamente para esta finalidade (pode criar um GUID, utilizando o **novo Guid** cmdlet).</span><span class="sxs-lookup"><span data-stu-id="0a8c7-121">The script sets the **ConfigurationID** property of LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="0a8c7-122">O **ConfigurationID** é o que utiliza o MMC para encontrar a configuração adequada no servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-122">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="0a8c7-123">O ficheiro MOF de configuração no servidor de solicitação deve ter o nome _ConfigurationID_. MOF, onde _ConfigurationID_ valor o **ConfigurationID** propriedade de destino MMC do nó.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-123">The configuration MOF file on the pull server must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="smb-pull-server"></a><span data-ttu-id="0a8c7-124">Servidor de solicitação SMB</span><span class="sxs-lookup"><span data-stu-id="0a8c7-124">SMB pull server</span></span>

<span data-ttu-id="0a8c7-125">Para configurar um cliente para as configurações de solicitação de um servidor do SMB, utilize um **ConfigurationRepositoryShare** bloco.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-125">To set up a client to pull configurations from an SMB server, use a **ConfigurationRepositoryShare** block.</span></span> <span data-ttu-id="0a8c7-126">Num **ConfigurationRepositoryShare** bloco, especifique o caminho para o servidor, definindo o **SourcePath** propriedade.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-126">In a **ConfigurationRepositoryShare** block, you specify the path to the server by setting the **SourcePath** property.</span></span> <span data-ttu-id="0a8c7-127">A configuração meta do seguinte configura o nó de destino para solicitar a partir de um servidor de solicitação SMB denominado **SMBPullServer**.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-127">The following metaconfiguration configures the target node to pull from an SMB pull server named **SMBPullServer**.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\PullSource'

        }
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a><span data-ttu-id="0a8c7-128">Servidores de recursos e o relatório</span><span class="sxs-lookup"><span data-stu-id="0a8c7-128">Resource and report servers</span></span>

<span data-ttu-id="0a8c7-129">Se especificar apenas um **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** bloquear na configuração da MMC (do exemplo anterior), o cliente de solicitação irá solicitar recursos a partir de servidor especificado, mas não enviarão relatórios ao mesmo.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-129">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span> <span data-ttu-id="0a8c7-130">Pode utilizar um servidor de solicitação único para configurações, recursos e relatórios, mas tem de criar um **ReportRepositoryWeb** bloco para configurar o Reporting Services.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-130">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

<span data-ttu-id="0a8c7-131">O exemplo seguinte mostra uma configuração meta do que configura um cliente para enviar relatórios de dados, para um servidor de solicitação único e recursos e configurações de extração.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-131">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }


        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="0a8c7-132">Também pode especificar os servidores de extração diferente para recursos e relatórios.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-132">You can also specify different pull servers for resources and reporting.</span></span> <span data-ttu-id="0a8c7-133">Para especificar um servidor de recurso, a utilização de uma um **ResourceRepositoryWeb** (para um servidor de solicitação web) ou um **ResourceRepositoryShare** blocos (por um servidor de solicitação SMB).</span><span class="sxs-lookup"><span data-stu-id="0a8c7-133">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="0a8c7-134">Para especificar um servidor de relatórios, pode utilizar um **ReportRepositoryWeb** bloco.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-134">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="0a8c7-135">Um servidor de relatórios não pode ser um servidor do SMB.</span><span class="sxs-lookup"><span data-stu-id="0a8c7-135">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="0a8c7-136">A configuração meta do seguinte configura uma solicitação de cliente para obter as respetivas configurações de **CONTOSO PullSrv** e respetivos recursos da **CONTOSO ResourceSrv**e para enviar relatórios de estado para  **CONTOSO ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="0a8c7-136">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## <a name="see-also"></a><span data-ttu-id="0a8c7-137">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="0a8c7-137">See Also</span></span>

* [<span data-ttu-id="0a8c7-138">Configurar um cliente de extração com nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="0a8c7-138">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)