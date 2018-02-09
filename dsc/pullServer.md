---
ms.date: 2018-02-02
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Serviço de solicitação do DSC"
ms.openlocfilehash: d5e24dcc093c73d8ebbaa618517193dacc4f2aaf
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/09/2018
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="42cac-103">Serviço de solicitação de configuração do estado pretendido</span><span class="sxs-lookup"><span data-stu-id="42cac-103">Desired State Configuration Pull Service</span></span>

> <span data-ttu-id="42cac-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="42cac-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="42cac-105">Gestor de configuração locais podem ser geridos centralmente por uma solução de serviço de extração.</span><span class="sxs-lookup"><span data-stu-id="42cac-105">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="42cac-106">Quando utilizar esta abordagem, o nó que está a ser gerido está registado com um serviço e atribuído uma configuração nas definições do MMC.</span><span class="sxs-lookup"><span data-stu-id="42cac-106">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="42cac-107">A configuração e todos os recursos de DSC necessários como dependências para a configuração são transferidos para a máquina e utilizados pelo MMC para gerir a configuração.</span><span class="sxs-lookup"><span data-stu-id="42cac-107">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="42cac-108">Informações sobre o estado da máquina que está a ser gerido são carregadas para o serviço de relatórios.</span><span class="sxs-lookup"><span data-stu-id="42cac-108">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="42cac-109">Este conceito é referido como "serviço de solicitação".</span><span class="sxs-lookup"><span data-stu-id="42cac-109">This concept is referred to as "pull service".</span></span>

<span data-ttu-id="42cac-110">As opções de atuais para o serviço de solicitação incluem:</span><span class="sxs-lookup"><span data-stu-id="42cac-110">The current options for pull service include:</span></span>

- <span data-ttu-id="42cac-111">Serviço de configuração de estado de Desired de automatização do Azure</span><span class="sxs-lookup"><span data-stu-id="42cac-111">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="42cac-112">Um serviço de solicitação em execução no Windows Server</span><span class="sxs-lookup"><span data-stu-id="42cac-112">A pull service running on Windows Server</span></span>
- <span data-ttu-id="42cac-113">Comunidade mantida soluções de código aberto</span><span class="sxs-lookup"><span data-stu-id="42cac-113">Community maintained open source solutions</span></span>
- <span data-ttu-id="42cac-114">Uma partilha SMB</span><span class="sxs-lookup"><span data-stu-id="42cac-114">An SMB share</span></span>

