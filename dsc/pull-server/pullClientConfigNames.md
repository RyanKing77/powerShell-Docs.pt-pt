---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Configurar um cliente de solicitação através de nomes de configuração no PowerShell 5.0 e posterior
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688078"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="a8784-103">Configurar um cliente de solicitação através de nomes de configuração no PowerShell 5.0 e posterior</span><span class="sxs-lookup"><span data-stu-id="a8784-103">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="a8784-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a8784-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a8784-105">O servidor de solicitação (recurso do Windows *DSC-serviço*) é um componente suportado do Windows Server no entanto, não existem planos para oferecer novas funcionalidades ou capacidades.</span><span class="sxs-lookup"><span data-stu-id="a8784-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="a8784-106">É recomendado para começar a fazer a transição geridos os clientes [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação de mensagens em fila no Windows Server) ou uma das soluções da Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="a8784-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="a8784-107">Antes de configurar um cliente de solicitação, deve configurar um servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="a8784-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="a8784-108">Embora esta ordem não é necessária, ele ajuda na resolução de problemas e ajuda a garantir que o registo foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="a8784-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="a8784-109">Para configurar um servidor de solicitação, pode usar os seguintes guias:</span><span class="sxs-lookup"><span data-stu-id="a8784-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="a8784-110">Configurar um servidor de solicitação de SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="a8784-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="a8784-111">Configurar um servidor de solicitação de HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="a8784-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="a8784-112">Cada nó de destino pode ser configurado para transferir configurações, recursos e até mesmo comunicou o seu estado.</span><span class="sxs-lookup"><span data-stu-id="a8784-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="a8784-113">As secções abaixo mostram-lhe como configurar um cliente de solicitação com uma partilha SMB ou o servidor de solicitação de DSC de HTTP.</span><span class="sxs-lookup"><span data-stu-id="a8784-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="a8784-114">Quando atualiza LCM o nó, será contactado por para a localização configurada para transferir quaisquer configurações atribuídas.</span><span class="sxs-lookup"><span data-stu-id="a8784-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="a8784-115">Se não existirem quaisquer recursos necessários no nó, será transferida-los automaticamente na localização de configurado.</span><span class="sxs-lookup"><span data-stu-id="a8784-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="a8784-116">Se o nó está configurado com um [Report Server](reportServer.md), em seguida, esse irá comunicar o estado da operação.</span><span class="sxs-lookup"><span data-stu-id="a8784-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> <span data-ttu-id="a8784-117">**Tenha em atenção**: Este tópico aplica-se para PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="a8784-117">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="a8784-118">Para obter informações sobre como configurar um cliente de solicitação no PowerShell 4.0, consulte [configurar um cliente de solicitação com o ID de configuração no PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="a8784-118">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="a8784-119">Configurar o cliente de solicitação LCM</span><span class="sxs-lookup"><span data-stu-id="a8784-119">Configure the pull client LCM</span></span>

