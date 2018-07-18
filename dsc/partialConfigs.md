---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Configurações parciais de PowerShell Desired State Configuration
ms.openlocfilehash: 6d344b666421aba5745945f6148570e4c8229c1a
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093937"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>Configurações parciais de PowerShell Desired State Configuration

> Aplica-se a: Windows PowerShell 5.0 e posterior.

No PowerShell 5.0, Desired State Configuration (DSC) permite que as configurações sejam entregues em fragmentos e de várias origens. O Gestor de configuração Local (LCM) no nó de destino prepara os fragmentos antes de aplicá-los como uma configuração única. Esta capacidade permite a partilha de controlo da configuração entre as equipes ou indivíduos.
Por exemplo, se dois ou mais equipes de desenvolvedores estiver a colaborar num serviço, eles cada querer criar configurações para gerir a sua parte do serviço. Cada uma das seguintes configurações poderia ser extraída dos servidores de solicitação de diferentes e poderia ser adicionados em diferentes fases do desenvolvimento. Configurações parciais também permitem a diferentes pessoas ou equipas controlar diferentes aspetos de configuração de nós sem ter de coordenar a edição de um documento de configuração única. Por exemplo, uma equipe pode ser responsável por implementar uma VM e o sistema operativo, enquanto outra equipe pode implementar outras aplicações e serviços nessa VM. Configurações parciais, cada equipe pode criar sua própria configuração, sem qualquer um deles desnecessariamente a ser complicado.

Pode utilizar configurações parciais no modo push, no modo de solicitação ou uma combinação dos dois.

## <a name="partial-configurations-in-push-mode"></a>Configurações parciais no modo de push

