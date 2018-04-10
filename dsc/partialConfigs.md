---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Configurações de parciais de configuração de estado pretendido do PowerShell
ms.openlocfilehash: cd2812724c2279a7effc4739f23193c1dc836ce5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="4b003-103">Configurações de parciais de configuração de estado pretendido do PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b003-103">PowerShell Desired State Configuration partial configurations</span></span>

><span data-ttu-id="4b003-104">Aplica-se a: Windows PowerShell 5.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="4b003-104">Applies To: Windows PowerShell 5.0 and later.</span></span>

<span data-ttu-id="4b003-105">No PowerShell 5.0, configuração de estado pretendido (DSC) permite que as configurações ser entregue no fragmentos e de várias origens.</span><span class="sxs-lookup"><span data-stu-id="4b003-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="4b003-106">O Gestor de configuração Local (MMC) no nó de destino coloca os fragmentos em conjunto antes de aplicá-las como uma configuração única.</span><span class="sxs-lookup"><span data-stu-id="4b003-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="4b003-107">Esta capacidade permite a partilha de controlo da configuração entre equipas ou indivíduos.</span><span class="sxs-lookup"><span data-stu-id="4b003-107">This capability allows sharing control of configuration between teams or individuals.</span></span>
<span data-ttu-id="4b003-108">Por exemplo, se duas ou mais agrupamentos de programadores estiverem a colaborar num serviço, poderá cada pretendem criar configurações para gerir os respetivos parte do serviço.</span><span class="sxs-lookup"><span data-stu-id="4b003-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="4b003-109">Cada uma destas configurações foi ser solicitada a partir de servidores de extração diferente, e pode ser adicionados em diferentes fases de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="4b003-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="4b003-110">Configurações parciais também permitem diferentes pessoas ou equipas controlar diferentes aspetos de configuração de nós sem ter de se coordenar a edição de um documento de configuração única.</span><span class="sxs-lookup"><span data-stu-id="4b003-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="4b003-111">Por exemplo, uma equipa pode ser responsável por implementar uma VM e o sistema operativo, enquanto outra equipa poderá implementar outras aplicações e serviços nessa VM.</span><span class="sxs-lookup"><span data-stu-id="4b003-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="4b003-112">Com configurações parciais, cada equipa pode criar a suas próprias configuração, sem um da ser complicou desnecessariamente.</span><span class="sxs-lookup"><span data-stu-id="4b003-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="4b003-113">Pode utilizar configurações parciais no modo de push, modo de extração ou uma combinação dos dois.</span><span class="sxs-lookup"><span data-stu-id="4b003-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="4b003-114">Configurações parciais no modo de push</span><span class="sxs-lookup"><span data-stu-id="4b003-114">Partial configurations in push mode</span></span>
<span data-ttu-id="4b003-115">Para utilizar configurações parciais no modo de push, configurar o MMC no nó de destino para receber as configurações parciais.</span><span class="sxs-lookup"><span data-stu-id="4b003-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="4b003-116">Cada configuração parcial deve ser enviada para o destino utilizando o cmdlet Publish-DSCConfiguration.</span><span class="sxs-lookup"><span data-stu-id="4b003-116">Each partial configuration must be pushed to the target by using the Publish-DSCConfiguration cmdlet.</span></span> <span data-ttu-id="4b003-117">O nó de destino, em seguida, combina a configuração parcial para uma configuração única e pode aplicar a configuração ao chamar o [início DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4b003-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="4b003-118">Configurar o MMC para configurações parcial do modo de push</span><span class="sxs-lookup"><span data-stu-id="4b003-118">Configuring the LCM for push-mode partial configurations</span></span>
<span data-ttu-id="4b003-119">Para configurar MMC para configurações parciais no modo de push, crie um **DSCLocalConfigurationManager** configuração com um **PartialConfiguration** bloco para cada configuração parcial.</span><span class="sxs-lookup"><span data-stu-id="4b003-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="4b003-120">Para obter mais informações sobre como configurar o MMC, consulte [Windows configurar o Gestor de configuração Local](https://technet.microsoft.com/library/mt421188.aspx).</span><span class="sxs-lookup"><span data-stu-id="4b003-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](https://technet.microsoft.com/library/mt421188.aspx).</span></span>
<span data-ttu-id="4b003-121">O exemplo seguinte mostra uma configuração de MMC que espera duas configurações parciais — que implementa o sistema operativo e outro que implementa e configura o SharePoint.</span><span class="sxs-lookup"><span data-stu-id="4b003-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

           PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="4b003-122">O **RefreshMode** cada configuração parcial está definida como "Push".</span><span class="sxs-lookup"><span data-stu-id="4b003-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="4b003-123">Os nomes do **PartialConfiguration** blocos (neste caso, "ServiceAccountConfig" e "SharePointConfig") tem de corresponder exatamente os nomes das configurações que são enviadas por push para o nó de destino.</span><span class="sxs-lookup"><span data-stu-id="4b003-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

><span data-ttu-id="4b003-124">**Nota:** com o nome de cada **PartialConfiguration** bloco tem de coincidir com o nome da configuração real conforme especificado no script de configuração, não o nome do ficheiro MOF, que deve ser o nome do nó de destino ou `localhost`.</span><span class="sxs-lookup"><span data-stu-id="4b003-124">**Note:** The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="4b003-125">Publicar e iniciar configurações parcial do modo de push</span><span class="sxs-lookup"><span data-stu-id="4b003-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="4b003-126">Em seguida, chame [publicar DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) para cada configuração, transmitir as pastas que contêm os documentos de configuração como a **caminho** parâmetros.</span><span class="sxs-lookup"><span data-stu-id="4b003-126">You then call [Publish-DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="4b003-127">`Publish-DSCConfiguration`coloca os ficheiros MOF de configuração para os nós de destino.</span><span class="sxs-lookup"><span data-stu-id="4b003-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="4b003-128">Depois de publicar ambas as configurações, pode chamar `Start-DSCConfiguration –UseExisting` no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="4b003-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="4b003-129">Por exemplo, se tiver compilado os seguintes documentos MOF de configuração no nó de criação:</span><span class="sxs-lookup"><span data-stu-id="4b003-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

```powershell
PS C:\PartialConfigTest> Get-ChildItem -Recurse


    Directory: C:\PartialConfigTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig


    Directory: C:\PartialConfigTest\ServiceAccountConfig


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof


    Directory: C:\DscTests\SharePointConfig


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

<span data-ttu-id="4b003-130">Seria publicar e executar as configurações da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="4b003-130">You would publish and run the configurations as follows:</span></span>

```powershell
PS C:\PartialConfigTest> Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Start-DscConfiguration -UseExisting -ComputerName 'TestVM'

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

><span data-ttu-id="4b003-131">**Nota:** o utilizador que executa o [publicar DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) cmdlet tem de ter privilégios de administrador no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="4b003-131">**Note:** The user running the [Publish-DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="4b003-132">Configurações parciais no modo de extração</span><span class="sxs-lookup"><span data-stu-id="4b003-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="4b003-133">Podem ser solicitadas configurações parciais de uma ou mais servidores de extração (para obter mais informações sobre servidores de solicitação, consulte [Windows PowerShell pretendido Estado solicitação servidores de configuração](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="4b003-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="4b003-134">Para tal, tem de configurar o MMC no nó de destino para solicitar as configurações de parciais e o nome e localize os documentos de configuração corretamente nos servidores de extração.</span><span class="sxs-lookup"><span data-stu-id="4b003-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="4b003-135">Configurar o MMC para configurações de nó de solicitação</span><span class="sxs-lookup"><span data-stu-id="4b003-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="4b003-136">Para configurar o MMC para solicitar parciais configurações de um servidor de solicitação, definir o servidor de solicitação num **ConfigurationRepositoryWeb** (para um servidor de solicitação HTTP) ou **ConfigurationRepositoryShare** ( para um servidor de solicitação SMB) bloco.</span><span class="sxs-lookup"><span data-stu-id="4b003-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="4b003-137">Em seguida, criar **PartialConfiguration** blocos que se referem para o servidor de solicitação, utilizando o **ConfigurationSource** propriedade.</span><span class="sxs-lookup"><span data-stu-id="4b003-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="4b003-138">Também tem de criar um **definições** bloco para especificar que o MMC utiliza o modo de extração e para especificar o **ConfigurationNames** ou **ConfigurationID** que o servidor de solicitação e utilização do nó de destino para identificar as configurações.</span><span class="sxs-lookup"><span data-stu-id="4b003-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="4b003-139">A configuração meta seguinte define um servidor de solicitação HTTP com o nome CONTOSO PullSrv e duas configurações parciais que utilizam esse servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="4b003-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="4b003-140">Para obter mais informações sobre como configurar o utilizando o MMC **ConfigurationNames**, consulte [configurar um cliente de solicitação utilizando nomes de configuração](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="4b003-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span>
<span data-ttu-id="4b003-141">Para obter informações sobre como configurar o utilizando o MMC **ConfigurationID**, consulte [configurar um cliente de extração com o ID de configuração](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="4b003-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="4b003-142">Configurar o MMC para configurações de modo de extração utilizando nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="4b003-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }

}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="4b003-143">Configurar o MMC para configurações de modo de extração utilizando ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="4b003-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="4b003-144">Pode solicitar parciais configurações de mais do que um servidor de solicitação — apenas terá de definir a cada servidor de solicitação e, em seguida, consulte o servidor de solicitação adequado em cada **PartialConfiguration** bloco.</span><span class="sxs-lookup"><span data-stu-id="4b003-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="4b003-145">Depois de criar a configuração meta, deve executá-la para criar um documento de configuração (um ficheiro MOF) e, em seguida, chame [conjunto DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) para configurar o MMC.</span><span class="sxs-lookup"><span data-stu-id="4b003-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="4b003-146">Atribuição de nomes e colocar os documentos de configuração no servidor de solicitação (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="4b003-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="4b003-147">Os documentos de configuração parcial tem de ser colocados na pasta especificada como a **ConfigurationPath** no `web.config` ficheiro para o servidor de solicitação (normalmente `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="4b003-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="4b003-148">Nomenclatura de configuração de documentos no servidor de solicitação no PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="4b003-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="4b003-149">Se estiver a extrair apenas uma configuração parcial de um servidor de solicitação individuais, o documento de configuração pode ter qualquer nome.</span><span class="sxs-lookup"><span data-stu-id="4b003-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span>
<span data-ttu-id="4b003-150">Se estiver a extrair mais de uma configuração parcial de um servidor de solicitação, o documento de configuração pode ter um nome a `<ConfigurationName>.mof`, onde _ConfigurationName_ é o nome da configuração da parcial, ou `<ConfigurationName>.<NodeName>.mof`, em que  _ConfigurationName_ é o nome da configuração da parcial, e _NodeName_ é o nome do nó de destino.</span><span class="sxs-lookup"><span data-stu-id="4b003-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where _ConfigurationName_ is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where  _ConfigurationName_ is the name of the partial configuration, and _NodeName_ is the name of the target node.</span></span>
<span data-ttu-id="4b003-151">Isto permite-lhe solicitação configurações do servidor de solicitação do Automation DSC do Azure.</span><span class="sxs-lookup"><span data-stu-id="4b003-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>


#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="4b003-152">Nomenclatura de configuração de documentos no servidor de solicitação no PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4b003-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="4b003-153">Os documentos de configuração devem ter o nome da seguinte forma: `ConfigurationName.mof`, onde _ConfigurationName_ é o nome da configuração parcial.</span><span class="sxs-lookup"><span data-stu-id="4b003-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where _ConfigurationName_ is the name of the partial configuration.</span></span> <span data-ttu-id="4b003-154">Para o nosso exemplo, os documentos de configuração devem ter o nome da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="4b003-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="4b003-155">Atribuição de nomes e colocar os documentos de configuração no servidor de solicitação (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="4b003-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="4b003-156">Os documentos de configuração parcial tem de ser colocados na pasta especificada como a **ConfigurationPath** no `web.config` ficheiro para o servidor de solicitação (normalmente `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="4b003-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="4b003-157">Os documentos de configuração devem ter o nome da seguinte forma: _ConfigurationName_.</span><span class="sxs-lookup"><span data-stu-id="4b003-157">The configuration documents must be named as follows: _ConfigurationName_.</span></span> <span data-ttu-id="4b003-158">_ConfigurationID_`.mof`, onde _ConfigurationName_ é o nome da configuração parcial e _ConfigurationID_ o ID de configuração está definido na MMC no destino nó.</span><span class="sxs-lookup"><span data-stu-id="4b003-158">_ConfigurationID_`.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="4b003-159">Para o nosso exemplo, os documentos de configuração devem ter o nome da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="4b003-159">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```


### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="4b003-160">Executar configurações parciais de um servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="4b003-160">Running partial configurations from a pull server</span></span>

<span data-ttu-id="4b003-161">Depois do MMC no nó de destino foi configurado e a configuração documentos tiverem sido criados e com o nome corretamente no servidor de solicitação, o nó de destino transmitirão as configurações parciais, combine-os e aplicar a configuração resultante regulares intervalos tal como especificado pelo **RefreshFrequencyMins** propriedade a MMC.</span><span class="sxs-lookup"><span data-stu-id="4b003-161">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="4b003-162">Se pretender forçar uma atualização, pode chamar o [atualização DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) cmdlet, extraia as configurações e, em seguida, `Start-DSCConfiguration –UseExisting` para aplicá-las.</span><span class="sxs-lookup"><span data-stu-id="4b003-162">If you want to force a refresh, you can call the [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>


## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="4b003-163">Configurações parciais nos modos push e pull mistos</span><span class="sxs-lookup"><span data-stu-id="4b003-163">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="4b003-164">Também pode misturar push e pull modos para configurações parciais.</span><span class="sxs-lookup"><span data-stu-id="4b003-164">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="4b003-165">Ou seja, pode ter uma configuração parcial solicitada de um servidor de solicitação, enquanto outra configuração parcial é premida.</span><span class="sxs-lookup"><span data-stu-id="4b003-165">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="4b003-166">Especifique o modo de atualização para cada configuração parcial, conforme descrito nas secções anteriores.</span><span class="sxs-lookup"><span data-stu-id="4b003-166">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span>
<span data-ttu-id="4b003-167">Por exemplo, a configuração meta seguinte descreve o mesmo exemplo, com o `ServiceAccountConfig` parcial configuração no modo de extração e `SharePointConfig` parcial configuração no modo de push.</span><span class="sxs-lookup"><span data-stu-id="4b003-167">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="4b003-168">Modos push e pull mistos utilizando ConfigurationNames</span><span class="sxs-lookup"><span data-stu-id="4b003-168">Mixed push and pull modes using ConfigurationNames</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="4b003-169">Modos push e pull mistos utilizando ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="4b003-169">Mixed push and pull modes using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="4b003-170">Tenha em atenção que o **RefreshMode** especificado no bloco de definições é "Solicitar", mas o **RefreshMode** para o `SharePointConfig` configuração parcial é "Push".</span><span class="sxs-lookup"><span data-stu-id="4b003-170">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="4b003-171">Nome e localizar os ficheiros de MOF configuração conforme descrito acima para os respetivos modos de atualização do respetivo.</span><span class="sxs-lookup"><span data-stu-id="4b003-171">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span> <span data-ttu-id="4b003-172">Chamar **publicar DSCConfiguration** para publicar o `SharePointConfig` configuração parcial e aguarde que o `ServiceAccountConfig` configuração para ser solicitados a partir do servidor de solicitação ou forçar uma atualização ao chamar [ Atualização DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).</span><span class="sxs-lookup"><span data-stu-id="4b003-172">Call **Publish-DSCConfiguration** to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="4b003-173">Exemplo de configuração ServiceAccountConfig parcial</span><span class="sxs-lookup"><span data-stu-id="4b003-173">Example ServiceAccountConfig Partial Configuration</span></span>

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration


    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential

        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig

```
## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="4b003-174">Exemplo de configuração SharePointConfig parcial</span><span class="sxs-lookup"><span data-stu-id="4b003-174">Example SharePointConfig Partial Configuration</span></span>
```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```
##<a name="see-also"></a><span data-ttu-id="4b003-175">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="4b003-175">See Also</span></span>

<span data-ttu-id="4b003-176">**Conceitos**
[servidores de solicitação de configuração do estado pretendido do Windows PowerShell](pullServer.md)</span><span class="sxs-lookup"><span data-stu-id="4b003-176">**Concepts**
[Windows PowerShell Desired State Configuration Pull Servers](pullServer.md)</span></span>

[<span data-ttu-id="4b003-177">Configurar o Gestor de configuração Local do Windows</span><span class="sxs-lookup"><span data-stu-id="4b003-177">Windows Configuring the Local Configuration Manager</span></span>](https://technet.microsoft.com/library/mt421188.aspx)