<span data-ttu-id="a8784-120">Executar qualquer um dos exemplos abaixo cria uma nova pasta de saída com o nome **PullClientConfigName** e coloca um ficheiro MOF de metaconfiguration lá.</span><span class="sxs-lookup"><span data-stu-id="a8784-120">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="a8784-121">Neste caso, o ficheiro MOF de metaconfiguration será denominado `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="a8784-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="a8784-122">Para aplicar a configuração, chame o **Set-dsclocalconfigurationmanager para** cmdlet, com o **caminho** definido para a localização do ficheiro MOF metaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="a8784-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="a8784-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a8784-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="a8784-124">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="a8784-124">Configuration Name</span></span>

<span data-ttu-id="a8784-125">Os exemplos abaixo conjuntos a **ConfigurationName** propriedade do LCM para o nome de uma configuração compilada anteriormente, criada para este fim.</span><span class="sxs-lookup"><span data-stu-id="a8784-125">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="a8784-126">O **ConfigurationName** é o que o LCM utiliza para encontrar a configuração adequada no servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="a8784-126">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="a8784-127">O ficheiro MOF de configuração no servidor de solicitação deve ter o nome `<ConfigurationName>.mof`, neste caso, "ClientConfig.mof".</span><span class="sxs-lookup"><span data-stu-id="a8784-127">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="a8784-128">Para obter mais informações, consulte [configurações de publicação de mensagens em fila para um servidor de solicitação (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="a8784-128">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="a8784-129">Configurar um cliente de solicitação para transferir configurações</span><span class="sxs-lookup"><span data-stu-id="a8784-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="a8784-130">Cada cliente tem de ser configurada no **Pull** modo e tendo em conta o url do servidor pull onde está armazenada a respetiva configuração.</span><span class="sxs-lookup"><span data-stu-id="a8784-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="a8784-131">Para tal, tem de configurar o Gestor de configuração Local (LCM) com as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="a8784-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="a8784-132">Para configurar o LCM, cria um tipo especial de configuração, decorada com o **dsclocalconfigurationmanager para** atributo.</span><span class="sxs-lookup"><span data-stu-id="a8784-132">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="a8784-133">Para obter mais informações sobre como configurar o LCM, consulte [configurar o Gestor de configuração Local](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="a8784-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="a8784-134">O script a seguir configura o LCM para configurações de solicitação de um servidor com o nome "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="a8784-134">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="a8784-135">No script, o **ConfigurationRepositoryWeb** bloco define o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="a8784-135">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="a8784-136">O **ServerURL** propriedade especifica o ponto final para o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="a8784-136">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="a8784-137">O **RegistrationKey** propriedade é uma chave partilhada entre todos os nós de cliente para um servidor de solicitação e esse servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="a8784-137">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="a8784-138">O mesmo valor é armazenado num arquivo no servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="a8784-138">The same value is stored in a file on the pull server.</span></span>
  > <span data-ttu-id="a8784-139">**Tenha em atenção**: As chaves de registo só funcionam com o **web** extrair servidores.</span><span class="sxs-lookup"><span data-stu-id="a8784-139">**Note**: Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="a8784-140">Ainda tem de utilizar **ConfigurationID** com um **SMB** servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="a8784-140">You must still use **ConfigurationID** with an **SMB** pull server.</span></span>
  > <span data-ttu-id="a8784-141">Para obter informações sobre como configurar um servidor de solicitação usando **ConfigurationID**, consulte [como configurar um cliente de solicitação através do ID de configuração](pullClientConfigId.md)</span><span class="sxs-lookup"><span data-stu-id="a8784-141">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="a8784-142">O **ConfigurationNames** propriedade é uma matriz que especifica os nomes das configurações se destina o nó de cliente.</span><span class="sxs-lookup"><span data-stu-id="a8784-142">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
  ><span data-ttu-id="a8784-143">**Nota:** Se especificar mais do que um valor no **ConfigurationNames**, também tem de especificar **PartialConfiguration** bloqueia na sua configuração.</span><span class="sxs-lookup"><span data-stu-id="a8784-143">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
  ><span data-ttu-id="a8784-144">Para obter informações sobre configurações parciais, consulte [configurações parciais de PowerShell Desired State Configuration](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="a8784-144">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

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

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="a8784-145">Configurar um cliente extrair para recursos de download</span><span class="sxs-lookup"><span data-stu-id="a8784-145">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="a8784-146">Se especificar apenas uma **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** bloco na sua configuração de LCM (como no exemplo anterior), irá fazer com que o cliente de solicitação recursos a partir do mesmo localização onde estão armazenados os ficheiros de ". MOF".</span><span class="sxs-lookup"><span data-stu-id="a8784-146">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="a8784-147">Também pode especificar diferentes localizações onde os clientes podem transferir recursos.</span><span class="sxs-lookup"><span data-stu-id="a8784-147">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="a8784-148">Para especificar um servidor de recurso, a utilização de uma um **ResourceRepositoryWeb** (para um servidor de solicitação da web) ou uma **ResourceRepositoryShare** bloco (para um servidor de solicitação SMB).</span><span class="sxs-lookup"><span data-stu-id="a8784-148">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="a8784-149">O exemplo seguinte mostra um metaconfiguration que configura um cliente para transferir configurações a partir de um servidor de solicitação e recursos a partir de uma partilha SMB.</span><span class="sxs-lookup"><span data-stu-id="a8784-149">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

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

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="a8784-150">Configurar um cliente de solicitação para comunicar o Estado</span><span class="sxs-lookup"><span data-stu-id="a8784-150">Set up a Pull Client to report status</span></span>

<span data-ttu-id="a8784-151">Pode utilizar um servidor de solicitação única para configurações, recursos e geração de relatórios.</span><span class="sxs-lookup"><span data-stu-id="a8784-151">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="a8784-152">Geração de relatórios não está configurada para os clientes por predefinição.</span><span class="sxs-lookup"><span data-stu-id="a8784-152">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="a8784-153">Para configurar um cliente para comunicar o estado, tem de criar uma **ReportRepositoryWeb** bloco.</span><span class="sxs-lookup"><span data-stu-id="a8784-153">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="a8784-154">O exemplo seguinte mostra um metaconfiguration que configura um cliente pull configurações e recursos e enviar relatórios de dados, para um servidor de solicitação única.</span><span class="sxs-lookup"><span data-stu-id="a8784-154">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="a8784-155">Um servidor de relatórios não pode ser uma partilha SMB.</span><span class="sxs-lookup"><span data-stu-id="a8784-155">A report server cannot be an SMB share.</span></span>

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
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="a8784-156">Veja Também</span><span class="sxs-lookup"><span data-stu-id="a8784-156">See Also</span></span>

* [<span data-ttu-id="a8784-157">Como configurar um cliente de solicitação com o ID de configuração</span><span class="sxs-lookup"><span data-stu-id="a8784-157">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="a8784-158">Como configurar um servidor de solicitação da web de DSC</span><span class="sxs-lookup"><span data-stu-id="a8784-158">Setting up a DSC web pull server</span></span>](pullServer.md)
