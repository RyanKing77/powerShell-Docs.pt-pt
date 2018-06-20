---
ms.date: 04/11/2018
keywords: DSC, do powershell, a configuração, a configuração
title: Serviço de Solicitação de DSC
ms.openlocfilehash: 057da50843e79ae31eef4fea1fa58e882a9d1ace
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189997"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="70b03-103">Serviço de solicitação de configuração do estado pretendido</span><span class="sxs-lookup"><span data-stu-id="70b03-103">Desired State Configuration Pull Service</span></span>

> <span data-ttu-id="70b03-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="70b03-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="70b03-105">O servidor de solicitação (funcionalidade do Windows *DSC serviço*) é um componente suportado do Windows Server no entanto, são não planos para oferecer novas funcionalidades ou capacidades.</span><span class="sxs-lookup"><span data-stu-id="70b03-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="70b03-106">É recomendado para começar a transição geridos os clientes [Automation DSC do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação no Windows Server) ou uma das soluções de Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="70b03-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="70b03-107">Gestor de configuração locais podem ser geridos centralmente por uma solução de serviço de extração.</span><span class="sxs-lookup"><span data-stu-id="70b03-107">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="70b03-108">Quando utilizar esta abordagem, o nó que está a ser gerido está registado com um serviço e atribuído uma configuração nas definições do MMC.</span><span class="sxs-lookup"><span data-stu-id="70b03-108">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="70b03-109">A configuração e todos os recursos de DSC necessários como dependências para a configuração são transferidos para a máquina e utilizados pelo MMC para gerir a configuração.</span><span class="sxs-lookup"><span data-stu-id="70b03-109">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="70b03-110">Informações sobre o estado da máquina que está a ser gerido são carregadas para o serviço de relatórios.</span><span class="sxs-lookup"><span data-stu-id="70b03-110">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="70b03-111">Este conceito é referido como "serviço de extração."</span><span class="sxs-lookup"><span data-stu-id="70b03-111">This concept is referred to as "pull service."</span></span>

<span data-ttu-id="70b03-112">As opções de atuais para o serviço de solicitação incluem:</span><span class="sxs-lookup"><span data-stu-id="70b03-112">The current options for pull service include:</span></span>

- <span data-ttu-id="70b03-113">Serviço de configuração de estado de Desired de automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="70b03-113">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="70b03-114">Um serviço de solicitação em execução no Windows Server</span><span class="sxs-lookup"><span data-stu-id="70b03-114">A pull service running on Windows Server</span></span>
- <span data-ttu-id="70b03-115">Comunidade mantida soluções de open source</span><span class="sxs-lookup"><span data-stu-id="70b03-115">Community maintained open-source solutions</span></span>
- <span data-ttu-id="70b03-116">Uma partilha SMB</span><span class="sxs-lookup"><span data-stu-id="70b03-116">An SMB share</span></span>

