---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Configurar um cliente de solicitação através de IDs de configuração
ms.openlocfilehash: 93e533fd4e729e1af0124ad69ca7e384e1cb3aa4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a><span data-ttu-id="f3228-103">Configurar um cliente de solicitação através de IDs de configuração</span><span class="sxs-lookup"><span data-stu-id="f3228-103">Setting up a pull client using configuration ID</span></span>

> <span data-ttu-id="f3228-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f3228-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="f3228-105">Cada nó de destino tem de ser disse para utilizar o modo de extração e dado o URL onde pode contactar o servidor de solicitação para obter as configurações.</span><span class="sxs-lookup"><span data-stu-id="f3228-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="f3228-106">Para tal, tem de configurar o Gestor de configuração Local (MMC) com as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="f3228-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="f3228-107">Para configurar o MMC, cria um tipo especial de configuração, decorado com o **DSCLocalConfigurationManager** atributo.</span><span class="sxs-lookup"><span data-stu-id="f3228-107">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="f3228-108">Para obter mais informações sobre como configurar o MMC, consulte [configurar o Gestor de configuração Local](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="f3228-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="f3228-109">**Tenha em atenção**: Este tópico aplica-se ao PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="f3228-109">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="f3228-110">Para obter informações sobre como configurar um cliente de solicitação no PowerShell 4.0, consulte [configurar um cliente de extração com o ID de configuração no PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="f3228-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="f3228-111">O script seguinte configura o MMC para as configurações de solicitação de um servidor com o nome "CONTOSO-PullSrv".</span><span class="sxs-lookup"><span data-stu-id="f3228-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="f3228-112">O script, o **ConfigurationRepositoryWeb** bloco define o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="f3228-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="f3228-113">O **ServerURL**</span><span class="sxs-lookup"><span data-stu-id="f3228-113">The **ServerURL**</span></span>

<span data-ttu-id="f3228-114">Depois deste script é executado, cria uma nova pasta de saída com o nome **PullClientConfigID** e coloca não existe um ficheiro MOF de configuração meta.</span><span class="sxs-lookup"><span data-stu-id="f3228-114">After this script runs, it creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="f3228-115">Neste caso, o ficheiro MOF de configuração meta será designado `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="f3228-115">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="f3228-116">Para aplicar a configuração, chame o **conjunto DscLocalConfigurationManager** cmdlet, com o **caminho** definido para a localização do ficheiro MOF configuração meta.</span><span class="sxs-lookup"><span data-stu-id="f3228-116">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="f3228-117">Por exemplo: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span><span class="sxs-lookup"><span data-stu-id="f3228-117">For example: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span></span>

## <a name="configuration-id"></a><span data-ttu-id="f3228-118">ID de configuração</span><span class="sxs-lookup"><span data-stu-id="f3228-118">Configuration ID</span></span>

<span data-ttu-id="f3228-119">Os conjuntos de script a **ConfigurationID** propriedade da MMC para um GUID que tinha de ser criado previamente para esta finalidade (pode criar um GUID, utilizando o **novo Guid** cmdlet).</span><span class="sxs-lookup"><span data-stu-id="f3228-119">The script sets the **ConfigurationID** property of LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="f3228-120">O **ConfigurationID** é o que utiliza o MMC para encontrar a configuração adequada no servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="f3228-120">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="f3228-121">O ficheiro MOF de configuração no servidor de solicitação deve ter o nome _ConfigurationID_. MOF, onde _ConfigurationID_ valor o **ConfigurationID** propriedade de destino MMC do nó.</span><span class="sxs-lookup"><span data-stu-id="f3228-121">The configuration MOF file on the pull server must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="smb-pull-server"></a><span data-ttu-id="f3228-122">Servidor de solicitação SMB</span><span class="sxs-lookup"><span data-stu-id="f3228-122">SMB pull server</span></span>

<span data-ttu-id="f3228-123">Para configurar um cliente para as configurações de solicitação de um servidor do SMB, utilize um **ConfigurationRepositoryShare** bloco.</span><span class="sxs-lookup"><span data-stu-id="f3228-123">To set up a client to pull configurations from an SMB server, use a **ConfigurationRepositoryShare** block.</span></span> <span data-ttu-id="f3228-124">Num **ConfigurationRepositoryShare** bloco, especifique o caminho para o servidor, definindo o **SourcePath** propriedade.</span><span class="sxs-lookup"><span data-stu-id="f3228-124">In a **ConfigurationRepositoryShare** block, you specify the path to the server by setting the **SourcePath** property.</span></span> <span data-ttu-id="f3228-125">A configuração meta do seguinte configura o nó de destino para solicitar a partir de um servidor de solicitação SMB denominado **SMBPullServer**.</span><span class="sxs-lookup"><span data-stu-id="f3228-125">The following metaconfiguration configures the target node to pull from an SMB pull server named **SMBPullServer**.</span></span>

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

## <a name="resource-and-report-servers"></a><span data-ttu-id="f3228-126">Servidores de recursos e o relatório</span><span class="sxs-lookup"><span data-stu-id="f3228-126">Resource and report servers</span></span>

<span data-ttu-id="f3228-127">Se especificar apenas um **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** bloquear na configuração da MMC (do exemplo anterior), o cliente de solicitação irá solicitar recursos a partir de servidor especificado, mas não enviarão relatórios ao mesmo.</span><span class="sxs-lookup"><span data-stu-id="f3228-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span> <span data-ttu-id="f3228-128">Pode utilizar um servidor de solicitação único para configurações, recursos e relatórios, mas tem de criar um **ReportRepositoryWeb** bloco para configurar o Reporting Services.</span><span class="sxs-lookup"><span data-stu-id="f3228-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

<span data-ttu-id="f3228-129">O exemplo seguinte mostra uma configuração meta do que configura um cliente para enviar relatórios de dados, para um servidor de solicitação único e recursos e configurações de extração.</span><span class="sxs-lookup"><span data-stu-id="f3228-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="f3228-130">Também pode especificar os servidores de extração diferente para recursos e relatórios.</span><span class="sxs-lookup"><span data-stu-id="f3228-130">You can also specify different pull servers for resources and reporting.</span></span> <span data-ttu-id="f3228-131">Para especificar um servidor de recurso, a utilização de uma um **ResourceRepositoryWeb** (para um servidor de solicitação web) ou um **ResourceRepositoryShare** blocos (por um servidor de solicitação SMB).</span><span class="sxs-lookup"><span data-stu-id="f3228-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="f3228-132">Para especificar um servidor de relatórios, pode utilizar um **ReportRepositoryWeb** bloco.</span><span class="sxs-lookup"><span data-stu-id="f3228-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="f3228-133">Um servidor de relatórios não pode ser um servidor do SMB.</span><span class="sxs-lookup"><span data-stu-id="f3228-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="f3228-134">A configuração meta do seguinte configura uma solicitação de cliente para obter as respetivas configurações de **CONTOSO PullSrv** e respetivos recursos da **CONTOSO ResourceSrv**e para enviar relatórios de estado para  **CONTOSO ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="f3228-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f3228-135">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="f3228-135">See Also</span></span>

* [<span data-ttu-id="f3228-136">Configurar um cliente de extração com nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="f3228-136">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)