Para usar configurações parciais em modo push, configurar o LCM no nó de destino para receber as configurações parciais. Cada configuração parcial deve ser colocada no destino, utilizando o `Publish-DSCConfiguration` cmdlet. O nó de destino, em seguida, combina a configuração parcial numa única configuração, e pode aplicar a configuração ao chamar o [Start-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>Configurar o LCM para configurações parcial do modo de push

Para configurar o LCM para configurações parciais no modo push, crie uma **dsclocalconfigurationmanager para** configuração com um **PartialConfiguration** bloco para cada configuração parcial. Para obter mais informações sobre como configurar o LCM, consulte [configurar o Gestor de configuração Local do Windows](/powershell/dsc/metaConfig).
O exemplo seguinte mostra uma configuração de LCM que espera duas configurações parciais — um que implementa o sistema operacional e um que implementa e configura o SharePoint.

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

O **RefreshMode** cada configuração parcial está definida como "Push". Os nomes da **PartialConfiguration** blocos (no caso, "ServiceAccountConfig" e "SharePointConfig") tem de corresponder exatamente os nomes das configurações que são enviados por push para o nó de destino.

> [!Note]
> Com o nome de cada **PartialConfiguration** bloco tem de corresponder o nome real da configuração conforme é especificado com o script de configuração, não o nome do ficheiro MOF, que deve ser o nome do nó de destino ou `localhost`.

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>Publicação e a partir de configurações parciais do modo de push

Em seguida, chame [Publish-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) para cada configuração, passando as pastas que contêm os documentos de configuração como a **caminho** parâmetros. `Publish-DSCConfiguration`coloca os ficheiros MOF de configuração para os nós de destino. Depois de publicar as duas configurações, pode chamar `Start-DSCConfiguration –UseExisting` no nó de destino.

Por exemplo, se o ter compilado os seguintes documentos MOF de configuração no nó de criação:

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\DscTests\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

Imagem da publicação e execute as configurações da seguinte forma:

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> O utilizador que executa o [Publish-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet tem de ter privilégios de administrador no nó de destino.

## <a name="partial-configurations-in-pull-mode"></a>Configurações parciais no modo de solicitação

Configurações parciais podem ser obtidas a partir de um ou mais servidores de extração (para obter mais informações sobre servidores de extração, consulte [Windows PowerShell Desired State Configuration Pull servidores](pullServer.md). Para tal, tem de configurar o LCM no nó de destino para extrair as configurações de parciais e dê um nome e localize os documentos de configuração corretamente nos servidores de pull.

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>Configurar o LCM para configurações de nó de extração

Para configurar o LCM para solicitar configurações parciais a partir de um servidor de solicitação, define o servidor de solicitação em qualquer um uma **ConfigurationRepositoryWeb** (para um servidor de solicitação HTTP) ou **ConfigurationRepositoryShare** ( para um servidor de solicitação SMB) bloco. Em seguida, crie **PartialConfiguration** blocos que se referem para o servidor de solicitação, utilizando o **ConfigurationSource** propriedade. Terá também de criar uma **configurações** bloco para especificar que o LCM usa o modo de solicitação e especificar a **ConfigurationNames** ou **ConfigurationID** que o servidor de solicitação e utilização do nó de destino para identificar as configurações. A seguinte configuração de meta define um servidor de solicitação HTTP com o nome CONTOSO-PullSrv e servidor de solicitação de duas configurações parciais que usá-lo.

Para obter mais informações sobre como configurar o LCM usando **ConfigurationNames**, consulte [configuração de um cliente de solicitação através de nomes de configuração](pullClientConfigNames.md).
Para obter informações sobre como configurar o LCM usando **ConfigurationID**, consulte [configuração de um cliente de solicitação através do ID de configuração](pullClientConfigID.md).

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>Configurar o LCM para configurações de modo de solicitação com nomes de configuração

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>Configurar o LCM para configurações de modo de solicitação com ConfigurationID

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

Pode extrair configurações parciais de mais do que um servidor de solicitação — apenas terá de definir cada servidor de solicitação e, em seguida, consulte o servidor de solicitação apropriada em cada **PartialConfiguration** bloco.

Depois de criar a meta-configuração, tem de executá-lo para criar um documento de configuração (um ficheiro MOF) e, em seguida, chame [Set-dsclocalconfigurationmanager para](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) para configurar o LCM.

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>Atribuição de nomes e colocar os documentos de configuração no servidor de solicitação (ConfigurationNames)

Os documentos de configuração parcial tem de ser colocados na pasta especificada como a **ConfigurationPath** no `web.config` ficheiro para o servidor de solicitação (normalmente `C:\Program Files\WindowsPowerShell\DscService\Configuration`).

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>Nomenclatura de configuração de documentos no servidor de solicitação no PowerShell 5.1

Se está extraindo apenas uma configuração parcial de um servidor de solicitação individuais, o documento de configuração pode ter qualquer nome.
Se está extraindo mais do que uma configuração parcial a partir de um servidor de solicitação, o documento de configuração pode ser com o nome `<ConfigurationName>.mof`, onde *ConfigurationName* é o nome da configuração parcial, ou `<ConfigurationName>.<NodeName>.mof`, em que  *ConfigurationName* é o nome da configuração parcial, e *NodeName* é o nome do nó de destino.
Isso permite que pull configurações do servidor de solicitação de DSC de automatização do Azure.

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>Nomenclatura de configuração de documentos no servidor de solicitação no PowerShell 5.0

Os documentos de configuração tem de ter o nome da seguinte forma: `ConfigurationName.mof`, onde *ConfigurationName* é o nome da configuração parcial. No nosso exemplo, os documentos de configuração devem ter o nome da seguinte forma:

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>Atribuição de nomes e colocar os documentos de configuração no servidor de solicitação (ConfigurationID)

Os documentos de configuração parcial tem de ser colocados na pasta especificada como a **ConfigurationPath** no `web.config` ficheiro para o servidor de solicitação (normalmente `C:\Program Files\WindowsPowerShell\DscService\Configuration`). Os documentos de configuração tem de ter o nome da seguinte forma: _ConfigurationName_. * ConfigurationID8`.mof`, onde _ConfigurationName_ é o nome da configuração parcial e _ConfigurationID_ é o ID de configuração é definido no LCM no nó de destino. No nosso exemplo, os documentos de configuração devem ter o nome da seguinte forma:

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a>Executar configurações parciais de um servidor de solicitação

Depois do LCM no nó de destino foi configurado e a configuração de documentos tenham sido criados e com o nome corretamente no servidor de solicitação, o nó de destino irá fazer com que as configurações parciais, combiná-los e aplicar a configuração resultante regulares intervalos como especificado pelos **RefreshFrequencyMins** propriedade do LCM. Se quiser forçar uma atualização, pode chamar o [Update-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, para extrair as configurações e, em seguida, `Start-DSCConfiguration –UseExisting` aplicá-las.

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>Configurações parciais em modos de push e pull mistos

Também pode combinar push e pull modos para configurações parciais. Ou seja, poderia ter uma configuração parcial que é obtida a partir de um servidor de solicitação, enquanto outra configuração parcial é emitidos via push. Especifique o modo de atualização para cada configuração parcial, conforme descrito nas secções anteriores.
Por exemplo, a seguinte configuração de meta descreve o mesmo exemplo, com o `ServiceAccountConfig` configuração parcial no modo de solicitação e o `SharePointConfig` configuração parcial no modo push.

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>Modos de push e pull mistos usando ConfigurationNames

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>Modos de push e pull mistos usando ConfigurationID

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

Tenha em atenção que o **RefreshMode** especificada no bloco de definições é o "Pull", mas o **RefreshMode** para o `SharePointConfig` configuração parcial é "Push".

Dê um nome e localizar os ficheiros MOF de configuração, conforme descrito acima para seus modos de atualização respectiva. Chamar `Publish-DSCConfiguration` para publicar o `SharePointConfig` configuração parcial e aguardar a `ServiceAccountConfig` configuração a ser obtido a partir do servidor de solicitação ou forçar uma atualização ao chamar [Update-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).

## <a name="example-serviceaccountconfig-partial-configuration"></a>Exemplo de configuração de ServiceAccountConfig parcial

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig
```

## <a name="example-sharepointconfig-partial-configuration"></a>Exemplo de configuração de SharePointConfig parcial

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a>Consulte Também

[Windows PowerShell Desired State Configuration Pull servidores](pullServer.md)

[Configurar o Gestor de configuração Local do Windows](/powershell/dsc/metaConfig)