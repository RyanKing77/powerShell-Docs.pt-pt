---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Configurar um cliente de solicitação com IDs de configuração no PowerShell 4.0
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405277"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>Configurar um cliente de solicitação com IDs de configuração no PowerShell 4.0

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> O servidor de solicitação (recurso do Windows *DSC-serviço*) é um componente suportado do Windows Server no entanto, não existem planos para oferecer novas funcionalidades ou capacidades. É recomendado para começar a fazer a transição geridos os clientes [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação de mensagens em fila no Windows Server) ou uma das soluções da Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).

Antes de configurar um cliente de solicitação, deve configurar um servidor de solicitação. Embora esta ordem não é necessária, ele ajuda na resolução de problemas e ajuda a garantir que o registo foi concluída com êxito. Para configurar um servidor de solicitação, pode usar os seguintes guias:

- [Configurar um servidor de solicitação de SMB de DSC](pullServerSmb.md)
- [Configurar um servidor de solicitação de HTTP de DSC](pullServer.md)

Cada nó de destino pode ser configurado para transferir configurações, recursos e até mesmo comunicou o seu estado. As secções abaixo mostram-lhe como configurar um cliente de solicitação com uma partilha SMB ou o servidor de solicitação de DSC de HTTP. Quando atualiza LCM o nó, será contactado por para a localização configurada para transferir quaisquer configurações atribuídas. Se não existirem quaisquer recursos necessários no nó, será transferida-los automaticamente na localização de configurado. Se o nó está configurado com um [Report Server](reportServer.md), em seguida, esse irá comunicar o estado da operação.

## <a name="configure-the-pull-client-lcm"></a>Configurar o cliente de solicitação LCM

Executar qualquer um dos exemplos abaixo cria uma nova pasta de saída com o nome **PullClientConfigID** e coloca um ficheiro MOF de metaconfiguration lá. Neste caso, o ficheiro MOF de metaconfiguration será denominado `localhost.meta.mof`.

Para aplicar a configuração, chame o **Set-dsclocalconfigurationmanager para** cmdlet, com o **caminho** definido para a localização do ficheiro MOF metaconfiguration. Por exemplo:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>ID de configuração

Os exemplos abaixo conjunto a **ConfigurationID** propriedade do MMC para um **Guid** que haviam sido criados anteriormente para esta finalidade. O **ConfigurationID** é o que o LCM utiliza para encontrar a configuração adequada no servidor de solicitação. O ficheiro MOF de configuração no servidor de solicitação deve ser nomeado `ConfigurationID.mof`, onde *ConfigurationID* é o valor da **ConfigurationID** propriedade do LCM o nó de destino. Para obter mais informações, consulte [configurações de publicação de mensagens em fila para um servidor de solicitação (v4/v5)](publishConfigs.md).

Pode criar um aleatório **Guid** usando o exemplo abaixo.

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>Configurar um cliente de solicitação para transferir configurações

Cada cliente tem de ser configurada no **Pull** modo e tendo em conta o url do servidor pull onde está armazenada a respetiva configuração. Para tal, tem de configurar o Gestor de configuração Local (LCM) com as informações necessárias. Para configurar o LCM, cria um tipo especial de configuração, com um **LocalConfigurationManager** bloco. Para obter mais informações sobre como configurar o LCM, consulte [configurar o Gestor de configuração Local](../managing-nodes/metaConfig4.md).

## <a name="http-dsc-pull-server"></a>Servidor de solicitação de DSC de HTTP

Se o servidor de solicitação é configurado como um serviço web, defina o **DownloadManagerName** ao **WebDownloadManager**. O **WebDownloadManager** exige a especificação de um **ServerUrl** para o **DownloadManagerCustomData** chave. Também pode especificar um valor para **AllowUnsecureConnection**, como no exemplo abaixo. O script a seguir configura o LCM para configurações de solicitação de um servidor com o nome "PullServer".

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>Partilha SMB

Se o servidor de solicitação é configurado como uma partilha de ficheiros SMB, em vez de um serviço da web, é definir os **DownloadManagerName** ao **DscFileDownloadManager** em vez do **WebDownLoadManager**. O **DscFileDownloadManager** exige a especificação de um **SourcePath** propriedade no **DownloadManagerCustomData**. O script seguinte configura o LCM para solicitar configurações a partir de uma partilha SMB com o nome "SmbDscShare" num servidor com o nome "CONTOSO-SERVER".

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a>Próximos Passos

Depois de configurar o cliente de solicitação, pode utilizar os seguintes guias para realizar os passos seguintes:

- [Publicar as configurações para um servidor de solicitação (v4/v5)](publishConfigs.md)
- [Pacote e o carregamento de recursos para um servidor de solicitação (v4)](package-upload-resources.md)

## <a name="see-also"></a>Consulte Também

- [Configurar um servidor de solicitação da web de DSC](pullServer.md)
- [Configurar um servidor de solicitação SMB de DSC](pullServerSMB.md)
