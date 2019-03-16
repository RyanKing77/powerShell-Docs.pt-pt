---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Configurar um cliente de solicitação através de IDs de configuração no PowerShell 5.0 e posterior
ms.openlocfilehash: 14db98d240bc87aca3ee985db08c14b7c65d8bb8
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055721"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>Configurar um cliente de solicitação através de IDs de configuração no PowerShell 5.0 e posterior

> Aplica-se a: Windows PowerShell 5.0

> [!IMPORTANT]
> O servidor de solicitação (recurso do Windows *DSC-serviço*) é um componente suportado do Windows Server no entanto, não existem planos para oferecer novas funcionalidades ou capacidades. É recomendado para começar a fazer a transição geridos os clientes [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação de mensagens em fila no Windows Server) ou uma das soluções da Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).

Antes de configurar um cliente de solicitação, deve configurar um servidor de solicitação. Embora esta ordem não é necessária, ele ajuda na resolução de problemas e ajuda a garantir que o registo foi concluída com êxito. Para configurar um servidor de solicitação, pode usar os seguintes guias:

- [Configurar um servidor de solicitação de SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de solicitação de HTTP de DSC](pullServer.md)

Cada nó de destino pode ser configurado para transferir configurações, recursos e até mesmo comunicou o seu estado. As secções abaixo mostram-lhe como configurar um cliente de solicitação com uma partilha SMB ou o servidor de solicitação de DSC de HTTP. Quando atualiza LCM o nó, será contactado por para a localização configurada para transferir quaisquer configurações atribuídas. Se não existirem quaisquer recursos necessários no nó, será transferida-los automaticamente na localização de configurado. Se o nó está configurado com um [Report Server](reportServer.md), em seguida, esse irá comunicar o estado da operação.

