---
ms.date: 03/04/2019
keywords: DSC, powershell, configuração, a configuração
title: Serviço de Solicitação de DSC
ms.openlocfilehash: 3cb2ca09111100f39589072a0d8e7010f9188efb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079409"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="f7ae5-103">Serviço de solicitação do Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="f7ae5-103">Desired State Configuration Pull Service</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f7ae5-104">O servidor de solicitação (recurso do Windows *DSC-serviço*) é um componente suportado do Windows Server no entanto, não existem planos para oferecer novas funcionalidades ou capacidades.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-104">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="f7ae5-105">É recomendado para começar a fazer a transição geridos os clientes [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação de mensagens em fila no Windows Server) ou uma das soluções da Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="f7ae5-105">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="f7ae5-106">Gestor de configuração local podem ser geridos centralmente por uma solução de serviço de solicitação.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-106">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="f7ae5-107">Ao usar essa abordagem, o nó que está a ser gerido é registado com um serviço e atribuído uma configuração nas definições do LCM.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-107">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="f7ae5-108">A configuração e todos os recursos de DSC necessários como dependências para a configuração são transferidos para o computador e utilizados pelo LCM para gerir a configuração.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-108">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="f7ae5-109">Informações sobre o estado da máquina a ser gerido são carregadas para o serviço de relatórios.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-109">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="f7ae5-110">Esse conceito é conhecido como "serviço de solicitação de".</span><span class="sxs-lookup"><span data-stu-id="f7ae5-110">This concept is referred to as "pull service."</span></span>

<span data-ttu-id="f7ae5-111">As opções atuais de serviço pull incluem:</span><span class="sxs-lookup"><span data-stu-id="f7ae5-111">The current options for pull service include:</span></span>

- <span data-ttu-id="f7ae5-112">Serviço de Azure Automation Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="f7ae5-112">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="f7ae5-113">Um serviço pull de execução no Windows Server</span><span class="sxs-lookup"><span data-stu-id="f7ae5-113">A pull service running on Windows Server</span></span>
- <span data-ttu-id="f7ae5-114">Comunidade mantido soluções de código aberto</span><span class="sxs-lookup"><span data-stu-id="f7ae5-114">Community maintained open-source solutions</span></span>
- <span data-ttu-id="f7ae5-115">Uma partilha de SMB</span><span class="sxs-lookup"><span data-stu-id="f7ae5-115">An SMB share</span></span>

