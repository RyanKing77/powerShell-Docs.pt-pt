---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
title: Melhoramentos de DSC na WMF 5.1
ms.openlocfilehash: ce897dab2344455453e9bf2d0b5a897f9abb4392
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/27/2017
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="a2752-103">Melhoramentos na configuração do estado pretendido (DSC) no WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="a2752-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="a2752-104">Melhoramentos de recursos do DSC classe</span><span class="sxs-lookup"><span data-stu-id="a2752-104">DSC class resource improvements</span></span>

<span data-ttu-id="a2752-105">No WMF 5.1, podemos ter corrigido os seguintes problemas conhecidos:</span><span class="sxs-lookup"><span data-stu-id="a2752-105">In WMF 5.1, we have fixed the following known issues:</span></span>
* <span data-ttu-id="a2752-106">Get-DscConfiguration pode devolver valores vazios (nulos) ou erros, se um tipo de tabela complexas/hash é devolvido pela função Get() de um recurso de DSC com base na classe.</span><span class="sxs-lookup"><span data-stu-id="a2752-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
* <span data-ttu-id="a2752-107">Get-DscConfiguration devolve um erro se a credencial de RunAs é utilizada na configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="a2752-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
* <span data-ttu-id="a2752-108">Recursos baseados em classe não podem ser utilizado numa configuração composta.</span><span class="sxs-lookup"><span data-stu-id="a2752-108">Class-based resource cannot be used in a composite configuration.</span></span>
* <span data-ttu-id="a2752-109">Início DscConfiguration bloqueia se recursos baseados na classe tem uma propriedade do seu próprio tipo.</span><span class="sxs-lookup"><span data-stu-id="a2752-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
* <span data-ttu-id="a2752-110">Recursos baseados em classe não podem ser utilizado como um recurso exclusivo.</span><span class="sxs-lookup"><span data-stu-id="a2752-110">Class-based resource cannot be used as an exclusive resource.</span></span>


## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="a2752-111">Melhoramentos de depuração de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="a2752-111">DSC resource debugging improvements</span></span>
<span data-ttu-id="a2752-112">No WMF 5.0, o depurador do PowerShell não parou no método de recursos baseados na classe (Get/conjunto/teste) diretamente.</span><span class="sxs-lookup"><span data-stu-id="a2752-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span>
<span data-ttu-id="a2752-113">No WMF 5.1, o depurador interrompe no método baseado em classe de recursos da mesma forma que nos métodos de recursos baseados em MOF.</span><span class="sxs-lookup"><span data-stu-id="a2752-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="a2752-114">Cliente de solicitação do DSC suporta o TLS 1.1 e TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="a2752-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span> 
<span data-ttu-id="a2752-115">Anteriormente, o cliente de solicitação do DSC apenas suportado SSL3.0 e TLS1.0 através de ligações de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a2752-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span> <span data-ttu-id="a2752-116">Quando forçado a utilizar protocolos mais seguros, o cliente de solicitação deixaria de funcionar.</span><span class="sxs-lookup"><span data-stu-id="a2752-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span> <span data-ttu-id="a2752-117">WMF 5.1, o cliente de solicitação do DSC já não suporta SSL 3.0 e adiciona suporte para os protocolos TLS 1.1 e TLS 1.2 mais seguros.</span><span class="sxs-lookup"><span data-stu-id="a2752-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>  

## <a name="improved-pull-server-registration"></a><span data-ttu-id="a2752-118">Registo do servidor de solicitação melhorada</span><span class="sxs-lookup"><span data-stu-id="a2752-118">Improved pull server registration</span></span> ##