<span data-ttu-id="42cac-115">**A solução recomendada**, e a opção com mais funcionalidades disponíveis, é [Automation DSC do Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="42cac-115">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="42cac-116">O serviço do Azure pode gerir nós no local em centros de dados privados ou em nuvens públicas, tais como o Azure e AWS.</span><span class="sxs-lookup"><span data-stu-id="42cac-116">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="42cac-117">Para ambientes privados em que os servidores não é possível ligar diretamente à Internet, considere limitar o tráfego de saída para apenas o intervalo de IP de Azure publicado (consulte [intervalos de IP do Datacenter do Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="42cac-117">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="42cac-118">As funcionalidades do serviço online que não estão atualmente disponíveis no serviço de solicitação no Windows Server incluem:</span><span class="sxs-lookup"><span data-stu-id="42cac-118">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>
- <span data-ttu-id="42cac-119">Todos os dados são encriptados em trânsito e o restante</span><span class="sxs-lookup"><span data-stu-id="42cac-119">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="42cac-120">Certificados de cliente são criados e geridos automaticamente</span><span class="sxs-lookup"><span data-stu-id="42cac-120">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="42cac-121">Armazenam segredos para gerir centralmente [palavras-passe/credenciais](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), ou [variáveis](https://docs.microsoft.com/en-us/azure/automation/automation-variables) tais como nomes de servidor ou cadeias de ligação</span><span class="sxs-lookup"><span data-stu-id="42cac-121">Secrets store for centrally managing [passwords/credentials](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), or [variables](https://docs.microsoft.com/en-us/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="42cac-122">Gerir centralmente o nó [configuração MMC](metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="42cac-122">Centrally manage node [LCM configuration](metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="42cac-123">Atribuir centralmente configurações para nós de cliente</span><span class="sxs-lookup"><span data-stu-id="42cac-123">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="42cac-124">Configuração de versão é alterada para "grupos canary" para fins de teste antes de atingir a produção</span><span class="sxs-lookup"><span data-stu-id="42cac-124">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="42cac-125">Gráfico de relatórios</span><span class="sxs-lookup"><span data-stu-id="42cac-125">Graphical reporting</span></span>
  - <span data-ttu-id="42cac-126">Detalhes de estado ao nível de recursos do DSC de granularidade</span><span class="sxs-lookup"><span data-stu-id="42cac-126">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="42cac-127">Mensagens de erro verbosas provenientes de máquinas de cliente para resolução de problemas</span><span class="sxs-lookup"><span data-stu-id="42cac-127">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="42cac-128">[Integração com o Log Analytics do Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) para alertar, tarefas automatizadas, a aplicação Android/iOS para relatórios e alertas</span><span class="sxs-lookup"><span data-stu-id="42cac-128">[Integration with Azure Log Analytics](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="42cac-129">Serviço de solicitação do DSC no Windows Server</span><span class="sxs-lookup"><span data-stu-id="42cac-129">DSC pull service in Windows Server</span></span>

<span data-ttu-id="42cac-130">É possível configurar um serviço de solicitação para ser executado no Windows Server.</span><span class="sxs-lookup"><span data-stu-id="42cac-130">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="42cac-131">Volte a ser aconselhado que a solução de serviço de solicitação incluída no Windows Server inclui apenas capacidades de armazenamento de configurações/módulos para transferência e capturar os dados de relatório na base de dados.</span><span class="sxs-lookup"><span data-stu-id="42cac-131">Please be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="42cac-132">Não inclui muitas das funcionalidades oferecidas pelo serviço do Azure e, por isso, não é uma ferramenta boa para avaliar como o serviço poderia ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="42cac-132">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="42cac-133">O serviço de solicitação disponibilizado no Windows Server é um serviço web do IIS que utiliza uma interface de OData para fazer com que os ficheiros de configuração de DSC disponíveis para nós de destino quando os nós peça-lhes.</span><span class="sxs-lookup"><span data-stu-id="42cac-133">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="42cac-134">Requisitos para utilizar um servidor de solicitação:</span><span class="sxs-lookup"><span data-stu-id="42cac-134">Requirements for using a pull server:</span></span>

- <span data-ttu-id="42cac-135">Um servidor a executar:</span><span class="sxs-lookup"><span data-stu-id="42cac-135">A server running:</span></span>
  - <span data-ttu-id="42cac-136">WMF/PowerShell 5.0 ou superior</span><span class="sxs-lookup"><span data-stu-id="42cac-136">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="42cac-137">Função de servidor IIS</span><span class="sxs-lookup"><span data-stu-id="42cac-137">IIS server role</span></span>
  - <span data-ttu-id="42cac-138">Serviço de DSC</span><span class="sxs-lookup"><span data-stu-id="42cac-138">DSC Service</span></span>
- <span data-ttu-id="42cac-139">Idealmente, algumas significa de gerar um certificado, para proteger as credenciais transmitidas para Gestor de configuração Local (MMC) em nós de destino</span><span class="sxs-lookup"><span data-stu-id="42cac-139">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="42cac-140">A melhor forma de configurar o Windows Server para o serviço de solicitação do anfitrião está a utilizar uma configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="42cac-140">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="42cac-141">Um script de exemplo é fornecido abaixo.</span><span class="sxs-lookup"><span data-stu-id="42cac-141">An example script is provided below.</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="42cac-142">Utilizar o recurso de xDSCWebService</span><span class="sxs-lookup"><span data-stu-id="42cac-142">Using the xDSCWebService resource</span></span>

<span data-ttu-id="42cac-143">A forma mais fácil de configurar um servidor de solicitação web consiste em utilizar o recurso de xWebService incluído no módulo xPSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="42cac-143">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="42cac-144">Os passos seguintes explicam como utilizar o recurso uma configuração de que configura o serviço web.</span><span class="sxs-lookup"><span data-stu-id="42cac-144">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="42cac-145">Chamar o [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet para instalar o **xPSDesiredStateConfiguration** módulo.</span><span class="sxs-lookup"><span data-stu-id="42cac-145">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="42cac-146">**Tenha em atenção**: **Install-Module** está incluído no **PowerShellGet** módulo, que está incluído no PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="42cac-146">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="42cac-147">Pode transferir o **PowerShellGet** módulo para o PowerShell 3.0 e 4.0 em [pré-visualização de módulos do PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="42cac-147">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> 
1. <span data-ttu-id="42cac-148">Obter um certificado SSL para o servidor de solicitação do DSC de uma autoridade de certificação fidedigna-se dentro da sua organização ou uma autoridade de pública.</span><span class="sxs-lookup"><span data-stu-id="42cac-148">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="42cac-149">O certificado recebido a partir da autoridade de normalmente se encontra no formato PFX.</span><span class="sxs-lookup"><span data-stu-id="42cac-149">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="42cac-150">Instale o certificado no nó que irá tornar-se o servidor de solicitação do DSC na localização predefinida que deve ser CERT: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="42cac-150">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="42cac-151">Anote o thumbprint do certificado.</span><span class="sxs-lookup"><span data-stu-id="42cac-151">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="42cac-152">Selecione um GUID para ser utilizado como a chave de registo.</span><span class="sxs-lookup"><span data-stu-id="42cac-152">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="42cac-153">Para gerar um através do PowerShell, introduza o seguinte na linha de PS e prima enter: '``` [guid]::newGuid()```'ou'```New-Guid```'.</span><span class="sxs-lookup"><span data-stu-id="42cac-153">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="42cac-154">Esta chave será utilizada por nós de cliente como uma chave partilhada para autenticar durante o registo.</span><span class="sxs-lookup"><span data-stu-id="42cac-154">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="42cac-155">Para obter mais informações, consulte a secção de chave de registo abaixo.</span><span class="sxs-lookup"><span data-stu-id="42cac-155">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="42cac-156">No ISE do PowerShell, iniciar (F5), o seguinte script de configuração (incluído na pasta de exemplo a **xPSDesiredStateConfiguration** módulo como Sample_xDscWebService.ps1).</span><span class="sxs-lookup"><span data-stu-id="42cac-156">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="42cac-157">Este script configura o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="42cac-157">This script sets up the pull server.</span></span>

```powershell
    configuration Sample_xDscPullServer
    {
        param
        (
                [string[]]$NodeName = 'localhost',

                [ValidateNotNullOrEmpty()]
                [string] $certificateThumbPrint,

                [Parameter(Mandatory)]
                [ValidateNotNullOrEmpty()]
                [string] $RegistrationKey
         )

         Import-DSCResource -ModuleName xPSDesiredStateConfiguration
         Import-DSCResource –ModuleName PSDesiredStateConfiguration

         Node $NodeName
         {
             WindowsFeature DSCServiceFeature
             {
                 Ensure = 'Present'
                 Name   = 'DSC-Service'
             }

             xDscWebService PSDSCPullServer
             {
                 Ensure                   = 'Present'
                 EndpointName             = 'PSDSCPullServer'
                 Port                     = 8080
                 PhysicalPath             = "$env:SystemDrive\inetpub\PSDSCPullServer"
                 CertificateThumbPrint    = $certificateThumbPrint
                 ModulePath               = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                 ConfigurationPath        = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                 State                    = 'Started'
                 DependsOn                = '[WindowsFeature]DSCServiceFeature'
                 UseSecurityBestPractices = $false
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

1. <span data-ttu-id="42cac-158">Execute a configuração, transmitir o thumbprint do certificado SSL como o **certificateThumbPrint** parâmetro e um registo GUID de chave como o **RegistrationKey** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="42cac-158">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose

```

#### <a name="registration-key"></a><span data-ttu-id="42cac-159">Chave de registo</span><span class="sxs-lookup"><span data-stu-id="42cac-159">Registration Key</span></span>

<span data-ttu-id="42cac-160">Para permitir nós registar o servidor para que estes possam utilizar nomes de configuração em vez de um ID de configuração de cliente, uma chave de registo que foi criada na configuração acima é guardada num ficheiro denominado `RegistrationKeys.txt` no `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="42cac-160">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="42cac-161">A chave de registo funciona como um segredo partilhado utilizado durante o registo inicial pelo cliente com o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="42cac-161">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="42cac-162">O cliente irá gerar um certificado autoassinado que é utilizado para autenticar exclusivamente para o servidor de solicitação assim que o registo é concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="42cac-162">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="42cac-163">O thumbprint deste certificado é armazenado localmente e associado ao URL do servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="42cac-163">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="42cac-164">**Tenha em atenção**: as chaves de registo não são suportadas no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="42cac-164">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span> 

<span data-ttu-id="42cac-165">Para configurar um nó para autenticar com o servidor de solicitação, o registo chave tem de ser a configuração meta para qualquer nó de destino que irá registar este servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="42cac-165">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="42cac-166">Tenha em atenção que o **RegistrationKey** a configuração meta do abaixo é removido depois da máquina de destino registou com êxito e de que o valor '140a952b-b9d6-406b-b416-e0f759c9c0e4' tem de corresponder ao valor armazenado no Ficheiro de RegistrationKeys.txt no servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="42cac-166">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="42cac-167">Sempre processe o valor da chave de registo de forma segura, a porque a saber o permite que qualquer máquina de destino registar o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="42cac-167">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey    = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes


```

> <span data-ttu-id="42cac-168">**Tenha em atenção**: O **ReportServerWeb** secção permite que os dados sejam enviados para o servidor de solicitação de relatórios.</span><span class="sxs-lookup"><span data-stu-id="42cac-168">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="42cac-169">A falta do **ConfigurationID** propriedade no ficheiro de configuração meta significa implicitamente esse servidor de solicitação é suportar a versão de V2 do protocolo de servidor de solicitação para um registo inicial é necessário.</span><span class="sxs-lookup"><span data-stu-id="42cac-169">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="42cac-170">Por outro lado, a presença de um **ConfigurationID** significa que é utilizada a versão de V1 do protocolo de servidor de solicitação e que não existe nenhum processamento do registo.</span><span class="sxs-lookup"><span data-stu-id="42cac-170">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="42cac-171">**Tenha em atenção**: num PUSH cenário, um erro existe o relase atual que torna necessárias para definir uma propriedade de ConfigurationID no ficheiro de configuração meta de nós que nunca tenha registado com um servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="42cac-171">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="42cac-172">Este procedimento irá forçar o protocolo de servidor de solicitação V1 e evitar as mensagens de falha de registo.</span><span class="sxs-lookup"><span data-stu-id="42cac-172">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="42cac-173">Colocar recursos e configurações</span><span class="sxs-lookup"><span data-stu-id="42cac-173">Placing configurations and resources</span></span>

<span data-ttu-id="42cac-174">Após a extração servidor conclusão da configuração, as pastas definidas pelo **ConfigurationPath** e **ModulePath** propriedades na configuração do servidor de solicitação são onde irá colocar módulos e configurações que estarão disponíveis para nós de destino, a extrair.</span><span class="sxs-lookup"><span data-stu-id="42cac-174">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="42cac-175">Estes ficheiros têm de estar num formato específico para o servidor de solicitação processar corretamente.</span><span class="sxs-lookup"><span data-stu-id="42cac-175">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="42cac-176">Formato de módulo de pacote de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="42cac-176">DSC resource module package format</span></span>

<span data-ttu-id="42cac-177">Cada módulo de recursos tem de ser zipado e com o nome de acordo com o padrão seguinte `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="42cac-177">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span>
<span data-ttu-id="42cac-178">Por exemplo, um módulo com o nome xWebAdminstration com uma versão do módulo de 3.1.2.0 seria possível com o nome 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="42cac-178">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span>
<span data-ttu-id="42cac-179">Cada versão do módulo tem de estar contido num ficheiro zip único.</span><span class="sxs-lookup"><span data-stu-id="42cac-179">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="42cac-180">Uma vez que existe apenas uma única versão de um recurso em cada ficheiro zip o formato de módulo adicionado no WMF 5.0 com suporte para várias versões de módulo num único diretório não é suportado.</span><span class="sxs-lookup"><span data-stu-id="42cac-180">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="42cac-181">Isto significa que antes do empacotamento dos módulos de recursos de DSC para utilização com o servidor de solicitação, terá de efetuar uma alteração de pequena para a estrutura de diretórios.</span><span class="sxs-lookup"><span data-stu-id="42cac-181">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="42cac-182">O formato predefinido de módulos que contém os recursos de DSC na WMF 5.0 é ' {pasta do módulo}\{versão do módulo} \DscResources\{pasta de recursos de DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="42cac-182">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="42cac-183">Antes de empacotamento para o servidor de solicitação basta remover a **{versão do módulo}** pasta para o caminho fica ' {pasta do módulo} \DscResources\{pasta de recursos de DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="42cac-183">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="42cac-184">Com esta alteração, zip a pasta, conforme descrito acima e colocar esses ficheiros zip no **ModulePath** pasta.</span><span class="sxs-lookup"><span data-stu-id="42cac-184">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="42cac-185">Utilize `new-dscchecksum {module zip file}` para criar um ficheiro de soma de verificação para o módulo recentemente adicionado.</span><span class="sxs-lookup"><span data-stu-id="42cac-185">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="42cac-186">Formato MOF de configuração</span><span class="sxs-lookup"><span data-stu-id="42cac-186">Configuration MOF format</span></span>

<span data-ttu-id="42cac-187">Um ficheiro MOF de configuração tem de estar associados a um ficheiro de soma de verificação para que o MMC num nó de destino pode validar a configuração.</span><span class="sxs-lookup"><span data-stu-id="42cac-187">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="42cac-188">Para criar uma soma de verificação, chame o [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="42cac-188">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span>
<span data-ttu-id="42cac-189">O cmdlet assume um **caminho** parâmetro que especifica a pasta onde está localizada a configuração MOF.</span><span class="sxs-lookup"><span data-stu-id="42cac-189">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="42cac-190">O cmdlet cria um ficheiro de soma de verificação chamado `ConfigurationMOFName.mof.checksum`, onde `ConfigurationMOFName` é o nome do ficheiro mof configuração.</span><span class="sxs-lookup"><span data-stu-id="42cac-190">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="42cac-191">Se existirem mais de uma configuração MOF ficheiros na pasta especificada, é criada uma soma de verificação para cada configuração na pasta.</span><span class="sxs-lookup"><span data-stu-id="42cac-191">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="42cac-192">Colocar os ficheiros MOF e os respetivos ficheiros de soma de verificação associados no **ConfigurationPath** pasta.</span><span class="sxs-lookup"><span data-stu-id="42cac-192">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="42cac-193">**Tenha em atenção**: Se alterar o ficheiro MOF de configuração de qualquer forma, também tem de recriar o ficheiro de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="42cac-193">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="42cac-194">As ferramentas</span><span class="sxs-lookup"><span data-stu-id="42cac-194">Tooling</span></span>

<span data-ttu-id="42cac-195">Para efetuar a definição de cópia de segurança, validar e gerir o servidor de solicitação mais fácil, as ferramentas seguintes estão incluídas como exemplos na versão mais recente do módulo xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="42cac-195">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="42cac-196">Um módulo que irão ajudá-lo com o empacotamento módulos de recursos de DSC e ficheiros de configuração para utilização no servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="42cac-196">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="42cac-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="42cac-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="42cac-198">Exemplos abaixo:</span><span class="sxs-lookup"><span data-stu-id="42cac-198">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="42cac-199">Um script que valida o servidor de solicitação está configurado corretamente.</span><span class="sxs-lookup"><span data-stu-id="42cac-199">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="42cac-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="42cac-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="42cac-201">Soluções de Comunidade do serviço de solicitação</span><span class="sxs-lookup"><span data-stu-id="42cac-201">Community Solutions for Pull Service</span></span>

<span data-ttu-id="42cac-202">A Comunidade do DSC tem criadas várias soluções para implementar o protocolo de serviço de extração.</span><span class="sxs-lookup"><span data-stu-id="42cac-202">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="42cac-203">Para on-premises ambientes que estes oferecem capacidades de solicitação do serviço e uma oportunidade para contribuir fazer uma cópia à Comunidade com melhoramentos incrementais.</span><span class="sxs-lookup"><span data-stu-id="42cac-203">For on-premises environments these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="42cac-204">Tug</span><span class="sxs-lookup"><span data-stu-id="42cac-204">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="42cac-205">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="42cac-205">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="42cac-206">Solicitar a configuração do cliente</span><span class="sxs-lookup"><span data-stu-id="42cac-206">Pull client configuration</span></span>

<span data-ttu-id="42cac-207">Os tópicos seguintes descrevem como configurar clientes de solicitação detalhadamente:</span><span class="sxs-lookup"><span data-stu-id="42cac-207">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="42cac-208">Configurar um cliente de solicitação do DSC com um ID de configuração</span><span class="sxs-lookup"><span data-stu-id="42cac-208">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="42cac-209">Configurar um cliente de solicitação do DSC com nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="42cac-209">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="42cac-210">Configurações parciais</span><span class="sxs-lookup"><span data-stu-id="42cac-210">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="42cac-211">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42cac-211">See also</span></span>

- [<span data-ttu-id="42cac-212">Descrição geral da configuração do estado pretendido do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="42cac-212">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="42cac-213">Aplicar configurações</span><span class="sxs-lookup"><span data-stu-id="42cac-213">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="42cac-214">Utilizar um servidor de relatório de DSC</span><span class="sxs-lookup"><span data-stu-id="42cac-214">Using a DSC report server</span></span>](reportServer.md)
