---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Melhorias de DSC no WMF 5.1
ms.openlocfilehash: e7f20bfa865777aeac8f083959782317cfdf6cde
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856232"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="be1fa-103">Melhorias na Desired State Configuration (DSC) no WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="be1fa-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="be1fa-104">Aprimoramentos de recursos de classe de DSC</span><span class="sxs-lookup"><span data-stu-id="be1fa-104">DSC class resource improvements</span></span>

<span data-ttu-id="be1fa-105">No WMF 5.1, podemos corrigir os seguintes problemas conhecidos:</span><span class="sxs-lookup"><span data-stu-id="be1fa-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="be1fa-106">Get-dscconfiguration para pode devolver valores vazios (nulos) ou erros, se um tipo de tabela de hash/complexo é devolvido pela função de GET () de um recurso de DSC baseados na classe.</span><span class="sxs-lookup"><span data-stu-id="be1fa-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="be1fa-107">Get-dscconfiguration para devolve o erro se a credencial de RunAs é utilizada na configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="be1fa-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="be1fa-108">Recursos com base na classe não podem ser utilizado numa configuração composta.</span><span class="sxs-lookup"><span data-stu-id="be1fa-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="be1fa-109">Start-dscconfiguration para bloqueia se recursos com base na classe tem uma propriedade de seu próprio tipo.</span><span class="sxs-lookup"><span data-stu-id="be1fa-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="be1fa-110">Não não possível utilizar recursos com base na classe como um recurso exclusivo.</span><span class="sxs-lookup"><span data-stu-id="be1fa-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="be1fa-111">Melhorias na depuração de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="be1fa-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="be1fa-112">No WMF 5.0, o depurador do PowerShell não parou o método de recursos com base na classe (Get/Set/teste) diretamente.</span><span class="sxs-lookup"><span data-stu-id="be1fa-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span> <span data-ttu-id="be1fa-113">No WMF 5.1, o depurador será interrompido o método de recursos com base na classe da mesma forma que nos métodos de recursos baseados em MOF.</span><span class="sxs-lookup"><span data-stu-id="be1fa-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="be1fa-114">Cliente de solicitação de DSC oferece suporte a TLS 1.1 e TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="be1fa-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="be1fa-115">Anteriormente, o cliente de solicitação de DSC apenas suportado SSL3.0 e TLS 1.0 através de ligações de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="be1fa-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span> <span data-ttu-id="be1fa-116">Quando a obrigatoriedade de usar protocolos mais seguros, o cliente de solicitação seria deixe de funcionar.</span><span class="sxs-lookup"><span data-stu-id="be1fa-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span> <span data-ttu-id="be1fa-117">No WMF 5.1, o cliente de solicitação de DSC já não suporta SSL 3.0 e adiciona suporte aos protocolos mais seguros de TLS 1.1 e TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="be1fa-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="be1fa-118">Registo do servidor pull melhorada</span><span class="sxs-lookup"><span data-stu-id="be1fa-118">Improved pull server registration</span></span>

