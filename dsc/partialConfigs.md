---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Configurações de parciais de configuração de estado pretendido do PowerShell
ms.openlocfilehash: e6d80b065ad9e68517d2952b7643e4c611d82a0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189980"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>Configurações de parciais de configuração de estado pretendido do PowerShell

>Aplica-se a: Windows PowerShell 5.0 e posterior.

No PowerShell 5.0, configuração de estado pretendido (DSC) permite que as configurações ser entregue no fragmentos e de várias origens. O Gestor de configuração Local (MMC) no nó de destino coloca os fragmentos em conjunto antes de aplicá-las como uma configuração única. Esta capacidade permite a partilha de controlo da configuração entre equipas ou indivíduos.
Por exemplo, se duas ou mais agrupamentos de programadores estiverem a colaborar num serviço, poderá cada pretendem criar configurações para gerir os respetivos parte do serviço. Cada uma destas configurações foi ser solicitada a partir de servidores de extração diferente, e pode ser adicionados em diferentes fases de desenvolvimento. Configurações parciais também permitem diferentes pessoas ou equipas controlar diferentes aspetos de configuração de nós sem ter de se coordenar a edição de um documento de configuração única. Por exemplo, uma equipa pode ser responsável por implementar uma VM e o sistema operativo, enquanto outra equipa poderá implementar outras aplicações e serviços nessa VM. Com configurações parciais, cada equipa pode criar a suas próprias configuração, sem um da ser complicou desnecessariamente.

Pode utilizar configurações parciais no modo de push, modo de extração ou uma combinação dos dois.

