---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Configurações parciais de PowerShell Desired State Configuration
ms.openlocfilehash: b2b17e35597707eb97ecdcea9dda4466deeab0cb
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405076"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="15adb-103">Configurações parciais de PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="15adb-103">PowerShell Desired State Configuration partial configurations</span></span>

<span data-ttu-id="15adb-104">_Aplica-se a: Windows PowerShell 5.0 e posterior._</span><span class="sxs-lookup"><span data-stu-id="15adb-104">_Applies To: Windows PowerShell 5.0 and later._</span></span>

<span data-ttu-id="15adb-105">No PowerShell 5.0, Desired State Configuration (DSC) permite que as configurações sejam entregues em fragmentos e de várias origens.</span><span class="sxs-lookup"><span data-stu-id="15adb-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="15adb-106">O Gestor de configuração Local (LCM) no nó de destino prepara os fragmentos antes de aplicá-los como uma configuração única.</span><span class="sxs-lookup"><span data-stu-id="15adb-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="15adb-107">Esta capacidade permite a partilha de controlo da configuração entre as equipes ou indivíduos.</span><span class="sxs-lookup"><span data-stu-id="15adb-107">This capability allows sharing control of configuration between teams or individuals.</span></span> <span data-ttu-id="15adb-108">Por exemplo, se dois ou mais equipes de desenvolvedores estiver a colaborar num serviço, eles cada querer criar configurações para gerir a sua parte do serviço.</span><span class="sxs-lookup"><span data-stu-id="15adb-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="15adb-109">Cada uma das seguintes configurações poderia ser extraída dos servidores de solicitação de diferentes e poderia ser adicionados em diferentes fases do desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="15adb-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="15adb-110">Configurações parciais também permitem a diferentes pessoas ou equipas controlar diferentes aspetos de configuração de nós sem ter de coordenar a edição de um documento de configuração única.</span><span class="sxs-lookup"><span data-stu-id="15adb-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="15adb-111">Por exemplo, uma equipe pode ser responsável por implementar uma VM e o sistema operativo, enquanto outra equipe pode implementar outras aplicações e serviços nessa VM.</span><span class="sxs-lookup"><span data-stu-id="15adb-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="15adb-112">Configurações parciais, cada equipe pode criar sua própria configuração, sem qualquer um deles desnecessariamente a ser complicado.</span><span class="sxs-lookup"><span data-stu-id="15adb-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="15adb-113">Pode utilizar configurações parciais no modo push, no modo de solicitação ou uma combinação dos dois.</span><span class="sxs-lookup"><span data-stu-id="15adb-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="15adb-114">Configurações parciais no modo de push</span><span class="sxs-lookup"><span data-stu-id="15adb-114">Partial configurations in push mode</span></span>

