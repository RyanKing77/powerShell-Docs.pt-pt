---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Configurar um cliente de solicitação através de nomes de configuração
ms.openlocfilehash: d71376d84b9d4b0e74fdccab4b9249b2ca4263cb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a>Configurar um cliente de solicitação através de nomes de configuração

> Aplica-se a: O Windows PowerShell 5.0

> [!IMPORTANT]
> O servidor de solicitação (funcionalidade do Windows *DSC serviço*) é um componente suportado do Windows Server no entanto, são não planos para oferecer novas funcionalidades ou capacidades. É recomendado para começar a transição geridos os clientes [Automation DSC do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação no Windows Server) ou uma das soluções de Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).

Cada nó de destino tem de ser disse para utilizar o modo de extração e dado o URL onde pode contactar o servidor de solicitação para obter as configurações.
Para tal, tem de configurar o Gestor de configuração Local (MMC) com as informações necessárias.
Para configurar o MMC, cria um tipo especial de configuração, decorado com o **DSCLocalConfigurationManager** atributo.
Para obter mais informações sobre como configurar o MMC, consulte [configurar o Gestor de configuração Local](metaConfig.md).

> **Tenha em atenção**: Este tópico aplica-se ao PowerShell 5.0.
Para obter informações sobre como configurar um cliente de solicitação no PowerShell 4.0, consulte [configurar um cliente de extração com o ID de configuração no PowerShell 4.0](pullClientConfigID4.md)

O script seguinte configura o MMC para as configurações de solicitação de um servidor com o nome "CONTOSO-PullSrv":

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

O script, o **ConfigurationRepositoryWeb** bloco define o servidor de solicitação.
O **ServerURL** propriedade especifica o ponto final para o servidor de solicitação.

O **RegistrationKey** propriedade é uma chave partilhada entre todos os nós de cliente para um servidor de solicitação e esse servidor de solicitação.
O mesmo valor é armazenado num ficheiro no servidor de solicitação.

O **ConfigurationNames** propriedade é uma matriz que especifica os nomes das configurações destinadas para o nó de cliente.
No servidor de solicitação, o MOF ficheiro de configuração para este nó de cliente deve ter o nome *ConfigurationNames*. MOF, onde *ConfigurationNames* corresponde ao valor da **ConfigurationNames**  propriedade definida nesta configuração meta.

>**Nota:** se especificar mais do que um valor no **ConfigurationNames**, também tem de especificar **PartialConfiguration** bloqueios na sua configuração.
Para informações sobre configurações parciais, consulte [configurações parciais de configuração de estado pretendido do PowerShell](partialConfigs.md).

Depois deste script é executado, cria uma nova pasta de saída com o nome **PullClientConfigNames** e coloca não existe um ficheiro MOF de configuração meta.
Neste caso, o ficheiro MOF de configuração meta será designado `localhost.meta.mof`.

Para aplicar a configuração, chame o **conjunto DscLocalConfigurationManager** cmdlet, com o **caminho** definido para a localização do ficheiro MOF configuração meta.

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> **Tenha em atenção**: as chaves de registo só funcionam com servidores de solicitação da web.
Ainda tem de utilizar **ConfigurationID** com um servidor de solicitação do SMB.
Para obter informações sobre como configurar um servidor de solicitação utilizando **ConfigurationID**, consulte [configurar um cliente de extração com o ID de configuração](PullClientConfigNames.md)

## <a name="resource-and-report-servers"></a>Servidores de recursos e o relatório

Se especificar apenas um **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** bloquear na configuração da MMC (do exemplo anterior), o cliente de solicitação irá solicitar recursos a partir de servidor especificado, mas não enviarão relatórios ao mesmo.
Pode utilizar um servidor de solicitação único para configurações, recursos e relatórios, mas tem de criar um **ReportRepositoryWeb** bloco para configurar o Reporting Services.
O exemplo seguinte mostra uma configuração meta do que configura um cliente para enviar relatórios de dados, para um servidor de solicitação único e recursos e configurações de extração.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigNames
```

Também pode especificar os servidores de extração diferente para recursos e relatórios.
Para especificar um servidor de recurso, a utilização de uma um **ResourceRepositoryWeb** (para um servidor de solicitação web) ou um **ResourceRepositoryShare** blocos (por um servidor de solicitação SMB).
Para especificar um servidor de relatórios, pode utilizar um **ReportRepositoryWeb** bloco.
Um servidor de relatórios não pode ser um servidor do SMB.
A configuração meta do seguinte configura uma solicitação de cliente para obter as respetivas configurações de **CONTOSO PullSrv** e respetivos recursos da **CONTOSO ResourceSrv**e para enviar relatórios de estado para  **CONTOSO ReportSrv**:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>Consulte Também

* [Configurar um cliente de extração com o ID de configuração](PullClientConfigNames.md)
* [Configurar um servidor de solicitação do DSC web](pullServer.md)