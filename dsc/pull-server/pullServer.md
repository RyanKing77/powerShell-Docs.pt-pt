---
ms.date: 03/04/2019
keywords: DSC, PowerShell, configuração, instalação
title: Serviço de Solicitação de DSC
ms.openlocfilehash: 865eae5813e0c7b656a4158f0b1350e60f1e3291
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986528"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="a6d1d-103">Serviço de pull de configuração de estado desejado</span><span class="sxs-lookup"><span data-stu-id="a6d1d-103">Desired State Configuration Pull Service</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6d1d-104">O servidor de pull (Windows Feature *DSC-Service*) é um componente com suporte do Windows Server, no entanto, não há planos para oferecer novos recursos ou funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-104">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="a6d1d-105">É recomendável começar a fazer a transição de clientes gerenciados para o [Azure DSC de automação](/azure/automation/automation-dsc-getting-started) (inclui recursos além do servidor de pull no Windows Server) ou uma das soluções da Comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="a6d1d-105">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="a6d1d-106">Os Configuration Manager locais podem ser gerenciados centralmente por uma solução de serviço de pull.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-106">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="a6d1d-107">Ao usar essa abordagem, o nó que está sendo gerenciado é registrado com um serviço e atribuiu uma configuração nas configurações do LCM.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-107">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="a6d1d-108">A configuração e todos os recursos de DSC necessários como dependências para a configuração são baixados para o computador e usados pelo LCM para gerenciar a configuração.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-108">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="a6d1d-109">As informações sobre o estado da máquina que está sendo gerenciada são carregadas no serviço para relatórios.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-109">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="a6d1d-110">Esse conceito é conhecido como "serviço de pull".</span><span class="sxs-lookup"><span data-stu-id="a6d1d-110">This concept is referred to as "pull service."</span></span>

<span data-ttu-id="a6d1d-111">As opções atuais para o serviço de pull incluem:</span><span class="sxs-lookup"><span data-stu-id="a6d1d-111">The current options for pull service include:</span></span>

- <span data-ttu-id="a6d1d-112">Serviço de configuração de estado desejado da automação do Azure</span><span class="sxs-lookup"><span data-stu-id="a6d1d-112">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="a6d1d-113">Um serviço de pull em execução no Windows Server</span><span class="sxs-lookup"><span data-stu-id="a6d1d-113">A pull service running on Windows Server</span></span>
- <span data-ttu-id="a6d1d-114">Soluções de código aberto mantidas pela Comunidade</span><span class="sxs-lookup"><span data-stu-id="a6d1d-114">Community maintained open-source solutions</span></span>
- <span data-ttu-id="a6d1d-115">Um compartilhamento SMB</span><span class="sxs-lookup"><span data-stu-id="a6d1d-115">An SMB share</span></span>

