---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Configurar um cliente de solicitação com IDs de configuração no PowerShell 4.0
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405277"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a><span data-ttu-id="21077-103">Configurar um cliente de solicitação com IDs de configuração no PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="21077-103">Set up a Pull Client using Configuration IDs in PowerShell 4.0</span></span>

><span data-ttu-id="21077-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="21077-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="21077-105">O servidor de solicitação (recurso do Windows *DSC-serviço*) é um componente suportado do Windows Server no entanto, não existem planos para oferecer novas funcionalidades ou capacidades.</span><span class="sxs-lookup"><span data-stu-id="21077-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="21077-106">É recomendado para começar a fazer a transição geridos os clientes [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação de mensagens em fila no Windows Server) ou uma das soluções da Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="21077-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="21077-107">Antes de configurar um cliente de solicitação, deve configurar um servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="21077-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="21077-108">Embora esta ordem não é necessária, ele ajuda na resolução de problemas e ajuda a garantir que o registo foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="21077-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="21077-109">Para configurar um servidor de solicitação, pode usar os seguintes guias:</span><span class="sxs-lookup"><span data-stu-id="21077-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="21077-110">Configurar um servidor de solicitação de SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="21077-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="21077-111">Configurar um servidor de solicitação de HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="21077-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="21077-112">Cada nó de destino pode ser configurado para transferir configurações, recursos e até mesmo comunicou o seu estado.</span><span class="sxs-lookup"><span data-stu-id="21077-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="21077-113">As secções abaixo mostram-lhe como configurar um cliente de solicitação com uma partilha SMB ou o servidor de solicitação de DSC de HTTP.</span><span class="sxs-lookup"><span data-stu-id="21077-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="21077-114">Quando atualiza LCM o nó, será contactado por para a localização configurada para transferir quaisquer configurações atribuídas.</span><span class="sxs-lookup"><span data-stu-id="21077-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="21077-115">Se não existirem quaisquer recursos necessários no nó, será transferida-los automaticamente na localização de configurado.</span><span class="sxs-lookup"><span data-stu-id="21077-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="21077-116">Se o nó está configurado com um [Report Server](reportServer.md), em seguida, esse irá comunicar o estado da operação.</span><span class="sxs-lookup"><span data-stu-id="21077-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="21077-117">Configurar o cliente de solicitação LCM</span><span class="sxs-lookup"><span data-stu-id="21077-117">Configure the pull client LCM</span></span>

