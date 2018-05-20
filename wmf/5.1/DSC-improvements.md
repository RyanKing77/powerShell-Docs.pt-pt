---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Melhoramentos de DSC na WMF 5.1
ms.openlocfilehash: 32bdde6d43d17cc76c454fe10b00097753a9eebe
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/19/2018
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>Melhoramentos na configuração do estado pretendido (DSC) no WMF 5.1

## <a name="dsc-class-resource-improvements"></a>Melhoramentos de recursos do DSC classe

No WMF 5.1, podemos ter corrigido os seguintes problemas conhecidos:

- Get-DscConfiguration pode devolver valores vazios (nulos) ou erros, se um tipo de tabela complexas/hash é devolvido pela função Get() de um recurso de DSC com base na classe.
- Get-DscConfiguration devolve um erro se a credencial de RunAs é utilizada na configuração de DSC.
- Recursos baseados em classe não podem ser utilizado numa configuração composta.
- Início DscConfiguration bloqueia se recursos baseados na classe tem uma propriedade do seu próprio tipo.
- Recursos baseados em classe não podem ser utilizado como um recurso exclusivo.

## <a name="dsc-resource-debugging-improvements"></a>Melhoramentos de depuração de recursos de DSC

No WMF 5.0, o depurador do PowerShell não parou no método de recursos baseados na classe (Get/conjunto/teste) diretamente.
No WMF 5.1, o depurador interrompe no método baseado em classe de recursos da mesma forma que nos métodos de recursos baseados em MOF.

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>Cliente de solicitação do DSC suporta o TLS 1.1 e TLS 1.2

Anteriormente, o cliente de solicitação do DSC apenas suportado SSL3.0 e TLS1.0 através de ligações de HTTPS.
Quando forçado a utilizar protocolos mais seguros, o cliente de solicitação deixaria de funcionar.
WMF 5.1, o cliente de solicitação do DSC já não suporta SSL 3.0 e adiciona suporte para os protocolos TLS 1.1 e TLS 1.2 mais seguros.

## <a name="improved-pull-server-registration"></a>Registo do servidor de solicitação melhorada

Nas versões anteriores do WMF, registos/reporting simultâneas pedidos para um servidor de solicitação do DSC ao utilizar a base de dados ESENT seriam levar a MMC registar e/ou reportar a falhar.
Nestes casos, os registos de eventos no servidor de solicitação tem o erro "Nome de instância já em utilização."
Isto foi devido a um padrão incorreto, que está a ser utilizado para aceder à base de dados ESENT num cenário de vários threads.
No WMF 5.1, este problema.
Em simultâneo registos ou relatórios (que envolve a base de dados de ESENT) funciona bem em WMF 5.1.
Este problema é aplicável apenas a base de dados ESENT e não se aplica à base de dados OLEDB.

## <a name="enable-circular-log-on-esent-database-instance"></a>Ativar o registo Circular na instância de base de dados ESENT

Na versão de eariler do DSC PullServer, os ficheiros de registo da base de dados ESENT foram ao preencher o espaço em disco do becouse pullserver que estava a ser criada a instância de base de dados sem o registo circular. Nesta versão, terá a opção para controlar o comportamento de registo circular de instância utilizando o pullserver Web. config. Por predefinição CircularLogging está definido como TRUE.