<span data-ttu-id="be1fa-119">Nas versões anteriores do WMF, pedidos de registos/reporting simultâneas de mensagens em fila para um servidor de solicitação de DSC ao utilizar a base de dados ESENT poderia levar a LCM falhar ao registar e/ou relatório.</span><span class="sxs-lookup"><span data-stu-id="be1fa-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span> <span data-ttu-id="be1fa-120">Nesses casos, os registos de eventos no servidor de solicitação tem o erro "Nome da instância já em utilização."</span><span class="sxs-lookup"><span data-stu-id="be1fa-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span> <span data-ttu-id="be1fa-121">Isto foi provocado por um padrão incorreto a ser utilizado para aceder a base de dados ESENT num cenário de vários threads.</span><span class="sxs-lookup"><span data-stu-id="be1fa-121">This was caused by an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span> <span data-ttu-id="be1fa-122">No WMF 5.1, este problema foi corrigido.</span><span class="sxs-lookup"><span data-stu-id="be1fa-122">In WMF 5.1, this issue has been fixed.</span></span> <span data-ttu-id="be1fa-123">Registos em simultâneo ou geração de relatórios (envolvendo a base de dados ESENT) funciona bem no WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="be1fa-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span> <span data-ttu-id="be1fa-124">Este problema é aplicável apenas para a base de dados ESENT e não se aplica à base de dados OLEDB.</span><span class="sxs-lookup"><span data-stu-id="be1fa-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="be1fa-125">Ativar registo Circular na instância de base de dados ESENT</span><span class="sxs-lookup"><span data-stu-id="be1fa-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="be1fa-126">Na versão de eariler do DSC PullServer, os ficheiros de registo de base de dados ESENT foram preenchendo o espaço de disco do becouse pullserver que a instância de base de dados estava a ser criada sem o registo circular.</span><span class="sxs-lookup"><span data-stu-id="be1fa-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="be1fa-127">Nesta versão, tem a opção para controlar o comportamento de registo circular de instância utilizando o pullserver Web. config.</span><span class="sxs-lookup"><span data-stu-id="be1fa-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="be1fa-128">Por predefinição CircularLogging está definido como TRUE.</span><span class="sxs-lookup"><span data-stu-id="be1fa-128">By default CircularLogging is set to TRUE.</span></span>

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a><span data-ttu-id="be1fa-129">Suporte WOW64 para palavra-chave de configuração</span><span class="sxs-lookup"><span data-stu-id="be1fa-129">WOW64 support for Configuration Keyword</span></span>

<span data-ttu-id="be1fa-130">O `Configuration` palavra-chave é agora suportada em WOW64 num computador de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="be1fa-130">The `Configuration` keyword is now supported in WOW64 on a 64-bit computer.</span></span> <span data-ttu-id="be1fa-131">Isso significa que uma configuração de DSC pode ser definida e compilada num 32-bit processo, como o Windows PowerShell ISE (x86) em execução num computador de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="be1fa-131">This means that a DSC configuration can be defined and compiled within a 32-bit process such as Windows PowerShell ISE (x86) running on a 64-bit computer.</span></span>

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="be1fa-132">Extrair a Convenção de nomenclatura de configuração parcial</span><span class="sxs-lookup"><span data-stu-id="be1fa-132">Pull partial configuration naming convention</span></span>

<span data-ttu-id="be1fa-133">Na versão anterior, a Convenção de nomenclatura para uma configuração parcial foi que o nome do ficheiro MOF no servidor/serviço pull deve corresponder o nome da configuração parcial especificado nas definições do Gestor de configuração local que por sua vez tem de corresponder a nome da configuração incorporada no ficheiro MOF.</span><span class="sxs-lookup"><span data-stu-id="be1fa-133">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="be1fa-134">Ver os instantâneos abaixo:</span><span class="sxs-lookup"><span data-stu-id="be1fa-134">See the snapshots below:</span></span>

- <span data-ttu-id="be1fa-135">Definições de configuração local que define uma configuração parcial que um nó está autorizado a receber.</span><span class="sxs-lookup"><span data-stu-id="be1fa-135">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

  ![Metaconfiguration de exemplo](../images/MetaConfigPartialOne.png)

- <span data-ttu-id="be1fa-137">Definição de configuração parcial de exemplo</span><span class="sxs-lookup"><span data-stu-id="be1fa-137">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="be1fa-138">"ConfigurationName" incorporado no ficheiro MOF gerado.</span><span class="sxs-lookup"><span data-stu-id="be1fa-138">'ConfigurationName' embedded in the generated MOF file.</span></span>

  ![Ficheiro mof gerado de exemplo](../images/PartialGeneratedMof.png)

