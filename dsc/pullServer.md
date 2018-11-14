---
ms.date: 04/11/2018
keywords: DSC, powershell, configuração, a configuração
title: Serviço de Solicitação de DSC
ms.openlocfilehash: 2ef48b88cc9e14da452e0d19e5a0f43fc8a95ab2
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619165"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="b4f25-103">Serviço de solicitação do Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="b4f25-103">Desired State Configuration Pull Service</span></span>

> <span data-ttu-id="b4f25-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b4f25-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4f25-105">O servidor de solicitação (recurso do Windows *DSC-serviço*) é um componente suportado do Windows Server no entanto, não existem planos para oferecer novas funcionalidades ou capacidades.</span><span class="sxs-lookup"><span data-stu-id="b4f25-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="b4f25-106">É recomendado para começar a fazer a transição geridos os clientes [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação de mensagens em fila no Windows Server) ou uma das soluções da Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="b4f25-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="b4f25-107">Gestor de configuração local podem ser geridos centralmente por uma solução de serviço de solicitação.</span><span class="sxs-lookup"><span data-stu-id="b4f25-107">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="b4f25-108">Ao usar essa abordagem, o nó que está a ser gerido é registado com um serviço e atribuído uma configuração nas definições do LCM.</span><span class="sxs-lookup"><span data-stu-id="b4f25-108">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="b4f25-109">A configuração e todos os recursos de DSC necessários como dependências para a configuração são transferidos para o computador e utilizados pelo LCM para gerir a configuração.</span><span class="sxs-lookup"><span data-stu-id="b4f25-109">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="b4f25-110">Informações sobre o estado da máquina a ser gerido são carregadas para o serviço de relatórios.</span><span class="sxs-lookup"><span data-stu-id="b4f25-110">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="b4f25-111">Esse conceito é conhecido como "serviço de solicitação de".</span><span class="sxs-lookup"><span data-stu-id="b4f25-111">This concept is referred to as "pull service."</span></span>

<span data-ttu-id="b4f25-112">As opções atuais de serviço pull incluem:</span><span class="sxs-lookup"><span data-stu-id="b4f25-112">The current options for pull service include:</span></span>

- <span data-ttu-id="b4f25-113">Serviço de Azure Automation Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="b4f25-113">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="b4f25-114">Um serviço pull de execução no Windows Server</span><span class="sxs-lookup"><span data-stu-id="b4f25-114">A pull service running on Windows Server</span></span>
- <span data-ttu-id="b4f25-115">Comunidade mantido soluções de código aberto</span><span class="sxs-lookup"><span data-stu-id="b4f25-115">Community maintained open-source solutions</span></span>
- <span data-ttu-id="b4f25-116">Uma partilha de SMB</span><span class="sxs-lookup"><span data-stu-id="b4f25-116">An SMB share</span></span>