> [!NOTE]
> Este tópico aplica-se para PowerShell 5.0. Para obter informações sobre como configurar um cliente de solicitação no PowerShell 4.0, consulte [como configurar um cliente de solicitação com o ID de configuração no PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Configurar o cliente de solicitação LCM

Executar qualquer um dos exemplos abaixo cria uma nova pasta de saída com o nome **PullClientConfigID** e coloca um ficheiro MOF de metaconfiguration lá. Neste caso, o ficheiro MOF de metaconfiguration será denominado `localhost.meta.mof`.

Para aplicar a configuração, chame o **Set-dsclocalconfigurationmanager para** cmdlet, com o **caminho** definido para a localização do ficheiro MOF metaconfiguration. Por exemplo:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>ID de configuração

Os exemplos abaixo conjuntos a **ConfigurationID** propriedade do MMC para um **Guid** que haviam sido criados anteriormente para esta finalidade. O **ConfigurationID** é o que o LCM utiliza para encontrar a configuração adequada no servidor de solicitação. O ficheiro MOF de configuração no servidor de solicitação deve ser nomeado `ConfigurationID.mof`, onde *ConfigurationID* é o valor da **ConfigurationID** propriedade do LCM o nó de destino. Para obter mais informações, consulte [configurações de publicação de mensagens em fila para um servidor de solicitação (v4/v5)](publishConfigs.md).

Pode criar um aleatório **Guid** usando o exemplo abaixo, ou utilizando o [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.

```powershell
[System.Guid]::NewGuid()
```

Para obter mais informações sobre como utilizar **Guids** no seu ambiente, consulte [planear Guids](/powershell/dsc/secureserver#guids).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurar um cliente de solicitação para transferir configurações

Cada cliente tem de ser configurada no **Pull** modo e tendo em conta o url do servidor pull onde está armazenada a respetiva configuração. Para tal, tem de configurar o Gestor de configuração Local (LCM) com as informações necessárias. Para configurar o LCM, cria um tipo especial de configuração, decorada com o **dsclocalconfigurationmanager para** atributo. Para obter mais informações sobre como configurar o LCM, consulte [configurar o Gestor de configuração Local](../managing-nodes/metaConfig.md).

### <a name="http-dsc-pull-server"></a>Servidor de solicitação de DSC de HTTP

O script a seguir configura o LCM para configurações de solicitação de um servidor com o nome "CONTOSO-PullSrv".

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

No script, o **ConfigurationRepositoryWeb** bloco define o servidor de solicitação. O **ServerUrl** Especifica o url de solicitação do DSC

### <a name="smb-share"></a>Partilha SMB

O script a seguir configura o LCM para configurações de solicitação da partilha de SMB `\\SMBPullServer\Pull`.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

No script, o **ConfigurationRepositoryShare** bloco define o servidor de solicitação, que neste caso, é apenas uma partilha SMB.

## <a name="set-up-a-pull-client-to-download-resources"></a>Configurar um cliente extrair para recursos de download

Se especificar apenas o **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** bloco na sua configuração de LCM (como nos exemplos anteriores), irá fazer com que o cliente de solicitação recursos a partir da mesma localização obtém suas configurações. Também é possível especificar localizações separadas para recursos. Para especificar uma localização de recursos como um servidor separado, utilize o **ResourceRepositoryWeb** bloco. Para especificar uma localização de recursos como uma partilha de SMB, utilize o **ResourceRepositoryShare** bloco.

> [!NOTE]
> Pode combinar **ConfigurationRepositoryWeb** com **ResourceRepositoryShare** ou **ConfigurationRepositoryShare** com **ResourceRepositoryWeb** . Exemplos disso não são apresentados abaixo.

### <a name="http-dsc-pull-server"></a>Servidor de solicitação de DSC de HTTP

O metaconfiguration seguinte configura um cliente de solicitação para obter configurações a partir **CONTOSO-PullSrv** e os respetivos recursos da **CONTOSO-ResourceSrv**.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>Partilha SMB

O exemplo seguinte mostra um metaconfiguration que configura um cliente para as configurações de solicitação da partilha de SMB `\\SMBPullServer\Configurations`e os recursos da partilha SMB `\\SMBPullServer\Resources`.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a>Transferir automaticamente os recursos no modo de Push

A partir do PowerShell 5.0, seus clientes de solicitação podem transferir módulos da partilha de SMB, mesmo quando estão configurados para **Push** modo. Isso é especialmente útil em cenários onde não pretende configurar um servidor de solicitação. O **ResourceRepositoryShare** block pode ser usado sem especificar um **ConfigurationRepositoryShare**. O exemplo seguinte mostra um metaconfiguration que configura um cliente para receber recursos de uma partilha SMB `\\SMBPullServer\Resources`. Quando o nó está **PUSHED** uma configuração, ele irá transferir automaticamente todos os recursos necessários, da partilha especificada.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a>Configurar um cliente de solicitação para comunicar o Estado

Por predefinição, nós não enviarão relatórios para um servidor de solicitação configurado. Pode utilizar um servidor de solicitação única para configurações, recursos e geração de relatórios, mas tem de criar uma **ReportRepositoryWeb** bloco para configurar os relatórios.

### <a name="http-dsc-pull-server"></a>Servidor de solicitação de DSC de HTTP

O exemplo seguinte mostra um metaconfiguration que configura um cliente pull configurações e recursos e enviar relatórios de dados, para um servidor de solicitação única.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

Para especificar um servidor de relatórios, utilize um **ReportRepositoryWeb** bloco. Um servidor de relatórios não pode ser um servidor do SMB.
O metaconfiguration seguinte configura um cliente de solicitação para obter configurações a partir de **CONTOSO-PullSrv** e os respetivos recursos da **CONTOSO-ResourceSrv**e para enviar relatórios de estado para  **CONTOSO-ReportSrv**:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>Partilha SMB

Um servidor de relatórios não pode ser uma partilha SMB.

## <a name="next-steps"></a>Próximos Passos

Depois de configurar o cliente de solicitação, pode utilizar os seguintes guias para realizar os passos seguintes:

- [Publicar as configurações para um servidor de solicitação (v4/v5)](publishConfigs.md)
- [Pacote e o carregamento de recursos para um servidor de solicitação (v4)](package-upload-resources.md)

## <a name="see-also"></a>Veja Também

* [Como configurar um cliente de solicitação com nomes de configuração](pullClientConfigNames.md)