<span data-ttu-id="70b03-117">**A solução recomendada**, e a opção com mais funcionalidades disponíveis, é [Automation DSC do Azure](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="70b03-117">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="70b03-118">O serviço do Azure pode gerir nós no local em centros de dados privados ou em nuvens públicas, tais como o Azure e AWS.</span><span class="sxs-lookup"><span data-stu-id="70b03-118">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="70b03-119">Para ambientes privados em que os servidores não é possível ligar diretamente à Internet, considere limitar o tráfego de saída para apenas o intervalo de IP de Azure publicado (consulte [intervalos de IP do Datacenter do Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="70b03-119">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="70b03-120">As funcionalidades do serviço online que não estão atualmente disponíveis no serviço de solicitação no Windows Server incluem:</span><span class="sxs-lookup"><span data-stu-id="70b03-120">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>
- <span data-ttu-id="70b03-121">Todos os dados são encriptados em trânsito e o restante</span><span class="sxs-lookup"><span data-stu-id="70b03-121">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="70b03-122">Certificados de cliente são criados e geridos automaticamente</span><span class="sxs-lookup"><span data-stu-id="70b03-122">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="70b03-123">Armazenam segredos para gerir centralmente [palavras-passe/credenciais](/azure/automation/automation-credentials), ou [variáveis](/azure/automation/automation-variables) tais como nomes de servidor ou cadeias de ligação</span><span class="sxs-lookup"><span data-stu-id="70b03-123">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="70b03-124">Gerir centralmente o nó [configuração MMC](metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="70b03-124">Centrally manage node [LCM configuration](metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="70b03-125">Atribuir centralmente configurações para nós de cliente</span><span class="sxs-lookup"><span data-stu-id="70b03-125">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="70b03-126">Configuração de versão é alterada para "grupos canary" para fins de teste antes de atingir a produção</span><span class="sxs-lookup"><span data-stu-id="70b03-126">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="70b03-127">Gráfico de relatórios</span><span class="sxs-lookup"><span data-stu-id="70b03-127">Graphical reporting</span></span>
  - <span data-ttu-id="70b03-128">Detalhes de estado ao nível de recursos do DSC de granularidade</span><span class="sxs-lookup"><span data-stu-id="70b03-128">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="70b03-129">Mensagens de erro verbosas provenientes de máquinas de cliente para resolução de problemas</span><span class="sxs-lookup"><span data-stu-id="70b03-129">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="70b03-130">[Integração com o Log Analytics do Azure](/azure/automation/automation-dsc-diagnostics) para alertar, tarefas automatizadas, a aplicação Android/iOS para relatórios e alertas</span><span class="sxs-lookup"><span data-stu-id="70b03-130">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="70b03-131">Serviço de solicitação do DSC no Windows Server</span><span class="sxs-lookup"><span data-stu-id="70b03-131">DSC pull service in Windows Server</span></span>

<span data-ttu-id="70b03-132">É possível configurar um serviço de solicitação para ser executado no Windows Server.</span><span class="sxs-lookup"><span data-stu-id="70b03-132">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="70b03-133">Ser-se de que a solução de serviço de solicitação incluída no Windows Server inclui apenas capacidades de armazenamento de configurações/módulos para transferência e capturar os dados de relatório na base de dados.</span><span class="sxs-lookup"><span data-stu-id="70b03-133">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="70b03-134">Não inclui muitas das funcionalidades oferecidas pelo serviço do Azure e, por isso, não é uma ferramenta boa para avaliar como o serviço poderia ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="70b03-134">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="70b03-135">O serviço de solicitação disponibilizado no Windows Server é um serviço web do IIS que utiliza uma interface de OData para fazer com que os ficheiros de configuração de DSC disponíveis para nós de destino quando os nós peça-lhes.</span><span class="sxs-lookup"><span data-stu-id="70b03-135">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="70b03-136">Requisitos para utilizar um servidor de solicitação:</span><span class="sxs-lookup"><span data-stu-id="70b03-136">Requirements for using a pull server:</span></span>

- <span data-ttu-id="70b03-137">Um servidor a executar:</span><span class="sxs-lookup"><span data-stu-id="70b03-137">A server running:</span></span>
  - <span data-ttu-id="70b03-138">WMF/PowerShell 5.0 ou superior</span><span class="sxs-lookup"><span data-stu-id="70b03-138">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="70b03-139">Função de servidor IIS</span><span class="sxs-lookup"><span data-stu-id="70b03-139">IIS server role</span></span>
  - <span data-ttu-id="70b03-140">Serviço de DSC</span><span class="sxs-lookup"><span data-stu-id="70b03-140">DSC Service</span></span>
- <span data-ttu-id="70b03-141">Idealmente, algumas significa de gerar um certificado, para proteger as credenciais transmitidas para Gestor de configuração Local (MMC) em nós de destino</span><span class="sxs-lookup"><span data-stu-id="70b03-141">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="70b03-142">A melhor forma de configurar o Windows Server para o serviço de solicitação do anfitrião está a utilizar uma configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="70b03-142">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="70b03-143">Um script de exemplo é fornecido abaixo.</span><span class="sxs-lookup"><span data-stu-id="70b03-143">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="70b03-144">Sistemas de base de dados suportados</span><span class="sxs-lookup"><span data-stu-id="70b03-144">Supported database systems</span></span>

|<span data-ttu-id="70b03-145">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="70b03-145">WMF 4.0</span></span>   |<span data-ttu-id="70b03-146">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="70b03-146">WMF 5.0</span></span>  |<span data-ttu-id="70b03-147">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="70b03-147">WMF 5.1</span></span> |<span data-ttu-id="70b03-148">WMF 5.1 (Windows Server Insider pré-visualização 17090)</span><span class="sxs-lookup"><span data-stu-id="70b03-148">WMF 5.1 (Windows Server Insider Preview 17090)</span></span>|
|---------|---------|---------|---------|
|<span data-ttu-id="70b03-149">MDB</span><span class="sxs-lookup"><span data-stu-id="70b03-149">MDB</span></span>     |<span data-ttu-id="70b03-150">ESENT (predefinição), MDB</span><span class="sxs-lookup"><span data-stu-id="70b03-150">ESENT (Default), MDB</span></span> |<span data-ttu-id="70b03-151">ESENT (predefinição), MDB</span><span class="sxs-lookup"><span data-stu-id="70b03-151">ESENT (Default), MDB</span></span>|<span data-ttu-id="70b03-152">ESENT (predefinição), do SQL Server, MDB</span><span class="sxs-lookup"><span data-stu-id="70b03-152">ESENT (Default), SQL Server, MDB</span></span>

<span data-ttu-id="70b03-153">A partir da versão 17090 de [pré-visualização do Windows Server Insider](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server é uma opção suportada para o serviço de extração (funcionalidade do Windows *DSC serviço*).</span><span class="sxs-lookup"><span data-stu-id="70b03-153">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span>  <span data-ttu-id="70b03-154">Isto oferece uma nova opção de dimensionamento de ambientes de grandes dimensões DSC que não tenham sido migrados para [Automation DSC do Azure](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="70b03-154">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> <span data-ttu-id="70b03-155">**Tenha em atenção**: suporte do SQL Server não será adicionado as versões anteriores do WMF 5.1 (ou anterior) e só estará disponível em versões do Windows Server maiores que ou igual a 17090.</span><span class="sxs-lookup"><span data-stu-id="70b03-155">**Note**: SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="70b03-156">Para configurar o servidor de solicitação para utilizar o SQL Server, defina **SqlProvider** para `$true` e **SqlConnectionString** para uma cadeia de ligação de servidor de SQL válido.</span><span class="sxs-lookup"><span data-stu-id="70b03-156">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span>  <span data-ttu-id="70b03-157">Para obter mais informações, consulte [cadeias de ligação de SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="70b03-157">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="70b03-158">Para obter um exemplo de configuração do SQL Server com **xDscWebService**, leia primeiro [utilizando o recurso de xDscWebService](#using-the-xdscwebservice-resource) e, em seguida, reveja [Sample_xDscWebServiceRegistration_ UseSQLProvider.ps1 no GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="70b03-158">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="70b03-159">Utilizar o recurso de xDscWebService</span><span class="sxs-lookup"><span data-stu-id="70b03-159">Using the xDscWebService resource</span></span>

<span data-ttu-id="70b03-160">A forma mais fácil de configurar um servidor de solicitação web está a utilizar o **xDscWebService** recurso, incluído no **xPSDesiredStateConfiguration** módulo.</span><span class="sxs-lookup"><span data-stu-id="70b03-160">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span>
<span data-ttu-id="70b03-161">Os passos seguintes explicam como utilizar o recurso uma configuração de que configura o serviço web.</span><span class="sxs-lookup"><span data-stu-id="70b03-161">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="70b03-162">Chamar o [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet para instalar o **xPSDesiredStateConfiguration** módulo.</span><span class="sxs-lookup"><span data-stu-id="70b03-162">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="70b03-163">**Tenha em atenção**: **Install-Module** está incluído no **PowerShellGet** módulo, que está incluído no PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="70b03-163">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="70b03-164">Pode transferir o **PowerShellGet** módulo para o PowerShell 3.0 e 4.0 em [pré-visualização de módulos do PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="70b03-164">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
1. <span data-ttu-id="70b03-165">Obter um certificado SSL para o servidor de solicitação do DSC de uma autoridade de certificação fidedigna-se dentro da sua organização ou uma autoridade de pública.</span><span class="sxs-lookup"><span data-stu-id="70b03-165">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="70b03-166">O certificado recebido a partir da autoridade de normalmente se encontra no formato PFX.</span><span class="sxs-lookup"><span data-stu-id="70b03-166">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="70b03-167">Instale o certificado no nó que irá tornar-se o servidor de solicitação do DSC na localização predefinida, que deve ser CERT: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="70b03-167">Install the certificate on the node that will become the DSC Pull server in the default location, which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="70b03-168">Anote o thumbprint do certificado.</span><span class="sxs-lookup"><span data-stu-id="70b03-168">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="70b03-169">Selecione um GUID para ser utilizado como a chave de registo.</span><span class="sxs-lookup"><span data-stu-id="70b03-169">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="70b03-170">Para gerar um através do PowerShell, introduza o seguinte na linha de PS e prima enter: '``` [guid]::newGuid()```'ou'```New-Guid```'.</span><span class="sxs-lookup"><span data-stu-id="70b03-170">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="70b03-171">Esta chave será utilizada por nós de cliente como uma chave partilhada para autenticar durante o registo.</span><span class="sxs-lookup"><span data-stu-id="70b03-171">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="70b03-172">Para obter mais informações, consulte a secção de chave de registo abaixo.</span><span class="sxs-lookup"><span data-stu-id="70b03-172">For more information, see the Registration Key section below.</span></span>
1. <span data-ttu-id="70b03-173">No ISE do PowerShell, iniciar (F5), o seguinte script de configuração (incluído na pasta de exemplos de **xPSDesiredStateConfiguration** módulo como Sample_xDscWebServiceRegistration.ps1).</span><span class="sxs-lookup"><span data-stu-id="70b03-173">In the PowerShell ISE, start (F5) the following configuration script (included in the Examples folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebServiceRegistration.ps1).</span></span> <span data-ttu-id="70b03-174">Este script configura o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="70b03-174">This script sets up the pull server.</span></span>

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

1. <span data-ttu-id="70b03-175">Execute a configuração, transmitir o thumbprint do certificado SSL como o **certificateThumbPrint** parâmetro e um registo GUID de chave como o **RegistrationKey** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="70b03-175">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

```powershell
# To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
# and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
dir Cert:\LocalMachine\my

# Then include this thumbprint when running the configuration
Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

# Run the compiled configuration to make the target node a DSC Pull Server
Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
```

#### <a name="registration-key"></a><span data-ttu-id="70b03-176">Chave de registo</span><span class="sxs-lookup"><span data-stu-id="70b03-176">Registration Key</span></span>

<span data-ttu-id="70b03-177">Para permitir nós registar o servidor para que estes possam utilizar nomes de configuração em vez de um ID de configuração de cliente, uma chave de registo que foi criada na configuração acima é guardada num ficheiro denominado `RegistrationKeys.txt` no `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="70b03-177">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="70b03-178">A chave de registo funciona como um segredo partilhado utilizado durante o registo inicial pelo cliente com o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="70b03-178">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="70b03-179">O cliente irá gerar um certificado autoassinado que é utilizado para autenticar exclusivamente para o servidor de solicitação assim que o registo é concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="70b03-179">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="70b03-180">O thumbprint deste certificado é armazenado localmente e associado ao URL do servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="70b03-180">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="70b03-181">**Tenha em atenção**: as chaves de registo não são suportadas no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="70b03-181">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="70b03-182">Para poder configurar um nó para autenticar com o servidor de solicitação, a chave de registo tem de ser a configuração meta para qualquer nó de destino que irá registar este servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="70b03-182">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="70b03-183">Tenha em atenção que o **RegistrationKey** a configuração meta do abaixo é removido depois da máquina de destino registou com êxito e de que o valor '140a952b-b9d6-406b-b416-e0f759c9c0e4' tem de corresponder ao valor armazenado no Ficheiro de RegistrationKeys.txt no servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="70b03-183">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="70b03-184">Sempre processe o valor da chave de registo de forma segura, a porque a saber o permite que qualquer máquina de destino registar o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="70b03-184">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

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

> <span data-ttu-id="70b03-185">**Tenha em atenção**: O **ReportServerWeb** secção permite que os dados sejam enviados para o servidor de solicitação de relatórios.</span><span class="sxs-lookup"><span data-stu-id="70b03-185">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="70b03-186">A falta do **ConfigurationID** propriedade no ficheiro de configuração meta significa implicitamente esse servidor de solicitação é suportar a versão de V2 do protocolo de servidor de solicitação para um registo inicial é necessário.</span><span class="sxs-lookup"><span data-stu-id="70b03-186">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="70b03-187">Por outro lado, a presença de um **ConfigurationID** significa que é utilizada a versão de V1 do protocolo de servidor de solicitação e que não existe nenhum processamento do registo.</span><span class="sxs-lookup"><span data-stu-id="70b03-187">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="70b03-188">**Tenha em atenção**: num PUSH cenário, um erro existe na versão atual que torna necessárias para definir uma propriedade de ConfigurationID no ficheiro de configuração meta de nós que nunca tenha registado com um servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="70b03-188">**Note**: In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="70b03-189">Este procedimento irá forçar o protocolo de servidor de solicitação V1 e evitar as mensagens de falha de registo.</span><span class="sxs-lookup"><span data-stu-id="70b03-189">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="70b03-190">Colocar recursos e configurações</span><span class="sxs-lookup"><span data-stu-id="70b03-190">Placing configurations and resources</span></span>

<span data-ttu-id="70b03-191">Após a extração servidor conclusão da configuração, as pastas definidas pelo **ConfigurationPath** e **ModulePath** propriedades na configuração do servidor de solicitação são onde irá colocar módulos e configurações que estarão disponíveis para nós de destino, a extrair.</span><span class="sxs-lookup"><span data-stu-id="70b03-191">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="70b03-192">Estes ficheiros têm de estar num formato específico para o servidor de solicitação processar corretamente.</span><span class="sxs-lookup"><span data-stu-id="70b03-192">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="70b03-193">Formato de módulo de pacote de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="70b03-193">DSC resource module package format</span></span>

<span data-ttu-id="70b03-194">Cada módulo de recursos tem de ser zipado e nomeado, de acordo com o padrão seguinte `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="70b03-194">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>
<span data-ttu-id="70b03-195">Por exemplo, um módulo com o nome xWebAdminstration com uma versão do módulo de 3.1.2.0 seria possível com o nome 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="70b03-195">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span>
<span data-ttu-id="70b03-196">Cada versão do módulo tem de estar contido num ficheiro zip único.</span><span class="sxs-lookup"><span data-stu-id="70b03-196">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="70b03-197">Uma vez que existe apenas uma única versão de um recurso em cada ficheiro zip, o formato de módulo adicionado no WMF 5.0 com suporte para várias versões de módulo num único diretório não é suportado.</span><span class="sxs-lookup"><span data-stu-id="70b03-197">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="70b03-198">Isto significa que antes do empacotamento dos módulos de recursos de DSC para utilização com o servidor de solicitação, terá de efetuar uma alteração de pequena para a estrutura de diretórios.</span><span class="sxs-lookup"><span data-stu-id="70b03-198">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="70b03-199">O formato predefinido de módulos que contém os recursos de DSC na WMF 5.0 é ' {pasta do módulo}\{versão do módulo} \DscResources\{pasta de recursos de DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="70b03-199">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="70b03-200">Antes de empacotamento para o servidor de solicitação, remova o **{versão do módulo}** pasta para o caminho fica ' {pasta do módulo} \DscResources\{pasta de recursos de DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="70b03-200">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="70b03-201">Com esta alteração, zip a pasta, conforme descrito acima e colocar esses ficheiros zip no **ModulePath** pasta.</span><span class="sxs-lookup"><span data-stu-id="70b03-201">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="70b03-202">Utilize `New-DscChecksum {module zip file}` para criar um ficheiro de soma de verificação para o módulo recentemente adicionado.</span><span class="sxs-lookup"><span data-stu-id="70b03-202">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="70b03-203">Formato MOF de configuração</span><span class="sxs-lookup"><span data-stu-id="70b03-203">Configuration MOF format</span></span>

<span data-ttu-id="70b03-204">Um ficheiro MOF de configuração tem de estar associados a um ficheiro de soma de verificação para que o MMC num nó de destino pode validar a configuração.</span><span class="sxs-lookup"><span data-stu-id="70b03-204">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="70b03-205">Para criar uma soma de verificação, chame o [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70b03-205">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span></span>
<span data-ttu-id="70b03-206">O cmdlet assume um **caminho** parâmetro que especifica a pasta onde está localizada a configuração MOF.</span><span class="sxs-lookup"><span data-stu-id="70b03-206">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="70b03-207">O cmdlet cria um ficheiro de soma de verificação chamado `ConfigurationMOFName.mof.checksum`, onde `ConfigurationMOFName` é o nome do ficheiro mof configuração.</span><span class="sxs-lookup"><span data-stu-id="70b03-207">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="70b03-208">Se existirem mais de uma configuração MOF ficheiros na pasta especificada, é criada uma soma de verificação para cada configuração na pasta.</span><span class="sxs-lookup"><span data-stu-id="70b03-208">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="70b03-209">Colocar os ficheiros MOF e os respetivos ficheiros de soma de verificação associados no **ConfigurationPath** pasta.</span><span class="sxs-lookup"><span data-stu-id="70b03-209">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="70b03-210">**Tenha em atenção**: Se alterar o ficheiro MOF de configuração de qualquer forma, também tem de recriar o ficheiro de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="70b03-210">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="70b03-211">As ferramentas</span><span class="sxs-lookup"><span data-stu-id="70b03-211">Tooling</span></span>

<span data-ttu-id="70b03-212">Para efetuar a definição de cópia de segurança, validar e gerir o servidor de solicitação mais fácil, as ferramentas seguintes estão incluídas como exemplos na versão mais recente do módulo xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="70b03-212">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="70b03-213">Um módulo que irão ajudá-lo com o empacotamento módulos de recursos de DSC e ficheiros de configuração para utilização no servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="70b03-213">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="70b03-214">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="70b03-214">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="70b03-215">Exemplos abaixo:</span><span class="sxs-lookup"><span data-stu-id="70b03-215">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="70b03-216">Um script que valida o servidor de solicitação está configurado corretamente.</span><span class="sxs-lookup"><span data-stu-id="70b03-216">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="70b03-217">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="70b03-217">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="70b03-218">Soluções de Comunidade do serviço de solicitação</span><span class="sxs-lookup"><span data-stu-id="70b03-218">Community Solutions for Pull Service</span></span>

<span data-ttu-id="70b03-219">A Comunidade do DSC tem criadas várias soluções para implementar o protocolo de serviço de extração.</span><span class="sxs-lookup"><span data-stu-id="70b03-219">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="70b03-220">Para ambientes no local, estes oferecem capacidades de solicitação do serviço e uma oportunidade para contribuir para a Comunidade com melhoramentos incrementais.</span><span class="sxs-lookup"><span data-stu-id="70b03-220">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="70b03-221">Tug</span><span class="sxs-lookup"><span data-stu-id="70b03-221">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="70b03-222">DSC TRÆK</span><span class="sxs-lookup"><span data-stu-id="70b03-222">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="70b03-223">Solicitar a configuração do cliente</span><span class="sxs-lookup"><span data-stu-id="70b03-223">Pull client configuration</span></span>

<span data-ttu-id="70b03-224">Os tópicos seguintes descrevem como configurar clientes de solicitação detalhadamente:</span><span class="sxs-lookup"><span data-stu-id="70b03-224">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="70b03-225">Configurar um cliente de solicitação do DSC com um ID de configuração</span><span class="sxs-lookup"><span data-stu-id="70b03-225">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="70b03-226">Configurar um cliente de solicitação do DSC com nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="70b03-226">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="70b03-227">Configurações parciais</span><span class="sxs-lookup"><span data-stu-id="70b03-227">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="70b03-228">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70b03-228">See also</span></span>

- [<span data-ttu-id="70b03-229">Descrição geral da configuração do estado pretendido do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="70b03-229">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="70b03-230">Aplicar configurações</span><span class="sxs-lookup"><span data-stu-id="70b03-230">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="70b03-231">Utilizar um servidor de relatório de DSC</span><span class="sxs-lookup"><span data-stu-id="70b03-231">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="70b03-232">[[MS-DSCPM]: pretendido protocolo de modelo de extração de configuração de estado](https://msdn.microsoft.com/library/dn393548.aspx)</span><span class="sxs-lookup"><span data-stu-id="70b03-232">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx)</span></span>
- <span data-ttu-id="70b03-233">[[MS-DSCPM]: pretendido Errata de protocolo de modelo de extração de configuração de estado](https://msdn.microsoft.com/library/mt612824.aspx)</span><span class="sxs-lookup"><span data-stu-id="70b03-233">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx)</span></span>