## <a name="partial-configurations-in-push-mode"></a>Configurações parciais no modo de push
Para utilizar configurações parciais no modo de push, configurar o MMC no nó de destino para receber as configurações parciais. Cada configuração parcial deve ser enviada para o destino utilizando o cmdlet Publish-DSCConfiguration. O nó de destino, em seguida, combina a configuração parcial para uma configuração única e pode aplicar a configuração ao chamar o [início DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>Configurar o MMC para configurações parcial do modo de push
Para configurar MMC para configurações parciais no modo de push, crie um **DSCLocalConfigurationManager** configuração com um **PartialConfiguration** bloco para cada configuração parcial. Para obter mais informações sobre como configurar o MMC, consulte [Windows configurar o Gestor de configuração Local](https://technet.microsoft.com/library/mt421188.aspx).
O exemplo seguinte mostra uma configuração de MMC que espera duas configurações parciais — que implementa o sistema operativo e outro que implementa e configura o SharePoint.

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

O **RefreshMode** cada configuração parcial está definida como "Push". Os nomes do **PartialConfiguration** blocos (neste caso, "ServiceAccountConfig" e "SharePointConfig") tem de corresponder exatamente os nomes das configurações que são enviadas por push para o nó de destino.

>**Nota:** com o nome de cada **PartialConfiguration** bloco tem de coincidir com o nome da configuração real conforme especificado no script de configuração, não o nome do ficheiro MOF, que deve ser o nome do nó de destino ou `localhost`.

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>Publicar e iniciar configurações parcial do modo de push

Em seguida, chame [publicar DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) para cada configuração, transmitir as pastas que contêm os documentos de configuração como a **caminho** parâmetros. `Publish-DSCConfiguration`coloca os ficheiros MOF de configuração para os nós de destino. Depois de publicar ambas as configurações, pode chamar `Start-DSCConfiguration –UseExisting` no nó de destino.

Por exemplo, se tiver compilado os seguintes documentos MOF de configuração no nó de criação:

```powershell
PS C:\PartialConfigTest> Get-ChildItem -Recurse


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

Seria publicar e executar as configurações da seguinte forma:

```powershell
PS C:\PartialConfigTest> Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Start-DscConfiguration -UseExisting -ComputerName 'TestVM'

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

>**Nota:** o utilizador que executa o [publicar DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) cmdlet tem de ter privilégios de administrador no nó de destino.

## <a name="partial-configurations-in-pull-mode"></a>Configurações parciais no modo de extração

Podem ser solicitadas configurações parciais de uma ou mais servidores de extração (para obter mais informações sobre servidores de solicitação, consulte [Windows PowerShell pretendido Estado solicitação servidores de configuração](pullServer.md). Para tal, tem de configurar o MMC no nó de destino para solicitar as configurações de parciais e o nome e localize os documentos de configuração corretamente nos servidores de extração.

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>Configurar o MMC para configurações de nó de solicitação

Para configurar o MMC para solicitar parciais configurações de um servidor de solicitação, definir o servidor de solicitação num **ConfigurationRepositoryWeb** (para um servidor de solicitação HTTP) ou **ConfigurationRepositoryShare** ( para um servidor de solicitação SMB) bloco. Em seguida, criar **PartialConfiguration** blocos que se referem para o servidor de solicitação, utilizando o **ConfigurationSource** propriedade. Também tem de criar um **definições** bloco para especificar que o MMC utiliza o modo de extração e para especificar o **ConfigurationNames** ou **ConfigurationID** que o servidor de solicitação e utilização do nó de destino para identificar as configurações. A configuração meta seguinte define um servidor de solicitação HTTP com o nome CONTOSO PullSrv e duas configurações parciais que utilizam esse servidor de solicitação.

Para obter mais informações sobre como configurar o utilizando o MMC **ConfigurationNames**, consulte [configurar um cliente de solicitação utilizando nomes de configuração](pullClientConfigNames.md).
Para obter informações sobre como configurar o utilizando o MMC **ConfigurationID**, consulte [configurar um cliente de extração com o ID de configuração](pullClientConfigID.md).

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>Configurar o MMC para configurações de modo de extração utilizando nomes de configuração

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>Configurar o MMC para configurações de modo de extração utilizando ConfigurationID

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

Pode solicitar parciais configurações de mais do que um servidor de solicitação — apenas terá de definir a cada servidor de solicitação e, em seguida, consulte o servidor de solicitação adequado em cada **PartialConfiguration** bloco.

Depois de criar a configuração meta, deve executá-la para criar um documento de configuração (um ficheiro MOF) e, em seguida, chame [conjunto DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) para configurar o MMC.

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>Atribuição de nomes e colocar os documentos de configuração no servidor de solicitação (ConfigurationNames)

Os documentos de configuração parcial tem de ser colocados na pasta especificada como a **ConfigurationPath** no `web.config` ficheiro para o servidor de solicitação (normalmente `C:\Program Files\WindowsPowerShell\DscService\Configuration`).

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>Nomenclatura de configuração de documentos no servidor de solicitação no PowerShell 5.1

Se estiver a extrair apenas uma configuração parcial de um servidor de solicitação individuais, o documento de configuração pode ter qualquer nome.
Se estiver a extrair mais de uma configuração parcial de um servidor de solicitação, o documento de configuração pode ter um nome a `<ConfigurationName>.mof`, onde _ConfigurationName_ é o nome da configuração da parcial, ou `<ConfigurationName>.<NodeName>.mof`, em que  _ConfigurationName_ é o nome da configuração da parcial, e _NodeName_ é o nome do nó de destino.
Isto permite-lhe solicitação configurações do servidor de solicitação do Automation DSC do Azure.


#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>Nomenclatura de configuração de documentos no servidor de solicitação no PowerShell 5.0

Os documentos de configuração devem ter o nome da seguinte forma: `ConfigurationName.mof`, onde _ConfigurationName_ é o nome da configuração parcial. Para o nosso exemplo, os documentos de configuração devem ter o nome da seguinte forma:

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>Atribuição de nomes e colocar os documentos de configuração no servidor de solicitação (ConfigurationID)

Os documentos de configuração parcial tem de ser colocados na pasta especificada como a **ConfigurationPath** no `web.config` ficheiro para o servidor de solicitação (normalmente `C:\Program Files\WindowsPowerShell\DscService\Configuration`). Os documentos de configuração devem ter o nome da seguinte forma: _ConfigurationName_. _ConfigurationID_`.mof`, onde _ConfigurationName_ é o nome da configuração parcial e _ConfigurationID_ o ID de configuração está definido na MMC no destino nó. Para o nosso exemplo, os documentos de configuração devem ter o nome da seguinte forma:

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```


### <a name="running-partial-configurations-from-a-pull-server"></a>Executar configurações parciais de um servidor de solicitação

Depois do MMC no nó de destino foi configurado e a configuração documentos tiverem sido criados e com o nome corretamente no servidor de solicitação, o nó de destino transmitirão as configurações parciais, combine-os e aplicar a configuração resultante regulares intervalos tal como especificado pelo **RefreshFrequencyMins** propriedade a MMC. Se pretender forçar uma atualização, pode chamar o [atualização DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) cmdlet, extraia as configurações e, em seguida, `Start-DSCConfiguration –UseExisting` para aplicá-las.


## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>Configurações parciais nos modos push e pull mistos

Também pode misturar push e pull modos para configurações parciais. Ou seja, pode ter uma configuração parcial solicitada de um servidor de solicitação, enquanto outra configuração parcial é premida. Especifique o modo de atualização para cada configuração parcial, conforme descrito nas secções anteriores.
Por exemplo, a configuração meta seguinte descreve o mesmo exemplo, com o `ServiceAccountConfig` parcial configuração no modo de extração e `SharePointConfig` parcial configuração no modo de push.

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>Modos push e pull mistos utilizando ConfigurationNames

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>Modos push e pull mistos utilizando ConfigurationID

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

Tenha em atenção que o **RefreshMode** especificado no bloco de definições é "Solicitar", mas o **RefreshMode** para o `SharePointConfig` configuração parcial é "Push".

Nome e localizar os ficheiros de MOF configuração conforme descrito acima para os respetivos modos de atualização do respetivo. Chamar **publicar DSCConfiguration** para publicar o `SharePointConfig` configuração parcial e aguarde que o `ServiceAccountConfig` configuração para ser solicitados a partir do servidor de solicitação ou forçar uma atualização ao chamar [ Atualização DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).

## <a name="example-serviceaccountconfig-partial-configuration"></a>Exemplo de configuração ServiceAccountConfig parcial

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
## <a name="example-sharepointconfig-partial-configuration"></a>Exemplo de configuração SharePointConfig parcial
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
##<a name="see-also"></a>Consulte Também

**Conceitos**
[servidores de solicitação de configuração do estado pretendido do Windows PowerShell](pullServer.md)

[Configurar o Gestor de configuração Local do Windows](https://technet.microsoft.com/library/mt421188.aspx)