<span data-ttu-id="a2752-119">Nas versões anteriores do WMF, registos/reporting simultâneas pedidos para um servidor de solicitação do DSC ao utilizar a base de dados ESENT seriam levar a MMC registar e/ou reportar a falhar.</span><span class="sxs-lookup"><span data-stu-id="a2752-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span> <span data-ttu-id="a2752-120">Nestes casos, os registos de eventos no servidor de solicitação tem o erro "Nome de instância já em utilização."</span><span class="sxs-lookup"><span data-stu-id="a2752-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span>
<span data-ttu-id="a2752-121">Isto foi devido a um padrão incorreto, que está a ser utilizado para aceder à base de dados ESENT num cenário de vários threads.</span><span class="sxs-lookup"><span data-stu-id="a2752-121">This was due to an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span> <span data-ttu-id="a2752-122">No WMF 5.1, este problema.</span><span class="sxs-lookup"><span data-stu-id="a2752-122">In WMF 5.1, this issue has been fixed.</span></span> <span data-ttu-id="a2752-123">Em simultâneo registos ou relatórios (que envolve a base de dados de ESENT) funciona bem em WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="a2752-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span> <span data-ttu-id="a2752-124">Este problema é aplicável apenas a base de dados ESENT e não se aplica à base de dados OLEDB.</span><span class="sxs-lookup"><span data-stu-id="a2752-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span> 

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="a2752-125">Ativar o registo Circular na instância de base de dados ESENT</span><span class="sxs-lookup"><span data-stu-id="a2752-125">Enable Circular log on ESENT database instance</span></span>
<span data-ttu-id="a2752-126">Na versão de eariler do DSC PullServer, os ficheiros de registo da base de dados ESENT foram ao preencher o espaço em disco do becouse pullserver que estava a ser criada a instância de base de dados sem o registo circular.</span><span class="sxs-lookup"><span data-stu-id="a2752-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="a2752-127">Nesta versão, terá a opção para controlar o comportamento de registo circular de instância utilizando o pullserver Web. config.</span><span class="sxs-lookup"><span data-stu-id="a2752-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="a2752-128">Por predefinição CircularLogging está definido como TRUE.</span><span class="sxs-lookup"><span data-stu-id="a2752-128">By default CircularLogging is set to TRUE.</span></span>
```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```
## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="a2752-129">Solicitar a Convenção de nomenclatura de configuração parcial</span><span class="sxs-lookup"><span data-stu-id="a2752-129">Pull partial configuration naming convention</span></span>
<span data-ttu-id="a2752-130">Na versão anterior, a Convenção de nomenclatura para uma configuração parcial foi que o nome do ficheiro MOF no servidor/serviço de extração deve corresponder ao nome da configuração parcial especificado nas definições de Gestor de configuração locais, que por sua vez tem de corresponder à o nome da configuração incorporado no ficheiro MOF.</span><span class="sxs-lookup"><span data-stu-id="a2752-130">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span> 

<span data-ttu-id="a2752-131">Ver os instantâneos abaixo:</span><span class="sxs-lookup"><span data-stu-id="a2752-131">See the snapshots below:</span></span>

<span data-ttu-id="a2752-132">• Definições de configuração local que define uma configuração parcial que um nó está autorizado a receber.</span><span class="sxs-lookup"><span data-stu-id="a2752-132">•   Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

![Configuração meta do exemplo](../images/MetaConfigPartialOne.png)

<span data-ttu-id="a2752-134">Definição de configuração parcial de exemplo de •</span><span class="sxs-lookup"><span data-stu-id="a2752-134">•   Sample partial configuration definition</span></span> 

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

<span data-ttu-id="a2752-135">• 'ConfigurationName' incorporado no ficheiro MOF gerado.</span><span class="sxs-lookup"><span data-stu-id="a2752-135">•   'ConfigurationName' embedded in the generated MOF file.</span></span>

![Ficheiro mof gerado de exemplo](../images/PartialGeneratedMof.png)

<span data-ttu-id="a2752-137">• FileName no repositório de configuração de solicitação</span><span class="sxs-lookup"><span data-stu-id="a2752-137">•   FileName in the pull configuration repository</span></span> 

![Nome do ficheiro no repositório de configuração](../images/PartialInConfigRepository.png)

