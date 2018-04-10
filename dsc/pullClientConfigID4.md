---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Configurar um cliente de extração com o ID de configuração no PowerShell 4.0
ms.openlocfilehash: 7074d842b7b99ef3fb6498b6dbc1e561b14caf16
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a>Configurar um cliente de extração com o ID de configuração no PowerShell 4.0

>Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

Cada nó de destino tem de ser disse para utilizar o modo de extração e dado o URL onde pode contactar o servidor de solicitação para obter as configurações. Para tal, tem de configurar o Gestor de configuração Local (MMC) com as informações necessárias. Para configurar o MMC, cria um tipo especial de configuração conhecido como uma "configuração meta do". Para obter mais informações sobre como configurar o MMC, consulte [Windows PowerShell 4.0 pretendido estado de configuração Local do Configuration Manager](metaConfig4.md)

O script seguinte configura o MMC para as configurações de solicitação de um servidor com o nome "PullServer":

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

O script, **DownloadManagerCustomData** transmite o URL do servidor de solicitação e (para este exemplo) permite uma ligação segura.

Depois deste script é executado, cria uma nova pasta de saída designada **SimpleMetaConfigurationForPull** e coloca não existe um ficheiro MOF de configuração meta.

Para aplicar a configuração, utilize **conjunto DscLocalConfigurationManager** com parâmetros **ComputerName** (utilize "localhost") e **caminho** (o caminho para a localização do destino de ficheiro de localhost.meta.mof deste nó). Por exemplo:
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a>ID de configuração
Os conjuntos de script a **ConfigurationID** propriedade da MMC como um GUID que tinha de ser criado previamente para esta finalidade (pode criar um GUID, utilizando o **novo Guid** cmdlet). O **ConfigurationID** é o que utiliza o MMC para encontrar a configuração adequada no servidor de solicitação. O ficheiro MOF de configuração no servidor de solicitação deve ter o nome `ConfigurationID.mof`, onde *ConfigurationID* valor o **ConfigurationID** propriedade do MMC do nó de destino.

## <a name="pulling-from-an-smb-server"></a>Extrair a partir de um servidor do SMB

Se o servidor de solicitação está configurado como uma partilha de ficheiros SMB, em vez de um serviço web, especifique o **DscFileDownloadManager** em vez do **WebDownLoadManager**.
O **DscFileDownloadManager** demora um **SourcePath** propriedade em vez de **ServerUrl**. O script seguinte configura o MMC para solicitar as configurações de partilha SMB com o nome "SmbDscShare" num servidor com o nome "CONTOSO-SERVER":

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a>Consulte Também

- [Configurar um servidor de solicitação do DSC web](pullServer.md)
- [Configurar um servidor de solicitação SMB de DSC](pullServerSMB.md)