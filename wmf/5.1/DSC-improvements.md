---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Melhorias de DSC no WMF 5.1
ms.openlocfilehash: 92f82d62550e105a187fd7c0c58b49367c646a7e
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523047"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="96deb-103">Melhorias na Desired State Configuration (DSC) no WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="96deb-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="96deb-104">Aprimoramentos de recursos de classe de DSC</span><span class="sxs-lookup"><span data-stu-id="96deb-104">DSC class resource improvements</span></span>

<span data-ttu-id="96deb-105">No WMF 5.1, podemos corrigir os seguintes problemas conhecidos:</span><span class="sxs-lookup"><span data-stu-id="96deb-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="96deb-106">Get-dscconfiguration para pode devolver valores vazios (nulos) ou erros, se um tipo de tabela de hash/complexo é devolvido pela função de GET () de um recurso de DSC baseados na classe.</span><span class="sxs-lookup"><span data-stu-id="96deb-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="96deb-107">Get-dscconfiguration para devolve o erro se a credencial de RunAs é utilizada na configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="96deb-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="96deb-108">Recursos com base na classe não podem ser utilizado numa configuração composta.</span><span class="sxs-lookup"><span data-stu-id="96deb-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="96deb-109">Start-dscconfiguration para bloqueia se recursos com base na classe tem uma propriedade de seu próprio tipo.</span><span class="sxs-lookup"><span data-stu-id="96deb-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="96deb-110">Não não possível utilizar recursos com base na classe como um recurso exclusivo.</span><span class="sxs-lookup"><span data-stu-id="96deb-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="96deb-111">Melhorias na depuração de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="96deb-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="96deb-112">No WMF 5.0, o depurador do PowerShell não parou o método de recursos com base na classe (Get/Set/teste) diretamente.</span><span class="sxs-lookup"><span data-stu-id="96deb-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span>
<span data-ttu-id="96deb-113">No WMF 5.1, o depurador será interrompido o método de recursos com base na classe da mesma forma que nos métodos de recursos baseados em MOF.</span><span class="sxs-lookup"><span data-stu-id="96deb-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="96deb-114">Cliente de solicitação de DSC oferece suporte a TLS 1.1 e TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="96deb-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="96deb-115">Anteriormente, o cliente de solicitação de DSC apenas suportado SSL3.0 e TLS 1.0 através de ligações de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="96deb-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span>
<span data-ttu-id="96deb-116">Quando a obrigatoriedade de usar protocolos mais seguros, o cliente de solicitação seria deixe de funcionar.</span><span class="sxs-lookup"><span data-stu-id="96deb-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span>
<span data-ttu-id="96deb-117">No WMF 5.1, o cliente de solicitação de DSC já não suporta SSL 3.0 e adiciona suporte aos protocolos mais seguros de TLS 1.1 e TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="96deb-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="96deb-118">Registo do servidor pull melhorada</span><span class="sxs-lookup"><span data-stu-id="96deb-118">Improved pull server registration</span></span>

<span data-ttu-id="96deb-119">Nas versões anteriores do WMF, pedidos de registos/reporting simultâneas de mensagens em fila para um servidor de solicitação de DSC ao utilizar a base de dados ESENT poderia levar a LCM falhar ao registar e/ou relatório.</span><span class="sxs-lookup"><span data-stu-id="96deb-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span>
<span data-ttu-id="96deb-120">Nesses casos, os registos de eventos no servidor de solicitação tem o erro "Nome da instância já em utilização."</span><span class="sxs-lookup"><span data-stu-id="96deb-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span>
<span data-ttu-id="96deb-121">Isto foi devido a um padrão incorreto a ser utilizado para aceder a base de dados ESENT num cenário de vários threads.</span><span class="sxs-lookup"><span data-stu-id="96deb-121">This was due to an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span>
<span data-ttu-id="96deb-122">No WMF 5.1, este problema foi corrigido.</span><span class="sxs-lookup"><span data-stu-id="96deb-122">In WMF 5.1, this issue has been fixed.</span></span>
<span data-ttu-id="96deb-123">Registos em simultâneo ou geração de relatórios (envolvendo a base de dados ESENT) funciona bem no WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="96deb-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span>
<span data-ttu-id="96deb-124">Este problema é aplicável apenas para a base de dados ESENT e não se aplica à base de dados OLEDB.</span><span class="sxs-lookup"><span data-stu-id="96deb-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="96deb-125">Ativar registo Circular na instância de base de dados ESENT</span><span class="sxs-lookup"><span data-stu-id="96deb-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="96deb-126">Na versão de eariler do DSC PullServer, os ficheiros de registo de base de dados ESENT foram preenchendo o espaço de disco do becouse pullserver que a instância de base de dados estava a ser criada sem o registo circular.</span><span class="sxs-lookup"><span data-stu-id="96deb-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="96deb-127">Nesta versão, tem a opção para controlar o comportamento de registo circular de instância utilizando o pullserver Web. config.</span><span class="sxs-lookup"><span data-stu-id="96deb-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="96deb-128">Por predefinição CircularLogging está definido como TRUE.</span><span class="sxs-lookup"><span data-stu-id="96deb-128">By default CircularLogging is set to TRUE.</span></span>

