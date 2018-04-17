---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Configurar um cliente de solicitação através de nomes de configuração
ms.openlocfilehash: 7c8f204cc646e52ad5e953d6c7ad9e4e906d8a5b
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a><span data-ttu-id="fd99b-103">Configurar um cliente de solicitação através de nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="fd99b-103">Setting up a pull client using configuration names</span></span>

> <span data-ttu-id="fd99b-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fd99b-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd99b-105">O servidor de solicitação (funcionalidade do Windows *DSC serviço*) é um componente suportado do Windows Server no entanto, são não planos para oferecer novas funcionalidades ou capacidades.</span><span class="sxs-lookup"><span data-stu-id="fd99b-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="fd99b-106">É recomendado para começar a transição geridos os clientes [Automation DSC do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação no Windows Server) ou uma das soluções de Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="fd99b-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="fd99b-107">Cada nó de destino tem de ser disse para utilizar o modo de extração e dado o URL onde pode contactar o servidor de solicitação para obter as configurações.</span><span class="sxs-lookup"><span data-stu-id="fd99b-107">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span>
<span data-ttu-id="fd99b-108">Para tal, tem de configurar o Gestor de configuração Local (MMC) com as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="fd99b-108">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span>
<span data-ttu-id="fd99b-109">Para configurar o MMC, cria um tipo especial de configuração, decorado com o **DSCLocalConfigurationManager** atributo.</span><span class="sxs-lookup"><span data-stu-id="fd99b-109">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span>
<span data-ttu-id="fd99b-110">Para obter mais informações sobre como configurar o MMC, consulte [configurar o Gestor de configuração Local](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="fd99b-110">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="fd99b-111">**Tenha em atenção**: Este tópico aplica-se ao PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="fd99b-111">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="fd99b-112">Para obter informações sobre como configurar um cliente de solicitação no PowerShell 4.0, consulte [configurar um cliente de extração com o ID de configuração no PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="fd99b-112">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="fd99b-113">O script seguinte configura o MMC para as configurações de solicitação de um servidor com o nome "CONTOSO-PullSrv":</span><span class="sxs-lookup"><span data-stu-id="fd99b-113">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv":</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="fd99b-114">O script, o **ConfigurationRepositoryWeb** bloco define o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="fd99b-114">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span>
<span data-ttu-id="fd99b-115">O **ServerURL** propriedade especifica o ponto final para o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="fd99b-115">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

<span data-ttu-id="fd99b-116">O **RegistrationKey** propriedade é uma chave partilhada entre todos os nós de cliente para um servidor de solicitação e esse servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="fd99b-116">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span>
<span data-ttu-id="fd99b-117">O mesmo valor é armazenado num ficheiro no servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="fd99b-117">The same value is stored in a file on the pull server.</span></span>

<span data-ttu-id="fd99b-118">O **ConfigurationNames** propriedade é uma matriz que especifica os nomes das configurações destinadas para o nó de cliente.</span><span class="sxs-lookup"><span data-stu-id="fd99b-118">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
<span data-ttu-id="fd99b-119">No servidor de solicitação, o MOF ficheiro de configuração para este nó de cliente deve ter o nome *ConfigurationNames*. MOF, onde *ConfigurationNames* corresponde ao valor da **ConfigurationNames**  propriedade definida nesta configuração meta.</span><span class="sxs-lookup"><span data-stu-id="fd99b-119">On the pull server, the configuration MOF file for this client node must be named *ConfigurationNames*.mof, where *ConfigurationNames* matches the value of the **ConfigurationNames** property you set in this metaconfiguration.</span></span>

><span data-ttu-id="fd99b-120">**Nota:** se especificar mais do que um valor no **ConfigurationNames**, também tem de especificar **PartialConfiguration** bloqueios na sua configuração.</span><span class="sxs-lookup"><span data-stu-id="fd99b-120">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
<span data-ttu-id="fd99b-121">Para informações sobre configurações parciais, consulte [configurações parciais de configuração de estado pretendido do PowerShell](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="fd99b-121">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

<span data-ttu-id="fd99b-122">Depois deste script é executado, cria uma nova pasta de saída com o nome **PullClientConfigNames** e coloca não existe um ficheiro MOF de configuração meta.</span><span class="sxs-lookup"><span data-stu-id="fd99b-122">After this script runs, it creates a new output folder named **PullClientConfigNames** and puts a metaconfiguration MOF file there.</span></span>
<span data-ttu-id="fd99b-123">Neste caso, o ficheiro MOF de configuração meta será designado `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="fd99b-123">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="fd99b-124">Para aplicar a configuração, chame o **conjunto DscLocalConfigurationManager** cmdlet, com o **caminho** definido para a localização do ficheiro MOF configuração meta.</span><span class="sxs-lookup"><span data-stu-id="fd99b-124">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span>

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> <span data-ttu-id="fd99b-125">**Tenha em atenção**: as chaves de registo só funcionam com servidores de solicitação da web.</span><span class="sxs-lookup"><span data-stu-id="fd99b-125">**Note**: Registration keys work only with web pull servers.</span></span>
<span data-ttu-id="fd99b-126">Ainda tem de utilizar **ConfigurationID** com um servidor de solicitação do SMB.</span><span class="sxs-lookup"><span data-stu-id="fd99b-126">You must still use **ConfigurationID** with an SMB pull server.</span></span>
<span data-ttu-id="fd99b-127">Para obter informações sobre como configurar um servidor de solicitação utilizando **ConfigurationID**, consulte [configurar um cliente de extração com o ID de configuração](PullClientConfigNames.md)</span><span class="sxs-lookup"><span data-stu-id="fd99b-127">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](PullClientConfigNames.md)</span></span>

## <a name="resource-and-report-servers"></a><span data-ttu-id="fd99b-128">Servidores de recursos e o relatório</span><span class="sxs-lookup"><span data-stu-id="fd99b-128">Resource and report servers</span></span>

<span data-ttu-id="fd99b-129">Se especificar apenas um **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** bloquear na configuração da MMC (do exemplo anterior), o cliente de solicitação irá solicitar recursos a partir de servidor especificado, mas não enviarão relatórios ao mesmo.</span><span class="sxs-lookup"><span data-stu-id="fd99b-129">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span>
<span data-ttu-id="fd99b-130">Pode utilizar um servidor de solicitação único para configurações, recursos e relatórios, mas tem de criar um **ReportRepositoryWeb** bloco para configurar o Reporting Services.</span><span class="sxs-lookup"><span data-stu-id="fd99b-130">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>
<span data-ttu-id="fd99b-131">O exemplo seguinte mostra uma configuração meta do que configura um cliente para enviar relatórios de dados, para um servidor de solicitação único e recursos e configurações de extração.</span><span class="sxs-lookup"><span data-stu-id="fd99b-131">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="fd99b-132">Também pode especificar os servidores de extração diferente para recursos e relatórios.</span><span class="sxs-lookup"><span data-stu-id="fd99b-132">You can also specify different pull servers for resources and reporting.</span></span>
<span data-ttu-id="fd99b-133">Para especificar um servidor de recurso, a utilização de uma um **ResourceRepositoryWeb** (para um servidor de solicitação web) ou um **ResourceRepositoryShare** blocos (por um servidor de solicitação SMB).</span><span class="sxs-lookup"><span data-stu-id="fd99b-133">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="fd99b-134">Para especificar um servidor de relatórios, pode utilizar um **ReportRepositoryWeb** bloco.</span><span class="sxs-lookup"><span data-stu-id="fd99b-134">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span>
<span data-ttu-id="fd99b-135">Um servidor de relatórios não pode ser um servidor do SMB.</span><span class="sxs-lookup"><span data-stu-id="fd99b-135">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="fd99b-136">A configuração meta do seguinte configura uma solicitação de cliente para obter as respetivas configurações de **CONTOSO PullSrv** e respetivos recursos da **CONTOSO ResourceSrv**e para enviar relatórios de estado para  **CONTOSO ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="fd99b-136">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="fd99b-137">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="fd99b-137">See Also</span></span>

* [<span data-ttu-id="fd99b-138">Configurar um cliente de extração com o ID de configuração</span><span class="sxs-lookup"><span data-stu-id="fd99b-138">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="fd99b-139">Configurar um servidor de solicitação do DSC web</span><span class="sxs-lookup"><span data-stu-id="fd99b-139">Setting up a DSC web pull server</span></span>](pullServer.md)