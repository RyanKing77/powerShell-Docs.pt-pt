---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Configurar um cliente de extração com o ID de configuração no PowerShell 4.0
ms.openlocfilehash: f9bea92f1a2dce94792d72e03bef884d2729f3c0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a><span data-ttu-id="47517-103">Configurar um cliente de extração com o ID de configuração no PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="47517-103">Setting up a pull client using configuration ID in PowerShell 4.0</span></span>

><span data-ttu-id="47517-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="47517-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="47517-105">Cada nó de destino tem de ser disse para utilizar o modo de extração e dado o URL onde pode contactar o servidor de solicitação para obter as configurações.</span><span class="sxs-lookup"><span data-stu-id="47517-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="47517-106">Para tal, tem de configurar o Gestor de configuração Local (MMC) com as informações necessárias.</span><span class="sxs-lookup"><span data-stu-id="47517-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="47517-107">Para configurar o MMC, cria um tipo especial de configuração conhecido como uma "configuração meta do".</span><span class="sxs-lookup"><span data-stu-id="47517-107">To configure the LCM, you create a special type of configuration known as a "metaconfiguration".</span></span> <span data-ttu-id="47517-108">Para obter mais informações sobre como configurar o MMC, consulte [Windows PowerShell 4.0 pretendido estado de configuração Local do Configuration Manager](metaConfig4.md)</span><span class="sxs-lookup"><span data-stu-id="47517-108">For more information about configuring the LCM, see [Windows PowerShell 4.0 Desired State Configuration Local Configuration Manager](metaConfig4.md)</span></span>

<span data-ttu-id="47517-109">O script seguinte configura o MMC para as configurações de solicitação de um servidor com o nome "PullServer":</span><span class="sxs-lookup"><span data-stu-id="47517-109">The following script configures the LCM to pull configurations from a server named "PullServer":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

<span data-ttu-id="47517-110">O script, **DownloadManagerCustomData** transmite o URL do servidor de solicitação e (para este exemplo) permite uma ligação segura.</span><span class="sxs-lookup"><span data-stu-id="47517-110">In the script, **DownloadManagerCustomData** passes the URL of the pull server and (for this example) allows an unsecured connection.</span></span>

<span data-ttu-id="47517-111">Depois deste script é executado, cria uma nova pasta de saída designada **SimpleMetaConfigurationForPull** e coloca não existe um ficheiro MOF de configuração meta.</span><span class="sxs-lookup"><span data-stu-id="47517-111">After this script runs, it creates a new output folder called **SimpleMetaConfigurationForPull** and puts a metaconfiguration MOF file there.</span></span>

<span data-ttu-id="47517-112">Para aplicar a configuração, utilize **conjunto DscLocalConfigurationManager** com parâmetros **ComputerName** (utilize "localhost") e **caminho** (o caminho para a localização do destino de ficheiro de localhost.meta.mof deste nó).</span><span class="sxs-lookup"><span data-stu-id="47517-112">To apply the configuration, use **Set-DscLocalConfigurationManager** with parameters for **ComputerName** (use “localhost”) and **Path** (the path to the location of the target node’s localhost.meta.mof file).</span></span> <span data-ttu-id="47517-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="47517-113">For example:</span></span>
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="47517-114">ID de configuração</span><span class="sxs-lookup"><span data-stu-id="47517-114">Configuration ID</span></span>
<span data-ttu-id="47517-115">Os conjuntos de script a **ConfigurationID** propriedade da MMC como um GUID que tinha de ser criado previamente para esta finalidade (pode criar um GUID, utilizando o **novo Guid** cmdlet).</span><span class="sxs-lookup"><span data-stu-id="47517-115">The script sets the **ConfigurationID** property of the LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="47517-116">O **ConfigurationID** é o que utiliza o MMC para encontrar a configuração adequada no servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="47517-116">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="47517-117">O ficheiro MOF de configuração no servidor de solicitação deve ter o nome `ConfigurationID.mof`, onde *ConfigurationID* valor o **ConfigurationID** propriedade do MMC do nó de destino.</span><span class="sxs-lookup"><span data-stu-id="47517-117">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="pulling-from-an-smb-server"></a><span data-ttu-id="47517-118">Extrair a partir de um servidor do SMB</span><span class="sxs-lookup"><span data-stu-id="47517-118">Pulling from an SMB server</span></span>

<span data-ttu-id="47517-119">Se o servidor de solicitação está configurado como uma partilha de ficheiros SMB, em vez de um serviço web, especifique o **DscFileDownloadManager** em vez do **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="47517-119">If the pull server is set up as an SMB file share, rather than a web service, you specify the **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span>
<span data-ttu-id="47517-120">O **DscFileDownloadManager** demora um **SourcePath** propriedade em vez de **ServerUrl**.</span><span class="sxs-lookup"><span data-stu-id="47517-120">The **DscFileDownloadManager** takes a **SourcePath** property instead of **ServerUrl**.</span></span> <span data-ttu-id="47517-121">O script seguinte configura o MMC para solicitar as configurações de partilha SMB com o nome "SmbDscShare" num servidor com o nome "CONTOSO-SERVER":</span><span class="sxs-lookup"><span data-stu-id="47517-121">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a><span data-ttu-id="47517-122">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="47517-122">See Also</span></span>

- [<span data-ttu-id="47517-123">Configurar um servidor de solicitação do DSC web</span><span class="sxs-lookup"><span data-stu-id="47517-123">Setting up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="47517-124">Configurar um servidor de solicitação SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="47517-124">Setting up a DSC SMB pull server</span></span>](pullServerSMB.md)