```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="96deb-129">Extrair a Convenção de nomenclatura de configuração parcial</span><span class="sxs-lookup"><span data-stu-id="96deb-129">Pull partial configuration naming convention</span></span>

<span data-ttu-id="96deb-130">Na versão anterior, a Convenção de nomenclatura para uma configuração parcial foi que o nome do ficheiro MOF no servidor/serviço pull deve corresponder o nome da configuração parcial especificado nas definições do Gestor de configuração local que por sua vez tem de corresponder a nome da configuração incorporada no ficheiro MOF.</span><span class="sxs-lookup"><span data-stu-id="96deb-130">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="96deb-131">Ver os instantâneos abaixo:</span><span class="sxs-lookup"><span data-stu-id="96deb-131">See the snapshots below:</span></span>

- <span data-ttu-id="96deb-132">Definições de configuração local que define uma configuração parcial que um nó está autorizado a receber.</span><span class="sxs-lookup"><span data-stu-id="96deb-132">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

![Metaconfiguration de exemplo](../images/MetaConfigPartialOne.png)

- <span data-ttu-id="96deb-134">Definição de configuração parcial de exemplo</span><span class="sxs-lookup"><span data-stu-id="96deb-134">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="96deb-135">"ConfigurationName" incorporado no ficheiro MOF gerado.</span><span class="sxs-lookup"><span data-stu-id="96deb-135">'ConfigurationName' embedded in the generated MOF file.</span></span>

![Ficheiro mof gerado de exemplo](../images/PartialGeneratedMof.png)

- <span data-ttu-id="96deb-137">Nome de ficheiro no repositório de configuração de solicitação</span><span class="sxs-lookup"><span data-stu-id="96deb-137">FileName in the pull configuration repository</span></span>

![Nome do ficheiro no repositório de configuração](../images/PartialInConfigRepository.png)

<span data-ttu-id="96deb-139">Nome do serviço de automatização do Azure gerado ficheiros MOF como `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="96deb-139">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="96deb-140">Portanto, a configuração abaixo é compilado para PartialOne.localhost.mof.</span><span class="sxs-lookup"><span data-stu-id="96deb-140">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

<span data-ttu-id="96deb-141">Isso tornou impossível para solicitação um da sua configuração parcial do serviço de automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="96deb-141">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