<span data-ttu-id="a6d1d-116">**A solução recomendada**e a opção com a maioria dos recursos disponíveis é o [Azure DSC de automação](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="a6d1d-116">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="a6d1d-117">O serviço do Azure pode gerenciar nós locais em data centers privados ou em nuvens públicas, como Azure e AWS.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-117">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="a6d1d-118">Para ambientes privados em que os servidores não podem se conectar diretamente à Internet, considere limitar o tráfego de saída para apenas o intervalo de IPS do Azure publicado (consulte [intervalos de IP do datacenter do Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="a6d1d-118">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="a6d1d-119">Os recursos do serviço online que não estão disponíveis atualmente no serviço de pull no Windows Server incluem:</span><span class="sxs-lookup"><span data-stu-id="a6d1d-119">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>

- <span data-ttu-id="a6d1d-120">Todos os dados são criptografados em trânsito e em repouso</span><span class="sxs-lookup"><span data-stu-id="a6d1d-120">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="a6d1d-121">Os certificados de cliente são criados e gerenciados automaticamente</span><span class="sxs-lookup"><span data-stu-id="a6d1d-121">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="a6d1d-122">Repositório de segredos para gerenciar centralmente [senhas/credenciais](/azure/automation/automation-credentials)ou [variáveis](/azure/automation/automation-variables) como nomes de servidor ou cadeias de conexão</span><span class="sxs-lookup"><span data-stu-id="a6d1d-122">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="a6d1d-123">Gerenciar centralmente a [configuração do LCM](../managing-nodes/metaConfig.md#basic-settings) do nó</span><span class="sxs-lookup"><span data-stu-id="a6d1d-123">Centrally manage node [LCM configuration](../managing-nodes/metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="a6d1d-124">Atribuir centralmente configurações a nós de cliente</span><span class="sxs-lookup"><span data-stu-id="a6d1d-124">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="a6d1d-125">Liberar alterações de configuração para "grupos de canário" para teste antes de alcançar a produção</span><span class="sxs-lookup"><span data-stu-id="a6d1d-125">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="a6d1d-126">Relatórios gráficos</span><span class="sxs-lookup"><span data-stu-id="a6d1d-126">Graphical reporting</span></span>
  - <span data-ttu-id="a6d1d-127">Detalhes de status no nível de granularidade do recurso de DSC</span><span class="sxs-lookup"><span data-stu-id="a6d1d-127">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="a6d1d-128">Mensagens de erro detalhadas de computadores cliente para solução de problemas</span><span class="sxs-lookup"><span data-stu-id="a6d1d-128">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="a6d1d-129">[Integração com o Azure log Analytics](/azure/automation/automation-dsc-diagnostics) para alertas, tarefas automatizadas, aplicativo Android/Ios para relatórios e alertas</span><span class="sxs-lookup"><span data-stu-id="a6d1d-129">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="a6d1d-130">Serviço de pull de DSC no Windows Server</span><span class="sxs-lookup"><span data-stu-id="a6d1d-130">DSC pull service in Windows Server</span></span>

<span data-ttu-id="a6d1d-131">É possível configurar um serviço de pull para ser executado no Windows Server.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-131">It is possible to configure a pull service to run on Windows Server.</span></span>
<span data-ttu-id="a6d1d-132">Lembre-se de que a solução de serviço de pull incluída no Windows Server inclui apenas recursos de armazenamento de configurações/módulos para baixar e capturar dados de relatório no banco de dado.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-132">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="a6d1d-133">Ele não inclui muitos dos recursos oferecidos pelo serviço no Azure e, portanto, não é uma boa ferramenta para avaliar como o serviço seria usado.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-133">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="a6d1d-134">O serviço de pull oferecido no Windows Server é um serviço Web no IIS que usa uma interface OData para disponibilizar os arquivos de configuração DSC para nós de destino quando esses nós os solicitam.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-134">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="a6d1d-135">Requisitos para usar um servidor de pull:</span><span class="sxs-lookup"><span data-stu-id="a6d1d-135">Requirements for using a pull server:</span></span>

- <span data-ttu-id="a6d1d-136">Um servidor executando:</span><span class="sxs-lookup"><span data-stu-id="a6d1d-136">A server running:</span></span>
  - <span data-ttu-id="a6d1d-137">WMF/PowerShell 4,0 ou superior</span><span class="sxs-lookup"><span data-stu-id="a6d1d-137">WMF/PowerShell 4.0 or greater</span></span>
  - <span data-ttu-id="a6d1d-138">Função de servidor do IIS</span><span class="sxs-lookup"><span data-stu-id="a6d1d-138">IIS server role</span></span>
  - <span data-ttu-id="a6d1d-139">Serviço DSC</span><span class="sxs-lookup"><span data-stu-id="a6d1d-139">DSC Service</span></span>
- <span data-ttu-id="a6d1d-140">Idealmente, alguns meios de gerar um certificado, para proteger as credenciais passadas para o Configuration Manager local (LCM) nos nós de destino</span><span class="sxs-lookup"><span data-stu-id="a6d1d-140">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="a6d1d-141">A melhor maneira de configurar o Windows Server para hospedar o serviço de pull é usar uma configuração DSC.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-141">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="a6d1d-142">Um script de exemplo é fornecido abaixo.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-142">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="a6d1d-143">Sistemas de banco de dados com suporte</span><span class="sxs-lookup"><span data-stu-id="a6d1d-143">Supported database systems</span></span>

|<span data-ttu-id="a6d1d-144">WMF 4,0</span><span class="sxs-lookup"><span data-stu-id="a6d1d-144">WMF 4.0</span></span>   |<span data-ttu-id="a6d1d-145">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="a6d1d-145">WMF 5.0</span></span>  |<span data-ttu-id="a6d1d-146">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="a6d1d-146">WMF 5.1</span></span> |<span data-ttu-id="a6d1d-147">WMF 5,1 (Windows Server Insider Preview 17090)</span><span class="sxs-lookup"><span data-stu-id="a6d1d-147">WMF 5.1 (Windows Server Insider Preview 17090)</span></span>|
|---------|---------|---------|---------|
|<span data-ttu-id="a6d1d-148">MDB</span><span class="sxs-lookup"><span data-stu-id="a6d1d-148">MDB</span></span>     |<span data-ttu-id="a6d1d-149">ESENT (padrão), MDB</span><span class="sxs-lookup"><span data-stu-id="a6d1d-149">ESENT (Default), MDB</span></span> |<span data-ttu-id="a6d1d-150">ESENT (padrão), MDB</span><span class="sxs-lookup"><span data-stu-id="a6d1d-150">ESENT (Default), MDB</span></span>|<span data-ttu-id="a6d1d-151">ESENT (padrão), SQL Server, MDB</span><span class="sxs-lookup"><span data-stu-id="a6d1d-151">ESENT (Default), SQL Server, MDB</span></span>

<span data-ttu-id="a6d1d-152">A partir da versão 17090 do [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server é uma opção com suporte para o serviço de pull (Windows Feature *DSC-Service*).</span><span class="sxs-lookup"><span data-stu-id="a6d1d-152">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span> <span data-ttu-id="a6d1d-153">Isso fornece uma nova opção para dimensionar grandes ambientes de DSC que não foram migrados para o [Azure DSC de automação](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="a6d1d-153">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> [!NOTE]
> <span data-ttu-id="a6d1d-154">SQL Server suporte não será adicionado às versões anteriores do WMF 5,1 (ou anteriores) e estará disponível apenas em versões do Windows Server maiores ou iguais a 17090.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-154">SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="a6d1d-155">Para configurar o servidor de pull para usar SQL Server, defina como `$true` e SqlConnectionString como uma cadeia de conexão de SQL Server válida.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-155">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span> <span data-ttu-id="a6d1d-156">Para obter mais informações, consulte cadeias de [conexão SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="a6d1d-156">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="a6d1d-157">Para obter um exemplo de configuração de SQL Server com **xDscWebService**, leia primeiro [usando o recurso xDscWebService](#using-the-xdscwebservice-resource) e, em seguida, examine [Sample_xDscWebServiceRegistration_UseSQLProvider. ps1 no GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="a6d1d-157">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="a6d1d-158">Usando o recurso xDscWebService</span><span class="sxs-lookup"><span data-stu-id="a6d1d-158">Using the xDscWebService resource</span></span>

<span data-ttu-id="a6d1d-159">A maneira mais fácil de configurar um servidor de pull da Web é usar o recurso **xDscWebService** , incluído no módulo **xPSDesiredStateConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="a6d1d-159">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span>
<span data-ttu-id="a6d1d-160">As etapas a seguir explicam como usar o recurso em uma configuração que configura o serviço Web.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-160">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="a6d1d-161">Chame o cmdlet [install-Module](/powershell/module/PowershellGet/Install-Module) para instalar o módulo **xPSDesiredStateConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="a6d1d-161">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span>
   > [!NOTE]
   > <span data-ttu-id="a6d1d-162">O **install-Module** está incluído no módulo **PowerShellGet** , que está incluído no PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-162">**Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="a6d1d-163">Você pode baixar o módulo **PowerShellGet** para o PowerShell 3,0 e 4,0 na versão [prévia dos módulos do PowerShell do PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="a6d1d-163">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
2. <span data-ttu-id="a6d1d-164">Obtenha um certificado SSL para o servidor de pull de DSC de uma autoridade de certificação confiável, seja na sua organização ou em uma autoridade pública.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-164">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="a6d1d-165">O certificado recebido da autoridade geralmente está no formato PFX.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-165">The certificate received from the authority is usually in the PFX format.</span></span>
3. <span data-ttu-id="a6d1d-166">Instale o certificado no nó que se tornará o servidor de pull de DSC no local padrão, que deve `CERT:\LocalMachine\My`ser.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-166">Install the certificate on the node that will become the DSC Pull server in the default location, which should be `CERT:\LocalMachine\My`.</span></span>
   - <span data-ttu-id="a6d1d-167">Anote a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-167">Make a note of the certificate thumbprint.</span></span>
4. <span data-ttu-id="a6d1d-168">Selecione um GUID a ser usado como a chave de registro.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-168">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="a6d1d-169">Para gerar um usando o PowerShell, insira o seguinte no prompt do PS e pressione `[guid]::newGuid()` Enter `New-Guid`: ou.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-169">To generate one using PowerShell enter the following at the PS prompt and press enter: `[guid]::newGuid()` or `New-Guid`.</span></span> <span data-ttu-id="a6d1d-170">Essa chave será usada por nós de cliente como uma chave compartilhada para autenticar durante o registro.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-170">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="a6d1d-171">Para obter mais informações, consulte a seção chave de registro abaixo.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-171">For more information, see the Registration Key section below.</span></span>
5. <span data-ttu-id="a6d1d-172">No ISE do PowerShell, inicie (F5) o script de configuração a seguir (incluído na pasta de exemplos do módulo xPSDesiredStateConfiguration `Sample_xDscWebServiceRegistration.ps1`como).</span><span class="sxs-lookup"><span data-stu-id="a6d1d-172">In the PowerShell ISE, start (F5) the following configuration script (included in the Examples folder of the **xPSDesiredStateConfiguration** module as `Sample_xDscWebServiceRegistration.ps1`).</span></span> <span data-ttu-id="a6d1d-173">Esse script configura o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-173">This script sets up the pull server.</span></span>

    ```powershell
    configuration Sample_xDscWebServiceRegistration
    {
        param
        (
            [string[]]$NodeName = 'localhost',

            [ValidateNotNullOrEmpty()]
            [string] $certificateThumbPrint,

            [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
        )

        Import-DSCResource -ModuleName PSDesiredStateConfiguration
        Import-DSCResource -ModuleName xPSDesiredStateConfiguration

        Node $NodeName
        {
            WindowsFeature DSCServiceFeature
            {
                Ensure = "Present"
                Name   = "DSC-Service"
            }

            xDscWebService PSDSCPullServer
            {
                Ensure                  = "Present"
                EndpointName            = "PSDSCPullServer"
                Port                    = 8080
                PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
                CertificateThumbPrint   = $certificateThumbPrint
                ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                State                   = "Started"
                DependsOn               = "[WindowsFeature]DSCServiceFeature"
                RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
                AcceptSelfSignedCertificates = $true
                UseSecurityBestPractices     = $true
                Enable32BitAppOnWin64   = $false
            }

            File RegistrationKeyFile
            {
                Ensure          = 'Present'
                Type            = 'File'
                DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
                Contents        = $RegistrationKey
            }
        }
    }
    ```

6. <span data-ttu-id="a6d1d-174">Execute a configuração, passando a impressão digital do certificado SSL como o parâmetro **certificateThumbPrint** e uma chave de registro GUID como o parâmetro **RegistrationKey** :</span><span class="sxs-lookup"><span data-stu-id="a6d1d-174">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="a6d1d-175">Chave de registro</span><span class="sxs-lookup"><span data-stu-id="a6d1d-175">Registration Key</span></span>

<span data-ttu-id="a6d1d-176">Para permitir que os nós de cliente se registrem no servidor para que eles possam usar nomes de configuração em vez de uma ID de configuração, uma chave de registro que foi criada pela configuração acima `RegistrationKeys.txt` é `C:\Program Files\WindowsPowerShell\DscService`salva em um arquivo chamado em.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-176">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="a6d1d-177">A chave de registro funciona como um segredo compartilhado usado durante o registro inicial pelo cliente com o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-177">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="a6d1d-178">O cliente irá gerar um certificado autoassinado que será usado para autenticar exclusivamente o servidor de pull depois que o registro for concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-178">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="a6d1d-179">A impressão digital desse certificado é armazenada localmente e associada à URL do servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-179">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="a6d1d-180">Não há suporte para chaves de registro no PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-180">Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="a6d1d-181">Para configurar um nó para autenticar com o servidor de pull, a chave de registro deve estar na metaconfiguração para qualquer nó de destino que será registrado com esse servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-181">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="a6d1d-182">Observe que o **RegistrationKey** na metaconfiguração abaixo é removido depois que o computador de destino foi registrado com êxito e que o valor deve corresponder ao valor armazenado no `RegistrationKeys.txt` arquivo no servidor de pull (' 140a952b-b9d6-406B-b416-e0f759c9c0e4 ' para este exemplo).</span><span class="sxs-lookup"><span data-stu-id="a6d1d-182">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value must match the value stored in the `RegistrationKeys.txt` file on the pull server ('140a952b-b9d6-406b-b416-e0f759c9c0e4' for this example).</span></span> <span data-ttu-id="a6d1d-183">Sempre trate o valor da chave de registro com segurança, pois saber que ele permite que qualquer computador de destino se registre no servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-183">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to set up pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> [!NOTE]
> <span data-ttu-id="a6d1d-184">A seção **ReportServerWeb** permite que os dados de relatório sejam enviados para o servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-184">The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="a6d1d-185">A falta da propriedade **ConfigurationId** no arquivo de metaconfiguração significa implicitamente que o servidor de pull dá suporte à versão v2 do protocolo de servidor de pull para que um registro inicial seja necessário.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-185">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="a6d1d-186">Por outro lado, a presença de uma **ConfigurationId** significa que a versão v1 do protocolo de servidor de pull é usada e não há nenhum processamento de registro.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-186">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

> [!NOTE]
> <span data-ttu-id="a6d1d-187">Em um cenário de PUSH, existe um bug na versão atual que torna necessário definir uma propriedade ConfigurationId no arquivo de metaconfiguração para nós que nunca foram registrados com um servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-187">In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="a6d1d-188">Isso forçará o protocolo de servidor de pull v1 e evitará mensagens de falha de registro.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-188">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="a6d1d-189">Colocando configurações e recursos</span><span class="sxs-lookup"><span data-stu-id="a6d1d-189">Placing configurations and resources</span></span>

<span data-ttu-id="a6d1d-190">Depois que a instalação do servidor de pull for concluída, as pastas definidas pelas propriedades **ConfigurationPath** e **ModulePath** na configuração do servidor de pull serão onde você colocará os módulos e as configurações que estarão disponíveis para o recebimento dos nós de destino.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-190">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="a6d1d-191">Esses arquivos precisam estar em um formato específico para que o servidor de pull os processe corretamente.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-191">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="a6d1d-192">Formato do pacote do módulo de recurso DSC</span><span class="sxs-lookup"><span data-stu-id="a6d1d-192">DSC resource module package format</span></span>

<span data-ttu-id="a6d1d-193">Cada módulo de recurso precisa ser compactado e nomeado de acordo com o `{Module Name}_{Module Version}.zip`padrão a seguir.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-193">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>

<span data-ttu-id="a6d1d-194">Por exemplo, um módulo chamado xWebAdminstration com uma versão de módulo de 3.1.2.0 seria nomeado `xWebAdministration_3.1.2.0.zip`.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-194">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named `xWebAdministration_3.1.2.0.zip`.</span></span>
<span data-ttu-id="a6d1d-195">Cada versão de um módulo deve estar contida em um único arquivo zip.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-195">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="a6d1d-196">Como há apenas uma única versão de um recurso em cada arquivo zip, não há suporte para o formato de módulo adicionado no WMF 5,0 com suporte para várias versões de módulo em um único diretório.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-196">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="a6d1d-197">Isso significa que, antes de empacotar módulos de recursos de DSC para uso com o servidor de pull, você precisará fazer uma pequena alteração na estrutura do diretório.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-197">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="a6d1d-198">O formato padrão dos módulos que contêm o recurso DSC no WMF `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`5,0 é.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-198">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="a6d1d-199">Antes de empacotar para o servidor de pull, remova a pasta **{módulo Version}** para que `{Module Folder}\DscResources\{DSC Resource Folder}\`o caminho se torne.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-199">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="a6d1d-200">Com essa alteração, compacte a pasta conforme descrito acima e coloque esses arquivos zip na pasta **ModulePath**</span><span class="sxs-lookup"><span data-stu-id="a6d1d-200">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="a6d1d-201">Use `New-DscChecksum {module zip file}` para criar um arquivo de soma de verificação para o módulo recém-adicionado.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-201">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="a6d1d-202">Formato MOF de configuração</span><span class="sxs-lookup"><span data-stu-id="a6d1d-202">Configuration MOF format</span></span>

<span data-ttu-id="a6d1d-203">Um arquivo MOF de configuração precisa ser emparelhado com um arquivo de soma de verificação para que um LCM em um nó de destino possa validar a configuração.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-203">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="a6d1d-204">Para criar uma soma de verificação, chame o cmdlet [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) .</span><span class="sxs-lookup"><span data-stu-id="a6d1d-204">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span></span>
<span data-ttu-id="a6d1d-205">O cmdlet usa um parâmetro **path** que especifica a pasta onde o MOF de configuração está localizado.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-205">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="a6d1d-206">O cmdlet cria um arquivo de soma `ConfigurationMOFName.mof.checksum`de verificação `ConfigurationMOFName` chamado, em que é o nome do arquivo MOF de configuração.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-206">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="a6d1d-207">Se houver mais de um arquivo MOF de configuração na pasta especificada, uma soma de verificação será criada para cada configuração na pasta.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-207">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="a6d1d-208">Coloque os arquivos MOF e seus arquivos de soma de verificação associados na pasta **ConfigurationPath**</span><span class="sxs-lookup"><span data-stu-id="a6d1d-208">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="a6d1d-209">Se você alterar o arquivo MOF de configuração de alguma forma, também deverá recriar o arquivo de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-209">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="a6d1d-210">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="a6d1d-210">Tooling</span></span>

<span data-ttu-id="a6d1d-211">Para facilitar a configuração, a validação e o gerenciamento do servidor de pull, as seguintes ferramentas são incluídas como exemplos na versão mais recente do módulo xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="a6d1d-211">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="a6d1d-212">Um módulo que ajudará a empacotar módulos de recursos de DSC e arquivos de configuração para uso no servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-212">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span>
   <span data-ttu-id="a6d1d-213">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="a6d1d-213">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span>
   <span data-ttu-id="a6d1d-214">Exemplos abaixo:</span><span class="sxs-lookup"><span data-stu-id="a6d1d-214">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="a6d1d-215">Um script que valida o servidor de pull está configurado corretamente.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-215">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="a6d1d-216">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="a6d1d-216">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="a6d1d-217">Soluções da Comunidade para serviço de pull</span><span class="sxs-lookup"><span data-stu-id="a6d1d-217">Community Solutions for Pull Service</span></span>

<span data-ttu-id="a6d1d-218">A comunidade de DSC criou várias soluções para implementar o protocolo de serviço de pull.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-218">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="a6d1d-219">Para ambientes locais, eles oferecem recursos de serviço de pull e uma oportunidade de contribuir de volta para a Comunidade com aprimoramentos incrementais.</span><span class="sxs-lookup"><span data-stu-id="a6d1d-219">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="a6d1d-220">Levemente</span><span class="sxs-lookup"><span data-stu-id="a6d1d-220">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="a6d1d-221">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="a6d1d-221">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="a6d1d-222">Configuração do cliente de pull</span><span class="sxs-lookup"><span data-stu-id="a6d1d-222">Pull client configuration</span></span>

<span data-ttu-id="a6d1d-223">Os tópicos a seguir descrevem a configuração de clientes de pull em detalhes:</span><span class="sxs-lookup"><span data-stu-id="a6d1d-223">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="a6d1d-224">Configurar um cliente de pull de DSC usando uma ID de configuração</span><span class="sxs-lookup"><span data-stu-id="a6d1d-224">Set up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="a6d1d-225">Configurar um cliente de pull de DSC usando nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="a6d1d-225">Set up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="a6d1d-226">Configurações parciais</span><span class="sxs-lookup"><span data-stu-id="a6d1d-226">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="a6d1d-227">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6d1d-227">See also</span></span>

- [<span data-ttu-id="a6d1d-228">Visão geral da configuração de estado desejado do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a6d1d-228">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="a6d1d-229">Aplicar configurações</span><span class="sxs-lookup"><span data-stu-id="a6d1d-229">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="a6d1d-230">Utilizar um servidor de relatório de DSC</span><span class="sxs-lookup"><span data-stu-id="a6d1d-230">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="a6d1d-231">[[MS-DSCPM]: Protocolo de modelo de pull de configuração de estado desejado](https://msdn.microsoft.com/library/dn393548.aspx)</span><span class="sxs-lookup"><span data-stu-id="a6d1d-231">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx)</span></span>
- <span data-ttu-id="a6d1d-232">[[MS-DSCPM]: Errata do protocolo do modelo pull da configuração de estado desejado](https://msdn.microsoft.com/library/mt612824.aspx)</span><span class="sxs-lookup"><span data-stu-id="a6d1d-232">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx)</span></span>
