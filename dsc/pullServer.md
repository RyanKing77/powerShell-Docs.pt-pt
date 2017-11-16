---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Configurar um servidor de solicitação do DSC web"
ms.openlocfilehash: 03d4d148c87854b146091aa0e8d815b8c35def72
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/31/2017
---
# <a name="setting-up-a-dsc-web-pull-server"></a><span data-ttu-id="e0187-103">Configurar um servidor de solicitação do DSC web</span><span class="sxs-lookup"><span data-stu-id="e0187-103">Setting up a DSC web pull server</span></span>

> <span data-ttu-id="e0187-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e0187-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="e0187-105">Um servidor de solicitação do DSC web é um serviço web do IIS que utiliza uma interface de OData para fazer com que os ficheiros de configuração de DSC disponíveis para nós de destino quando os nós peça-lhes.</span><span class="sxs-lookup"><span data-stu-id="e0187-105">A DSC web pull server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="e0187-106">Requisitos para utilizar um servidor de solicitação:</span><span class="sxs-lookup"><span data-stu-id="e0187-106">Requirements for using a pull server:</span></span>

* <span data-ttu-id="e0187-107">Um servidor a executar:</span><span class="sxs-lookup"><span data-stu-id="e0187-107">A server running:</span></span>
  - <span data-ttu-id="e0187-108">WMF/PowerShell 5.0 ou superior</span><span class="sxs-lookup"><span data-stu-id="e0187-108">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="e0187-109">Função de servidor IIS</span><span class="sxs-lookup"><span data-stu-id="e0187-109">IIS server role</span></span>
  - <span data-ttu-id="e0187-110">Serviço de DSC</span><span class="sxs-lookup"><span data-stu-id="e0187-110">DSC Service</span></span>
* <span data-ttu-id="e0187-111">Idealmente, algumas significa de gerar um certificado, para proteger as credenciais transmitidas para Gestor de configuração Local (MMC) em nós de destino</span><span class="sxs-lookup"><span data-stu-id="e0187-111">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="e0187-112">Pode adicionar a função de servidor IIS e o serviço de DSC com o Assistente Adicionar funções e funcionalidades no Gestor de servidores ou utilizando o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0187-112">You can add the IIS server role and DSC Service with the Add Roles and Features wizard in Server Manager, or by using PowerShell.</span></span> <span data-ttu-id="e0187-113">Os scripts de exemplo incluídos neste tópico irão processar ambos estes passos para si, bem como.</span><span class="sxs-lookup"><span data-stu-id="e0187-113">The sample scripts included in this topic will handle both of these steps for you as well.</span></span>

