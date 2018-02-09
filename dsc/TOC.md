# [Descrição Geral](overview.md)

## [Descrição Geral da Configuração do Estado Pretendido para Decisores](decisionMaker.md)

## [Descrição Geral da Configuração do Estado Pretendido para Engenheiros](DscForEngineers.md)

## [Início rápido da DSC](quickStart.md)

# [Configurações](configurations.md)

## [Aplicar configurações](enactingConfigurations.md)

## [Separar dados de configuração e de ambiente](separatingEnvData.md)

## [Utilizar recursos com várias versões](sxsResource.md)

## [Executar a DSC com as credenciais do utilizador](runAsUser.md)

## [Especificar dependências entre nós](crossNodeDependencies.md)

## [Dados de configuração](configData.md)

### [Opções de credenciais nos dados de configuração](configDataCredentials.md)

## [Configurações de aninhamento](compositeConfigs.md)

## [Proteger o ficheiro MOF de configuração](secureMOF.md)

## [Configurações Parciais](partialConfigs.md)

## [Escrever a ajuda das configurações da DSC](configHelp.md)

## [Configurar uma máquina virtual no arranque inicial através da DSC](bootstrapDsc.md)

### [Chave de registo DSCAutomationHostEnabled](DSCAutomationHostEnabled.md)

# [Recursos](resources.md)

## [Recursos incorporados](builtInResource.md)

### [Recurso Archive](archiveResource.md)

### [Recurso Environment](environmentResource.md)

### [Recurso File](fileResource.md)

### [Recurso Group](groupResource.md)

### [Recurso GroupSet](groupSetResource.md)

### [Recurso Log](logResource.md)

### [Recurso Package](packageResource.md)

### [Recurso ProcessSet](processSetResource.md)

### [Recurso Registry](registryResource.md)

### [Recurso Script](scriptResource.md)

### [Recurso Service](serviceResource.md)

### [Recurso ServiceSet](serviceSetResource.md)

### [Recurso User](userResource.md)

### [WaitForAllResource](waitForAllResource.md)

### [WaitForAnyResource](waitForAnyResource.md)

### [WaitForSomeResource](waitForSomeResource.md)

### [Recurso WindowsFeature](windowsfeatureResource.md)

### [Recurso WindowsFeatureSet](windowsFeatureSetResource.md)

### [Recurso WindowsOptionalFeature](windowsOptionalFeatureResource.md)

### [Recurso WindowsOptionalFeatureSet](windowsOptionalFeatureSetResource.md)

### [Recurso WindowsPackageCab](windowsPackageCabResource.md)

### [Recurso WindowsProcess](windowsProcessResource.md)

## [Criar recursos personalizados](authoringResource.md) 

### [Recursos personalizados baseados em MOF](authoringResourceMOF.md)

#### [Recurso baseado em MOF em C#](authoringResourceMofCS.md)

### [Recursos personalizados baseados em classe](authoringResourceClass.md)

### [Recursos compostos](authoringResourceComposite.md)

### [Escrever um recurso de DSC de instância única (melhor prática)](singleInstance.md)

### [Lista de verificação de criação de recursos](resourceAuthoringChecklist.md)

## [Depurar os recursos de DSC](debugResource.md)

## [Chamar os métodos de recursos de DSC diretamente](directCallResource.md)

# Gestor de Configuração Local

## [Configurar o Gestor de Configuração Local (LCM)](metaConfig.md)

## [Configurar o LCM no PowerShell 4.0](metaConfig4.md)

# Modelo de solicitação de DSC

## [Serviço de Solicitação de DSC](pullServer.md)

## [Configurar um servidor de solicitação SMB de DSC](pullServerSMB.md)

## [Configurar um cliente de solicitação](pullClient.md)

### [Configurar um cliente de solicitação através de nomes de configuração](pullClientConfigNames.md)

### [Configurar um cliente de solicitação através de IDs de configuração](pullClientConfigID.md)

## [Utilizar um servidor de relatório de DSC](reportServer.md)

## [Melhores práticas do servidor de solicitação](secureServer.md)

# [Exemplos de DSC](dscExamples.md)

## [Criar um pipeline CI/CD com DSC, Pester e Visual Studio Team Services](dscCiCd.md)

## [Separar dados de configuração e de ambiente](separatingEnvData.md)

# [Resolução de Problemas de DSC](troubleshooting.md)

# [Utilizar a DSC no Servidor Nano](nanoDsc.md)

# DSC no Linux

## [Introdução à DSC para Linux](lnxGettingStarted.md)

## [Recursos incorporados para Linux](lnxBuiltInResources.md)

### [Recurso nxArchive](lnxArchiveResource.md)

### [Recurso nxEnvironment](lnxEnvironmentResource.md)

### [Recurso nxFile](lnxFileResource.md)

### [Recurso nxFileLine](lnxFileLineResource.md)

### [Recurso nxGroup](lnxGroupResource.md)

### [Recurso nxPackage](lnxPackageResource.md)

### [Recurso nxService](lnxServiceResource.md)

### [Recurso nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md)

### [Recurso nxUser](lnxUserResource.md)

# [Utilizar a DSC no Microsoft Azure](azureDsc.md)

# Referência MOF de DSC

## [Classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager.md)

### [Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-applyconfiguration.md)

### [Método DisableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)

### [Método EnableDebugConfiguration da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)

### [Método GetConfiguration da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-getconfiguration.md)

### [Método GetConfigurationResultOutput da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)

### [Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)

### [Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)

### [Método PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)

### [Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-removeconfiguration.md)

### [Método ResourceGet da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-resourceget.md)

### [Método ResourceSet da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-resourceset.md)

### [Método ResourceTest da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-resourcetest.md)

### [Método RollBack da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-rollback.md)

### [Método SendConfiguration da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-sendconfiguration.md)

### [Método SendConfigurationApply da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)

### [Método SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)

### [Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)

### [Método StopConfiguration da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-stopconfiguration.md)

### [Método TestConfiguration da classe MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-testconfiguration.md)

# Mais Recursos

## [Documentos Técnicos](whitepapers.md)
