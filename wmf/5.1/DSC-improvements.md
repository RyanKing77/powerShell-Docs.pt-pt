---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Melhorias de DSC no WMF 5.1
ms.openlocfilehash: 92f82d62550e105a187fd7c0c58b49367c646a7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085589"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>Melhorias na Desired State Configuration (DSC) no WMF 5.1

## <a name="dsc-class-resource-improvements"></a>Aprimoramentos de recursos de classe de DSC

No WMF 5.1, podemos corrigir os seguintes problemas conhecidos:

- Get-dscconfiguration para pode devolver valores vazios (nulos) ou erros, se um tipo de tabela de hash/complexo é devolvido pela função de GET () de um recurso de DSC baseados na classe.
- Get-dscconfiguration para devolve o erro se a credencial de RunAs é utilizada na configuração de DSC.
- Recursos com base na classe não podem ser utilizado numa configuração composta.
- Start-dscconfiguration para bloqueia se recursos com base na classe tem uma propriedade de seu próprio tipo.
- Não não possível utilizar recursos com base na classe como um recurso exclusivo.

## <a name="dsc-resource-debugging-improvements"></a>Melhorias na depuração de recursos de DSC

No WMF 5.0, o depurador do PowerShell não parou o método de recursos com base na classe (Get/Set/teste) diretamente.
No WMF 5.1, o depurador será interrompido o método de recursos com base na classe da mesma forma que nos métodos de recursos baseados em MOF.

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>Cliente de solicitação de DSC oferece suporte a TLS 1.1 e TLS 1.2

Anteriormente, o cliente de solicitação de DSC apenas suportado SSL3.0 e TLS 1.0 através de ligações de HTTPS.
Quando a obrigatoriedade de usar protocolos mais seguros, o cliente de solicitação seria deixe de funcionar.
No WMF 5.1, o cliente de solicitação de DSC já não suporta SSL 3.0 e adiciona suporte aos protocolos mais seguros de TLS 1.1 e TLS 1.2.

## <a name="improved-pull-server-registration"></a>Registo do servidor pull melhorada

Nas versões anteriores do WMF, pedidos de registos/reporting simultâneas de mensagens em fila para um servidor de solicitação de DSC ao utilizar a base de dados ESENT poderia levar a LCM falhar ao registar e/ou relatório.
Nesses casos, os registos de eventos no servidor de solicitação tem o erro "Nome da instância já em utilização."
Isto foi devido a um padrão incorreto a ser utilizado para aceder a base de dados ESENT num cenário de vários threads.
No WMF 5.1, este problema foi corrigido.
Registos em simultâneo ou geração de relatórios (envolvendo a base de dados ESENT) funciona bem no WMF 5.1.
Este problema é aplicável apenas para a base de dados ESENT e não se aplica à base de dados OLEDB.

## <a name="enable-circular-log-on-esent-database-instance"></a>Ativar registo Circular na instância de base de dados ESENT

Na versão de eariler do DSC PullServer, os ficheiros de registo de base de dados ESENT foram preenchendo o espaço de disco do becouse pullserver que a instância de base de dados estava a ser criada sem o registo circular. Nesta versão, tem a opção para controlar o comportamento de registo circular de instância utilizando o pullserver Web. config. Por predefinição CircularLogging está definido como TRUE.