## <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="e0187-114">Utilizar o recurso de xDSCWebService</span><span class="sxs-lookup"><span data-stu-id="e0187-114">Using the xDSCWebService resource</span></span>
<span data-ttu-id="e0187-115">A forma mais fácil de configurar um servidor de solicitação web consiste em utilizar o recurso de xWebService incluído no módulo xPSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="e0187-115">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span> <span data-ttu-id="e0187-116">Os passos seguintes explicam como utilizar o recurso uma configuração de que configura o serviço web.</span><span class="sxs-lookup"><span data-stu-id="e0187-116">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="e0187-117">Chamar o [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet para instalar o **xPSDesiredStateConfiguration** módulo.</span><span class="sxs-lookup"><span data-stu-id="e0187-117">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="e0187-118">**Tenha em atenção**: **Install-Module** está incluído no **PowerShellGet** módulo, que está incluído no PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="e0187-118">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="e0187-119">Pode transferir o **PowerShellGet** módulo para o PowerShell 3.0 e 4.0 em [pré-visualização de módulos do PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="e0187-119">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> 
1. <span data-ttu-id="e0187-120">Obter um certificado SSL para o servidor de solicitação do DSC de uma autoridade de certificação fidedigna-se dentro da sua organização ou uma autoridade de pública.</span><span class="sxs-lookup"><span data-stu-id="e0187-120">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="e0187-121">O certificado recebido a partir da autoridade de normalmente se encontra no formato PFX.</span><span class="sxs-lookup"><span data-stu-id="e0187-121">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="e0187-122">Instale o certificado no nó que irá tornar-se o servidor de solicitação do DSC na localização predefinida que deve ser CERT: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="e0187-122">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="e0187-123">Anote o thumbprint do certificado.</span><span class="sxs-lookup"><span data-stu-id="e0187-123">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="e0187-124">Selecione um GUID para ser utilizado como a chave de registo.</span><span class="sxs-lookup"><span data-stu-id="e0187-124">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="e0187-125">Para gerar um através do PowerShell, introduza o seguinte na linha de PS e prima enter: '``` [guid]::newGuid()```'ou'```New-Guid```'.</span><span class="sxs-lookup"><span data-stu-id="e0187-125">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="e0187-126">Esta chave será utilizada por nós de cliente como uma chave partilhada para autenticar durante o registo.</span><span class="sxs-lookup"><span data-stu-id="e0187-126">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="e0187-127">Para obter mais informações, consulte a secção de chave de registo abaixo.</span><span class="sxs-lookup"><span data-stu-id="e0187-127">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="e0187-128">No ISE do PowerShell, iniciar (F5), o seguinte script de configuração (incluído na pasta de exemplo a **xPSDesiredStateConfiguration** módulo como Sample_xDscWebService.ps1).</span><span class="sxs-lookup"><span data-stu-id="e0187-128">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="e0187-129">Este script configura o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="e0187-129">This script sets up the pull server.</span></span>
  
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

1. <span data-ttu-id="e0187-130">Execute a configuração, transmitir o thumbprint do certificado SSL como o **certificateThumbPrint** parâmetro e um registo GUID de chave como o **RegistrationKey** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="e0187-130">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

## <a name="registration-key"></a><span data-ttu-id="e0187-131">Chave de registo</span><span class="sxs-lookup"><span data-stu-id="e0187-131">Registration Key</span></span>
<span data-ttu-id="e0187-132">Para permitir nós registar o servidor para que estes possam utilizar nomes de configuração em vez de um ID de configuração de cliente, uma chave de registo que foi criada na configuração acima é guardada num ficheiro denominado `RegistrationKeys.txt` no `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="e0187-132">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="e0187-133">A chave de registo funciona como um segredo partilhado utilizado durante o registo inicial pelo cliente com o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="e0187-133">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="e0187-134">O cliente irá gerar um certificado autoassinado que é utilizado para autenticar exclusivamente para o servidor de solicitação assim que o registo é concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="e0187-134">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="e0187-135">O thumbprint deste certificado é armazenado localmente e associado ao URL do servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="e0187-135">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="e0187-136">**Tenha em atenção**: as chaves de registo não são suportadas no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="e0187-136">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span> 

<span data-ttu-id="e0187-137">Para configurar um nó para autenticar com o servidor de solicitação, o registo chave tem de ser a configuração meta para qualquer nó de destino que irá registar este servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="e0187-137">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="e0187-138">Tenha em atenção que o **RegistrationKey** a configuração meta do abaixo é removido depois da máquina de destino registou com êxito e de que o valor '140a952b-b9d6-406b-b416-e0f759c9c0e4' tem de corresponder ao valor armazenado no Ficheiro de RegistrationKeys.txt no servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="e0187-138">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="e0187-139">Sempre processe o valor da chave de registo de forma segura, a porque a saber o permite que qualquer máquina de destino registar o servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="e0187-139">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

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
> <span data-ttu-id="e0187-140">**Tenha em atenção**: O **ReportServerWeb** secção permite que os dados sejam enviados para o servidor de solicitação de relatórios.</span><span class="sxs-lookup"><span data-stu-id="e0187-140">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span> 

<span data-ttu-id="e0187-141">A falta do **ConfigurationID** propriedade no ficheiro de configuração meta significa implicitamente esse servidor de solicitação é suportar a versão de V2 do protocolo de servidor de solicitação para um registo inicial é necessário.</span><span class="sxs-lookup"><span data-stu-id="e0187-141">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span> <span data-ttu-id="e0187-142">Por outro lado, a presença de um **ConfigurationID** significa que é utilizada a versão de V1 do protocolo de servidor de solicitação e que não existe nenhum processamento do registo.</span><span class="sxs-lookup"><span data-stu-id="e0187-142">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="e0187-143">**Tenha em atenção**: num PUSH cenário, um erro existe o relase atual que torna necessárias para definir uma propriedade de ConfigurationID no ficheiro de configuração meta de nós que nunca tenha registado com um servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="e0187-143">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="e0187-144">Este procedimento irá forçar o protocolo de servidor de solicitação V1 e evitar as mensagens de falha de registo.</span><span class="sxs-lookup"><span data-stu-id="e0187-144">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="e0187-145">Colocar recursos e configurações</span><span class="sxs-lookup"><span data-stu-id="e0187-145">Placing configurations and resources</span></span>

<span data-ttu-id="e0187-146">Após a extração servidor conclusão da configuração, as pastas definidas pelo **ConfigurationPath** e **ModulePath** propriedades na configuração do servidor de solicitação são onde irá colocar módulos e configurações que estarão disponíveis para nós de destino, a extrair.</span><span class="sxs-lookup"><span data-stu-id="e0187-146">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span> <span data-ttu-id="e0187-147">Estes ficheiros têm de estar num formato específico para o servidor de solicitação processar corretamente.</span><span class="sxs-lookup"><span data-stu-id="e0187-147">These files need to be in a specific format in order for the pull server to correctly process them.</span></span> 

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="e0187-148">Formato de módulo de pacote de recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="e0187-148">DSC resource module package format</span></span>

<span data-ttu-id="e0187-149">Cada módulo de recursos tem de ser zipado e com o nome de acordo com o padrão seguinte `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="e0187-149">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="e0187-150">Por exemplo, um módulo com o nome xWebAdminstration com uma versão do módulo de 3.1.2.0 seria possível com o nome 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="e0187-150">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="e0187-151">Cada versão do módulo tem de estar contido num ficheiro zip único.</span><span class="sxs-lookup"><span data-stu-id="e0187-151">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="e0187-152">Uma vez que existe apenas uma única versão de um recurso em cada ficheiro zip o formato de módulo adicionado no WMF 5.0 com suporte para várias versões de módulo num único diretório não é suportado.</span><span class="sxs-lookup"><span data-stu-id="e0187-152">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="e0187-153">Isto significa que antes do empacotamento dos módulos de recursos de DSC para utilização com o servidor de solicitação, terá de efetuar uma alteração de pequena para a estrutura de diretórios.</span><span class="sxs-lookup"><span data-stu-id="e0187-153">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span> <span data-ttu-id="e0187-154">O formato predefinido de módulos que contém os recursos de DSC na WMF 5.0 é ' {pasta do módulo}\{versão do módulo} \DscResources\{pasta de recursos de DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="e0187-154">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="e0187-155">Antes de empacotamento para o servidor de solicitação basta remover a **{versão do módulo}** pasta para o caminho fica ' {pasta do módulo} \DscResources\{pasta de recursos de DSC}\'.</span><span class="sxs-lookup"><span data-stu-id="e0187-155">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="e0187-156">Com esta alteração, zip a pasta, conforme descrito acima e colocar esses ficheiros zip no **ModulePath** pasta.</span><span class="sxs-lookup"><span data-stu-id="e0187-156">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="e0187-157">Utilize `new-dscchecksum {module zip file}` para criar um ficheiro de soma de verificação para o módulo recentemente adicionado.</span><span class="sxs-lookup"><span data-stu-id="e0187-157">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="e0187-158">Formato MOF de configuração</span><span class="sxs-lookup"><span data-stu-id="e0187-158">Configuration MOF format</span></span> 
<span data-ttu-id="e0187-159">Um ficheiro MOF de configuração tem de estar associados a um ficheiro de soma de verificação para que o MMC num nó de destino pode validar a configuração.</span><span class="sxs-lookup"><span data-stu-id="e0187-159">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="e0187-160">Para criar uma soma de verificação, chame o [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e0187-160">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="e0187-161">O cmdlet assume um **caminho** parâmetro que especifica a pasta onde está localizada a configuração MOF.</span><span class="sxs-lookup"><span data-stu-id="e0187-161">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="e0187-162">O cmdlet cria um ficheiro de soma de verificação chamado `ConfigurationMOFName.mof.checksum`, onde `ConfigurationMOFName` é o nome do ficheiro mof configuração.</span><span class="sxs-lookup"><span data-stu-id="e0187-162">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="e0187-163">Se existirem mais de uma configuração MOF ficheiros na pasta especificada, é criada uma soma de verificação para cada configuração na pasta.</span><span class="sxs-lookup"><span data-stu-id="e0187-163">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span> <span data-ttu-id="e0187-164">Colocar os ficheiros MOF e os respetivos ficheiros de soma de verificação associados no o **ConfigurationPath** pasta.</span><span class="sxs-lookup"><span data-stu-id="e0187-164">Place the MOF files and their associated checksum files in the the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="e0187-165">**Tenha em atenção**: Se alterar o ficheiro MOF de configuração de qualquer forma, também tem de recriar o ficheiro de soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="e0187-165">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="tooling"></a><span data-ttu-id="e0187-166">As ferramentas</span><span class="sxs-lookup"><span data-stu-id="e0187-166">Tooling</span></span>
<span data-ttu-id="e0187-167">Para efetuar a definição de cópia de segurança, validar e gerir o servidor de solicitação mais fácil, as ferramentas seguintes estão incluídas como exemplos na versão mais recente do módulo xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="e0187-167">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>
1. <span data-ttu-id="e0187-168">Um módulo que irão ajudá-lo com o empacotamento módulos de recursos de DSC e ficheiros de configuração para utilização no servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="e0187-168">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="e0187-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="e0187-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="e0187-170">Exemplos abaixo:</span><span class="sxs-lookup"><span data-stu-id="e0187-170">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="e0187-171">Um script que valida o servidor de solicitação está configurado corretamente.</span><span class="sxs-lookup"><span data-stu-id="e0187-171">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="e0187-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="e0187-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>


## <a name="pull-client-configuration"></a><span data-ttu-id="e0187-173">Solicitar a configuração do cliente</span><span class="sxs-lookup"><span data-stu-id="e0187-173">Pull client configuration</span></span> 
<span data-ttu-id="e0187-174">Os tópicos seguintes descrevem como configurar clientes de solicitação detalhadamente:</span><span class="sxs-lookup"><span data-stu-id="e0187-174">The following topics describe setting up pull clients in detail:</span></span>

* [<span data-ttu-id="e0187-175">Configurar um cliente de solicitação do DSC com um ID de configuração</span><span class="sxs-lookup"><span data-stu-id="e0187-175">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
* [<span data-ttu-id="e0187-176">Configurar um cliente de solicitação do DSC com nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="e0187-176">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="e0187-177">Configurações parciais</span><span class="sxs-lookup"><span data-stu-id="e0187-177">Partial configurations</span></span>](partialConfigs.md)


## <a name="see-also"></a><span data-ttu-id="e0187-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0187-178">See also</span></span>
* [<span data-ttu-id="e0187-179">Descrição geral da configuração do estado pretendido do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e0187-179">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="e0187-180">Enacting configurações</span><span class="sxs-lookup"><span data-stu-id="e0187-180">Enacting configurations</span></span>](enactingConfigurations.md)
* [<span data-ttu-id="e0187-181">Utilizar um servidor de relatório de DSC</span><span class="sxs-lookup"><span data-stu-id="e0187-181">Using a DSC report server</span></span>](reportServer.md)

