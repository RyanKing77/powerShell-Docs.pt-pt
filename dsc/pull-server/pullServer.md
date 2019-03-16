---
ms.date: 03/04/2019
keywords: DSC, powershell, configuração, a configuração
title: Serviço de Solicitação de DSC
ms.openlocfilehash: 00e01e6c71226e6bde48b221e4e4fcf5f346feb4
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056775"
---
# <a name="desired-state-configuration-pull-service"></a>Serviço de solicitação do Desired State Configuration

> [!IMPORTANT]
> O servidor de solicitação (recurso do Windows *DSC-serviço*) é um componente suportado do Windows Server no entanto, não existem planos para oferecer novas funcionalidades ou capacidades. É recomendado para começar a fazer a transição geridos os clientes [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação de mensagens em fila no Windows Server) ou uma das soluções da Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).

Gestor de configuração local podem ser geridos centralmente por uma solução de serviço de solicitação.
Ao usar essa abordagem, o nó que está a ser gerido é registado com um serviço e atribuído uma configuração nas definições do LCM.
A configuração e todos os recursos de DSC necessários como dependências para a configuração são transferidos para o computador e utilizados pelo LCM para gerir a configuração.
Informações sobre o estado da máquina a ser gerido são carregadas para o serviço de relatórios.
Esse conceito é conhecido como "serviço de solicitação de".

As opções atuais de serviço pull incluem:

- Serviço de Azure Automation Desired State Configuration
- Um serviço pull de execução no Windows Server
- Comunidade mantido soluções de código aberto
- Uma partilha de SMB

**A solução recomendada**, e a opção com mais recursos disponíveis, é [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started).