<span data-ttu-id="96deb-142">No WMF 5.1, uma configuração parcial no servidor/serviço de solicitação pode ser nomeada como `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="96deb-142">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="96deb-143">Além disso, se uma máquina é extrair uma única configuração de uma solicitação, em seguida, o ficheiro de configuração sobre o repositório de configuração do servidor de solicitação de serviço/servidor pode ter qualquer nome de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="96deb-143">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span>
<span data-ttu-id="96deb-144">Essa flexibilidade nomenclatura permite-lhe gerir os nós parcialmente pelo serviço de automatização do Azure, onde alguma configuração para o seu nó estará disponível no DSC de automatização do Azure e com uma configuração parcial por si localmente.</span><span class="sxs-lookup"><span data-stu-id="96deb-144">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

<span data-ttu-id="96deb-145">Metaconfiguration abaixo configura um nó a ser geridas tanto localmente, bem como pela automatização do Azure de serviço.</span><span class="sxs-lookup"><span data-stu-id="96deb-145">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="96deb-146">Utilizar PsDscRunAsCredential com recursos compostos de DSC</span><span class="sxs-lookup"><span data-stu-id="96deb-146">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="96deb-147">Foi adicionado suporte para usar [ *PsDscRunAsCredential* ](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) com DSC [compostos](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) recursos.</span><span class="sxs-lookup"><span data-stu-id="96deb-147">We have added support for using [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) with DSC [Composite](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="96deb-148">Agora pode especificar um valor para PsDscRunAsCredential ao utilizar recursos compostos dentro de configurações.</span><span class="sxs-lookup"><span data-stu-id="96deb-148">You can now specify a value for PsDscRunAsCredential when using composite resources inside configurations.</span></span>
<span data-ttu-id="96deb-149">Quando especificado, todos os recursos é executado dentro de um recurso composto como um utilizador de RunAs.</span><span class="sxs-lookup"><span data-stu-id="96deb-149">When specified, all resources run inside a composite resource as a RunAs user.</span></span>
<span data-ttu-id="96deb-150">Se um recurso composto chama outro recurso composto, todos os respetivos recursos também são executados como usuário de RunAs.</span><span class="sxs-lookup"><span data-stu-id="96deb-150">If a composite resource calls another composite resource, all of its resources are also executed as RunAs user.</span></span>
<span data-ttu-id="96deb-151">As credenciais de RunAs são propagadas para qualquer nível na hierarquia de recursos compostos.</span><span class="sxs-lookup"><span data-stu-id="96deb-151">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span>
<span data-ttu-id="96deb-152">Se todos os recursos dentro de um recurso composto Especifica o seu próprio valor para PsDscRunAsCredential, um erro de intercalação resulta durante a compilação de configuração.</span><span class="sxs-lookup"><span data-stu-id="96deb-152">If any resource inside a composite resource specifies its own value for PsDscRunAsCredential, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="96deb-153">Este exemplo mostra a utilização com [WindowsFeatureSet](https://msdn.microsoft.com/powershell/wmf/dsc_newresources) compostos recursos incluídos no módulo PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="96deb-153">This example shows usage with [WindowsFeatureSet](https://msdn.microsoft.com/powershell/wmf/dsc_newresources) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="96deb-154">Módulo de DSC e a configuração validações de assinatura</span><span class="sxs-lookup"><span data-stu-id="96deb-154">DSC module and configuration signing validations</span></span>

<span data-ttu-id="96deb-155">No DSC, configurações e os módulos são distribuídos por computadores gerenciados do servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="96deb-155">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span>
<span data-ttu-id="96deb-156">Se o servidor de solicitação for comprometido, um invasor pode potencialmente modificar as configurações e os módulos no servidor de solicitação e fazer com que ele distribuídas para todos os nós geridos, comprometer todos eles.</span><span class="sxs-lookup"><span data-stu-id="96deb-156">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes, compromising all of them.</span></span>

<span data-ttu-id="96deb-157">No WMF 5.1, DSC oferece suporte a validar as assinaturas digitais em catálogo e a configuração (. Ficheiros MOF).</span><span class="sxs-lookup"><span data-stu-id="96deb-157">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span>
<span data-ttu-id="96deb-158">Esse recurso evita que nós de execução configurações ou arquivos de módulo que não estejam assinado por um signatário confiável ou que tenham sido adulterado depois que eles estejam assinados por signatário fidedigno.</span><span class="sxs-lookup"><span data-stu-id="96deb-158">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="96deb-159">A configuração de início de sessão e módulo</span><span class="sxs-lookup"><span data-stu-id="96deb-159">How to sign configuration and module</span></span>

***
* <span data-ttu-id="96deb-160">Ficheiros de configuração (. MOFs): O cmdlet do PowerShell existente [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) é expandido para suportar a assinatura de ficheiros MOF.</span><span class="sxs-lookup"><span data-stu-id="96deb-160">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) is extended to support signing of MOF files.</span></span>
* <span data-ttu-id="96deb-161">Módulos: Assinatura dos módulos é feito ao iniciar o catálogo de módulo correspondente através dos seguintes passos:</span><span class="sxs-lookup"><span data-stu-id="96deb-161">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
    1. <span data-ttu-id="96deb-162">Criar um arquivo de catálogo: um arquivo de catálogo contém uma coleção de hashes criptográficos ou thumbprints.</span><span class="sxs-lookup"><span data-stu-id="96deb-162">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span>
       <span data-ttu-id="96deb-163">Cada thumbprint corresponde a um ficheiro que está incluído no módulo.</span><span class="sxs-lookup"><span data-stu-id="96deb-163">Each thumbprint corresponds to a file that is included in the module.</span></span>
       <span data-ttu-id="96deb-164">O novo cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), foi adicionada para permitir que os utilizadores criar um arquivo de catálogo para o módulo.</span><span class="sxs-lookup"><span data-stu-id="96deb-164">The new cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), has been added to enable users to create a catalog file for their module.</span></span>
    2. <span data-ttu-id="96deb-165">Assinar o ficheiro de catálogo: uso [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) para assinar o ficheiro de catálogo.</span><span class="sxs-lookup"><span data-stu-id="96deb-165">Sign the catalog file: Use [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) to sign the catalog file.</span></span>
    3. <span data-ttu-id="96deb-166">Coloque o arquivo de catálogo dentro da pasta do módulo.</span><span class="sxs-lookup"><span data-stu-id="96deb-166">Place the catalog file inside the module folder.</span></span>
<span data-ttu-id="96deb-167">Por convenção, o arquivo de catálogo de módulo deve ser colocado sob a pasta de módulo com o mesmo nome que o módulo.</span><span class="sxs-lookup"><span data-stu-id="96deb-167">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="96deb-168">Definições de LocalConfigurationManager para ativar a assinatura de validações</span><span class="sxs-lookup"><span data-stu-id="96deb-168">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="96deb-169">Extração</span><span class="sxs-lookup"><span data-stu-id="96deb-169">Pull</span></span>

<span data-ttu-id="96deb-170">LocalConfigurationManager de um nó efetua a validação de assinatura de módulos e configurações com base nas definições de atuais.</span><span class="sxs-lookup"><span data-stu-id="96deb-170">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span>
<span data-ttu-id="96deb-171">Por predefinição, a validação da assinatura está desativada.</span><span class="sxs-lookup"><span data-stu-id="96deb-171">By default, signature validation is disabled.</span></span>
<span data-ttu-id="96deb-172">Validação da assinatura pode habilitado adicionando-o bloco de 'SignatureValidation' para a definição de meta-configuração do nó conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="96deb-172">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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
        # If the TrustedStorePath property is provided then LCM will use the custom path. Otherwise, the LCM will use default trusted store path (Cert:\LocalMachine\DSCStore) to find the signing certificate.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

<span data-ttu-id="96deb-173">Definir o metaconfiguration acima num nó permite que a validação da assinatura nas configurações transferidas e módulos.</span><span class="sxs-lookup"><span data-stu-id="96deb-173">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span>
<span data-ttu-id="96deb-174">O Gestor de configuração Local executa os seguintes passos para verificar as assinaturas digitais.</span><span class="sxs-lookup"><span data-stu-id="96deb-174">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="96deb-175">Verificar a assinatura num arquivo de configuração (. MOF) é válido.</span><span class="sxs-lookup"><span data-stu-id="96deb-175">Verify the signature on a configuration file (.MOF) is valid.</span></span>
   <span data-ttu-id="96deb-176">Ele usa o cmdlet do PowerShell [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), que é estendido de 5.1 para oferecer suporte a validação de assinatura do MOF.</span><span class="sxs-lookup"><span data-stu-id="96deb-176">It uses the PowerShell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), which is extended in 5.1 to support MOF signature validation.</span></span>
2. <span data-ttu-id="96deb-177">Certifique-se de que a autoridade de certificação que autorizado o signatário é fidedigna.</span><span class="sxs-lookup"><span data-stu-id="96deb-177">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="96deb-178">Baixe as dependências do módulo/recurso da configuração num local temporário.</span><span class="sxs-lookup"><span data-stu-id="96deb-178">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="96deb-179">Verificar a assinatura do catálogo incluída dentro do módulo.</span><span class="sxs-lookup"><span data-stu-id="96deb-179">Verify the signature of the catalog included inside the module.</span></span>
    * <span data-ttu-id="96deb-180">Encontrar um `<moduleName>.cat` de ficheiros e certifique-se a sua assinatura usando o cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span><span class="sxs-lookup"><span data-stu-id="96deb-180">Find a `<moduleName>.cat` file and verify its signature using the cmdlet  [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span></span>
    * <span data-ttu-id="96deb-181">Certifique-se de que a autoridade de certificação que autenticou o signatário é fidedigna.</span><span class="sxs-lookup"><span data-stu-id="96deb-181">Verify the certification authority that authenticated the signer is trusted.</span></span>
    * <span data-ttu-id="96deb-182">Certifique-se de que o conteúdo dos módulos não tem sido adulterado, usando o novo cmdlet [teste FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="96deb-182">Verify the content of the modules has not been tampered using the new cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span></span>
5. <span data-ttu-id="96deb-183">Install-Module para $env: ProgramFiles\WindowsPowerShell\Modules\\</span><span class="sxs-lookup"><span data-stu-id="96deb-183">Install-Module to $env:ProgramFiles\WindowsPowerShell\Modules\\</span></span>
6. <span data-ttu-id="96deb-184">Configuração do processo</span><span class="sxs-lookup"><span data-stu-id="96deb-184">Process configuration</span></span>

> <span data-ttu-id="96deb-185">Nota: Validação da assinatura no catálogo de módulo e a configuração só é executada quando a configuração é aplicada ao sistema pela primeira vez ou quando o módulo é transferido e instalado.</span><span class="sxs-lookup"><span data-stu-id="96deb-185">Note: Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
<span data-ttu-id="96deb-186">Execuções de consistência não validam a assinatura de Current.mof ou as respetivas dependências do módulo.</span><span class="sxs-lookup"><span data-stu-id="96deb-186">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span>
<span data-ttu-id="96deb-187">Se a verificação falhou em qualquer fase, por exemplo, se a configuração obtido a partir do servidor de solicitação não está assinado, em seguida, termina de processamento da configuração com o erro mostrado abaixo e são eliminados todos os ficheiros temporários.</span><span class="sxs-lookup"><span data-stu-id="96deb-187">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Exemplo de configuração de saída de erro](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="96deb-189">Da mesma forma, a extração de um módulo cujo catálogo não está assinado resultados no seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="96deb-189">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Módulo de saída de erro de exemplo](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="96deb-191">Push</span><span class="sxs-lookup"><span data-stu-id="96deb-191">Push</span></span>

<span data-ttu-id="96deb-192">Uma configuração fornecida utilizando a instalação push poderá ser adulterada na origem antes de ela entregue para o nó.</span><span class="sxs-lookup"><span data-stu-id="96deb-192">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span>
<span data-ttu-id="96deb-193">O Gestor de configuração Local executa os passos de validação de assinatura semelhante para configuração ou configurações migradas enviada por push ou publicadas.</span><span class="sxs-lookup"><span data-stu-id="96deb-193">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span>
<span data-ttu-id="96deb-194">Segue-se um exemplo completo de validação de assinatura para push.</span><span class="sxs-lookup"><span data-stu-id="96deb-194">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="96deb-195">Ative a validação de assinatura no nó.</span><span class="sxs-lookup"><span data-stu-id="96deb-195">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="96deb-196">Crie um ficheiro de configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="96deb-196">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="96deb-197">Tente enviar o ficheiro de configuração não assinados para o nó.</span><span class="sxs-lookup"><span data-stu-id="96deb-197">Try pushing the unsigned configuration file in to the node.</span></span>

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```

![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- <span data-ttu-id="96deb-199">Assinar o ficheiro de configuração com o certificado de assinatura de código.</span><span class="sxs-lookup"><span data-stu-id="96deb-199">Sign the configuration file using code-signing certificate.</span></span>

![SignMofFile](../images/SignMofFile.png)

- <span data-ttu-id="96deb-201">Tente enviar o ficheiro assinado da MOF.</span><span class="sxs-lookup"><span data-stu-id="96deb-201">Try pushing the signed MOF file.</span></span>

![SignMofFile](../images/PushSignedMof.png)
