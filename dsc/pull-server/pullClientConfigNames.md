---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Configurar um cliente de solicitação através de nomes de configuração no PowerShell 5.0 e posterior
ms.openlocfilehash: d591e2a757130ccecaf4eaf9f363f607fca82b93
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058198"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>Configurar um cliente de solicitação através de nomes de configuração no PowerShell 5.0 e posterior

> Aplica-se a: Windows PowerShell 5.0

> [!IMPORTANT]
> O servidor de solicitação (recurso do Windows *DSC-serviço*) é um componente suportado do Windows Server no entanto, não existem planos para oferecer novas funcionalidades ou capacidades. É recomendado para começar a fazer a transição geridos os clientes [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação de mensagens em fila no Windows Server) ou uma das soluções da Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).

Antes de configurar um cliente de solicitação, deve configurar um servidor de solicitação. Embora esta ordem não é necessária, ele ajuda na resolução de problemas e ajuda a garantir que o registo foi concluída com êxito. Para configurar um servidor de solicitação, pode usar os seguintes guias:

- [Configurar um servidor de solicitação de SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de solicitação de HTTP de DSC](pullServer.md)

Cada nó de destino pode ser configurado para transferir configurações, recursos e até mesmo comunicou o seu estado. As secções abaixo mostram-lhe como configurar um cliente de solicitação com uma partilha SMB ou o servidor de solicitação de DSC de HTTP. Quando atualiza LCM o nó, será contactado por para a localização configurada para transferir quaisquer configurações atribuídas. Se não existirem quaisquer recursos necessários no nó, será transferida-los automaticamente na localização de configurado. Se o nó está configurado com um [Report Server](reportServer.md), em seguida, esse irá comunicar o estado da operação.

> [!NOTE]
> Este tópico aplica-se para PowerShell 5.0.
> Para obter informações sobre como configurar um cliente de solicitação no PowerShell 4.0, consulte [configurar um cliente de solicitação com o ID de configuração no PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Configurar o cliente de solicitação LCM

Executar qualquer um dos exemplos abaixo cria uma nova pasta de saída com o nome **PullClientConfigName** e coloca um ficheiro MOF de metaconfiguration lá. Neste caso, o ficheiro MOF de metaconfiguration será denominado `localhost.meta.mof`.

Para aplicar a configuração, chame o **Set-dsclocalconfigurationmanager para** cmdlet, com o **caminho** definido para a localização do ficheiro MOF metaconfiguration. Por exemplo:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>Nome da configuração

Os exemplos abaixo conjuntos a **ConfigurationName** propriedade do LCM para o nome de uma configuração compilada anteriormente, criada para este fim. O **ConfigurationName** é o que o LCM utiliza para encontrar a configuração adequada no servidor de solicitação. O ficheiro MOF de configuração no servidor de solicitação deve ter o nome `<ConfigurationName>.mof`, neste caso, "ClientConfig.mof". Para obter mais informações, consulte [configurações de publicação de mensagens em fila para um servidor de solicitação (v4/v5)](publishConfigs.md).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurar um cliente de solicitação para transferir configurações

Cada cliente tem de ser configurada no **Pull** modo e tendo em conta o url do servidor pull onde está armazenada a respetiva configuração. Para tal, tem de configurar o Gestor de configuração Local (LCM) com as informações necessárias. Para configurar o LCM, cria um tipo especial de configuração, decorada com o **dsclocalconfigurationmanager para** atributo. Para obter mais informações sobre como configurar o LCM, consulte [configurar o Gestor de configuração Local](../managing-nodes/metaConfig.md).

O script a seguir configura o LCM para configurações de solicitação de um servidor com o nome "CONTOSO-PullSrv".

- No script, o **ConfigurationRepositoryWeb** bloco define o servidor de solicitação. O **ServerURL** propriedade especifica o ponto final para o servidor de solicitação.

- O **RegistrationKey** propriedade é uma chave partilhada entre todos os nós de cliente para um servidor de solicitação e esse servidor de solicitação. O mesmo valor é armazenado num arquivo no servidor de solicitação.
  > [!NOTE]
  > As chaves de registo só funcionam com o **web** extrair servidores. Ainda tem de utilizar **ConfigurationID** com um **SMB** servidor de solicitação.
  > Para obter informações sobre como configurar um servidor de solicitação usando **ConfigurationID**, consulte [como configurar um cliente de solicitação através do ID de configuração](pullClientConfigId.md)

- O **ConfigurationNames** propriedade é uma matriz que especifica os nomes das configurações se destina o nó de cliente.
  >**Nota:** Se especificar mais do que um valor no **ConfigurationNames**, também tem de especificar **PartialConfiguration** bloqueia na sua configuração.
  >Para obter informações sobre configurações parciais, consulte [configurações parciais de PowerShell Desired State Configuration](partialConfigs.md).

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

## <a name="set-up-a-pull-client-to-download-resources"></a>Configurar um cliente extrair para recursos de download

Se especificar apenas uma **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** bloco na sua configuração de LCM (como no exemplo anterior), irá fazer com que o cliente de solicitação recursos a partir do mesmo localização onde estão armazenados os ficheiros de ". MOF". Também pode especificar diferentes localizações onde os clientes podem transferir recursos. Para especificar um servidor de recurso, a utilização de uma um **ResourceRepositoryWeb** (para um servidor de solicitação da web) ou uma **ResourceRepositoryShare** bloco (para um servidor de solicitação SMB).

O exemplo seguinte mostra um metaconfiguration que configura um cliente para transferir configurações a partir de um servidor de solicitação e recursos a partir de uma partilha SMB.

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

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a>Configurar um cliente de solicitação para comunicar o Estado

Pode utilizar um servidor de solicitação única para configurações, recursos e geração de relatórios. Geração de relatórios não está configurada para os clientes por predefinição. Para configurar um cliente para comunicar o estado, tem de criar uma **ReportRepositoryWeb** bloco. O exemplo seguinte mostra um metaconfiguration que configura um cliente pull configurações e recursos e enviar relatórios de dados, para um servidor de solicitação única.

> [!NOTE]
> Um servidor de relatórios não pode ser uma partilha SMB.

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
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>Veja Também

* [Como configurar um cliente de solicitação com o ID de configuração](PullClientConfigNames.md)
* [Como configurar um servidor de solicitação da web de DSC](pullServer.md)