<span data-ttu-id="15adb-115">Para usar configurações parciais em modo push, configurar o LCM no nó de destino para receber as configurações parciais.</span><span class="sxs-lookup"><span data-stu-id="15adb-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="15adb-116">Cada configuração parcial deve ser colocada no destino, utilizando o `Publish-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15adb-116">Each partial configuration must be pushed to the target by using the `Publish-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="15adb-117">O nó de destino, em seguida, combina a configuração parcial numa única configuração, e pode aplicar a configuração ao chamar o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15adb-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="15adb-118">Configurar o LCM para configurações parcial do modo de push</span><span class="sxs-lookup"><span data-stu-id="15adb-118">Configuring the LCM for push-mode partial configurations</span></span>

<span data-ttu-id="15adb-119">Para configurar o LCM para configurações parciais no modo push, crie uma **dsclocalconfigurationmanager para** configuração com um **PartialConfiguration** bloco para cada configuração parcial.</span><span class="sxs-lookup"><span data-stu-id="15adb-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="15adb-120">Para obter mais informações sobre como configurar o LCM, consulte [configurar o Gestor de configuração Local do Windows](/powershell/dsc/metaConfig).</span><span class="sxs-lookup"><span data-stu-id="15adb-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](/powershell/dsc/metaConfig).</span></span> <span data-ttu-id="15adb-121">O exemplo seguinte mostra uma configuração de LCM que espera duas configurações parciais — um que implementa o sistema operacional e um que implementa e configura o SharePoint.</span><span class="sxs-lookup"><span data-stu-id="15adb-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

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

<span data-ttu-id="15adb-122">O **RefreshMode** cada configuração parcial está definida como "Push".</span><span class="sxs-lookup"><span data-stu-id="15adb-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="15adb-123">Os nomes da **PartialConfiguration** blocos (no caso, "ServiceAccountConfig" e "SharePointConfig") tem de corresponder exatamente os nomes das configurações que são enviados por push para o nó de destino.</span><span class="sxs-lookup"><span data-stu-id="15adb-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

> [!Note]
> <span data-ttu-id="15adb-124">Com o nome de cada **PartialConfiguration** bloco tem de corresponder o nome real da configuração conforme é especificado com o script de configuração, não o nome do ficheiro MOF, que deve ser o nome do nó de destino ou `localhost`.</span><span class="sxs-lookup"><span data-stu-id="15adb-124">The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="15adb-125">Publicação e a partir de configurações parciais do modo de push</span><span class="sxs-lookup"><span data-stu-id="15adb-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="15adb-126">Em seguida, chame [Publish-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) para cada configuração, passando as pastas que contêm os documentos de configuração como a **caminho** parâmetros.</span><span class="sxs-lookup"><span data-stu-id="15adb-126">You then call [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="15adb-127">`Publish-DSCConfiguration`coloca os ficheiros MOF de configuração para os nós de destino.</span><span class="sxs-lookup"><span data-stu-id="15adb-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="15adb-128">Depois de publicar as duas configurações, pode chamar `Start-DSCConfiguration –UseExisting` no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="15adb-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="15adb-129">Por exemplo, se o ter compilado os seguintes documentos MOF de configuração no nó de criação:</span><span class="sxs-lookup"><span data-stu-id="15adb-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

```powershell
Get-ChildItem -Recurse
```

```output
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