- <span data-ttu-id="be1fa-140">Nome de ficheiro no repositório de configuração de solicitação</span><span class="sxs-lookup"><span data-stu-id="be1fa-140">FileName in the pull configuration repository</span></span>

  ![Nome do ficheiro no repositório de configuração](../images/PartialInConfigRepository.png)

  <span data-ttu-id="be1fa-142">Nome do serviço de automatização do Azure gerado ficheiros MOF como `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="be1fa-142">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="be1fa-143">Portanto, a configuração abaixo é compilado para PartialOne.localhost.mof.</span><span class="sxs-lookup"><span data-stu-id="be1fa-143">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

  <span data-ttu-id="be1fa-144">Isso tornou impossível para solicitação um da sua configuração parcial do serviço de automatização do Azure.</span><span class="sxs-lookup"><span data-stu-id="be1fa-144">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

  <span data-ttu-id="be1fa-145">No WMF 5.1, uma configuração parcial no servidor/serviço de solicitação pode ser nomeada como `<ConfigurationName>.<NodeName>.mof`.</span><span class="sxs-lookup"><span data-stu-id="be1fa-145">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="be1fa-146">Além disso, se uma máquina é extrair uma única configuração de uma solicitação, em seguida, o ficheiro de configuração sobre o repositório de configuração do servidor de solicitação de serviço/servidor pode ter qualquer nome de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="be1fa-146">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span> <span data-ttu-id="be1fa-147">Essa flexibilidade nomenclatura permite-lhe gerir os nós parcialmente pelo serviço de automatização do Azure, onde alguma configuração para o seu nó estará disponível no DSC de automatização do Azure e com uma configuração parcial por si localmente.</span><span class="sxs-lookup"><span data-stu-id="be1fa-147">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

  <span data-ttu-id="be1fa-148">Metaconfiguration abaixo configura um nó a ser geridas tanto localmente, bem como pela automatização do Azure de serviço.</span><span class="sxs-lookup"><span data-stu-id="be1fa-148">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="be1fa-149">Utilizar PsDscRunAsCredential com recursos compostos de DSC</span><span class="sxs-lookup"><span data-stu-id="be1fa-149">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="be1fa-150">Foi adicionado suporte para usar [PsDscRunAsCredential](/powershell/dsc/configurations/runAsUser) com o DSC [compostos](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) recursos.</span><span class="sxs-lookup"><span data-stu-id="be1fa-150">We have added support for using [PsDscRunAsCredential](/powershell/dsc/configurations/runAsUser) with DSC [Composite](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="be1fa-151">Agora pode especificar um valor para **PsDscRunAsCredential** ao utilizar recursos compostos dentro de configurações.</span><span class="sxs-lookup"><span data-stu-id="be1fa-151">You can now specify a value for **PsDscRunAsCredential** when using composite resources inside configurations.</span></span> <span data-ttu-id="be1fa-152">Quando especificado, todos os recursos é executado dentro de um recurso composto como um utilizador de RunAs.</span><span class="sxs-lookup"><span data-stu-id="be1fa-152">When specified, all resources run inside a composite resource as a RunAs user.</span></span> <span data-ttu-id="be1fa-153">Se um recurso composto chama outro recurso composto, todos esses recursos também são executados como usuário de RunAs.</span><span class="sxs-lookup"><span data-stu-id="be1fa-153">If a composite resource calls another composite resource, all those resources are also executed as RunAs user.</span></span> <span data-ttu-id="be1fa-154">As credenciais de RunAs são propagadas para qualquer nível na hierarquia de recursos compostos.</span><span class="sxs-lookup"><span data-stu-id="be1fa-154">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span> <span data-ttu-id="be1fa-155">Se todos os recursos dentro de um recurso composto Especifica o seu próprio valor para **PsDscRunAsCredential**, resultados de um erro de intercalação durante a compilação de configuração.</span><span class="sxs-lookup"><span data-stu-id="be1fa-155">If any resource inside a composite resource specifies its own value for **PsDscRunAsCredential**, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="be1fa-156">Este exemplo mostra a utilização com o [WindowsFeatureSet](/powershell/dsc/reference/resources/windows/windowsfeaturesetresource) compostos recursos incluídos no módulo PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="be1fa-156">This example shows usage with the [WindowsFeatureSet](/powershell/dsc/reference/resources/windows/windowsfeaturesetresource) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="be1fa-157">Permitindo para recursos duplicados idênticos numa configuração</span><span class="sxs-lookup"><span data-stu-id="be1fa-157">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="be1fa-158">DSC não permitir nem lidar com definições em conflito de recursos dentro de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="be1fa-158">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="be1fa-159">Em vez de tentar resolver o conflito, simplesmente falhará.</span><span class="sxs-lookup"><span data-stu-id="be1fa-159">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="be1fa-160">Como a reutilização de configuração se torna mais utilizada por meio de recursos compostos, conflitos etc. ocorrerá com mais frequência.</span><span class="sxs-lookup"><span data-stu-id="be1fa-160">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="be1fa-161">Quando as definições de recursos em conflito são idênticas, DSC deve ser inteligente e permitir isso.</span><span class="sxs-lookup"><span data-stu-id="be1fa-161">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="be1fa-162">Com esta versão, oferecemos suporte a ter várias instâncias de recursos que têm definições idênticas:</span><span class="sxs-lookup"><span data-stu-id="be1fa-162">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="be1fa-163">Em versões anteriores, o resultado seria uma compilação com falhas devido a um conflito entre o WindowsFeature FE_IIS e instâncias de WindowsFeature Worker_IIS tentando Certifique-se a função de "servidor Web está instalada.</span><span class="sxs-lookup"><span data-stu-id="be1fa-163">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="be1fa-164">Tenha em atenção que *todos os* das propriedades que estão a ser configuradas são idênticos nessas duas configurações.</span><span class="sxs-lookup"><span data-stu-id="be1fa-164">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="be1fa-165">Uma vez que *todos os* as propriedades desses dois recursos são idênticos, tal resultará numa compilação bem-sucedida agora.</span><span class="sxs-lookup"><span data-stu-id="be1fa-165">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="be1fa-166">Se qualquer uma das propriedades são diferentes entre os dois recursos, eles não serão considerados idênticos e compilação irá falhar.</span><span class="sxs-lookup"><span data-stu-id="be1fa-166">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail.</span></span>

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="be1fa-167">Módulo de DSC e a configuração validações de assinatura</span><span class="sxs-lookup"><span data-stu-id="be1fa-167">DSC module and configuration signing validations</span></span>

<span data-ttu-id="be1fa-168">No DSC, configurações e os módulos são distribuídos por computadores gerenciados do servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="be1fa-168">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span> <span data-ttu-id="be1fa-169">Se o servidor de solicitação for comprometido, um invasor pode potencialmente modificar as configurações e os módulos no servidor de solicitação e distribuí para todos os nós geridos.</span><span class="sxs-lookup"><span data-stu-id="be1fa-169">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes.</span></span>

<span data-ttu-id="be1fa-170">No WMF 5.1, DSC oferece suporte a validar as assinaturas digitais em catálogo e a configuração (. Ficheiros MOF).</span><span class="sxs-lookup"><span data-stu-id="be1fa-170">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span> <span data-ttu-id="be1fa-171">Esse recurso evita que nós de execução configurações ou arquivos de módulo que não estejam assinado por um signatário confiável ou que tenham sido adulterado depois que eles estejam assinados por signatário fidedigno.</span><span class="sxs-lookup"><span data-stu-id="be1fa-171">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="be1fa-172">A configuração de início de sessão e módulo</span><span class="sxs-lookup"><span data-stu-id="be1fa-172">How to sign configuration and module</span></span>

- <span data-ttu-id="be1fa-173">Ficheiros de configuração (. MOFs): O cmdlet do PowerShell existente [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) é expandido para suportar a assinatura de ficheiros MOF.</span><span class="sxs-lookup"><span data-stu-id="be1fa-173">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) is extended to support signing of MOF files.</span></span>
- <span data-ttu-id="be1fa-174">Módulos: Assinatura de módulos é feito ao iniciar o catálogo de módulo correspondente através dos seguintes passos:</span><span class="sxs-lookup"><span data-stu-id="be1fa-174">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
  1. <span data-ttu-id="be1fa-175">Crie um ficheiro de catálogo: Um arquivo de catálogo contém uma coleção de hashes criptográficos ou thumbprints.</span><span class="sxs-lookup"><span data-stu-id="be1fa-175">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span> <span data-ttu-id="be1fa-176">Cada thumbprint corresponde a um ficheiro que está incluído no módulo.</span><span class="sxs-lookup"><span data-stu-id="be1fa-176">Each thumbprint corresponds to a file that is included in the module.</span></span> <span data-ttu-id="be1fa-177">O novo cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), foi adicionada para permitir que os utilizadores criar um arquivo de catálogo para o módulo.</span><span class="sxs-lookup"><span data-stu-id="be1fa-177">The new cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), has been added to enable users to create a catalog file for their module.</span></span>
  2. <span data-ttu-id="be1fa-178">Assinar o ficheiro de catálogo: Uso [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) para assinar o ficheiro de catálogo.</span><span class="sxs-lookup"><span data-stu-id="be1fa-178">Sign the catalog file: Use [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) to sign the catalog file.</span></span>
  3. <span data-ttu-id="be1fa-179">Coloque o arquivo de catálogo dentro da pasta do módulo.</span><span class="sxs-lookup"><span data-stu-id="be1fa-179">Place the catalog file inside the module folder.</span></span> <span data-ttu-id="be1fa-180">Por convenção, o arquivo de catálogo de módulo deve ser colocado sob a pasta de módulo com o mesmo nome que o módulo.</span><span class="sxs-lookup"><span data-stu-id="be1fa-180">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="be1fa-181">Definições de LocalConfigurationManager para ativar a assinatura de validações</span><span class="sxs-lookup"><span data-stu-id="be1fa-181">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="be1fa-182">Extração</span><span class="sxs-lookup"><span data-stu-id="be1fa-182">Pull</span></span>

<span data-ttu-id="be1fa-183">LocalConfigurationManager de um nó efetua a validação de assinatura de módulos e configurações com base nas definições de atuais.</span><span class="sxs-lookup"><span data-stu-id="be1fa-183">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span> <span data-ttu-id="be1fa-184">Por predefinição, a validação da assinatura está desativada.</span><span class="sxs-lookup"><span data-stu-id="be1fa-184">By default, signature validation is disabled.</span></span> <span data-ttu-id="be1fa-185">Validação da assinatura pode habilitado adicionando-o bloco de 'SignatureValidation' para a definição de meta-configuração do nó conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="be1fa-185">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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

<span data-ttu-id="be1fa-186">Definir o metaconfiguration acima num nó permite que a validação da assinatura nas configurações transferidas e módulos.</span><span class="sxs-lookup"><span data-stu-id="be1fa-186">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span> <span data-ttu-id="be1fa-187">O Gestor de configuração Local executa os seguintes passos para verificar as assinaturas digitais.</span><span class="sxs-lookup"><span data-stu-id="be1fa-187">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="be1fa-188">Verificar a assinatura num arquivo de configuração (. MOF) é válido com a `Get-AuthenticodeSignature` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="be1fa-188">Verify the signature on a configuration file (.MOF) is valid using the `Get-AuthenticodeSignature` cmdlet.</span></span>
2. <span data-ttu-id="be1fa-189">Certifique-se de que a autoridade de certificação que autorizado o signatário é fidedigna.</span><span class="sxs-lookup"><span data-stu-id="be1fa-189">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="be1fa-190">Baixe as dependências do módulo/recurso da configuração num local temporário.</span><span class="sxs-lookup"><span data-stu-id="be1fa-190">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="be1fa-191">Verificar a assinatura do catálogo incluída dentro do módulo.</span><span class="sxs-lookup"><span data-stu-id="be1fa-191">Verify the signature of the catalog included inside the module.</span></span>
   - <span data-ttu-id="be1fa-192">Encontrar um `<moduleName>.cat` de ficheiros e certifique-se de que sua assinatura usando `Get-AuthenticodeSignature`.</span><span class="sxs-lookup"><span data-stu-id="be1fa-192">Find a `<moduleName>.cat` file and verify its signature using `Get-AuthenticodeSignature`.</span></span>
   - <span data-ttu-id="be1fa-193">Certifique-se de que a autoridade de certificação que autenticou o signatário é fidedigna.</span><span class="sxs-lookup"><span data-stu-id="be1fa-193">Verify the certification authority that authenticated the signer is trusted.</span></span>
   - <span data-ttu-id="be1fa-194">Certifique-se de que o conteúdo dos módulos não tem sido adulterado, usando o novo cmdlet `Test-FileCatalog`.</span><span class="sxs-lookup"><span data-stu-id="be1fa-194">Verify the content of the modules has not been tampered using the new cmdlet `Test-FileCatalog`.</span></span>
5. <span data-ttu-id="be1fa-195">`Install-Module` Para `$env:ProgramFiles\WindowsPowerShell\Modules\`</span><span class="sxs-lookup"><span data-stu-id="be1fa-195">`Install-Module` to `$env:ProgramFiles\WindowsPowerShell\Modules\`</span></span>
6. <span data-ttu-id="be1fa-196">Configuração do processo</span><span class="sxs-lookup"><span data-stu-id="be1fa-196">Process configuration</span></span>

> [!NOTE]
> <span data-ttu-id="be1fa-197">Validação da assinatura no catálogo de módulo e a configuração só é executada quando a configuração é aplicada ao sistema pela primeira vez ou quando o módulo é transferido e instalado.</span><span class="sxs-lookup"><span data-stu-id="be1fa-197">Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
> <span data-ttu-id="be1fa-198">Execuções de consistência não validam a assinatura de Current.mof ou as respetivas dependências do módulo.</span><span class="sxs-lookup"><span data-stu-id="be1fa-198">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span> <span data-ttu-id="be1fa-199">Se a verificação falhou em qualquer fase, por exemplo, se a configuração obtido a partir do servidor de solicitação não está assinado, em seguida, termina de processamento da configuração com o erro mostrado abaixo e são eliminados todos os ficheiros temporários.</span><span class="sxs-lookup"><span data-stu-id="be1fa-199">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Exemplo de configuração de saída de erro](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="be1fa-201">Da mesma forma, a extração de um módulo cujo catálogo não está assinado resultados no seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="be1fa-201">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Módulo de saída de erro de exemplo](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="be1fa-203">Push</span><span class="sxs-lookup"><span data-stu-id="be1fa-203">Push</span></span>

<span data-ttu-id="be1fa-204">Uma configuração fornecida utilizando a instalação push poderá ser adulterada na origem antes de ela entregue para o nó.</span><span class="sxs-lookup"><span data-stu-id="be1fa-204">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span> <span data-ttu-id="be1fa-205">O Gestor de configuração Local executa os passos de validação de assinatura semelhante para configuração ou configurações migradas enviada por push ou publicadas.</span><span class="sxs-lookup"><span data-stu-id="be1fa-205">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span> <span data-ttu-id="be1fa-206">Segue-se um exemplo completo de validação de assinatura para push.</span><span class="sxs-lookup"><span data-stu-id="be1fa-206">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="be1fa-207">Ative a validação de assinatura no nó.</span><span class="sxs-lookup"><span data-stu-id="be1fa-207">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="be1fa-208">Crie um ficheiro de configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="be1fa-208">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="be1fa-209">Tente enviar o ficheiro de configuração não assinados para o nó.</span><span class="sxs-lookup"><span data-stu-id="be1fa-209">Try pushing the unsigned configuration file in to the node.</span></span>

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- <span data-ttu-id="be1fa-211">Assinar o ficheiro de configuração com o certificado de assinatura de código.</span><span class="sxs-lookup"><span data-stu-id="be1fa-211">Sign the configuration file using code-signing certificate.</span></span>

  ![SignMofFile](../images/SignMofFile.png)

- <span data-ttu-id="be1fa-213">Tente enviar o ficheiro assinado da MOF.</span><span class="sxs-lookup"><span data-stu-id="be1fa-213">Try pushing the signed MOF file.</span></span>

  ![SignMofFile](../images/PushSignedMof.png)