O serviço do Azure pode gerir nós no local nos centros de dados privados ou em clouds públicas, como o Azure e AWS.
Para ambientes privados em que os servidores não é possível ligar diretamente à Internet, considere limitar o tráfego de saída para apenas o intervalo de IP do Azure publicado (consulte [intervalos de IP de Datacenter do Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).

As funcionalidades do serviço online que não estão atualmente disponíveis no serviço pull no Windows Server incluem:

- Todos os dados são encriptados em trânsito e em repouso
- Certificados de cliente são criados e geridos automaticamente
- Arquivo de segredos para gerir centralmente [palavras-passe/credenciais](/azure/automation/automation-credentials), ou [variáveis](/azure/automation/automation-variables) tais como nomes de servidor ou cadeias de ligação
- Gerenciar centralmente nó [configuração LCM](../managing-nodes/metaConfig.md#basic-settings)
- Atribuir centralmente configurações a nós de cliente
- Configuração da versão é alterado para "grupos de proteção" para teste antes de chegar a produção
- Relatório de gráfico
  - Detalhe do status no nível de recursos de DSC de granularidade
  - Mensagens de erro detalhada das máquinas de cliente para resolução de problemas
- [Integração com o Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) para alertar, tarefas automatizadas, aplicações de Android/iOS para relatórios e alertas

## <a name="dsc-pull-service-in-windows-server"></a>Serviço de solicitação de DSC no Windows Server

É possível configurar um serviço de pull para ser executado no Windows Server.
Ser avisado que a solução de serviço pull incluída no Windows Server inclui capacidades únicas de armazenar configurações/modules para download e a captura de dados de relatório no banco de dados.
Não inclui muitas das funcionalidades oferecidas pelo serviço no Azure e, portanto, não é uma boa ferramenta para avaliar como o serviço deve ser utilizado.

O serviço pull oferecido no Windows Server é um serviço web no IIS que utilize uma interface de OData para disponibilizar os ficheiros de configuração de DSC em nós de destino quando esses nós peça para os mesmos.

Requisitos para utilizar um servidor de solicitação:

- Um servidor a executar:
  - WMF/PowerShell 4.0 ou superior
  - Função de servidor IIS
  - Serviço de DSC
- O ideal é que alguns significa de gerar um certificado, para proteger as credenciais transmitidas para Gestor de configuração Local (LCM) em nós de destino

A melhor forma de configurar o Windows Server para o serviço de solicitação do host é usar uma configuração de DSC.
Um script de exemplo é fornecido abaixo.

### <a name="supported-database-systems"></a>Sistemas de base de dados suportados

|WMF 4.0   |WMF 5.0  |WMF 5.1 |WMF 5.1 (Windows Server Insider Preview 17090)|
|---------|---------|---------|---------|
|MDB     |ESENT (predefinição), MDB |ESENT (predefinição), MDB|ESENT (predefinição), do SQL Server, MDB

A partir da versão 17090 dos [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), do SQL Server é uma opção suportada para o serviço de solicitação (funcionalidade do Windows *DSC-serviço*). Isso fornece uma nova opção de dimensionamento grandes ambientes de DSC que não foram migrados para [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started).

> [!NOTE]
> Suporte do SQL Server não será possível adicionar as versões anteriores do WMF 5.1 (ou anterior) e só estará disponível em versões do Windows Server maiores que ou iguais a 17090.

Para configurar o servidor de solicitação para utilizar o SQL Server, defina **SqlProvider** ao `$true` e **SqlConnectionString** para uma cadeia de ligação válida do SQL Server. Para obter mais informações, consulte [cadeias de ligação do SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).
Para obter um exemplo de configuração do SQL Server com **xDscWebService**, leia primeiro [usando o recurso de xDscWebService](#using-the-xdscwebservice-resource) e, em seguida, reveja [Sample_xDscWebServiceRegistration_ UseSQLProvider.ps1 no GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).

### <a name="using-the-xdscwebservice-resource"></a>Usando o recurso de xDscWebService

A maneira mais fácil de configurar um servidor de solicitação da web está a utilizar o **xDscWebService** recurso, incluído nos **xPSDesiredStateConfiguration** módulo.
Os passos seguintes explicam como usar o recurso numa configuração de que configura o serviço web.

1. Chamar o [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet para instalar o **xPSDesiredStateConfiguration** módulo.
   > [!NOTE]
   > **Install-Module** está incluído nos **PowerShellGet** módulo, que está incluído no PowerShell 5.0. Pode baixar o **PowerShellGet** módulo para o PowerShell 3.0 e 4.0 na [pré-visualização de módulos do PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
2. Obtenha um certificado SSL para o servidor de solicitação de DSC de uma autoridade de certificação fidedigna, se dentro da sua organização ou uma autoridade pública. O certificado recebido da autoridade geralmente se encontra no formato PFX.
3. Instalar o certificado no nó que irá tornar-se o servidor de solicitação do DSC na localização predefinida, que deve ser `CERT:\LocalMachine\My`.
   - Tome nota do thumbprint do certificado.
4. Selecione um GUID a ser utilizado como a chave de registo. Para gerar um com o PowerShell, introduza o seguinte na linha de comandos de PS e prima enter: `[guid]::newGuid()` ou `New-Guid`. Esta chave será utilizada por nós de cliente como uma chave partilhada para autenticar durante o registo. Para obter mais informações, consulte a secção de chave de registo abaixo.
5. No ISE do PowerShell, iniciar (F5), o seguinte script de configuração (incluído na pasta de exemplos do **xPSDesiredStateConfiguration** módulo como `Sample_xDscWebServiceRegistration.ps1`). Este script configura o servidor de solicitação.

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

6. Execute a configuração, passando o thumbprint do certificado SSL como o **certificateThumbPrint** parâmetro e um registo GUID da chave como o **RegistrationKey** parâmetro:

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a>Chave de registo

Para permitir que cliente nós registar com o servidor para que eles podem usar nomes de configuração em vez de um ID de configuração, uma chave de registo que foi criada pela configuração acima é guardada num ficheiro denominado `RegistrationKeys.txt` em `C:\Program Files\WindowsPowerShell\DscService`. A chave de registo funciona como um segredo partilhado utilizado durante o registo inicial pelo cliente com o servidor de solicitação. O cliente irá gerar um certificado autoassinado que é utilizado para autenticar exclusivamente para o servidor de solicitação, uma vez que o registo é concluído com êxito. O thumbprint deste certificado é armazenado localmente e associado com o URL do servidor de solicitação.

> [!NOTE]
> As chaves de registo não são suportadas no PowerShell 4.0.

Para configurar um nó para autenticar com o servidor de solicitação, a chave de registo tem de ser no metaconfiguration para qualquer nó de destino que irá registar este servidor de solicitação. Tenha em atenção que o **RegistrationKey** no metaconfiguration abaixo é removida depois da máquina de destino foi registado corretamente e que o valor tem de corresponder ao valor armazenado no `RegistrationKeys.txt` ficheiro no servidor de solicitação (' 140a952b-b9d6-406b-b416-e0f759c9c0e4' para este exemplo). Trate sempre o valor da chave de registo de forma segura, porque saber permite que qualquer máquina de destino registar com o servidor de solicitação.

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
> O **ReportServerWeb** seção permite que os dados sejam enviados para o servidor de solicitação de relatórios.

A falta do **ConfigurationID** propriedade no arquivo metaconfiguration implicitamente significa que esse servidor de solicitação é que suporta a versão V2 do protocolo de servidor pull para um registo inicial é necessário.
Por outro lado, a presença de um **ConfigurationID** significa que é utilizada a versão V1 do protocolo de servidor de solicitação e não existe nenhum processamento de registo.

> [!NOTE]
> Num cenário PUSH, um bug existe na versão atual que faz com que seja necessário definir uma propriedade de ConfigurationID no ficheiro metaconfiguration para nós que nunca tenha registado com um servidor de solicitação. Esta ação irá forçar o protocolo de servidor de solicitação do V1 e evitar mensagens de falha de registo.

## <a name="placing-configurations-and-resources"></a>Colocar recursos e configurações

Depois da solicitação servidor conclusão da configuração, as pastas definidas pelos **ConfigurationPath** e **ModulePath** propriedades na configuração do servidor de solicitação são onde irá colocar módulos e configurações que vai estar disponível para nós de destino efetuar pull.
Esses arquivos precisam ser num formato específico para que o servidor de solicitação para os processar corretamente.

### <a name="dsc-resource-module-package-format"></a>Formato de pacote do módulo de recursos de DSC

Cada módulo de recursos tem de ser comprimido e nomeado de acordo com o seguinte padrão `{Module Name}_{Module Version}.zip`.

Por exemplo, um módulo com o nome xWebAdminstration com uma versão do módulo do 3.1.2.0 teria o nome `xWebAdministration_3.2.1.0.zip`.
Cada versão de um módulo tem de estar contido num arquivo zip único.
Uma vez que existe apenas uma única versão de um recurso em cada arquivo zip, o formato do módulo adicionado no WMF 5.0 com suporte para várias versões do módulo num único diretório não é suportado.
Isso significa que, antes de empacotar os módulos de recursos de DSC para utilização com o servidor de solicitação precisará fazer uma pequena alteração para a estrutura de diretórios.
O formato de padrão de módulos que contém o recurso de DSC no WMF 5.0 é `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.
Antes de empacotamento tendo em vista o servidor de solicitação, remova os **{versão do módulo}** pasta para que o caminho se torna `{Module Folder}\DscResources\{DSC Resource Folder}\`.
Com esta alteração, zip na pasta, conforme descrito acima e colocar esses ficheiros zip no **ModulePath** pasta.

Utilize `New-DscChecksum {module zip file}` para criar um ficheiro de soma de verificação para o módulo recentemente adicionado.

### <a name="configuration-mof-format"></a>Formato MOF de configuração

Um ficheiro MOF de configuração tem de ser emparelhado com um ficheiro de soma de verificação para que um LCM num nó de destino pode validar a configuração.
Para criar uma soma de verificação, chamar o [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.
O cmdlet assume uma **caminho** parâmetro que especifica a pasta onde está localizada a MOF de configuração.
O cmdlet cria um ficheiro de soma de verificação com o nome `ConfigurationMOFName.mof.checksum`, onde `ConfigurationMOFName` é o nome do ficheiro de mof de configuração.
Se existirem mais de uma configuração de MOF ficheiros na pasta especificada, é criada uma soma de verificação para cada configuração na pasta.
Colocar os arquivos MOF e seus arquivos de soma de verificação associados no **ConfigurationPath** pasta.

> [!NOTE]
> Se alterar o ficheiro MOF de configuração de qualquer forma, também tem de recriar o arquivo de soma de verificação.

### <a name="tooling"></a>Ferramentas

Para que a definição de cópia de segurança, validação e gerir o servidor de solicitação fácil, as ferramentas seguintes estão incluídas como exemplos na versão mais recente do módulo xPSDesiredStateConfiguration:

1. Um módulo que o ajudará a com o empacotamento de ficheiros de configuração para utilização no servidor de solicitação e módulos de recursos de DSC.
   [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).
   Exemplos abaixo:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Um script que valida o servidor de solicitação está configurado corretamente. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).

## <a name="community-solutions-for-pull-service"></a>Soluções de Comunidade para o serviço de solicitação

A Comunidade de DSC é autor de várias soluções para implementar o protocolo de serviço de solicitação.
Para ambientes no local, elas oferecem capacidades do serviço de solicitação e uma oportunidade de contribuir para a Comunidade com melhorias incrementais.

- [Tug](https://github.com/powershellorg/tug)
- [DSC-TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>Configuração de cliente de solicitação

Os tópicos seguintes descrevem como configurar clientes de pull detalhadamente:

- [Configurar um cliente de solicitação de DSC com um ID de configuração](pullClientConfigID.md)
- [Configurar um cliente de solicitação de DSC com nomes de configuração](pullClientConfigNames.md)
- [Configurações parciais](partialConfigs.md)

## <a name="see-also"></a>Consulte também

- [Windows PowerShell Desired State Configuration descrição-geral](../overview/overview.md)
- [Aplicar configurações](enactingConfigurations.md)
- [Utilizar um servidor de relatório de DSC](reportServer.md)
- [[MS-DSCPM]: Desired State Configuration do protocolo de modelo de extração](https://msdn.microsoft.com/library/dn393548.aspx)
- [[MS-DSCPM]: Desired State Configuration Errata de protocolo de modelo de extração](https://msdn.microsoft.com/library/mt612824.aspx)