<span data-ttu-id="a2752-139">Nome do serviço de automatização do Azure gerado ficheiros MOF como `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="a2752-139">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="a2752-140">Por isso, a configuração abaixo compila para PartialOne.localhost.mof.</span><span class="sxs-lookup"><span data-stu-id="a2752-140">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

<span data-ttu-id="a2752-141">Isto efetuadas-impossíveis para solicitar um da sua configuração parcial do serviço de automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="a2752-141">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

<span data-ttu-id="a2752-142">No WMF 5.1, uma configuração de parcial, o serviço/servidor de solicitação pode ter o nome como `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="a2752-142">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="a2752-143">Além disso, se uma máquina é extrair uma única configuração de uma solicitação/serviço de servidor, em seguida, o ficheiro de configuração no repositório de configuração do servidor de solicitação pode ter um nome de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="a2752-143">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span> <span data-ttu-id="a2752-144">Esta flexibilidade nomenclatura permite-lhe gerir os nós parcialmente pelo serviço de automatização do Azure, onde algum tipo de configuração para o nó for proveniente do Automation DSC do Azure e com uma configuração parcial que gere localmente.</span><span class="sxs-lookup"><span data-stu-id="a2752-144">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

<span data-ttu-id="a2752-145">A configuração meta abaixo conjuntos de cópias de segurança um nó para ser gerido ambos localmente, bem como através da automatização do Azure service.</span><span class="sxs-lookup"><span data-stu-id="a2752-145">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

```powershell
  [DscLocalConfigurationManager()]
   Configuration RegistrationMetaConfig
   {
        Settings
        {
            RefreshFrequencyMins = 30
            RefreshMode = "PULL"            
        }

        ConfigurationRepositoryWeb web
        {
            ServerURL =  $endPoint
            RegistrationKey = $registrationKey
            ConfigurationNames = $configurationName
        }

        # Partial configuration managed by Azure Automation service.
        PartialConfiguration PartialConfigurationManagedByAzureAutomation
        {
            ConfigurationSource = "[ConfigurationRepositoryWeb]Web"   
        }
    
        # This partial configuration is managed locally.
        PartialConfiguration OnPremisesConfig
        {
            RefreshMode = "PUSH"
            ExclusiveResources = @("Script")
        }

   }

   RegistrationMetaConfig
   Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
 ```

# <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="a2752-146">Utilizar PsDscRunAsCredential com recursos de DSC compostos</span><span class="sxs-lookup"><span data-stu-id="a2752-146">Using PsDscRunAsCredential with DSC composite resources</span></span>   

<span data-ttu-id="a2752-147">Foi adicionado suporte para utilizar [ *PsDscRunAsCredential* ](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) com DSC [composto](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) recursos.</span><span class="sxs-lookup"><span data-stu-id="a2752-147">We have added support for using [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) with DSC [Composite](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) resources.</span></span>    

<span data-ttu-id="a2752-148">Agora pode especificar um valor para PsDscRunAsCredential quando utilizar recursos compostos dentro de configurações.</span><span class="sxs-lookup"><span data-stu-id="a2752-148">You can now specify a value for PsDscRunAsCredential when using composite resources inside configurations.</span></span> <span data-ttu-id="a2752-149">Quando especificado, todos os recursos executam dentro de um recurso composto como um utilizador de RunAs.</span><span class="sxs-lookup"><span data-stu-id="a2752-149">When specified, all resources run inside a composite resource as a RunAs user.</span></span> <span data-ttu-id="a2752-150">Se um recurso composto chama outro recurso composto, todos os respetivos recursos também são executados como utilizador de RunAs.</span><span class="sxs-lookup"><span data-stu-id="a2752-150">If a composite resource calls another composite resource, all of its resources are also executed as RunAs user.</span></span> <span data-ttu-id="a2752-151">As credenciais de RunAs sejam propagadas aos qualquer nível da hierarquia de recurso composto.</span><span class="sxs-lookup"><span data-stu-id="a2752-151">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span> <span data-ttu-id="a2752-152">Se qualquer recurso no interior de um recurso composto Especifica o seu próprio valor para PsDscRunAsCredential, um erro de intercalação resulta durante a compilação de configuração.</span><span class="sxs-lookup"><span data-stu-id="a2752-152">If any resource inside a composite resource specifies its own value for PsDscRunAsCredential, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="a2752-153">Este exemplo mostra a utilização com [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) composto recursos incluídos no módulo PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="a2752-153">This example shows usage with [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) composite resource included in PSDesiredStateConfiguration module.</span></span> 



