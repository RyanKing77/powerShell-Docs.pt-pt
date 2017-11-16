---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Configurar um cliente de extração com o ID de configuração"
ms.openlocfilehash: bb14bff95c626b65e2d0d0072c39e4c571cea4b0
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/27/2017
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a>Configurar um cliente de extração com o ID de configuração

> Aplica-se a: O Windows PowerShell 5.0

Cada nó de destino tem de ser disse para utilizar o modo de extração e dado o URL onde pode contactar o servidor de solicitação para obter as configurações. Para tal, tem de configurar o Gestor de configuração Local (MMC) com as informações necessárias. Para configurar o MMC, cria um tipo especial de configuração, decorado com o **DSCLocalConfigurationManager** atributo. Para obter mais informações sobre como configurar o MMC, consulte [configurar o Gestor de configuração Local](metaConfig.md).

> **Tenha em atenção**: Este tópico aplica-se ao PowerShell 5.0. Para obter informações sobre como configurar um cliente de solicitação no PowerShell 4.0, consulte [configurar um cliente de extração com o ID de configuração no PowerShell 4.0](pullClientConfigID4.md)

O script seguinte configura o MMC para as configurações de solicitação de um servidor com o nome "CONTOSO-PullSrv".

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

O script, o **ConfigurationRepositoryWeb** bloco define o servidor de solicitação. O **ServerURL**

Depois deste script é executado, cria uma nova pasta de saída com o nome **PullClientConfigID** e coloca não existe um ficheiro MOF de configuração meta. Neste caso, o ficheiro MOF de configuração meta será designado `localhost.meta.mof`.

Para aplicar a configuração, chame o **conjunto DscLocalConfigurationManager** cmdlet, com o **caminho** definido para a localização do ficheiro MOF configuração meta. Por exemplo: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`

## <a name="configuration-id"></a>ID de configuração

Os conjuntos de script a **ConfigurationID** propriedade da MMC para um GUID que tinha de ser criado previamente para esta finalidade (pode criar um GUID, utilizando o **novo Guid** cmdlet). O **ConfigurationID** é o que utiliza o MMC para encontrar a configuração adequada no servidor de solicitação. O ficheiro MOF de configuração no servidor de solicitação deve ter o nome _ConfigurationID_. MOF, onde _ConfigurationID_ valor o **ConfigurationID** propriedade de destino MMC do nó.

## <a name="smb-pull-server"></a>Servidor de solicitação SMB

Para configurar um cliente para as configurações de solicitação de um servidor do SMB, utilize um **ConfigurationRepositoryShare** bloco. Num **ConfigurationRepositoryShare** bloco, especifique o caminho para o servidor, definindo o **SourcePath** propriedade. A configuração meta do seguinte configura o nó de destino para solicitar a partir de um servidor de solicitação SMB denominado **SMBPullServer**.

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
            SourcePath = '\\SMBPullServer\PullSource'
            
        }     
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a>Servidores de recursos e o relatório

Se especificar apenas um **ConfigurationRepositoryWeb** ou **ConfigurationRepositoryShare** bloquear na configuração da MMC (do exemplo anterior), o cliente de solicitação irá solicitar recursos a partir de servidor especificado, mas não enviarão relatórios ao mesmo. Pode utilizar um servidor de solicitação único para configurações, recursos e relatórios, mas tem de criar um **ReportRepositoryWeb** bloco para configurar o Reporting Services. 

O exemplo seguinte mostra uma configuração meta do que configura um cliente para enviar relatórios de dados, para um servidor de solicitação único e recursos e configurações de extração.

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

Também pode especificar os servidores de extração diferente para recursos e relatórios. Para especificar um servidor de recurso, a utilização de uma um **ResourceRepositoryWeb** (para um servidor de solicitação web) ou um **ResourceRepositoryShare** blocos (por um servidor de solicitação SMB).
Para especificar um servidor de relatórios, pode utilizar um **ReportRepositoryWeb** bloco. Um servidor de relatórios não pode ser um servidor do SMB.
A configuração meta do seguinte configura uma solicitação de cliente para obter as respetivas configurações de **CONTOSO PullSrv** e respetivos recursos da **CONTOSO ResourceSrv**e para enviar relatórios de estado para  **CONTOSO ReportSrv**:

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

## <a name="see-also"></a>Consulte Também

* [Configurar um cliente de extração com nomes de configuração](pullClientConfigNames.md)