<span data-ttu-id="15adb-130">Imagem da publicação e execute as configurações da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="15adb-130">You would publish and run the configurations as follows:</span></span>

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> <span data-ttu-id="15adb-131">O utilizador que executa o [Publish-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet tem de ter privilégios de administrador no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="15adb-131">The user running the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="15adb-132">Configurações parciais no modo de solicitação</span><span class="sxs-lookup"><span data-stu-id="15adb-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="15adb-133">Configurações parciais podem ser obtidas a partir de um ou mais servidores de extração (para obter mais informações sobre servidores de extração, consulte [Windows PowerShell Desired State Configuration Pull servidores](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="15adb-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="15adb-134">Para tal, tem de configurar o LCM no nó de destino para extrair as configurações de parciais e dê um nome e localize os documentos de configuração corretamente nos servidores de pull.</span><span class="sxs-lookup"><span data-stu-id="15adb-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="15adb-135">Configurar o LCM para configurações de nó de extração</span><span class="sxs-lookup"><span data-stu-id="15adb-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="15adb-136">Para configurar o LCM para solicitar configurações parciais a partir de um servidor de solicitação, define o servidor de solicitação em qualquer um uma **ConfigurationRepositoryWeb** (para um servidor de solicitação HTTP) ou **ConfigurationRepositoryShare** ( para um servidor de solicitação SMB) bloco.</span><span class="sxs-lookup"><span data-stu-id="15adb-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="15adb-137">Em seguida, crie **PartialConfiguration** blocos que se referem para o servidor de solicitação, utilizando o **ConfigurationSource** propriedade.</span><span class="sxs-lookup"><span data-stu-id="15adb-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="15adb-138">Terá também de criar uma **configurações** bloco para especificar que o LCM usa o modo de solicitação e especificar a **ConfigurationNames** ou **ConfigurationID** que o servidor de solicitação e utilização do nó de destino para identificar as configurações.</span><span class="sxs-lookup"><span data-stu-id="15adb-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="15adb-139">A seguinte configuração de meta define um servidor de solicitação HTTP com o nome CONTOSO-PullSrv e servidor de solicitação de duas configurações parciais que usá-lo.</span><span class="sxs-lookup"><span data-stu-id="15adb-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="15adb-140">Para obter mais informações sobre como configurar o LCM usando **ConfigurationNames**, consulte [configuração de um cliente de solicitação através de nomes de configuração](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="15adb-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span> <span data-ttu-id="15adb-141">Para obter informações sobre como configurar o LCM usando **ConfigurationID**, consulte [configuração de um cliente de solicitação através do ID de configuração](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="15adb-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="15adb-142">Configurar o LCM para configurações de modo de solicitação com nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="15adb-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="15adb-143">Configurar o LCM para configurações de modo de solicitação com ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="15adb-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

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

<span data-ttu-id="15adb-144">Pode extrair configurações parciais de mais do que um servidor de solicitação — apenas terá de definir cada servidor de solicitação e, em seguida, consulte o servidor de solicitação apropriada em cada **PartialConfiguration** bloco.</span><span class="sxs-lookup"><span data-stu-id="15adb-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="15adb-145">Depois de criar a meta-configuração, tem de executá-lo para criar um documento de configuração (um ficheiro MOF) e, em seguida, chame [Set-dsclocalconfigurationmanager para](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) para configurar o LCM.</span><span class="sxs-lookup"><span data-stu-id="15adb-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="15adb-146">Atribuição de nomes e colocar os documentos de configuração no servidor de solicitação (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="15adb-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="15adb-147">Os documentos de configuração parcial tem de ser colocados na pasta especificada como a **ConfigurationPath** no `web.config` ficheiro para o servidor de solicitação (normalmente `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="15adb-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="15adb-148">Nomenclatura de configuração de documentos no servidor de solicitação no PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="15adb-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="15adb-149">Se está extraindo apenas uma configuração parcial de um servidor de solicitação individuais, o documento de configuração pode ter qualquer nome.</span><span class="sxs-lookup"><span data-stu-id="15adb-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span> <span data-ttu-id="15adb-150">Se está extraindo mais do que uma configuração parcial a partir de um servidor de solicitação, o documento de configuração pode ser com o nome `<ConfigurationName>.mof`, onde *ConfigurationName* é o nome da configuração parcial, ou `<ConfigurationName>.<NodeName>.mof`, em que *ConfigurationName* é o nome da configuração parcial, e *NodeName* é o nome do nó de destino.</span><span class="sxs-lookup"><span data-stu-id="15adb-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where *ConfigurationName* is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where *ConfigurationName* is the name of the partial configuration, and *NodeName* is the name of the target node.</span></span> <span data-ttu-id="15adb-151">Isso permite que pull configurações do servidor de solicitação de DSC de automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="15adb-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="15adb-152">Nomenclatura de configuração de documentos no servidor de solicitação no PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="15adb-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="15adb-153">Os documentos de configuração tem de ter o nome da seguinte forma: `ConfigurationName.mof`, onde *ConfigurationName* é o nome da configuração parcial.</span><span class="sxs-lookup"><span data-stu-id="15adb-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where *ConfigurationName* is the name of the partial configuration.</span></span> <span data-ttu-id="15adb-154">No nosso exemplo, os documentos de configuração devem ter o nome da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="15adb-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="15adb-155">Atribuição de nomes e colocar os documentos de configuração no servidor de solicitação (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="15adb-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="15adb-156">Os documentos de configuração parcial tem de ser colocados na pasta especificada como a **ConfigurationPath** no `web.config` ficheiro para o servidor de solicitação (normalmente `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="15adb-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="15adb-157">Os documentos de configuração tem de ter o nome da seguinte forma: `<ConfigurationName>.<ConfigurationID>.mof`, onde _ConfigurationName_ é o nome da configuração parcial e _ConfigurationID_ é a configuração de ID definido no LCM no nó de destino.</span><span class="sxs-lookup"><span data-stu-id="15adb-157">The configuration documents must be named as follows: `<ConfigurationName>.<ConfigurationID>.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="15adb-158">No nosso exemplo, os documentos de configuração devem ter o nome da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="15adb-158">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="15adb-159">Executar configurações parciais de um servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="15adb-159">Running partial configurations from a pull server</span></span>

<span data-ttu-id="15adb-160">Depois do LCM no nó de destino foi configurado e a configuração de documentos tenham sido criados e com o nome corretamente no servidor de solicitação, o nó de destino irá fazer com que as configurações parciais, combiná-los e aplicar a configuração resultante regulares intervalos como especificado pelos **RefreshFrequencyMins** propriedade do LCM.</span><span class="sxs-lookup"><span data-stu-id="15adb-160">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="15adb-161">Se quiser forçar uma atualização, pode chamar o [Update-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, para extrair as configurações e, em seguida, `Start-DSCConfiguration –UseExisting` aplicá-las.</span><span class="sxs-lookup"><span data-stu-id="15adb-161">If you want to force a refresh, you can call the [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="15adb-162">Configurações parciais em modos de push e pull mistos</span><span class="sxs-lookup"><span data-stu-id="15adb-162">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="15adb-163">Também pode combinar push e pull modos para configurações parciais.</span><span class="sxs-lookup"><span data-stu-id="15adb-163">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="15adb-164">Ou seja, poderia ter uma configuração parcial que é obtida a partir de um servidor de solicitação, enquanto outra configuração parcial é emitidos via push.</span><span class="sxs-lookup"><span data-stu-id="15adb-164">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="15adb-165">Especifique o modo de atualização para cada configuração parcial, conforme descrito nas secções anteriores.</span><span class="sxs-lookup"><span data-stu-id="15adb-165">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span> <span data-ttu-id="15adb-166">Por exemplo, a seguinte configuração de meta descreve o mesmo exemplo, com o `ServiceAccountConfig` configuração parcial no modo de solicitação e o `SharePointConfig` configuração parcial no modo push.</span><span class="sxs-lookup"><span data-stu-id="15adb-166">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="15adb-167">Modos de push e pull mistos usando ConfigurationNames</span><span class="sxs-lookup"><span data-stu-id="15adb-167">Mixed push and pull modes using ConfigurationNames</span></span>

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="15adb-168">Modos de push e pull mistos usando ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="15adb-168">Mixed push and pull modes using ConfigurationID</span></span>

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

<span data-ttu-id="15adb-169">Tenha em atenção que o **RefreshMode** especificada no bloco de definições é o "Pull", mas o **RefreshMode** para o `SharePointConfig` configuração parcial é "Push".</span><span class="sxs-lookup"><span data-stu-id="15adb-169">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="15adb-170">Dê um nome e localizar os ficheiros MOF de configuração, conforme descrito acima para seus modos de atualização respectiva.</span><span class="sxs-lookup"><span data-stu-id="15adb-170">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span>
<span data-ttu-id="15adb-171">Chamar `Publish-DSCConfiguration` para publicar o `SharePointConfig` configuração parcial e aguardar a `ServiceAccountConfig` configuração a ser obtido a partir do servidor de solicitação ou forçar uma atualização ao chamar [Update-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span><span class="sxs-lookup"><span data-stu-id="15adb-171">Call `Publish-DSCConfiguration` to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="15adb-172">Exemplo de configuração de ServiceAccountConfig parcial</span><span class="sxs-lookup"><span data-stu-id="15adb-172">Example ServiceAccountConfig Partial Configuration</span></span>

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

## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="15adb-173">Exemplo de configuração de SharePointConfig parcial</span><span class="sxs-lookup"><span data-stu-id="15adb-173">Example SharePointConfig Partial Configuration</span></span>

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

## <a name="see-also"></a><span data-ttu-id="15adb-174">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="15adb-174">See Also</span></span>

[<span data-ttu-id="15adb-175">Windows PowerShell Desired State Configuration Pull servidores</span><span class="sxs-lookup"><span data-stu-id="15adb-175">Windows PowerShell Desired State Configuration Pull Servers</span></span>](pullServer.md)

[<span data-ttu-id="15adb-176">Configurar o Gestor de configuração Local do Windows</span><span class="sxs-lookup"><span data-stu-id="15adb-176">Windows Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)