<span data-ttu-id="21077-118">Executar qualquer um dos exemplos abaixo cria uma nova pasta de saída com o nome **PullClientConfigID** e coloca um ficheiro MOF de metaconfiguration lá.</span><span class="sxs-lookup"><span data-stu-id="21077-118">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="21077-119">Neste caso, o ficheiro MOF de metaconfiguration será denominado `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="21077-119">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="21077-120">Para aplicar a configuração, chame o **Set-dsclocalconfigurationmanager para** cmdlet, com o **caminho** definido para a localização do ficheiro MOF metaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="21077-120">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="21077-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="21077-121">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="21077-122">ID de configuração</span><span class="sxs-lookup"><span data-stu-id="21077-122">Configuration ID</span></span>

<span data-ttu-id="21077-123">Os exemplos abaixo conjunto a **ConfigurationID** propriedade do MMC para um **Guid** que haviam sido criados anteriormente para esta finalidade.</span><span class="sxs-lookup"><span data-stu-id="21077-123">The examples below set the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="21077-124">O **ConfigurationID** é o que o LCM utiliza para encontrar a configuração adequada no servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="21077-124">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="21077-125">O ficheiro MOF de configuração no servidor de solicitação deve ser nomeado `ConfigurationID.mof`, onde *ConfigurationID* é o valor da **ConfigurationID** propriedade do LCM o nó de destino.</span><span class="sxs-lookup"><span data-stu-id="21077-125">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="21077-126">Para obter mais informações, consulte [configurações de publicação de mensagens em fila para um servidor de solicitação (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="21077-126">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="21077-127">Pode criar um aleatório **Guid** usando o exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="21077-127">You can create a random **Guid** using the example below.</span></span>

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="21077-128">Configurar um cliente de solicitação para transferir configurações</span><span class="sxs-lookup"><span data-stu-id="21077-128">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="21077-129">Cada cliente tem de ser configurada no **Pull** modo e tendo em conta o url do servidor pull onde está armazenada a respetiva configuração.</span><span class="sxs-lookup"><span data-stu-id="21077-129">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="21077-130">Para tal, tem de configurar o Gestor de configuração Local (LCM) com as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="21077-130">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="21077-131">Para configurar o LCM, cria um tipo especial de configuração, com um **LocalConfigurationManager** bloco.</span><span class="sxs-lookup"><span data-stu-id="21077-131">To configure the LCM, you create a special type of configuration, with a **LocalConfigurationManager** block.</span></span> <span data-ttu-id="21077-132">Para obter mais informações sobre como configurar o LCM, consulte [configurar o Gestor de configuração Local](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="21077-132">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md).</span></span>

## <a name="http-dsc-pull-server"></a><span data-ttu-id="21077-133">Servidor de solicitação de DSC de HTTP</span><span class="sxs-lookup"><span data-stu-id="21077-133">HTTP DSC Pull Server</span></span>

<span data-ttu-id="21077-134">Se o servidor de solicitação é configurado como um serviço web, defina o **DownloadManagerName** ao **WebDownloadManager**.</span><span class="sxs-lookup"><span data-stu-id="21077-134">If the pull server is set up as a web service, you set the **DownloadManagerName** to **WebDownloadManager**.</span></span> <span data-ttu-id="21077-135">O **WebDownloadManager** exige a especificação de um **ServerUrl** para o **DownloadManagerCustomData** chave.</span><span class="sxs-lookup"><span data-stu-id="21077-135">The **WebDownloadManager** requires that you specify a **ServerUrl** to the **DownloadManagerCustomData** key.</span></span> <span data-ttu-id="21077-136">Também pode especificar um valor para **AllowUnsecureConnection**, como no exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="21077-136">You can also specify a value for **AllowUnsecureConnection**, as in the example below.</span></span> <span data-ttu-id="21077-137">O script a seguir configura o LCM para configurações de solicitação de um servidor com o nome "PullServer".</span><span class="sxs-lookup"><span data-stu-id="21077-137">The following script configures the LCM to pull configurations from a server named "PullServer".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a><span data-ttu-id="21077-138">Partilha SMB</span><span class="sxs-lookup"><span data-stu-id="21077-138">SMB Share</span></span>

<span data-ttu-id="21077-139">Se o servidor de solicitação é configurado como uma partilha de ficheiros SMB, em vez de um serviço da web, é definir os **DownloadManagerName** ao **DscFileDownloadManager** em vez do **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="21077-139">If the pull server is set up as an SMB file share, rather than a web service, you set the **DownloadManagerName** to **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span> <span data-ttu-id="21077-140">O **DscFileDownloadManager** exige a especificação de um **SourcePath** propriedade no **DownloadManagerCustomData**.</span><span class="sxs-lookup"><span data-stu-id="21077-140">The **DscFileDownloadManager** requires that you specify a **SourcePath** property in the **DownloadManagerCustomData**.</span></span> <span data-ttu-id="21077-141">O script seguinte configura o LCM para solicitar configurações a partir de uma partilha SMB com o nome "SmbDscShare" num servidor com o nome "CONTOSO-SERVER".</span><span class="sxs-lookup"><span data-stu-id="21077-141">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a><span data-ttu-id="21077-142">Próximos Passos</span><span class="sxs-lookup"><span data-stu-id="21077-142">Next Steps</span></span>

<span data-ttu-id="21077-143">Depois de configurar o cliente de solicitação, pode utilizar os seguintes guias para realizar os passos seguintes:</span><span class="sxs-lookup"><span data-stu-id="21077-143">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="21077-144">Publicar as configurações para um servidor de solicitação (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="21077-144">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="21077-145">Pacote e o carregamento de recursos para um servidor de solicitação (v4)</span><span class="sxs-lookup"><span data-stu-id="21077-145">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="21077-146">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="21077-146">See Also</span></span>

- [<span data-ttu-id="21077-147">Configurar um servidor de solicitação da web de DSC</span><span class="sxs-lookup"><span data-stu-id="21077-147">Set up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="21077-148">Configurar um servidor de solicitação SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="21077-148">Set up a DSC SMB pull server</span></span>](pullServerSMB.md)