<span data-ttu-id="b4f25-117">**A solução recomendada**, e a opção com mais recursos disponíveis, é [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="b4f25-117">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="b4f25-118">O serviço do Azure pode gerir nós no local nos centros de dados privados ou em clouds públicas, como o Azure e AWS.</span><span class="sxs-lookup"><span data-stu-id="b4f25-118">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="b4f25-119">Para ambientes privados em que os servidores não é possível ligar diretamente à Internet, considere limitar o tráfego de saída para apenas o intervalo de IP do Azure publicado (consulte [intervalos de IP de Datacenter do Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="b4f25-119">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="b4f25-120">As funcionalidades do serviço online que não estão atualmente disponíveis no serviço pull no Windows Server incluem:</span><span class="sxs-lookup"><span data-stu-id="b4f25-120">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>
- <span data-ttu-id="b4f25-121">Todos os dados são encriptados em trânsito e em repouso</span><span class="sxs-lookup"><span data-stu-id="b4f25-121">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="b4f25-122">Certificados de cliente são criados e geridos automaticamente</span><span class="sxs-lookup"><span data-stu-id="b4f25-122">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="b4f25-123">Arquivo de segredos para gerir centralmente [palavras-passe/credenciais](/azure/automation/automation-credentials), ou [variáveis](/azure/automation/automation-variables) tais como nomes de servidor ou cadeias de ligação</span><span class="sxs-lookup"><span data-stu-id="b4f25-123">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="b4f25-124">Gerenciar centralmente nó [configuração LCM](metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="b4f25-124">Centrally manage node [LCM configuration](metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="b4f25-125">Atribuir centralmente configurações a nós de cliente</span><span class="sxs-lookup"><span data-stu-id="b4f25-125">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="b4f25-126">Configuração da versão é alterado para "grupos de proteção" para teste antes de chegar a produção</span><span class="sxs-lookup"><span data-stu-id="b4f25-126">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="b4f25-127">Relatório de gráfico</span><span class="sxs-lookup"><span data-stu-id="b4f25-127">Graphical reporting</span></span>
  - <span data-ttu-id="b4f25-128">Detalhe do status no nível de recursos de DSC de granularidade</span><span class="sxs-lookup"><span data-stu-id="b4f25-128">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="b4f25-129">Mensagens de erro detalhada das máquinas de cliente para resolução de problemas</span><span class="sxs-lookup"><span data-stu-id="b4f25-129">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="b4f25-130">[Integração com o Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) para alertar, tarefas automatizadas, aplicações de Android/iOS para relatórios e alertas</span><span class="sxs-lookup"><span data-stu-id="b4f25-130">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="b4f25-131">Serviço de solicitação de DSC no Windows Server</span><span class="sxs-lookup"><span data-stu-id="b4f25-131">DSC pull service in Windows Server</span></span>

<span data-ttu-id="b4f25-132">É possível configurar um serviço de pull para ser executado no Windows Server.</span><span class="sxs-lookup"><span data-stu-id="b4f25-132">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="b4f25-133">Ser avisado que a solução de serviço pull incluída no Windows Server inclui capacidades únicas de armazenar configurações/modules para download e a captura de dados de relatório no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b4f25-133">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="b4f25-134">Não inclui muitas das funcionalidades oferecidas pelo serviço no Azure e, portanto, não é uma boa ferramenta para avaliar como o serviço deve ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="b4f25-134">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="b4f25-135">O serviço pull oferecido no Windows Server é um serviço web no IIS que utilize uma interface de OData para disponibilizar os ficheiros de configuração de DSC em nós de destino quando esses nós peça para os mesmos.</span><span class="sxs-lookup"><span data-stu-id="b4f25-135">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="b4f25-136">Requisitos para utilizar um servidor de solicitação:</span><span class="sxs-lookup"><span data-stu-id="b4f25-136">Requirements for using a pull server:</span></span>

- <span data-ttu-id="b4f25-137">Um servidor a executar:</span><span class="sxs-lookup"><span data-stu-id="b4f25-137">A server running:</span></span>
  - <span data-ttu-id="b4f25-138">WMF/PowerShell 5.0 ou superior</span><span class="sxs-lookup"><span data-stu-id="b4f25-138">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="b4f25-139">Função de servidor IIS</span><span class="sxs-lookup"><span data-stu-id="b4f25-139">IIS server role</span></span>
  - <span data-ttu-id="b4f25-140">Serviço de DSC</span><span class="sxs-lookup"><span data-stu-id="b4f25-140">DSC Service</span></span>
- <span data-ttu-id="b4f25-141">O ideal é que alguns significa de gerar um certificado, para proteger as credenciais transmitidas para Gestor de configuração Local (LCM) em nós de destino</span><span class="sxs-lookup"><span data-stu-id="b4f25-141">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="b4f25-142">A melhor forma de configurar o Windows Server para o serviço de solicitação do host é usar uma configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="b4f25-142">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="b4f25-143">Um script de exemplo é fornecido abaixo.</span><span class="sxs-lookup"><span data-stu-id="b4f25-143">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="b4f25-144">Sistemas de base de dados suportados</span><span class="sxs-lookup"><span data-stu-id="b4f25-144">Supported database systems</span></span>

|<span data-ttu-id="b4f25-145">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="b4f25-145">WMF 4.0</span></span>   |<span data-ttu-id="b4f25-146">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="b4f25-146">WMF 5.0</span></span>  |<span data-ttu-id="b4f25-147">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="b4f25-147">WMF 5.1</span></span> |<span data-ttu-id="b4f25-148">WMF 5.1 (Windows Server Insider Preview 17090)</span><span class="sxs-lookup"><span data-stu-id="b4f25-148">WMF 5.1 (Windows Server Insider Preview 17090)</span></span>|
|---------|---------|---------|---------|
|<span data-ttu-id="b4f25-149">MDB</span><span class="sxs-lookup"><span data-stu-id="b4f25-149">MDB</span></span>     |<span data-ttu-id="b4f25-150">ESENT (predefinição), MDB</span><span class="sxs-lookup"><span data-stu-id="b4f25-150">ESENT (Default), MDB</span></span> |<span data-ttu-id="b4f25-151">ESENT (predefinição), MDB</span><span class="sxs-lookup"><span data-stu-id="b4f25-151">ESENT (Default), MDB</span></span>|<span data-ttu-id="b4f25-152">ESENT (predefinição), do SQL Server, MDB</span><span class="sxs-lookup"><span data-stu-id="b4f25-152">ESENT (Default), SQL Server, MDB</span></span>

<span data-ttu-id="b4f25-153">A partir da versão 17090 dos [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), do SQL Server é uma opção suportada para o serviço de solicitação (funcionalidade do Windows *DSC-serviço*).</span><span class="sxs-lookup"><span data-stu-id="b4f25-153">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span>  <span data-ttu-id="b4f25-154">Isso fornece uma nova opção de dimensionamento grandes ambientes de DSC que não foram migrados para [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="b4f25-154">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> <span data-ttu-id="b4f25-155">**Tenha em atenção**: suporte do SQL Server não será possível adicionar as versões anteriores do WMF 5.1 (ou anterior) e só estará disponível em versões do Windows Server maiores que ou iguais a 17090.</span><span class="sxs-lookup"><span data-stu-id="b4f25-155">**Note**: SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="b4f25-156">Para configurar o servidor de solicitação para utilizar o SQL Server, defina **SqlProvider** ao `$true` e **SqlConnectionString** para uma cadeia de ligação válida do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b4f25-156">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span>  <span data-ttu-id="b4f25-157">Para obter mais informações, consulte [cadeias de ligação do SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="b4f25-157">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="b4f25-158">Para obter um exemplo de configuração do SQL Server com **xDscWebService**, leia primeiro [usando o recurso de xDscWebService](#using-the-xdscwebservice-resource) e, em seguida, reveja [Sample_xDscWebServiceRegistration_ UseSQLProvider.ps1 no GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="b4f25-158">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="b4f25-159">Usando o recurso de xDscWebService</span><span class="sxs-lookup"><span data-stu-id="b4f25-159">Using the xDscWebService resource</span></span>

<span data-ttu-id="b4f25-160">A maneira mais fácil de configurar um servidor de solicitação da web está a utilizar o **xDscWebService** recurso, incluído nos **xPSDesiredStateConfiguration** módulo.</span><span class="sxs-lookup"><span data-stu-id="b4f25-160">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span>
<span data-ttu-id="b4f25-161">Os passos seguintes explicam como usar o recurso numa configuração de que configura o serviço web.</span><span class="sxs-lookup"><span data-stu-id="b4f25-161">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="b4f25-162">Chamar o [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet para instalar o **xPSDesiredStateConfiguration** módulo.</span><span class="sxs-lookup"><span data-stu-id="b4f25-162">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="b4f25-163">**Tenha em atenção**: **Install-Module** está incluído no **PowerShellGet** módulo, que está incluído no PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="b4f25-163">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="b4f25-164">Pode baixar o **PowerShellGet** módulo para o PowerShell 3.0 e 4.0 na [pré-visualização de módulos do PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="b4f25-164">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
1. <span data-ttu-id="b4f25-165">Obtenha um certificado SSL para o servidor de solicitação de DSC de uma autoridade de certificação fidedigna, se dentro da sua organização ou uma autoridade pública.</span><span class="sxs-lookup"><span data-stu-id="b4f25-165">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="b4f25-166">O certificado recebido da autoridade geralmente se encontra no formato PFX.</span><span class="sxs-lookup"><span data-stu-id="b4f25-166">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="b4f25-167">Instale o certificado no nó que irá tornar-se o servidor de solicitação do DSC na localização predefinida, que deve ser CERT: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="b4f25-167">Install the certificate on the node that will become the DSC Pull server in the default location, which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="b4f25-168">Tome nota do thumbprint do certificado.</span><span class="sxs-lookup"><span data-stu-id="b4f25-168">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="b4f25-169">Selecione um GUID a ser utilizado como a chave de registo.</span><span class="sxs-lookup"><span data-stu-id="b4f25-169">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="b4f25-170">Para gerar um com o PowerShell, introduza o seguinte na linha de comandos de PS e prima enter: '``` [guid]::newGuid()```'ou'```New-Guid```'.</span><span class="sxs-lookup"><span data-stu-id="b4f25-170">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="b4f25-171">Esta chave será utilizada por nós de cliente como uma chave partilhada para autenticar durante o registo.</span><span class="sxs-lookup"><span data-stu-id="b4f25-171">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="b4f25-172">Para obter mais informações, consulte a secção de chave de registo abaixo.</span><span class="sxs-lookup"><span data-stu-id="b4f25-172">For more information, see the Registration Key section below.</span></span>
1. <span data-ttu-id="b4f25-173">No ISE do PowerShell, iniciar (F5), o seguinte script de configuração (incluído na pasta de exemplos do **xPSDesiredStateConfiguration** módulo como Sample_xDscWebServiceRegistration.ps1).</span><span class="sxs-lookup"><span data-stu-id="b4f25-173">In the PowerShell ISE, start (F5) the following configuration script (included in the Examples folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebServiceRegistration.ps1).</span></span> <span data-ttu-id="b4f25-174">Este script configura o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="b4f25-174">This script sets up the pull server.</span></span>

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

1. <span data-ttu-id="b4f25-175">Execute a configuração, passando o thumbprint do certificado SSL como o **certificateThumbPrint** parâmetro e um registo GUID da chave como o **RegistrationKey** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="b4f25-175">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="b4f25-176">Chave de registo</span><span class="sxs-lookup"><span data-stu-id="b4f25-176">Registration Key</span></span>

<span data-ttu-id="b4f25-177">Para permitir que cliente nós registar com o servidor para que eles podem usar nomes de configuração em vez de um ID de configuração, uma chave de registo que foi criada pela configuração acima é guardada num ficheiro denominado `RegistrationKeys.txt` em `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="b4f25-177">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="b4f25-178">A chave de registo funciona como um segredo partilhado utilizado durante o registo inicial pelo cliente com o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="b4f25-178">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="b4f25-179">O cliente irá gerar um certificado autoassinado que é utilizado para autenticar exclusivamente para o servidor de solicitação, uma vez que o registo é concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="b4f25-179">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="b4f25-180">O thumbprint deste certificado é armazenado localmente e associado com o URL do servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="b4f25-180">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="b4f25-181">**Tenha em atenção**: chaves de registo não são suportadas no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="b4f25-181">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="b4f25-182">Para configurar um nó para autenticar com o servidor de solicitação, a chave de registo tem de ser no metaconfiguration para qualquer nó de destino que irá registar este servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="b4f25-182">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="b4f25-183">Tenha em atenção que o **RegistrationKey** no metaconfiguration abaixo é removida depois da máquina de destino foi registado corretamente e que o valor '140a952b-b9d6-406b-b416-e0f759c9c0e4' tem de corresponder ao valor armazenado no Ficheiro de RegistrationKeys.txt no servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="b4f25-183">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="b4f25-184">Trate sempre o valor da chave de registo de forma segura, porque saber permite que qualquer máquina de destino registar com o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="b4f25-184">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to setup pull server in previous configuration

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

> <span data-ttu-id="b4f25-185">**Tenha em atenção**: A **ReportServerWeb** seção permite que os dados sejam enviados para o servidor de solicitação de relatórios.</span><span class="sxs-lookup"><span data-stu-id="b4f25-185">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="b4f25-186">A falta do **ConfigurationID** propriedade no arquivo metaconfiguration implicitamente significa que esse servidor de solicitação é que suporta a versão V2 do protocolo de servidor pull para um registo inicial é necessário.</span><span class="sxs-lookup"><span data-stu-id="b4f25-186">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="b4f25-187">Por outro lado, a presença de um **ConfigurationID** significa que é utilizada a versão V1 do protocolo de servidor de solicitação e não existe nenhum processamento de registo.</span><span class="sxs-lookup"><span data-stu-id="b4f25-187">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="b4f25-188">**Tenha em atenção**: num PUSH cenário, um bug existe na versão atual que faz com que seja necessário definir uma propriedade de ConfigurationID no ficheiro metaconfiguration para nós que nunca tenha registado com um servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="b4f25-188">**Note**: In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="b4f25-189">Esta ação irá forçar o protocolo de servidor de solicitação do V1 e evitar mensagens de falha de registo.</span><span class="sxs-lookup"><span data-stu-id="b4f25-189">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="b4f25-190">Colocar recursos e configurações</span><span class="sxs-lookup"><span data-stu-id="b4f25-190">Placing configurations and resources</span></span>

<span data-ttu-id="b4f25-191">Depois da solicitação servidor conclusão da configuração, as pastas definidas pelos **ConfigurationPath** e **ModulePath** propriedades na configuração do servidor de solicitação são onde irá colocar módulos e configurações que vai estar disponível para nós de destino efetuar pull.</span><span class="sxs-lookup"><span data-stu-id="b4f25-191">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="b4f25-192">Esses arquivos precisam ser num formato específico para que o servidor de solicitação para os processar corretamente.</span><span class="sxs-lookup"><span data-stu-id="b4f25-192">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="b4f25-193">Formato de pacote do módulo de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="b4f25-193">DSC resource module package format</span></span>

<span data-ttu-id="b4f25-194">Cada módulo de recursos tem de ser comprimido e nomeado de acordo com o seguinte padrão `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="b4f25-194">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>
<span data-ttu-id="b4f25-195">Por exemplo, um módulo com o nome xWebAdminstration com uma versão do módulo do 3.1.2.0 teria o nome 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="b4f25-195">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span>
<span data-ttu-id="b4f25-196">Cada versão de um módulo tem de estar contido num arquivo zip único.</span><span class="sxs-lookup"><span data-stu-id="b4f25-196">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="b4f25-197">Uma vez que existe apenas uma única versão de um recurso em cada arquivo zip, o formato do módulo adicionado no WMF 5.0 com suporte para várias versões do módulo num único diretório não é suportado.</span><span class="sxs-lookup"><span data-stu-id="b4f25-197">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="b4f25-198">Isso significa que, antes de empacotar os módulos de recursos de DSC para utilização com o servidor de solicitação precisará fazer uma pequena alteração para a estrutura de diretórios.</span><span class="sxs-lookup"><span data-stu-id="b4f25-198">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="b4f25-199">O formato de padrão de módulos que contém o recurso de DSC no WMF 5.0 é ' {pasta do módulo}\{versão do módulo} \DscResources\{pasta de recurso de DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="b4f25-199">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="b4f25-200">Antes de empacotamento tendo em vista o servidor de solicitação, remova os **{versão do módulo}** pasta para que o caminho se torna ' {pasta do módulo} \DscResources\{pasta de recurso de DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="b4f25-200">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="b4f25-201">Com esta alteração, zip na pasta, conforme descrito acima e colocar esses ficheiros zip no **ModulePath** pasta.</span><span class="sxs-lookup"><span data-stu-id="b4f25-201">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="b4f25-202">Utilize `New-DscChecksum {module zip file}` para criar um ficheiro de soma de verificação para o módulo recentemente adicionado.</span><span class="sxs-lookup"><span data-stu-id="b4f25-202">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="b4f25-203">Formato MOF de configuração</span><span class="sxs-lookup"><span data-stu-id="b4f25-203">Configuration MOF format</span></span>

<span data-ttu-id="b4f25-204">Um ficheiro MOF de configuração tem de ser emparelhado com um ficheiro de soma de verificação para que um LCM num nó de destino pode validar a configuração.</span><span class="sxs-lookup"><span data-stu-id="b4f25-204">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="b4f25-205">Para criar uma soma de verificação, chamar o [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b4f25-205">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span></span>
<span data-ttu-id="b4f25-206">O cmdlet assume uma **caminho** parâmetro que especifica a pasta onde está localizada a MOF de configuração.</span><span class="sxs-lookup"><span data-stu-id="b4f25-206">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="b4f25-207">O cmdlet cria um ficheiro de soma de verificação com o nome `ConfigurationMOFName.mof.checksum`, onde `ConfigurationMOFName` é o nome do ficheiro de mof de configuração.</span><span class="sxs-lookup"><span data-stu-id="b4f25-207">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="b4f25-208">Se existirem mais de uma configuração de MOF ficheiros na pasta especificada, é criada uma soma de verificação para cada configuração na pasta.</span><span class="sxs-lookup"><span data-stu-id="b4f25-208">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="b4f25-209">Colocar os arquivos MOF e seus arquivos de soma de verificação associados no **ConfigurationPath** pasta.</span><span class="sxs-lookup"><span data-stu-id="b4f25-209">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="b4f25-210">**Tenha em atenção**: Se alterar o ficheiro MOF de configuração de qualquer forma, também tem de recriar o arquivo de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="b4f25-210">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="b4f25-211">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="b4f25-211">Tooling</span></span>

<span data-ttu-id="b4f25-212">Para que a definição de cópia de segurança, validação e gerir o servidor de solicitação fácil, as ferramentas seguintes estão incluídas como exemplos na versão mais recente do módulo xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="b4f25-212">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="b4f25-213">Um módulo que o ajudará a com o empacotamento de ficheiros de configuração para utilização no servidor de solicitação e módulos de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="b4f25-213">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="b4f25-214">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="b4f25-214">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="b4f25-215">Exemplos abaixo:</span><span class="sxs-lookup"><span data-stu-id="b4f25-215">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="b4f25-216">Um script que valida o servidor de solicitação está configurado corretamente.</span><span class="sxs-lookup"><span data-stu-id="b4f25-216">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="b4f25-217">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="b4f25-217">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="b4f25-218">Soluções de Comunidade para o serviço de solicitação</span><span class="sxs-lookup"><span data-stu-id="b4f25-218">Community Solutions for Pull Service</span></span>

<span data-ttu-id="b4f25-219">A Comunidade de DSC é autor de várias soluções para implementar o protocolo de serviço de solicitação.</span><span class="sxs-lookup"><span data-stu-id="b4f25-219">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="b4f25-220">Para ambientes no local, elas oferecem capacidades do serviço de solicitação e uma oportunidade de contribuir para a Comunidade com melhorias incrementais.</span><span class="sxs-lookup"><span data-stu-id="b4f25-220">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="b4f25-221">Tug</span><span class="sxs-lookup"><span data-stu-id="b4f25-221">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="b4f25-222">TRÆK DE DSC</span><span class="sxs-lookup"><span data-stu-id="b4f25-222">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="b4f25-223">Configuração de cliente de solicitação</span><span class="sxs-lookup"><span data-stu-id="b4f25-223">Pull client configuration</span></span>

<span data-ttu-id="b4f25-224">Os tópicos seguintes descrevem como configurar clientes de pull detalhadamente:</span><span class="sxs-lookup"><span data-stu-id="b4f25-224">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="b4f25-225">Como configurar um cliente de solicitação de DSC com um ID de configuração</span><span class="sxs-lookup"><span data-stu-id="b4f25-225">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="b4f25-226">Como configurar um cliente de solicitação de DSC com nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="b4f25-226">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="b4f25-227">Configurações parciais</span><span class="sxs-lookup"><span data-stu-id="b4f25-227">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="b4f25-228">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4f25-228">See also</span></span>

- [<span data-ttu-id="b4f25-229">Windows PowerShell Desired State Configuration descrição-geral</span><span class="sxs-lookup"><span data-stu-id="b4f25-229">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="b4f25-230">Aplicar configurações</span><span class="sxs-lookup"><span data-stu-id="b4f25-230">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="b4f25-231">Utilizar um servidor de relatório de DSC</span><span class="sxs-lookup"><span data-stu-id="b4f25-231">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="b4f25-232">[[MS-DSCPM]: Desired State Configuration do protocolo de modelo de extração](https://msdn.microsoft.com/library/dn393548.aspx)</span><span class="sxs-lookup"><span data-stu-id="b4f25-232">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx)</span></span>
- <span data-ttu-id="b4f25-233">[[MS-DSCPM]: Desired State Configuration Errata de protocolo de modelo de extração](https://msdn.microsoft.com/library/mt612824.aspx)</span><span class="sxs-lookup"><span data-stu-id="b4f25-233">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx)</span></span>