```powershell

Configuration InstallWindowsFeature     
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features 
        {  
            Name = @("Telnet-Client","SNMP-Service")  
            Ensure = "Present"  
            IncludeAllSubFeature = $true  
            PsDscRunAsCredential = Get-Credential   
        }  
    }

}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}


InstallWindowsFeature -ConfigurationData $configData 

```

##<a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="a2752-154">Módulo de DSC e configuração validações de assinatura</span><span class="sxs-lookup"><span data-stu-id="a2752-154">DSC module and configuration signing validations</span></span>
<span data-ttu-id="a2752-155">No DSC, módulos e configurações são distribuídos a computadores geridos do servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="a2752-155">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span> <span data-ttu-id="a2752-156">Se o servidor de solicitação for comprometido, um atacante pode potencialmente modificar as configurações e os módulos no servidor de solicitação e que o distribuídos a todos os nós geridos, comprometer todos eles.</span><span class="sxs-lookup"><span data-stu-id="a2752-156">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes, compromising all of them.</span></span> 

 <span data-ttu-id="a2752-157">WMF 5.1, DSC suporta a validação de assinaturas digitais no catálogo e a configuração (. Ficheiros MOF).</span><span class="sxs-lookup"><span data-stu-id="a2752-157">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span> <span data-ttu-id="a2752-158">Esta funcionalidade impede que nós executar configurações ou ficheiros de módulo que não estejam assinados por um signatário fidedigno ou que tenham sido adulteradas depois de terminada por signatário fidedigno.</span><span class="sxs-lookup"><span data-stu-id="a2752-158">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span> 



###<a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="a2752-159">Como a configuração de sessão e o módulo</span><span class="sxs-lookup"><span data-stu-id="a2752-159">How to sign configuration and module</span></span> 
***
* <span data-ttu-id="a2752-160">Ficheiros de configuração (. MOFs): O cmdlet do PowerShell existente [conjunto AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) é expandido para suportar a assinatura de ficheiros MOF.</span><span class="sxs-lookup"><span data-stu-id="a2752-160">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) is extended to support signing of MOF files.</span></span>  
* <span data-ttu-id="a2752-161">Módulos: Assinatura de módulos é feito ao iniciar o catálogo de módulo correspondente utilizando os seguintes passos:</span><span class="sxs-lookup"><span data-stu-id="a2752-161">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span> 
    1. <span data-ttu-id="a2752-162">Criar um ficheiro de catálogo: um ficheiro de catálogo contém uma coleção de hashes criptográficos ou thumbprints.</span><span class="sxs-lookup"><span data-stu-id="a2752-162">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span> 
       <span data-ttu-id="a2752-163">Cada thumbprint corresponde a um ficheiro que está incluído no módulo.</span><span class="sxs-lookup"><span data-stu-id="a2752-163">Each thumbprint corresponds to a file that is included in the module.</span></span> 
       <span data-ttu-id="a2752-164">O novo cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), foi adicionada ao permitir que os utilizadores criar um ficheiro de catálogo para o respetivo módulo.</span><span class="sxs-lookup"><span data-stu-id="a2752-164">The new cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), has been added to enable users to create a catalog file for their module.</span></span>
    2. <span data-ttu-id="a2752-165">Assinar o ficheiro de catálogo: Utilize [conjunto AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) para assinar o ficheiro de catálogo.</span><span class="sxs-lookup"><span data-stu-id="a2752-165">Sign the catalog file: Use [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) to sign the catalog file.</span></span>
    3. <span data-ttu-id="a2752-166">Coloque o ficheiro de catálogo dentro da pasta do módulo.</span><span class="sxs-lookup"><span data-stu-id="a2752-166">Place the catalog file inside the module folder.</span></span>
