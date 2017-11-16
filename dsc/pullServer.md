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
# <a name="setting-up-a-dsc-web-pull-server"></a>Configurar um servidor de solicitação do DSC web

> Aplica-se a: O Windows PowerShell 5.0

Um servidor de solicitação do DSC web é um serviço web do IIS que utiliza uma interface de OData para fazer com que os ficheiros de configuração de DSC disponíveis para nós de destino quando os nós peça-lhes.

Requisitos para utilizar um servidor de solicitação:

* Um servidor a executar:
  - WMF/PowerShell 5.0 ou superior
  - Função de servidor IIS
  - Serviço de DSC
* Idealmente, algumas significa de gerar um certificado, para proteger as credenciais transmitidas para Gestor de configuração Local (MMC) em nós de destino

Pode adicionar a função de servidor IIS e o serviço de DSC com o Assistente Adicionar funções e funcionalidades no Gestor de servidores ou utilizando o PowerShell. Os scripts de exemplo incluídos neste tópico irão processar ambos estes passos para si, bem como.

## <a name="using-the-xdscwebservice-resource"></a>Utilizar o recurso de xDSCWebService
A forma mais fácil de configurar um servidor de solicitação web consiste em utilizar o recurso de xWebService incluído no módulo xPSDesiredStateConfiguration. Os passos seguintes explicam como utilizar o recurso uma configuração de que configura o serviço web.

