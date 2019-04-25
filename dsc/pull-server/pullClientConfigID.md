---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Configurar um cliente de solicitação através de IDs de configuração no PowerShell 5.0 e posterior
ms.openlocfilehash: 14db98d240bc87aca3ee985db08c14b7c65d8bb8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079494"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="515fa-103">Configurar um cliente de solicitação através de IDs de configuração no PowerShell 5.0 e posterior</span><span class="sxs-lookup"><span data-stu-id="515fa-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="515fa-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="515fa-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="515fa-105">O servidor de solicitação (recurso do Windows *DSC-serviço*) é um componente suportado do Windows Server no entanto, não existem planos para oferecer novas funcionalidades ou capacidades.</span><span class="sxs-lookup"><span data-stu-id="515fa-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="515fa-106">É recomendado para começar a fazer a transição geridos os clientes [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação de mensagens em fila no Windows Server) ou uma das soluções da Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="515fa-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="515fa-107">Antes de configurar um cliente de solicitação, deve configurar um servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="515fa-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="515fa-108">Embora esta ordem não é necessária, ele ajuda na resolução de problemas e ajuda a garantir que o registo foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="515fa-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="515fa-109">Para configurar um servidor de solicitação, pode usar os seguintes guias:</span><span class="sxs-lookup"><span data-stu-id="515fa-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="515fa-110">Configurar um servidor de solicitação de SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="515fa-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="515fa-111">Configurar um servidor de solicitação de HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="515fa-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="515fa-112">Cada nó de destino pode ser configurado para transferir configurações, recursos e até mesmo comunicou o seu estado.</span><span class="sxs-lookup"><span data-stu-id="515fa-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="515fa-113">As secções abaixo mostram-lhe como configurar um cliente de solicitação com uma partilha SMB ou o servidor de solicitação de DSC de HTTP.</span><span class="sxs-lookup"><span data-stu-id="515fa-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="515fa-114">Quando atualiza LCM o nó, será contactado por para a localização configurada para transferir quaisquer configurações atribuídas.</span><span class="sxs-lookup"><span data-stu-id="515fa-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="515fa-115">Se não existirem quaisquer recursos necessários no nó, será transferida-los automaticamente na localização de configurado.</span><span class="sxs-lookup"><span data-stu-id="515fa-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="515fa-116">Se o nó está configurado com um [Report Server](reportServer.md), em seguida, esse irá comunicar o estado da operação.</span><span class="sxs-lookup"><span data-stu-id="515fa-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="515fa-117">Este tópico aplica-se para PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="515fa-117">This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="515fa-118">Para obter informações sobre como configurar um cliente de solicitação no PowerShell 4.0, consulte [como configurar um cliente de solicitação com o ID de configuração no PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="515fa-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="515fa-119">Configurar o cliente de solicitação LCM</span><span class="sxs-lookup"><span data-stu-id="515fa-119">Configure the pull client LCM</span></span>

<span data-ttu-id="515fa-120">Executar qualquer um dos exemplos abaixo cria uma nova pasta de saída com o nome **PullClientConfigID** e coloca um ficheiro MOF de metaconfiguration lá.</span><span class="sxs-lookup"><span data-stu-id="515fa-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="515fa-121">Neste caso, o ficheiro MOF de metaconfiguration será denominado `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="515fa-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="515fa-122">Para aplicar a configuração, chame o **Set-dsclocalconfigurationmanager para** cmdlet, com o **caminho** definido para a localização do ficheiro MOF metaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="515fa-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="515fa-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="515fa-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="515fa-124">ID de configuração</span><span class="sxs-lookup"><span data-stu-id="515fa-124">Configuration ID</span></span>

<span data-ttu-id="515fa-125">Os exemplos abaixo conjuntos a **ConfigurationID** propriedade do MMC para um **Guid** que haviam sido criados anteriormente para esta finalidade.</span><span class="sxs-lookup"><span data-stu-id="515fa-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="515fa-126">O **ConfigurationID** é o que o LCM utiliza para encontrar a configuração adequada no servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="515fa-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="515fa-127">O ficheiro MOF de configuração no servidor de solicitação deve ser nomeado `ConfigurationID.mof`, onde *ConfigurationID* é o valor da **ConfigurationID** propriedade do LCM o nó de destino.</span><span class="sxs-lookup"><span data-stu-id="515fa-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="515fa-128">Para obter mais informações, consulte [configurações de publicação de mensagens em fila para um servidor de solicitação (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="515fa-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="515fa-129">Pode criar um aleatório **Guid** usando o exemplo abaixo, ou utilizando o [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="515fa-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="515fa-130">Para obter mais informações sobre como utilizar **Guids** no seu ambiente, consulte [planear Guids](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="515fa-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="515fa-131">Configurar um cliente de solicitação para transferir configurações</span><span class="sxs-lookup"><span data-stu-id="515fa-131">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="515fa-132">Cada cliente tem de ser configurada no **Pull** modo e tendo em conta o url do servidor pull onde está armazenada a respetiva configuração.</span><span class="sxs-lookup"><span data-stu-id="515fa-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="515fa-133">Para tal, tem de configurar o Gestor de configuração Local (LCM) com as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="515fa-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="515fa-134">Para configurar o LCM, cria um tipo especial de configuração, decorada com o **dsclocalconfigurationmanager para** atributo.</span><span class="sxs-lookup"><span data-stu-id="515fa-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="515fa-135">Para obter mais informações sobre como configurar o LCM, consulte [configurar o Gestor de configuração Local](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="515fa-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="515fa-136">Servidor de solicitação de DSC de HTTP</span><span class="sxs-lookup"><span data-stu-id="515fa-136">HTTP DSC Pull Server</span></span>

<span data-ttu-id="515fa-137">O script a seguir configura o LCM para configurações de solicitação de um servidor com o nome "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="515fa-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="515fa-138">No script, o **ConfigurationRepositoryWeb** bloco define o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="515fa-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="515fa-139">O **ServerUrl** Especifica o url de solicitação do DSC</span><span class="sxs-lookup"><span data-stu-id="515fa-139">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="515fa-140">Partilha SMB</span><span class="sxs-lookup"><span data-stu-id="515fa-140">SMB Share</span></span>

<span data-ttu-id="515fa-141">O script a seguir configura o LCM para configurações de solicitação da partilha de SMB `\\SMBPullServer\Pull`.</span><span class="sxs-lookup"><span data-stu-id="515fa-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

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
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="515fa-142">No script, o **ConfigurationRepositoryShare** bloco define o servidor de solicitação, que neste caso, é apenas uma partilha SMB.</span><span class="sxs-lookup"><span data-stu-id="515fa-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="515fa-143">Configurar um cliente extrair para recursos de download</span><span class="sxs-lookup"><span data-stu-id="515fa-143">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="515fa-144">Se especificar apenas o **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** bloco na sua configuração de LCM (como nos exemplos anteriores), irá fazer com que o cliente de solicitação recursos a partir da mesma localização obtém suas configurações.</span><span class="sxs-lookup"><span data-stu-id="515fa-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="515fa-145">Também é possível especificar localizações separadas para recursos.</span><span class="sxs-lookup"><span data-stu-id="515fa-145">You can also specify separate locations for resources.</span></span> <span data-ttu-id="515fa-146">Para especificar uma localização de recursos como um servidor separado, utilize o **ResourceRepositoryWeb** bloco.</span><span class="sxs-lookup"><span data-stu-id="515fa-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="515fa-147">Para especificar uma localização de recursos como uma partilha de SMB, utilize o **ResourceRepositoryShare** bloco.</span><span class="sxs-lookup"><span data-stu-id="515fa-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="515fa-148">Pode combinar **ConfigurationRepositoryWeb** com **ResourceRepositoryShare** ou **ConfigurationRepositoryShare** com **ResourceRepositoryWeb** .</span><span class="sxs-lookup"><span data-stu-id="515fa-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="515fa-149">Exemplos disso não são apresentados abaixo.</span><span class="sxs-lookup"><span data-stu-id="515fa-149">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="515fa-150">Servidor de solicitação de DSC de HTTP</span><span class="sxs-lookup"><span data-stu-id="515fa-150">HTTP DSC Pull Server</span></span>

<span data-ttu-id="515fa-151">O metaconfiguration seguinte configura um cliente de solicitação para obter configurações a partir **CONTOSO-PullSrv** e os respetivos recursos da **CONTOSO-ResourceSrv**.</span><span class="sxs-lookup"><span data-stu-id="515fa-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

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
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="515fa-152">Partilha SMB</span><span class="sxs-lookup"><span data-stu-id="515fa-152">SMB Share</span></span>

<span data-ttu-id="515fa-153">O exemplo seguinte mostra um metaconfiguration que configura um cliente para as configurações de solicitação da partilha de SMB `\\SMBPullServer\Configurations`e os recursos da partilha SMB `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="515fa-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

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
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="515fa-154">Transferir automaticamente os recursos no modo de Push</span><span class="sxs-lookup"><span data-stu-id="515fa-154">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="515fa-155">A partir do PowerShell 5.0, seus clientes de solicitação podem transferir módulos da partilha de SMB, mesmo quando estão configurados para **Push** modo.</span><span class="sxs-lookup"><span data-stu-id="515fa-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="515fa-156">Isso é especialmente útil em cenários onde não pretende configurar um servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="515fa-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="515fa-157">O **ResourceRepositoryShare** block pode ser usado sem especificar um **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="515fa-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="515fa-158">O exemplo seguinte mostra um metaconfiguration que configura um cliente para receber recursos de uma partilha SMB `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="515fa-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="515fa-159">Quando o nó está **PUSHED** uma configuração, ele irá transferir automaticamente todos os recursos necessários, da partilha especificada.</span><span class="sxs-lookup"><span data-stu-id="515fa-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="515fa-160">Configurar um cliente de solicitação para comunicar o Estado</span><span class="sxs-lookup"><span data-stu-id="515fa-160">Set up a Pull Client to report status</span></span>

<span data-ttu-id="515fa-161">Por predefinição, nós não enviarão relatórios para um servidor de solicitação configurado.</span><span class="sxs-lookup"><span data-stu-id="515fa-161">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="515fa-162">Pode utilizar um servidor de solicitação única para configurações, recursos e geração de relatórios, mas tem de criar uma **ReportRepositoryWeb** bloco para configurar os relatórios.</span><span class="sxs-lookup"><span data-stu-id="515fa-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="515fa-163">Servidor de solicitação de DSC de HTTP</span><span class="sxs-lookup"><span data-stu-id="515fa-163">HTTP DSC Pull Server</span></span>

<span data-ttu-id="515fa-164">O exemplo seguinte mostra um metaconfiguration que configura um cliente pull configurações e recursos e enviar relatórios de dados, para um servidor de solicitação única.</span><span class="sxs-lookup"><span data-stu-id="515fa-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="515fa-165">Para especificar um servidor de relatórios, utilize um **ReportRepositoryWeb** bloco.</span><span class="sxs-lookup"><span data-stu-id="515fa-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="515fa-166">Um servidor de relatórios não pode ser um servidor do SMB.</span><span class="sxs-lookup"><span data-stu-id="515fa-166">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="515fa-167">O metaconfiguration seguinte configura um cliente de solicitação para obter configurações a partir de **CONTOSO-PullSrv** e os respetivos recursos da **CONTOSO-ResourceSrv**e para enviar relatórios de estado para  **CONTOSO-ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="515fa-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="515fa-168">Partilha SMB</span><span class="sxs-lookup"><span data-stu-id="515fa-168">SMB Share</span></span>

<span data-ttu-id="515fa-169">Um servidor de relatórios não pode ser uma partilha SMB.</span><span class="sxs-lookup"><span data-stu-id="515fa-169">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="515fa-170">Próximos Passos</span><span class="sxs-lookup"><span data-stu-id="515fa-170">Next Steps</span></span>

<span data-ttu-id="515fa-171">Depois de configurar o cliente de solicitação, pode utilizar os seguintes guias para realizar os passos seguintes:</span><span class="sxs-lookup"><span data-stu-id="515fa-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="515fa-172">Publicar as configurações para um servidor de solicitação (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="515fa-172">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="515fa-173">Pacote e o carregamento de recursos para um servidor de solicitação (v4)</span><span class="sxs-lookup"><span data-stu-id="515fa-173">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="515fa-174">Veja Também</span><span class="sxs-lookup"><span data-stu-id="515fa-174">See Also</span></span>

* [<span data-ttu-id="515fa-175">Como configurar um cliente de solicitação com nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="515fa-175">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