<span data-ttu-id="a2752-167">Por convenção, o ficheiro de catálogo de módulo deve ser colocado sob a pasta do módulo com o mesmo nome que o módulo.</span><span class="sxs-lookup"><span data-stu-id="a2752-167">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

###<a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="a2752-168">Definições de LocalConfigurationManager para ativar a assinatura validações</span><span class="sxs-lookup"><span data-stu-id="a2752-168">LocalConfigurationManager settings to enable signing validations</span></span>

####<a name="pull"></a><span data-ttu-id="a2752-169">Solicitação</span><span class="sxs-lookup"><span data-stu-id="a2752-169">Pull</span></span>
<span data-ttu-id="a2752-170">LocalConfigurationManager de um nó efetua a assinatura de validação de módulos e configurações com base nas respetivas definições atuais.</span><span class="sxs-lookup"><span data-stu-id="a2752-170">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span> <span data-ttu-id="a2752-171">Por predefinição, a validação da assinatura está desativada.</span><span class="sxs-lookup"><span data-stu-id="a2752-171">By default, signature validation is disabled.</span></span> <span data-ttu-id="a2752-172">Validação da assinatura podem ativados adicionando o bloco 'SignatureValidation' para a definição de configuração meta do nó como mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="a2752-172">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'        
    } 
    
    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # By default, LCM uses the default Windows trusted publisher store to validate the certificate chain. If TrustedStorePath property is specified, LCM uses this custom store for retrieving the trusted publishers to validate the content.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'            
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.       
    }
 
}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose 
 ```

<span data-ttu-id="a2752-173">Definir a configuração meta do acima num nó ativa a validação da assinatura em módulos e configurações transferidas.</span><span class="sxs-lookup"><span data-stu-id="a2752-173">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span> <span data-ttu-id="a2752-174">O Gestor de configuração Local efetua os seguintes passos para verificar as assinaturas digitais.</span><span class="sxs-lookup"><span data-stu-id="a2752-174">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="a2752-175">Verificar a assinatura de um ficheiro de configuração (. MOF) é válido.</span><span class="sxs-lookup"><span data-stu-id="a2752-175">Verify the signature on a configuration file (.MOF) is valid.</span></span> 
   <span data-ttu-id="a2752-176">Utiliza o cmdlet do PowerShell [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), que está alargado no 5.1 para suportar a validação da assinatura MOF.</span><span class="sxs-lookup"><span data-stu-id="a2752-176">It uses the PowerShell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), which is extended in 5.1 to support MOF signature validation.</span></span>
2. <span data-ttu-id="a2752-177">Certifique-se de que a autoridade de certificação autorizado o signatário é fidedigna.</span><span class="sxs-lookup"><span data-stu-id="a2752-177">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="a2752-178">Transferir as dependências de recursos/módulo da configuração para uma localização temporária.</span><span class="sxs-lookup"><span data-stu-id="a2752-178">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="a2752-179">Verificar a assinatura do catálogo incluído no interior do módulo.</span><span class="sxs-lookup"><span data-stu-id="a2752-179">Verify the signature of the catalog included inside the module.</span></span>
    * <span data-ttu-id="a2752-180">Localizar um `<moduleName>.cat` de ficheiros e certifique-se a assinatura utilizando o cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span><span class="sxs-lookup"><span data-stu-id="a2752-180">Find a `<moduleName>.cat` file and verify its signature using the cmdlet  [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span></span>
    * <span data-ttu-id="a2752-181">Certifique-se de que a autoridade de certificação que autenticadas de signatário é fidedigna.</span><span class="sxs-lookup"><span data-stu-id="a2752-181">Verify the certification authority that authenticated the signer is trusted.</span></span>
    * <span data-ttu-id="a2752-182">Certifique-se de que o conteúdo dos módulos tem não foram adulterado utilizando o novo cmdlet [teste FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="a2752-182">Verify the content of the modules has not been tampered using the new cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span></span>
5. <span data-ttu-id="a2752-183">Módulo de instalação para $env: ProgramFiles\WindowsPowerShell\Modules\\</span><span class="sxs-lookup"><span data-stu-id="a2752-183">Install-Module to $env:ProgramFiles\WindowsPowerShell\Modules\\</span></span>
6. <span data-ttu-id="a2752-184">Configuração de processo</span><span class="sxs-lookup"><span data-stu-id="a2752-184">Process configuration</span></span>

> <span data-ttu-id="a2752-185">Nota: Validação da assinatura no catálogo do módulo e a configuração só é executada quando a configuração é aplicada no sistema pela primeira vez ou quando o módulo é transferido e instalado.</span><span class="sxs-lookup"><span data-stu-id="a2752-185">Note: Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span> <span data-ttu-id="a2752-186">Execuções de consistência não validam a assinatura de Current.mof ou dependências de módulo.</span><span class="sxs-lookup"><span data-stu-id="a2752-186">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span>
<span data-ttu-id="a2752-187">Se a verificação falhou em qualquer fase, por exemplo, se a configuração é retirado do servidor de solicitação não está assinado, em seguida, termina o processamento da configuração com o erro abaixo e são eliminados todos os ficheiros temporários.</span><span class="sxs-lookup"><span data-stu-id="a2752-187">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Exemplo de configuração de saída de erro](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="a2752-189">Da mesma forma, a extrair um módulo cujo catálogo não está assinado resultados no seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="a2752-189">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Módulo de saída de erro de exemplo](../images/PullUnisgnedCatalog.png)

####<a name="push"></a><span data-ttu-id="a2752-191">Push</span><span class="sxs-lookup"><span data-stu-id="a2752-191">Push</span></span>
<span data-ttu-id="a2752-192">Uma configuração fornecida utilizando a emissão poderão ser adulterada na respetiva origem antes de entregar o nó.</span><span class="sxs-lookup"><span data-stu-id="a2752-192">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span> <span data-ttu-id="a2752-193">O Gestor de configuração Local efetua os passos de validação de assinatura semelhantes para configuration(s) premido ou publicado.</span><span class="sxs-lookup"><span data-stu-id="a2752-193">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span>
<span data-ttu-id="a2752-194">Abaixo está um exemplo completo de validação da assinatura de push.</span><span class="sxs-lookup"><span data-stu-id="a2752-194">Below is a complete example of signature validation for push.</span></span>

* <span data-ttu-id="a2752-195">Ative a validação da assinatura no nó.</span><span class="sxs-lookup"><span data-stu-id="a2752-195">Enable signature validation on the node.</span></span>

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'        
    } 
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'   
        SignedItemType =  'Configuration','Module'             
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
``` 
* <span data-ttu-id="a2752-196">Crie um ficheiro de configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="a2752-196">Create a sample configuration file.</span></span>

```powershell
# Sample configuration
Configuration Test
{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

* <span data-ttu-id="a2752-197">Tente enviar o ficheiro de configuração não assinados para o nó.</span><span class="sxs-lookup"><span data-stu-id="a2752-197">Try pushing the unsigned configuration file in to the node.</span></span> 

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
``` 
![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

* <span data-ttu-id="a2752-199">Assine o ficheiro de configuração utilizando o certificado de assinatura de código.</span><span class="sxs-lookup"><span data-stu-id="a2752-199">Sign the configuration file using code-signing certificate.</span></span>

![SignMofFile](../images/SignMofFile.png)

* <span data-ttu-id="a2752-201">Tente enviar o ficheiro MOF assinado.</span><span class="sxs-lookup"><span data-stu-id="a2752-201">Try pushing the signed MOF file.</span></span>

![SignMofFile](../images/PushSignedMof.png)