<span data-ttu-id="f7ae5-116">**A solução recomendada**, e a opção com mais recursos disponíveis, é [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="f7ae5-116">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="f7ae5-117">O serviço do Azure pode gerir nós no local nos centros de dados privados ou em clouds públicas, como o Azure e AWS.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-117">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="f7ae5-118">Para ambientes privados em que os servidores não é possível ligar diretamente à Internet, considere limitar o tráfego de saída para apenas o intervalo de IP do Azure publicado (consulte [intervalos de IP de Datacenter do Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="f7ae5-118">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="f7ae5-119">As funcionalidades do serviço online que não estão atualmente disponíveis no serviço pull no Windows Server incluem:</span><span class="sxs-lookup"><span data-stu-id="f7ae5-119">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>

- <span data-ttu-id="f7ae5-120">Todos os dados são encriptados em trânsito e em repouso</span><span class="sxs-lookup"><span data-stu-id="f7ae5-120">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="f7ae5-121">Certificados de cliente são criados e geridos automaticamente</span><span class="sxs-lookup"><span data-stu-id="f7ae5-121">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="f7ae5-122">Arquivo de segredos para gerir centralmente [palavras-passe/credenciais](/azure/automation/automation-credentials), ou [variáveis](/azure/automation/automation-variables) tais como nomes de servidor ou cadeias de ligação</span><span class="sxs-lookup"><span data-stu-id="f7ae5-122">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="f7ae5-123">Gerenciar centralmente nó [configuração LCM](../managing-nodes/metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="f7ae5-123">Centrally manage node [LCM configuration](../managing-nodes/metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="f7ae5-124">Atribuir centralmente configurações a nós de cliente</span><span class="sxs-lookup"><span data-stu-id="f7ae5-124">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="f7ae5-125">Configuração da versão é alterado para "grupos de proteção" para teste antes de chegar a produção</span><span class="sxs-lookup"><span data-stu-id="f7ae5-125">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="f7ae5-126">Relatório de gráfico</span><span class="sxs-lookup"><span data-stu-id="f7ae5-126">Graphical reporting</span></span>
  - <span data-ttu-id="f7ae5-127">Detalhe do status no nível de recursos de DSC de granularidade</span><span class="sxs-lookup"><span data-stu-id="f7ae5-127">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="f7ae5-128">Mensagens de erro detalhada das máquinas de cliente para resolução de problemas</span><span class="sxs-lookup"><span data-stu-id="f7ae5-128">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="f7ae5-129">[Integração com o Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) para alertar, tarefas automatizadas, aplicações de Android/iOS para relatórios e alertas</span><span class="sxs-lookup"><span data-stu-id="f7ae5-129">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="f7ae5-130">Serviço de solicitação de DSC no Windows Server</span><span class="sxs-lookup"><span data-stu-id="f7ae5-130">DSC pull service in Windows Server</span></span>

<span data-ttu-id="f7ae5-131">É possível configurar um serviço pull para ser executado no Windows Server.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-131">It is possible to configure a pull service to run on Windows Server.</span></span>
<span data-ttu-id="f7ae5-132">Ser avisado que a solução de serviço pull incluída no Windows Server inclui capacidades únicas de armazenar configurações/modules para download e a captura de dados de relatório no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-132">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="f7ae5-133">Não inclui muitas das funcionalidades oferecidas pelo serviço no Azure e, portanto, não é uma boa ferramenta para avaliar como o serviço deve ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-133">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="f7ae5-134">O serviço pull oferecido no Windows Server é um serviço web no IIS que utilize uma interface de OData para disponibilizar os ficheiros de configuração de DSC em nós de destino quando esses nós peça para os mesmos.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-134">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="f7ae5-135">Requisitos para utilizar um servidor de solicitação:</span><span class="sxs-lookup"><span data-stu-id="f7ae5-135">Requirements for using a pull server:</span></span>

- <span data-ttu-id="f7ae5-136">Um servidor a executar:</span><span class="sxs-lookup"><span data-stu-id="f7ae5-136">A server running:</span></span>
  - <span data-ttu-id="f7ae5-137">WMF/PowerShell 4.0 ou superior</span><span class="sxs-lookup"><span data-stu-id="f7ae5-137">WMF/PowerShell 4.0 or greater</span></span>
  - <span data-ttu-id="f7ae5-138">Função de servidor IIS</span><span class="sxs-lookup"><span data-stu-id="f7ae5-138">IIS server role</span></span>
  - <span data-ttu-id="f7ae5-139">Serviço de DSC</span><span class="sxs-lookup"><span data-stu-id="f7ae5-139">DSC Service</span></span>
- <span data-ttu-id="f7ae5-140">O ideal é que alguns significa de gerar um certificado, para proteger as credenciais transmitidas para Gestor de configuração Local (LCM) em nós de destino</span><span class="sxs-lookup"><span data-stu-id="f7ae5-140">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="f7ae5-141">A melhor forma de configurar o Windows Server para o serviço de solicitação do host é usar uma configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-141">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="f7ae5-142">Um script de exemplo é fornecido abaixo.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-142">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="f7ae5-143">Sistemas de base de dados suportados</span><span class="sxs-lookup"><span data-stu-id="f7ae5-143">Supported database systems</span></span>

|<span data-ttu-id="f7ae5-144">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="f7ae5-144">WMF 4.0</span></span>   |<span data-ttu-id="f7ae5-145">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="f7ae5-145">WMF 5.0</span></span>  |<span data-ttu-id="f7ae5-146">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="f7ae5-146">WMF 5.1</span></span> |<span data-ttu-id="f7ae5-147">WMF 5.1 (Windows Server Insider Preview 17090)</span><span class="sxs-lookup"><span data-stu-id="f7ae5-147">WMF 5.1 (Windows Server Insider Preview 17090)</span></span>|
|---------|---------|---------|---------|
|<span data-ttu-id="f7ae5-148">MDB</span><span class="sxs-lookup"><span data-stu-id="f7ae5-148">MDB</span></span>     |<span data-ttu-id="f7ae5-149">ESENT (predefinição), MDB</span><span class="sxs-lookup"><span data-stu-id="f7ae5-149">ESENT (Default), MDB</span></span> |<span data-ttu-id="f7ae5-150">ESENT (predefinição), MDB</span><span class="sxs-lookup"><span data-stu-id="f7ae5-150">ESENT (Default), MDB</span></span>|<span data-ttu-id="f7ae5-151">ESENT (predefinição), do SQL Server, MDB</span><span class="sxs-lookup"><span data-stu-id="f7ae5-151">ESENT (Default), SQL Server, MDB</span></span>

<span data-ttu-id="f7ae5-152">A partir da versão 17090 dos [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), do SQL Server é uma opção suportada para o serviço de solicitação (funcionalidade do Windows *DSC-serviço*).</span><span class="sxs-lookup"><span data-stu-id="f7ae5-152">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span> <span data-ttu-id="f7ae5-153">Isso fornece uma nova opção de dimensionamento grandes ambientes de DSC que não foram migrados para [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="f7ae5-153">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> [!NOTE]
> <span data-ttu-id="f7ae5-154">Suporte do SQL Server não será possível adicionar as versões anteriores do WMF 5.1 (ou anterior) e só estará disponível em versões do Windows Server maiores que ou iguais a 17090.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-154">SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="f7ae5-155">Para configurar o servidor de solicitação para utilizar o SQL Server, defina **SqlProvider** ao `$true` e **SqlConnectionString** para uma cadeia de ligação válida do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-155">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span> <span data-ttu-id="f7ae5-156">Para obter mais informações, consulte [cadeias de ligação do SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="f7ae5-156">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="f7ae5-157">Para obter um exemplo de configuração do SQL Server com **xDscWebService**, leia primeiro [usando o recurso de xDscWebService](#using-the-xdscwebservice-resource) e, em seguida, reveja [Sample_xDscWebServiceRegistration_ UseSQLProvider.ps1 no GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="f7ae5-157">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="f7ae5-158">Usando o recurso de xDscWebService</span><span class="sxs-lookup"><span data-stu-id="f7ae5-158">Using the xDscWebService resource</span></span>

<span data-ttu-id="f7ae5-159">A maneira mais fácil de configurar um servidor de solicitação da web está a utilizar o **xDscWebService** recurso, incluído nos **xPSDesiredStateConfiguration** módulo.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-159">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span>
<span data-ttu-id="f7ae5-160">Os passos seguintes explicam como usar o recurso numa configuração de que configura o serviço web.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-160">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="f7ae5-161">Chamar o [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet para instalar o **xPSDesiredStateConfiguration** módulo.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-161">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span>
   > [!NOTE]
   > <span data-ttu-id="f7ae5-162">**Install-Module** está incluído nos **PowerShellGet** módulo, que está incluído no PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-162">**Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="f7ae5-163">Pode baixar o **PowerShellGet** módulo para o PowerShell 3.0 e 4.0 na [pré-visualização de módulos do PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="f7ae5-163">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
2. <span data-ttu-id="f7ae5-164">Obtenha um certificado SSL para o servidor de solicitação de DSC de uma autoridade de certificação fidedigna, se dentro da sua organização ou uma autoridade pública.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-164">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="f7ae5-165">O certificado recebido da autoridade geralmente se encontra no formato PFX.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-165">The certificate received from the authority is usually in the PFX format.</span></span>
3. <span data-ttu-id="f7ae5-166">Instalar o certificado no nó que irá tornar-se o servidor de solicitação do DSC na localização predefinida, que deve ser `CERT:\LocalMachine\My`.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-166">Install the certificate on the node that will become the DSC Pull server in the default location, which should be `CERT:\LocalMachine\My`.</span></span>
   - <span data-ttu-id="f7ae5-167">Tome nota do thumbprint do certificado.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-167">Make a note of the certificate thumbprint.</span></span>
4. <span data-ttu-id="f7ae5-168">Selecione um GUID a ser utilizado como a chave de registo.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-168">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="f7ae5-169">Para gerar um com o PowerShell, introduza o seguinte na linha de comandos de PS e prima enter: `[guid]::newGuid()` ou `New-Guid`.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-169">To generate one using PowerShell enter the following at the PS prompt and press enter: `[guid]::newGuid()` or `New-Guid`.</span></span> <span data-ttu-id="f7ae5-170">Esta chave será utilizada por nós de cliente como uma chave partilhada para autenticar durante o registo.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-170">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="f7ae5-171">Para obter mais informações, consulte a secção de chave de registo abaixo.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-171">For more information, see the Registration Key section below.</span></span>
5. <span data-ttu-id="f7ae5-172">No ISE do PowerShell, iniciar (F5), o seguinte script de configuração (incluído na pasta de exemplos do **xPSDesiredStateConfiguration** módulo como `Sample_xDscWebServiceRegistration.ps1`).</span><span class="sxs-lookup"><span data-stu-id="f7ae5-172">In the PowerShell ISE, start (F5) the following configuration script (included in the Examples folder of the **xPSDesiredStateConfiguration** module as `Sample_xDscWebServiceRegistration.ps1`).</span></span> <span data-ttu-id="f7ae5-173">Este script configura o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-173">This script sets up the pull server.</span></span>

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

6. <span data-ttu-id="f7ae5-174">Execute a configuração, passando o thumbprint do certificado SSL como o **certificateThumbPrint** parâmetro e um registo GUID da chave como o **RegistrationKey** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="f7ae5-174">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="f7ae5-175">Chave de registo</span><span class="sxs-lookup"><span data-stu-id="f7ae5-175">Registration Key</span></span>

<span data-ttu-id="f7ae5-176">Para permitir que cliente nós registar com o servidor para que eles podem usar nomes de configuração em vez de um ID de configuração, uma chave de registo que foi criada pela configuração acima é guardada num ficheiro denominado `RegistrationKeys.txt` em `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-176">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="f7ae5-177">A chave de registo funciona como um segredo partilhado utilizado durante o registo inicial pelo cliente com o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-177">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="f7ae5-178">O cliente irá gerar um certificado autoassinado que é utilizado para autenticar exclusivamente para o servidor de solicitação, uma vez que o registo é concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-178">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="f7ae5-179">O thumbprint deste certificado é armazenado localmente e associado com o URL do servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-179">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="f7ae5-180">As chaves de registo não são suportadas no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-180">Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="f7ae5-181">Para configurar um nó para autenticar com o servidor de solicitação, a chave de registo tem de ser no metaconfiguration para qualquer nó de destino que irá registar este servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-181">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="f7ae5-182">Tenha em atenção que o **RegistrationKey** no metaconfiguration abaixo é removida depois da máquina de destino foi registado corretamente e que o valor tem de corresponder ao valor armazenado no `RegistrationKeys.txt` ficheiro no servidor de solicitação (' 140a952b-b9d6-406b-b416-e0f759c9c0e4' para este exemplo).</span><span class="sxs-lookup"><span data-stu-id="f7ae5-182">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value must match the value stored in the `RegistrationKeys.txt` file on the pull server ('140a952b-b9d6-406b-b416-e0f759c9c0e4' for this example).</span></span> <span data-ttu-id="f7ae5-183">Trate sempre o valor da chave de registo de forma segura, porque saber permite que qualquer máquina de destino registar com o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-183">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

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
> <span data-ttu-id="f7ae5-184">O **ReportServerWeb** seção permite que os dados sejam enviados para o servidor de solicitação de relatórios.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-184">The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="f7ae5-185">A falta do **ConfigurationID** propriedade no arquivo metaconfiguration implicitamente significa que esse servidor de solicitação é que suporta a versão V2 do protocolo de servidor pull para um registo inicial é necessário.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-185">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="f7ae5-186">Por outro lado, a presença de um **ConfigurationID** significa que é utilizada a versão V1 do protocolo de servidor de solicitação e não existe nenhum processamento de registo.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-186">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

> [!NOTE]
> <span data-ttu-id="f7ae5-187">Num cenário PUSH, um bug existe na versão atual que faz com que seja necessário definir uma propriedade de ConfigurationID no ficheiro metaconfiguration para nós que nunca tenha registado com um servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-187">In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="f7ae5-188">Esta ação irá forçar o protocolo de servidor de solicitação do V1 e evitar mensagens de falha de registo.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-188">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="f7ae5-189">Colocar recursos e configurações</span><span class="sxs-lookup"><span data-stu-id="f7ae5-189">Placing configurations and resources</span></span>

<span data-ttu-id="f7ae5-190">Depois da solicitação servidor conclusão da configuração, as pastas definidas pelos **ConfigurationPath** e **ModulePath** propriedades na configuração do servidor de solicitação são onde irá colocar módulos e configurações que vai estar disponível para nós de destino efetuar pull.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-190">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="f7ae5-191">Esses arquivos precisam ser num formato específico para que o servidor de solicitação para os processar corretamente.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-191">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="f7ae5-192">Formato de pacote do módulo de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="f7ae5-192">DSC resource module package format</span></span>

<span data-ttu-id="f7ae5-193">Cada módulo de recursos tem de ser comprimido e nomeado de acordo com o seguinte padrão `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-193">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>

<span data-ttu-id="f7ae5-194">Por exemplo, um módulo com o nome xWebAdminstration com uma versão do módulo do 3.1.2.0 teria o nome `xWebAdministration_3.2.1.0.zip`.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-194">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named `xWebAdministration_3.2.1.0.zip`.</span></span>
<span data-ttu-id="f7ae5-195">Cada versão de um módulo tem de estar contido num arquivo zip único.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-195">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="f7ae5-196">Uma vez que existe apenas uma única versão de um recurso em cada arquivo zip, o formato do módulo adicionado no WMF 5.0 com suporte para várias versões do módulo num único diretório não é suportado.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-196">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="f7ae5-197">Isso significa que, antes de empacotar os módulos de recursos de DSC para utilização com o servidor de solicitação precisará fazer uma pequena alteração para a estrutura de diretórios.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-197">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="f7ae5-198">O formato de padrão de módulos que contém o recurso de DSC no WMF 5.0 é `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-198">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="f7ae5-199">Antes de empacotamento tendo em vista o servidor de solicitação, remova os **{versão do módulo}** pasta para que o caminho se torna `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-199">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="f7ae5-200">Com esta alteração, zip na pasta, conforme descrito acima e colocar esses ficheiros zip no **ModulePath** pasta.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-200">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="f7ae5-201">Utilize `New-DscChecksum {module zip file}` para criar um ficheiro de soma de verificação para o módulo recentemente adicionado.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-201">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="f7ae5-202">Formato MOF de configuração</span><span class="sxs-lookup"><span data-stu-id="f7ae5-202">Configuration MOF format</span></span>

<span data-ttu-id="f7ae5-203">Um ficheiro MOF de configuração tem de ser emparelhado com um ficheiro de soma de verificação para que um LCM num nó de destino pode validar a configuração.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-203">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="f7ae5-204">Para criar uma soma de verificação, chamar o [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-204">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span></span>
<span data-ttu-id="f7ae5-205">O cmdlet assume uma **caminho** parâmetro que especifica a pasta onde está localizada a MOF de configuração.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-205">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="f7ae5-206">O cmdlet cria um ficheiro de soma de verificação com o nome `ConfigurationMOFName.mof.checksum`, onde `ConfigurationMOFName` é o nome do ficheiro de mof de configuração.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-206">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="f7ae5-207">Se existirem mais de uma configuração de MOF ficheiros na pasta especificada, é criada uma soma de verificação para cada configuração na pasta.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-207">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="f7ae5-208">Colocar os arquivos MOF e seus arquivos de soma de verificação associados no **ConfigurationPath** pasta.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-208">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="f7ae5-209">Se alterar o ficheiro MOF de configuração de qualquer forma, também tem de recriar o arquivo de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-209">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="f7ae5-210">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="f7ae5-210">Tooling</span></span>

<span data-ttu-id="f7ae5-211">Para que a definição de cópia de segurança, validação e gerir o servidor de solicitação fácil, as ferramentas seguintes estão incluídas como exemplos na versão mais recente do módulo xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="f7ae5-211">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="f7ae5-212">Um módulo que o ajudará a com o empacotamento de ficheiros de configuração para utilização no servidor de solicitação e módulos de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-212">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span>
   <span data-ttu-id="f7ae5-213">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="f7ae5-213">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span>
   <span data-ttu-id="f7ae5-214">Exemplos abaixo:</span><span class="sxs-lookup"><span data-stu-id="f7ae5-214">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="f7ae5-215">Um script que valida o servidor de solicitação está configurado corretamente.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-215">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="f7ae5-216">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="f7ae5-216">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="f7ae5-217">Soluções de Comunidade para o serviço de solicitação</span><span class="sxs-lookup"><span data-stu-id="f7ae5-217">Community Solutions for Pull Service</span></span>

<span data-ttu-id="f7ae5-218">A Comunidade de DSC é autor de várias soluções para implementar o protocolo de serviço de solicitação.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-218">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="f7ae5-219">Para ambientes no local, elas oferecem capacidades do serviço de solicitação e uma oportunidade de contribuir para a Comunidade com melhorias incrementais.</span><span class="sxs-lookup"><span data-stu-id="f7ae5-219">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="f7ae5-220">Tug</span><span class="sxs-lookup"><span data-stu-id="f7ae5-220">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="f7ae5-221">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="f7ae5-221">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="f7ae5-222">Configuração de cliente de solicitação</span><span class="sxs-lookup"><span data-stu-id="f7ae5-222">Pull client configuration</span></span>

<span data-ttu-id="f7ae5-223">Os tópicos seguintes descrevem como configurar clientes de pull detalhadamente:</span><span class="sxs-lookup"><span data-stu-id="f7ae5-223">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="f7ae5-224">Configurar um cliente de solicitação de DSC com um ID de configuração</span><span class="sxs-lookup"><span data-stu-id="f7ae5-224">Set up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="f7ae5-225">Configurar um cliente de solicitação de DSC com nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="f7ae5-225">Set up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="f7ae5-226">Configurações parciais</span><span class="sxs-lookup"><span data-stu-id="f7ae5-226">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="f7ae5-227">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7ae5-227">See also</span></span>

- [<span data-ttu-id="f7ae5-228">Windows PowerShell Desired State Configuration descrição-geral</span><span class="sxs-lookup"><span data-stu-id="f7ae5-228">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="f7ae5-229">Aplicar configurações</span><span class="sxs-lookup"><span data-stu-id="f7ae5-229">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="f7ae5-230">Utilizar um servidor de relatório de DSC</span><span class="sxs-lookup"><span data-stu-id="f7ae5-230">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="f7ae5-231">[[MS-DSCPM]: Desired State Configuration do protocolo de modelo de extração](https://msdn.microsoft.com/library/dn393548.aspx)</span><span class="sxs-lookup"><span data-stu-id="f7ae5-231">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx)</span></span>
- <span data-ttu-id="f7ae5-232">[[MS-DSCPM]: Desired State Configuration Errata de protocolo de modelo de extração](https://msdn.microsoft.com/library/mt612824.aspx)</span><span class="sxs-lookup"><span data-stu-id="f7ae5-232">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx)</span></span>
