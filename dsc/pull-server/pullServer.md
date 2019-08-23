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
# <a name="desired-state-configuration-pull-service"></a>Serviço de pull de configuração de estado desejado

> [!IMPORTANT]
> O servidor de pull (Windows Feature *DSC-Service*) é um componente com suporte do Windows Server, no entanto, não há planos para oferecer novos recursos ou funcionalidades. É recomendável começar a fazer a transição de clientes gerenciados para o [Azure DSC de automação](/azure/automation/automation-dsc-getting-started) (inclui recursos além do servidor de pull no Windows Server) ou uma das soluções da Comunidade listadas [aqui](pullserver.md#community-solutions-for-pull-service).

Os Configuration Manager locais podem ser gerenciados centralmente por uma solução de serviço de pull.
Ao usar essa abordagem, o nó que está sendo gerenciado é registrado com um serviço e atribuiu uma configuração nas configurações do LCM.
A configuração e todos os recursos de DSC necessários como dependências para a configuração são baixados para o computador e usados pelo LCM para gerenciar a configuração.
As informações sobre o estado da máquina que está sendo gerenciada são carregadas no serviço para relatórios.
Esse conceito é conhecido como "serviço de pull".

As opções atuais para o serviço de pull incluem:

- Serviço de configuração de estado desejado da automação do Azure
- Um serviço de pull em execução no Windows Server
- Soluções de código aberto mantidas pela Comunidade
- Um compartilhamento SMB

**A solução recomendada**e a opção com a maioria dos recursos disponíveis é o [Azure DSC de automação](/azure/automation/automation-dsc-getting-started).

O serviço do Azure pode gerenciar nós locais em data centers privados ou em nuvens públicas, como Azure e AWS.
Para ambientes privados em que os servidores não podem se conectar diretamente à Internet, considere limitar o tráfego de saída para apenas o intervalo de IPS do Azure publicado (consulte [intervalos de IP do datacenter do Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).

Os recursos do serviço online que não estão disponíveis atualmente no serviço de pull no Windows Server incluem:

- Todos os dados são criptografados em trânsito e em repouso
- Os certificados de cliente são criados e gerenciados automaticamente
- Repositório de segredos para gerenciar centralmente [senhas/credenciais](/azure/automation/automation-credentials)ou [variáveis](/azure/automation/automation-variables) como nomes de servidor ou cadeias de conexão
- Gerenciar centralmente a [configuração do LCM](../managing-nodes/metaConfig.md#basic-settings) do nó
- Atribuir centralmente configurações a nós de cliente
- Liberar alterações de configuração para "grupos de canário" para teste antes de alcançar a produção
- Relatórios gráficos
  - Detalhes de status no nível de granularidade do recurso de DSC
  - Mensagens de erro detalhadas de computadores cliente para solução de problemas
- [Integração com o Azure log Analytics](/azure/automation/automation-dsc-diagnostics) para alertas, tarefas automatizadas, aplicativo Android/Ios para relatórios e alertas

## <a name="dsc-pull-service-in-windows-server"></a>Serviço de pull de DSC no Windows Server

É possível configurar um serviço de pull para ser executado no Windows Server.
Lembre-se de que a solução de serviço de pull incluída no Windows Server inclui apenas recursos de armazenamento de configurações/módulos para baixar e capturar dados de relatório no banco de dado.
Ele não inclui muitos dos recursos oferecidos pelo serviço no Azure e, portanto, não é uma boa ferramenta para avaliar como o serviço seria usado.

O serviço de pull oferecido no Windows Server é um serviço Web no IIS que usa uma interface OData para disponibilizar os arquivos de configuração DSC para nós de destino quando esses nós os solicitam.

Requisitos para usar um servidor de pull:

- Um servidor executando:
  - WMF/PowerShell 4,0 ou superior
  - Função de servidor do IIS
  - Serviço DSC
- Idealmente, alguns meios de gerar um certificado, para proteger as credenciais passadas para o Configuration Manager local (LCM) nos nós de destino

A melhor maneira de configurar o Windows Server para hospedar o serviço de pull é usar uma configuração DSC.
Um script de exemplo é fornecido abaixo.

### <a name="supported-database-systems"></a>Sistemas de banco de dados com suporte

|WMF 4,0   |WMF 5.0  |WMF 5.1 |WMF 5,1 (Windows Server Insider Preview 17090)|
|---------|---------|---------|---------|
|MDB     |ESENT (padrão), MDB |ESENT (padrão), MDB|ESENT (padrão), SQL Server, MDB

A partir da versão 17090 do [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server é uma opção com suporte para o serviço de pull (Windows Feature *DSC-Service*). Isso fornece uma nova opção para dimensionar grandes ambientes de DSC que não foram migrados para o [Azure DSC de automação](/azure/automation/automation-dsc-getting-started).

> [!NOTE]
> SQL Server suporte não será adicionado às versões anteriores do WMF 5,1 (ou anteriores) e estará disponível apenas em versões do Windows Server maiores ou iguais a 17090.

Para configurar o servidor de pull para usar SQL Server, defina como `$true` e SqlConnectionString como uma cadeia de conexão de SQL Server válida. Para obter mais informações, consulte cadeias de [conexão SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).
Para obter um exemplo de configuração de SQL Server com **xDscWebService**, leia primeiro [usando o recurso xDscWebService](#using-the-xdscwebservice-resource) e, em seguida, examine [Sample_xDscWebServiceRegistration_UseSQLProvider. ps1 no GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).

### <a name="using-the-xdscwebservice-resource"></a>Usando o recurso xDscWebService

A maneira mais fácil de configurar um servidor de pull da Web é usar o recurso **xDscWebService** , incluído no módulo **xPSDesiredStateConfiguration** .
As etapas a seguir explicam como usar o recurso em uma configuração que configura o serviço Web.

1. Chame o cmdlet [install-Module](/powershell/module/PowershellGet/Install-Module) para instalar o módulo **xPSDesiredStateConfiguration** .
   > [!NOTE]
   > O **install-Module** está incluído no módulo **PowerShellGet** , que está incluído no PowerShell 5,0. Você pode baixar o módulo **PowerShellGet** para o PowerShell 3,0 e 4,0 na versão [prévia dos módulos do PowerShell do PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
2. Obtenha um certificado SSL para o servidor de pull de DSC de uma autoridade de certificação confiável, seja na sua organização ou em uma autoridade pública. O certificado recebido da autoridade geralmente está no formato PFX.
3. Instale o certificado no nó que se tornará o servidor de pull de DSC no local padrão, que deve `CERT:\LocalMachine\My`ser.
   - Anote a impressão digital do certificado.
4. Selecione um GUID a ser usado como a chave de registro. Para gerar um usando o PowerShell, insira o seguinte no prompt do PS e pressione `[guid]::newGuid()` Enter `New-Guid`: ou. Essa chave será usada por nós de cliente como uma chave compartilhada para autenticar durante o registro. Para obter mais informações, consulte a seção chave de registro abaixo.
5. No ISE do PowerShell, inicie (F5) o script de configuração a seguir (incluído na pasta de exemplos do módulo xPSDesiredStateConfiguration `Sample_xDscWebServiceRegistration.ps1`como). Esse script configura o servidor de pull.

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

6. Execute a configuração, passando a impressão digital do certificado SSL como o parâmetro **certificateThumbPrint** e uma chave de registro GUID como o parâmetro **RegistrationKey** :

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a>Chave de registro

Para permitir que os nós de cliente se registrem no servidor para que eles possam usar nomes de configuração em vez de uma ID de configuração, uma chave de registro que foi criada pela configuração acima `RegistrationKeys.txt` é `C:\Program Files\WindowsPowerShell\DscService`salva em um arquivo chamado em. A chave de registro funciona como um segredo compartilhado usado durante o registro inicial pelo cliente com o servidor de pull. O cliente irá gerar um certificado autoassinado que será usado para autenticar exclusivamente o servidor de pull depois que o registro for concluído com êxito. A impressão digital desse certificado é armazenada localmente e associada à URL do servidor de pull.

> [!NOTE]
> Não há suporte para chaves de registro no PowerShell 4,0.

Para configurar um nó para autenticar com o servidor de pull, a chave de registro deve estar na metaconfiguração para qualquer nó de destino que será registrado com esse servidor de pull. Observe que o **RegistrationKey** na metaconfiguração abaixo é removido depois que o computador de destino foi registrado com êxito e que o valor deve corresponder ao valor armazenado no `RegistrationKeys.txt` arquivo no servidor de pull (' 140a952b-b9d6-406B-b416-e0f759c9c0e4 ' para este exemplo). Sempre trate o valor da chave de registro com segurança, pois saber que ele permite que qualquer computador de destino se registre no servidor de pull.

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
> A seção **ReportServerWeb** permite que os dados de relatório sejam enviados para o servidor de pull.

A falta da propriedade **ConfigurationId** no arquivo de metaconfiguração significa implicitamente que o servidor de pull dá suporte à versão v2 do protocolo de servidor de pull para que um registro inicial seja necessário.
Por outro lado, a presença de uma **ConfigurationId** significa que a versão v1 do protocolo de servidor de pull é usada e não há nenhum processamento de registro.

> [!NOTE]
> Em um cenário de PUSH, existe um bug na versão atual que torna necessário definir uma propriedade ConfigurationId no arquivo de metaconfiguração para nós que nunca foram registrados com um servidor de pull. Isso forçará o protocolo de servidor de pull v1 e evitará mensagens de falha de registro.

## <a name="placing-configurations-and-resources"></a>Colocando configurações e recursos

Depois que a instalação do servidor de pull for concluída, as pastas definidas pelas propriedades **ConfigurationPath** e **ModulePath** na configuração do servidor de pull serão onde você colocará os módulos e as configurações que estarão disponíveis para o recebimento dos nós de destino.
Esses arquivos precisam estar em um formato específico para que o servidor de pull os processe corretamente.

### <a name="dsc-resource-module-package-format"></a>Formato do pacote do módulo de recurso DSC

Cada módulo de recurso precisa ser compactado e nomeado de acordo com o `{Module Name}_{Module Version}.zip`padrão a seguir.

Por exemplo, um módulo chamado xWebAdminstration com uma versão de módulo de 3.1.2.0 seria nomeado `xWebAdministration_3.1.2.0.zip`.
Cada versão de um módulo deve estar contida em um único arquivo zip.
Como há apenas uma única versão de um recurso em cada arquivo zip, não há suporte para o formato de módulo adicionado no WMF 5,0 com suporte para várias versões de módulo em um único diretório.
Isso significa que, antes de empacotar módulos de recursos de DSC para uso com o servidor de pull, você precisará fazer uma pequena alteração na estrutura do diretório.
O formato padrão dos módulos que contêm o recurso DSC no WMF `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`5,0 é.
Antes de empacotar para o servidor de pull, remova a pasta **{módulo Version}** para que `{Module Folder}\DscResources\{DSC Resource Folder}\`o caminho se torne.
Com essa alteração, compacte a pasta conforme descrito acima e coloque esses arquivos zip na pasta **ModulePath**

Use `New-DscChecksum {module zip file}` para criar um arquivo de soma de verificação para o módulo recém-adicionado.

### <a name="configuration-mof-format"></a>Formato MOF de configuração

Um arquivo MOF de configuração precisa ser emparelhado com um arquivo de soma de verificação para que um LCM em um nó de destino possa validar a configuração.
Para criar uma soma de verificação, chame o cmdlet [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) .
O cmdlet usa um parâmetro **path** que especifica a pasta onde o MOF de configuração está localizado.
O cmdlet cria um arquivo de soma `ConfigurationMOFName.mof.checksum`de verificação `ConfigurationMOFName` chamado, em que é o nome do arquivo MOF de configuração.
Se houver mais de um arquivo MOF de configuração na pasta especificada, uma soma de verificação será criada para cada configuração na pasta.
Coloque os arquivos MOF e seus arquivos de soma de verificação associados na pasta **ConfigurationPath**

> [!NOTE]
> Se você alterar o arquivo MOF de configuração de alguma forma, também deverá recriar o arquivo de soma de verificação.

### <a name="tooling"></a>Ferramentas

Para facilitar a configuração, a validação e o gerenciamento do servidor de pull, as seguintes ferramentas são incluídas como exemplos na versão mais recente do módulo xPSDesiredStateConfiguration:

1. Um módulo que ajudará a empacotar módulos de recursos de DSC e arquivos de configuração para uso no servidor de pull.
   [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).
   Exemplos abaixo:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Um script que valida o servidor de pull está configurado corretamente. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).

## <a name="community-solutions-for-pull-service"></a>Soluções da Comunidade para serviço de pull

A comunidade de DSC criou várias soluções para implementar o protocolo de serviço de pull.
Para ambientes locais, eles oferecem recursos de serviço de pull e uma oportunidade de contribuir de volta para a Comunidade com aprimoramentos incrementais.

- [Levemente](https://github.com/powershellorg/tug)
- [DSC-TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>Configuração do cliente de pull

Os tópicos a seguir descrevem a configuração de clientes de pull em detalhes:

- [Configurar um cliente de pull de DSC usando uma ID de configuração](pullClientConfigID.md)
- [Configurar um cliente de pull de DSC usando nomes de configuração](pullClientConfigNames.md)
- [Configurações parciais](partialConfigs.md)

## <a name="see-also"></a>Consulte também

- [Visão geral da configuração de estado desejado do Windows PowerShell](../overview/overview.md)
- [Aplicar configurações](enactingConfigurations.md)
- [Utilizar um servidor de relatório de DSC](reportServer.md)
- [[MS-DSCPM]: Protocolo de modelo de pull de configuração de estado desejado](https://msdn.microsoft.com/library/dn393548.aspx)
- [[MS-DSCPM]: Errata do protocolo do modelo pull da configuração de estado desejado](https://msdn.microsoft.com/library/mt612824.aspx)