```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="pull-partial-configuration-naming-convention"></a>Solicitar a Convenção de nomenclatura de configuração parcial

Na versão anterior, a Convenção de nomenclatura para uma configuração parcial foi que o nome do ficheiro MOF no servidor/serviço de extração deve corresponder ao nome da configuração parcial especificado nas definições de Gestor de configuração locais, que por sua vez tem de corresponder à o nome da configuração incorporado no ficheiro MOF.

Ver os instantâneos abaixo:

- Definições de configuração local que define uma configuração parcial que um nó está autorizado a receber.

![Configuração meta do exemplo](../images/MetaConfigPartialOne.png)

- Definição de configuração parcial de exemplo

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

- 'ConfigurationName' incorporado no ficheiro MOF gerado.

![Ficheiro mof gerado de exemplo](../images/PartialGeneratedMof.png)

- Nome do ficheiro no repositório de configuração de solicitação

![Nome do ficheiro no repositório de configuração](../images/PartialInConfigRepository.png)

Nome do serviço de automatização do Azure gerado ficheiros MOF como `<ConfigurationName>.<NodeName>.mof`.
Por isso, a configuração abaixo compila para PartialOne.localhost.mof.

Isto efetuadas-impossíveis para solicitar um da sua configuração parcial do serviço de automatização do Azure.

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

No WMF 5.1, uma configuração de parcial, o serviço/servidor de solicitação pode ter o nome como `<ConfigurationName>.<NodeName>.mof`.
Além disso, se uma máquina é extrair uma única configuração de uma solicitação/serviço de servidor, em seguida, o ficheiro de configuração no repositório de configuração do servidor de solicitação pode ter um nome de ficheiro.
Esta flexibilidade nomenclatura permite-lhe gerir os nós parcialmente pelo serviço de automatização do Azure, onde algum tipo de configuração para o nó for proveniente do Automation DSC do Azure e com uma configuração parcial que gere localmente.

A configuração meta abaixo conjuntos de cópias de segurança um nó para ser gerido ambos localmente, bem como através da automatização do Azure service.

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>Utilizar PsDscRunAsCredential com recursos de DSC compostos

Foi adicionado suporte para utilizar [ *PsDscRunAsCredential* ](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) com DSC [composto](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) recursos.

Agora pode especificar um valor para PsDscRunAsCredential quando utilizar recursos compostos dentro de configurações.
Quando especificado, todos os recursos executam dentro de um recurso composto como um utilizador de RunAs.
Se um recurso composto chama outro recurso composto, todos os respetivos recursos também são executados como utilizador de RunAs.
As credenciais de RunAs sejam propagadas aos qualquer nível da hierarquia de recurso composto.
Se qualquer recurso no interior de um recurso composto Especifica o seu próprio valor para PsDscRunAsCredential, um erro de intercalação resulta durante a compilação de configuração.

Este exemplo mostra a utilização com [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) composto recursos incluídos no módulo PSDesiredStateConfiguration.

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

## <a name="dsc-module-and-configuration-signing-validations"></a>Módulo de DSC e configuração validações de assinatura

No DSC, módulos e configurações são distribuídos a computadores geridos do servidor de solicitação.
Se o servidor de solicitação for comprometido, um atacante pode potencialmente modificar as configurações e os módulos no servidor de solicitação e que o distribuídos a todos os nós geridos, comprometer todos eles.

WMF 5.1, DSC suporta a validação de assinaturas digitais no catálogo e a configuração (. Ficheiros MOF).
Esta funcionalidade impede que nós executar configurações ou ficheiros de módulo que não estejam assinados por um signatário fidedigno ou que tenham sido adulteradas depois de terminada por signatário fidedigno.

### <a name="how-to-sign-configuration-and-module"></a>Como a configuração de sessão e o módulo

***
* Ficheiros de configuração (. MOFs): O cmdlet do PowerShell existente [conjunto AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) é expandido para suportar a assinatura de ficheiros MOF.
* Módulos: Assinatura de módulos é feito ao iniciar o catálogo de módulo correspondente utilizando os seguintes passos:
    1. Criar um ficheiro de catálogo: um ficheiro de catálogo contém uma coleção de hashes criptográficos ou thumbprints.
       Cada thumbprint corresponde a um ficheiro que está incluído no módulo.
       O novo cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), foi adicionada ao permitir que os utilizadores criar um ficheiro de catálogo para o respetivo módulo.
    2. Assinar o ficheiro de catálogo: Utilize [conjunto AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) para assinar o ficheiro de catálogo.
    3. Coloque o ficheiro de catálogo dentro da pasta do módulo.
Por convenção, o ficheiro de catálogo de módulo deve ser colocado sob a pasta do módulo com o mesmo nome que o módulo.

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>Definições de LocalConfigurationManager para ativar a assinatura validações

#### <a name="pull"></a>Solicitação

LocalConfigurationManager de um nó efetua a assinatura de validação de módulos e configurações com base nas respetivas definições atuais.
Por predefinição, a validação da assinatura está desativada.
Validação da assinatura podem ativados adicionando o bloco 'SignatureValidation' para a definição de configuração meta do nó como mostrado abaixo:

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

Definir a configuração meta do acima num nó ativa a validação da assinatura em módulos e configurações transferidas.
O Gestor de configuração Local efetua os seguintes passos para verificar as assinaturas digitais.

1. Verificar a assinatura de um ficheiro de configuração (. MOF) é válido.
   Utiliza o cmdlet do PowerShell [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), que está alargado no 5.1 para suportar a validação da assinatura MOF.
2. Certifique-se de que a autoridade de certificação autorizado o signatário é fidedigna.
3. Transferir as dependências de recursos/módulo da configuração para uma localização temporária.
4. Verificar a assinatura do catálogo incluído no interior do módulo.
    * Localizar um `<moduleName>.cat` de ficheiros e certifique-se a assinatura utilizando o cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).
    * Certifique-se de que a autoridade de certificação que autenticadas de signatário é fidedigna.
    * Certifique-se de que o conteúdo dos módulos tem não foram adulterado utilizando o novo cmdlet [teste FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).
5. Módulo de instalação para $env: ProgramFiles\WindowsPowerShell\Modules\
6. Configuração de processo

> Nota: Validação da assinatura no catálogo do módulo e a configuração só é executada quando a configuração é aplicada no sistema pela primeira vez ou quando o módulo é transferido e instalado.
Execuções de consistência não validam a assinatura de Current.mof ou dependências de módulo.
Se a verificação falhou em qualquer fase, por exemplo, se a configuração é retirado do servidor de solicitação não está assinado, em seguida, termina o processamento da configuração com o erro abaixo e são eliminados todos os ficheiros temporários.

![Exemplo de configuração de saída de erro](../images/PullUnsignedConfigFail.png)

Da mesma forma, a extrair um módulo cujo catálogo não está assinado resultados no seguinte erro:

![Módulo de saída de erro de exemplo](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a>Push

Uma configuração fornecida utilizando a emissão poderão ser adulterada na respetiva origem antes de entregar o nó.
O Gestor de configuração Local efetua os passos de validação de assinatura semelhantes para configuration(s) premido ou publicado.
Abaixo está um exemplo completo de validação da assinatura de push.

- Ative a validação da assinatura no nó.

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

- Crie um ficheiro de configuração de exemplo.

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

- Tente enviar o ficheiro de configuração não assinados para o nó.

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```

![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- Assine o ficheiro de configuração utilizando o certificado de assinatura de código.

![SignMofFile](../images/SignMofFile.png)

- Tente enviar o ficheiro MOF assinado.

![SignMofFile](../images/PushSignedMof.png)