```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="pull-partial-configuration-naming-convention"></a>Extrair a Convenção de nomenclatura de configuração parcial

Na versão anterior, a Convenção de nomenclatura para uma configuração parcial foi que o nome do ficheiro MOF no servidor/serviço pull deve corresponder o nome da configuração parcial especificado nas definições do Gestor de configuração local que por sua vez tem de corresponder a nome da configuração incorporada no ficheiro MOF.

Ver os instantâneos abaixo:

- Definições de configuração local que define uma configuração parcial que um nó está autorizado a receber.

![Metaconfiguration de exemplo](../images/MetaConfigPartialOne.png)

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

- "ConfigurationName" incorporado no ficheiro MOF gerado.

![Ficheiro mof gerado de exemplo](../images/PartialGeneratedMof.png)

- Nome de ficheiro no repositório de configuração de solicitação

![Nome do ficheiro no repositório de configuração](../images/PartialInConfigRepository.png)

Nome do serviço de automatização do Azure gerado ficheiros MOF como `<ConfigurationName>.<NodeName>.mof`.
Portanto, a configuração abaixo é compilado para PartialOne.localhost.mof.

Isso tornou impossível para solicitação um da sua configuração parcial do serviço de automatização do Azure.

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

No WMF 5.1, uma configuração parcial no servidor/serviço de solicitação pode ser nomeada como `<ConfigurationName>.<NodeName>.mof`.
Além disso, se uma máquina é extrair uma única configuração de uma solicitação, em seguida, o ficheiro de configuração sobre o repositório de configuração do servidor de solicitação de serviço/servidor pode ter qualquer nome de ficheiro.
Essa flexibilidade nomenclatura permite-lhe gerir os nós parcialmente pelo serviço de automatização do Azure, onde alguma configuração para o seu nó estará disponível no DSC de automatização do Azure e com uma configuração parcial por si localmente.

Metaconfiguration abaixo configura um nó a ser geridas tanto localmente, bem como pela automatização do Azure de serviço.

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>Utilizar PsDscRunAsCredential com recursos compostos de DSC

Foi adicionado suporte para usar [ *PsDscRunAsCredential* ](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) com DSC [compostos](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) recursos.

Agora pode especificar um valor para PsDscRunAsCredential ao utilizar recursos compostos dentro de configurações.
Quando especificado, todos os recursos é executado dentro de um recurso composto como um utilizador de RunAs.
Se um recurso composto chama outro recurso composto, todos os respetivos recursos também são executados como usuário de RunAs.
As credenciais de RunAs são propagadas para qualquer nível na hierarquia de recursos compostos.
Se todos os recursos dentro de um recurso composto Especifica o seu próprio valor para PsDscRunAsCredential, um erro de intercalação resulta durante a compilação de configuração.

Este exemplo mostra a utilização com [WindowsFeatureSet](https://msdn.microsoft.com/powershell/wmf/dsc_newresources) compostos recursos incluídos no módulo PSDesiredStateConfiguration.

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

## <a name="dsc-module-and-configuration-signing-validations"></a>Módulo de DSC e a configuração validações de assinatura

No DSC, configurações e os módulos são distribuídos por computadores gerenciados do servidor de solicitação.
Se o servidor de solicitação for comprometido, um invasor pode potencialmente modificar as configurações e os módulos no servidor de solicitação e fazer com que ele distribuídas para todos os nós geridos, comprometer todos eles.

No WMF 5.1, DSC oferece suporte a validar as assinaturas digitais em catálogo e a configuração (. Ficheiros MOF).
Esse recurso evita que nós de execução configurações ou arquivos de módulo que não estejam assinado por um signatário confiável ou que tenham sido adulterado depois que eles estejam assinados por signatário fidedigno.

### <a name="how-to-sign-configuration-and-module"></a>A configuração de início de sessão e módulo

***
* Ficheiros de configuração (. MOFs): O cmdlet do PowerShell existente [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) é expandido para suportar a assinatura de ficheiros MOF.
* Módulos: Assinatura de módulos é feito ao iniciar o catálogo de módulo correspondente através dos seguintes passos:
    1. Crie um ficheiro de catálogo: Um arquivo de catálogo contém uma coleção de hashes criptográficos ou thumbprints.
       Cada thumbprint corresponde a um ficheiro que está incluído no módulo.
       O novo cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), foi adicionada para permitir que os utilizadores criar um arquivo de catálogo para o módulo.
    2. Assinar o ficheiro de catálogo: Uso [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) para assinar o ficheiro de catálogo.
    3. Coloque o arquivo de catálogo dentro da pasta do módulo.
Por convenção, o arquivo de catálogo de módulo deve ser colocado sob a pasta de módulo com o mesmo nome que o módulo.

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>Definições de LocalConfigurationManager para ativar a assinatura de validações

#### <a name="pull"></a>Extração

LocalConfigurationManager de um nó efetua a validação de assinatura de módulos e configurações com base nas definições de atuais.
Por predefinição, a validação da assinatura está desativada.
Validação da assinatura pode habilitado adicionando-o bloco de 'SignatureValidation' para a definição de meta-configuração do nó conforme mostrado abaixo:

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

Definir o metaconfiguration acima num nó permite que a validação da assinatura nas configurações transferidas e módulos.
O Gestor de configuração Local executa os seguintes passos para verificar as assinaturas digitais.

1. Verificar a assinatura num arquivo de configuração (. MOF) é válido.
   Ele usa o cmdlet do PowerShell [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), que é estendido de 5.1 para oferecer suporte a validação de assinatura do MOF.
2. Certifique-se de que a autoridade de certificação que autorizado o signatário é fidedigna.
3. Baixe as dependências do módulo/recurso da configuração num local temporário.
4. Verificar a assinatura do catálogo incluída dentro do módulo.
    * Encontrar um `<moduleName>.cat` de ficheiros e certifique-se a sua assinatura usando o cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).
    * Certifique-se de que a autoridade de certificação que autenticou o signatário é fidedigna.
    * Certifique-se de que o conteúdo dos módulos não tem sido adulterado, usando o novo cmdlet [teste FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).
5. Install-Module para $env: ProgramFiles\WindowsPowerShell\Modules\
6. Configuração do processo

> Nota: Validação da assinatura no catálogo de módulo e a configuração só é executada quando a configuração é aplicada ao sistema pela primeira vez ou quando o módulo é transferido e instalado.
Execuções de consistência não validam a assinatura de Current.mof ou as respetivas dependências do módulo.
Se a verificação falhou em qualquer fase, por exemplo, se a configuração obtido a partir do servidor de solicitação não está assinado, em seguida, termina de processamento da configuração com o erro mostrado abaixo e são eliminados todos os ficheiros temporários.

![Exemplo de configuração de saída de erro](../images/PullUnsignedConfigFail.png)

Da mesma forma, a extração de um módulo cujo catálogo não está assinado resultados no seguinte erro:

![Módulo de saída de erro de exemplo](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a>Push

Uma configuração fornecida utilizando a instalação push poderá ser adulterada na origem antes de ela entregue para o nó.
O Gestor de configuração Local executa os passos de validação de assinatura semelhante para configuração ou configurações migradas enviada por push ou publicadas.
Segue-se um exemplo completo de validação de assinatura para push.

- Ative a validação de assinatura no nó.

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

- Assinar o ficheiro de configuração com o certificado de assinatura de código.

![SignMofFile](../images/SignMofFile.png)

- Tente enviar o ficheiro assinado da MOF.

![SignMofFile](../images/PushSignedMof.png)