1. Chamar o [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet para instalar o **xPSDesiredStateConfiguration** módulo. **Tenha em atenção**: **Install-Module** está incluído no **PowerShellGet** módulo, que está incluído no PowerShell 5.0. Pode transferir o **PowerShellGet** módulo para o PowerShell 3.0 e 4.0 em [pré-visualização de módulos do PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186). 
1. Obter um certificado SSL para o servidor de solicitação do DSC de uma autoridade de certificação fidedigna-se dentro da sua organização ou uma autoridade de pública. O certificado recebido a partir da autoridade de normalmente se encontra no formato PFX. Instale o certificado no nó que irá tornar-se o servidor de solicitação do DSC na localização predefinida que deve ser CERT: \LocalMachine\My. Anote o thumbprint do certificado.
1. Selecione um GUID para ser utilizado como a chave de registo. Para gerar um através do PowerShell, introduza o seguinte na linha de PS e prima enter: '``` [guid]::newGuid()```'ou'```New-Guid```'. Esta chave será utilizada por nós de cliente como uma chave partilhada para autenticar durante o registo. Para obter mais informações, consulte a secção de chave de registo abaixo.
1. No ISE do PowerShell, iniciar (F5), o seguinte script de configuração (incluído na pasta de exemplo a **xPSDesiredStateConfiguration** módulo como Sample_xDscWebService.ps1). Este script configura o servidor de solicitação.
  
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

1. Execute a configuração, transmitir o thumbprint do certificado SSL como o **certificateThumbPrint** parâmetro e um registo GUID de chave como o **RegistrationKey** parâmetro:

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

## <a name="registration-key"></a>Chave de registo
Para permitir nós registar o servidor para que estes possam utilizar nomes de configuração em vez de um ID de configuração de cliente, uma chave de registo que foi criada na configuração acima é guardada num ficheiro denominado `RegistrationKeys.txt` no `C:\Program Files\WindowsPowerShell\DscService`. A chave de registo funciona como um segredo partilhado utilizado durante o registo inicial pelo cliente com o servidor de solicitação. O cliente irá gerar um certificado autoassinado que é utilizado para autenticar exclusivamente para o servidor de solicitação assim que o registo é concluído com êxito. O thumbprint deste certificado é armazenado localmente e associado ao URL do servidor de solicitação.
> **Tenha em atenção**: as chaves de registo não são suportadas no PowerShell 4.0. 

Para configurar um nó para autenticar com o servidor de solicitação, o registo chave tem de ser a configuração meta para qualquer nó de destino que irá registar este servidor de solicitação. Tenha em atenção que o **RegistrationKey** a configuração meta do abaixo é removido depois da máquina de destino registou com êxito e de que o valor '140a952b-b9d6-406b-b416-e0f759c9c0e4' tem de corresponder ao valor armazenado no Ficheiro de RegistrationKeys.txt no servidor de solicitação. Sempre processe o valor da chave de registo de forma segura, a porque a saber o permite que qualquer máquina de destino registar o servidor de solicitação.

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
> **Tenha em atenção**: O **ReportServerWeb** secção permite que os dados sejam enviados para o servidor de solicitação de relatórios. 

A falta do **ConfigurationID** propriedade no ficheiro de configuração meta significa implicitamente esse servidor de solicitação é suportar a versão de V2 do protocolo de servidor de solicitação para um registo inicial é necessário. Por outro lado, a presença de um **ConfigurationID** significa que é utilizada a versão de V1 do protocolo de servidor de solicitação e que não existe nenhum processamento do registo.

>**Tenha em atenção**: num PUSH cenário, um erro existe o relase atual que torna necessárias para definir uma propriedade de ConfigurationID no ficheiro de configuração meta de nós que nunca tenha registado com um servidor de solicitação. Este procedimento irá forçar o protocolo de servidor de solicitação V1 e evitar as mensagens de falha de registo.

## <a name="placing-configurations-and-resources"></a>Colocar recursos e configurações

Após a extração servidor conclusão da configuração, as pastas definidas pelo **ConfigurationPath** e **ModulePath** propriedades na configuração do servidor de solicitação são onde irá colocar módulos e configurações que estarão disponíveis para nós de destino, a extrair. Estes ficheiros têm de estar num formato específico para o servidor de solicitação processar corretamente. 

### <a name="dsc-resource-module-package-format"></a>Formato de módulo de pacote de recursos de DSC

Cada módulo de recursos tem de ser zipado e com o nome de acordo com o padrão seguinte `{Module Name}_{Module Version}.zip`. Por exemplo, um módulo com o nome xWebAdminstration com uma versão do módulo de 3.1.2.0 seria possível com o nome 'xWebAdministration_3.2.1.0.zip'. Cada versão do módulo tem de estar contido num ficheiro zip único. Uma vez que existe apenas uma única versão de um recurso em cada ficheiro zip o formato de módulo adicionado no WMF 5.0 com suporte para várias versões de módulo num único diretório não é suportado. Isto significa que antes do empacotamento dos módulos de recursos de DSC para utilização com o servidor de solicitação, terá de efetuar uma alteração de pequena para a estrutura de diretórios. O formato predefinido de módulos que contém os recursos de DSC na WMF 5.0 é ' {pasta do módulo}\{versão do módulo} \DscResources\{pasta de recursos de DSC}\'. Antes de empacotamento para o servidor de solicitação basta remover a **{versão do módulo}** pasta para o caminho fica ' {pasta do módulo} \DscResources\{pasta de recursos de DSC}\'. Com esta alteração, zip a pasta, conforme descrito acima e colocar esses ficheiros zip no **ModulePath** pasta.

Utilize `new-dscchecksum {module zip file}` para criar um ficheiro de soma de verificação para o módulo recentemente adicionado.

### <a name="configuration-mof-format"></a>Formato MOF de configuração 
Um ficheiro MOF de configuração tem de estar associados a um ficheiro de soma de verificação para que o MMC num nó de destino pode validar a configuração. Para criar uma soma de verificação, chame o [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet. O cmdlet assume um **caminho** parâmetro que especifica a pasta onde está localizada a configuração MOF. O cmdlet cria um ficheiro de soma de verificação chamado `ConfigurationMOFName.mof.checksum`, onde `ConfigurationMOFName` é o nome do ficheiro mof configuração. Se existirem mais de uma configuração MOF ficheiros na pasta especificada, é criada uma soma de verificação para cada configuração na pasta. Colocar os ficheiros MOF e os respetivos ficheiros de soma de verificação associados no o **ConfigurationPath** pasta.

>**Tenha em atenção**: Se alterar o ficheiro MOF de configuração de qualquer forma, também tem de recriar o ficheiro de soma de verificação.

## <a name="tooling"></a>As ferramentas
Para efetuar a definição de cópia de segurança, validar e gerir o servidor de solicitação mais fácil, as ferramentas seguintes estão incluídas como exemplos na versão mais recente do módulo xPSDesiredStateConfiguration:
1. Um módulo que irão ajudá-lo com o empacotamento módulos de recursos de DSC e ficheiros de configuração para utilização no servidor de solicitação. [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1). Exemplos abaixo:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Um script que valida o servidor de solicitação está configurado corretamente. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).


## <a name="pull-client-configuration"></a>Solicitar a configuração do cliente 
Os tópicos seguintes descrevem como configurar clientes de solicitação detalhadamente:

* [Configurar um cliente de solicitação do DSC com um ID de configuração](pullClientConfigID.md)
* [Configurar um cliente de solicitação do DSC com nomes de configuração](pullClientConfigNames.md)
* [Configurações parciais](partialConfigs.md)


## <a name="see-also"></a>Consulte também
* [Descrição geral da configuração do estado pretendido do Windows PowerShell](overview.md)
* [Enacting configurações](enactingConfigurations.md)
* [Utilizar um servidor de relatório de DSC](reportServer.md)

