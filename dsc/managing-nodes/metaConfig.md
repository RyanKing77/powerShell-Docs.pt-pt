---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Configurar o Gestor de configuração Local
ms.openlocfilehash: 15d696587d54d4a6464096cfb78757c41e9185c6
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229507"
---
# <a name="configuring-the-local-configuration-manager"></a>Configurar o Gestor de configuração Local

> Aplica-se a: Windows PowerShell 5.0

O Gestor de configuração Local (LCM) é o mecanismo de Desired State Configuration (DSC).
O LCM é executado em cada nó de destino e é responsável por analisar e aplicar configurações que são enviadas para o nó.
Também é responsável por um número de outros aspectos do DSC, incluindo o seguinte.

- Determinar o modo de atualização (push ou pull).
- Especificar a frequência com que um nó recebe e enacts configurações.
- Associar o nó com o serviço de solicitação.
- Especificar configurações parciais.

Utilize um tipo especial de configuração para configurar o LCM para especificar cada um dos seguintes comportamentos.
As secções seguintes descrevem como configurar o LCM.

Windows PowerShell 5.0 introduziu novas definições para gerir o Gestor de configuração Local.
Para obter informações sobre como configurar o LCM no Windows PowerShell 4.0, consulte [configurar o Gestor de configuração de Local no anterior versões do Windows PowerShell](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Escrever e aplicar uma configuração de LCM

Para configurar o LCM, pode criar e executar um tipo especial de configuração que se aplica definições de LCM.
Para especificar uma configuração de LCM, use o atributo dsclocalconfigurationmanager para.
O código a seguir mostra uma configuração simples que define o LCM como modo push.

```powershell
[DSCLocalConfigurationManager()]
configuration LCMConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
        }
    }
}
```

O processo de aplicar as definições para LCM é semelhante ao aplicar uma configuração de DSC.
Irá criar uma configuração de LCM, compilá-la para um ficheiro MOF e aplicá-la para o nó.
Ao contrário das configurações de DSC, não aplicá uma configuração de LCM ao chamar o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.
Em vez disso, chama [Set-dsclocalconfigurationmanager para](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager), fornecendo o caminho para a configuração de LCM MOF como um parâmetro.
Depois de aplicá a configuração do LCM, pode ver as propriedades do LCM ao chamar o [Get-dsclocalconfigurationmanager para](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.

Uma configuração de LCM pode conter blocos apenas para um conjunto limitado de recursos.
No exemplo anterior, é o único recurso chamado **definições**.
Os outros recursos disponíveis são:

* **ConfigurationRepositoryWeb**: Especifica um serviço de solicitação HTTP para configurações.
* **ConfigurationRepositoryShare**: Especifica uma partilha de SMB de configurações.
* **ResourceRepositoryWeb**: Especifica um serviço de solicitação HTTP para os módulos.
* **ResourceRepositoryShare**: Especifica uma partilha de SMB de módulos.
* **ReportServerWeb**: Especifica um serviço de solicitação HTTP para que os relatórios são enviados.
* **PartialConfiguration**: fornece dados para ativar a configurações parciais.

## <a name="basic-settings"></a>Definições básicas

Além de especificar pontos finais de serviço de solicitação/caminhos e configurações parciais, todas as propriedades do LCM estão configuradas num **definições** bloco.
As seguintes propriedades estão disponíveis num **definições** bloco.

|  Propriedade  |  Tipo  |  Descrição   |
|----------- |------- |--------------- |
| ActionAfterReboot| string| Especifica o que acontece após um reinício durante a aplicação de uma configuração. Os valores possíveis são __"ContinueConfiguration"__ e __"StopConfiguration"__. <ul><li> __ContinueConfiguration__: Continue a aplicar a configuração atual após o reinício do computador. Este é o valor predefinido</li><li>__StopConfiguration__: Pare a configuração atual após o reinício do computador.</li></ul>|
| AllowModuleOverwrite| Bool| __$TRUE__ se novas configurações transferidas a partir do serviço de solicitação podem substituir os antigos no nó de destino. Caso contrário, $FALSE.|
| CertificateID| string| O thumbprint de um certificado utilizado para proteger as credenciais transmitidas numa configuração. Para obter mais informações, consulte [pretendem proteger as credenciais no Windows PowerShell Desired State Configuration](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)?. <br> __Nota:__ é gerida automaticamente se utilizar o serviço de solicitação de DSC de automatização do Azure.|
| ConfigurationDownloadManagers| CimInstance[]| Obsoleto. Uso __ConfigurationRepositoryWeb__ e __ConfigurationRepositoryShare__ pontos finais de serviço de blocos para definir o pull de configuração.|
| ConfigurationID| string| Para efeitos de compatibilidade com a solicitação mais antiga serviço versões. Um GUID que identifica o ficheiro de configuração para obter a partir de um serviço pull. O nó irá extrair configurações no serviço de solicitação, se o nome da configuração do MOF se chama ConfigurationID.mof.<br> __Nota:__ Se definir esta propriedade, registar o nó com um serviço pull de usando __RegistrationKey__ não funciona. Para obter mais informações, consulte [como configurar um cliente de solicitação com nomes de configuração](../pull-server/pullClientConfigNames.md).|
| ConfigurationMode| string | Especifica a forma como o LCM, na verdade, aplica-se a configuração para os nós de destino. Os valores possíveis são __"ApplyOnly"__,__"ApplyAndMonitor"__, e __"ApplyAndAutoCorrect"__. <ul><li>__ApplyOnly__: DSC aplica-se a configuração e não faz nada além disso, a menos que uma nova configuração é enviada por push para o nó de destino ou quando uma nova configuração é obtida a partir de um serviço. Depois de aplicativo inicial de uma nova configuração, DSC não verifica se desviam de um estado anteriormente configurado. Tenha em atenção que DSC irá tentar aplicar a configuração, até que seja bem-sucedida __ApplyOnly__ entra em vigor. </li><li> __ApplyAndMonitor__: Este é o valor predefinido. O LCM aplica-se quaisquer configurações de novo. Após a aplicação inicial de uma configuração de novo, se o nó de destino drifts do estado pretendido, o DSC relatórios discrepância nos registos. Tenha em atenção que DSC irá tentar aplicar a configuração, até que seja bem-sucedida __ApplyAndMonitor__ entra em vigor.</li><li>__ApplyAndAutoCorrect__: DSC aplica-se quaisquer configurações de novo. Depois de aplicativo inicial de uma nova configuração, se o nó de destino drifts do estado pretendido, DSC relatórios discrepância nos registos e, em seguida, voltar aplica-se a configuração atual.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| Como muitas vezes, em minutos, a configuração atual é verificada e aplicada. Esta propriedade é ignorada se a propriedade ConfigurationMode estiver definida como ApplyOnly. O valor predefinido é 15.|
| DebugMode| string| Os valores possíveis são __None__, __ForceModuleImport__, e __todos os__. <ul><li>Defina como __None__ a utilização de recursos em cache. Esta é a predefinição e deve ser usada em cenários de produção.</li><li>Na definição __ForceModuleImport__, faz com que o LCM recarregar quaisquer módulos de recursos de DSC, mesmo que tenha sido anteriormente carregados e armazenados em cache. Este problema afeta o desempenho de operações de DSC pois cada módulo é recarregado na utilização. Normalmente usaria este valor durante a depuração de um recurso</li><li>Nesta versão, __todos os__ são os mesmos __ForceModuleImport__</li></ul> |
| RebootNodeIfNeeded| Bool| Defina esta opção como `$true` para permitir que os recursos para reiniciar o nó utilizando o `$global:DSCMachineStatus` sinalizador. Caso contrário, terá de reiniciar manualmente o nó para qualquer configuração que requer ele. O valor predefinido é `$false`. Para utilizar esta definição quando uma condição de reinicialização é elaborada por algo que não seja o DSC (por exemplo, o programa de instalação do Windows), combinar esta definição com o [xPendingReboot](https://github.com/powershell/xpendingreboot) módulo.|
| RefreshMode| string| Especifica a forma como o LCM obtém configurações. Os valores possíveis são __"Desativado"__, __"Push"__, e __"Puxar"__. <ul><li>__Desativado__: Configurações de DSC estão desativadas para este nó.</li><li> __Push__: As configurações são iniciadas ao chamar o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet. A configuração é aplicada imediatamente para o nó. Este é o valor predefinido.</li><li>__Extrair:__ O nó está configurado para verificar regularmente para configurações de um serviço de solicitação ou o caminho SMB. Se esta propriedade estiver definida como __extrair__, tem de especificar um HTTP (serviço) ou o caminho SMB (partilha) num __ConfigurationRepositoryWeb__ ou __ConfigurationRepositoryShare__ bloco.</li></ul>|
| RefreshFrequencyMins| Uint32| O intervalo de tempo, em minutos, em que o LCM verifica um serviço pull para obter configurações atualizadas. Este valor é ignorado se o LCM não estiver configurado no modo de solicitação. O valor predefinido é 30.|
| ReportManagers| CimInstance[]| Obsoleto. Uso __ReportServerWeb__ blocos para definir um ponto de extremidade para enviar dados de relatórios para um serviço pull.|
| ResourceModuleManagers| CimInstance[]| Obsoleto. Uso __ResourceRepositoryWeb__ e __ResourceRepositoryShare__ blocos para definir a solicitação de serviço pontos de extremidade HTTP ou caminhos SMB, respectivamente.|
| PartialConfigurations| CimInstance| Não implementado. Não utilizar.|
| StatusRetentionTimeInDays | UInt32| O número de dias que o LCM mantém o estado da configuração atual.|

> [!NOTE]
> A LCM ser iniciada a **ConfigurationModeFrequencyMins** ciclo com base em:
>
> - Um novo metaconfig for aplicado através de `Set-DscLocalConfigurationManager`
> - Um reinício do computador
>
> Para qualquer condição em que o processo de temporizador sofre uma falha, o que será detetada dentro de 30 segundos e o ciclo será reiniciado.
> Uma operação simultânea pode atrasar o ciclo de a ser iniciada, se a duração desta operação excede a frequência de ciclo de configurado, o próximo temporizador não será iniciado.
>
> Exemplo, o metaconfig está configurado com uma frequência de solicitação de 15 minutos e uma solicitação ocorre no T1.  O nó não concluir o trabalho para 16 minutos.  O primeiro ciclo de 15 minutos é ignorado e pull seguinte irá ocorrer em T1 + 15 + 15.

## <a name="pull-service"></a>Serviço de solicitação

Configuração de LCM suporta definindo os seguintes tipos de pontos finais de serviço de solicitação:

- **Servidor de configuração**: Um repositório para configurações de DSC. Definir os servidores de configuração utilizando **ConfigurationRepositoryWeb** (para servidores baseados na web) e **ConfigurationRepositoryShare** (para servidores baseados em SMB) blocos.
- **Servidor de recurso**: Um repositório de recursos de DSC, empacotado como módulos do PowerShell. Definir os servidores de recursos utilizando **ResourceRepositoryWeb** (para servidores baseados na web) e **ResourceRepositoryShare** (para servidores baseados em SMB) blocos.
- **Servidor de relatórios**: Um serviço que DSC envia os dados de relatório para. Definir os servidores de relatórios usando **ReportServerWeb** blocos. Um servidor de relatórios tem de ser um serviço web.

Para obter mais detalhes sobre o serviço de solicitação, veja [serviço Pull do Desired State Configuration](../pull-server/pullServer.md).

## <a name="configuration-server-blocks"></a>Blocos do servidor de configuração

Para definir um servidor de configuração baseado na web, crie uma **ConfigurationRepositoryWeb** bloco.
R **ConfigurationRepositoryWeb** define as propriedades seguintes.

|Propriedade|Tipo|Descrição|
|---|---|---|
|AllowUnsecureConnection|Bool|Defina como **$TRUE** para permitir ligações a partir do nó para o servidor sem autenticação. Defina como **$FALSE** para exigir autenticação.|
|CertificateID|string|O thumbprint de um certificado utilizado para autenticar para o servidor.|
|ConfigurationNames|String[]|Uma matriz de nomes de configurações para ser solicitada por nó de destino. Estes são utilizados apenas se o nó está registado com o serviço pull utilizando um **RegistrationKey**. Para obter mais informações, consulte [como configurar um cliente de solicitação com nomes de configuração](../pull-server/pullClientConfigNames.md).|
|RegistrationKey|string|Um GUID que regista o nó com o serviço de solicitação. Para obter mais informações, consulte [como configurar um cliente de solicitação com nomes de configuração](../pull-server/pullClientConfigNames.md).|
|ServerURL|string|O URL do serviço de configuração.|
|ProxyURL*|string|O URL de proxy http para utilizar ao comunicar com o serviço de configuração.|
|ProxyCredential*|pscredential|Credencial que deve utilizar para o proxy de http.|

>! Tenha em atenção \* suportado no Windows versões 1809 e posteriores.

Veja um script de exemplo para simplificar a configurar o valor de ConfigurationRepositoryWeb para nós no local está disponível - [metaconfigurations geração DSC](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Para definir um servidor de configuração baseado em SMB, crie uma **ConfigurationRepositoryShare** bloco.
R **ConfigurationRepositoryShare** define as propriedades seguintes.

|Propriedade|Tipo|Descrição|
|---|---|---|
|Credencial|MSFT_Credential|A credencial utilizada para autenticar para a partilha SMB.|
|SourcePath|string|O caminho da partilha SMB.|

## <a name="resource-server-blocks"></a>Blocos de recursos de servidor

Para definir um servidor de recursos com base na web, crie uma **ResourceRepositoryWeb** bloco.
R **ResourceRepositoryWeb** define as propriedades seguintes.

|Propriedade|Tipo|Descrição|
|---|---|---|
|AllowUnsecureConnection|Bool|Defina como **$TRUE** para permitir ligações a partir do nó para o servidor sem autenticação. Defina como **$FALSE** para exigir autenticação.|
|CertificateID|string|O thumbprint de um certificado utilizado para autenticar para o servidor.|
|RegistrationKey|string|Um GUID que identifica o nó para o serviço de solicitação.|
|ServerURL|string|O URL do servidor de configuração.|
|ProxyURL*|string|O URL de proxy http para utilizar ao comunicar com o serviço de configuração.|
|ProxyCredential*|pscredential|Credencial que deve utilizar para o proxy de http.|

>! Tenha em atenção \* suportado no Windows versões 1809 e posteriores.

Veja um script de exemplo para simplificar a configurar o valor de ResourceRepositoryWeb para nós no local está disponível - [metaconfigurations geração DSC](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Para definir um servidor de recurso baseado em SMB, crie uma **ResourceRepositoryShare** bloco.
**ResourceRepositoryShare** define as propriedades seguintes.

|Propriedade|Tipo|Descrição|
|---|---|---|
|Credencial|MSFT_Credential|A credencial utilizada para autenticar para a partilha SMB. Para obter um exemplo de transmitir as credenciais, consulte [como configurar um servidor de solicitação SMB de DSC](../pull-server/pullServerSMB.md)|
|SourcePath|string|O caminho da partilha SMB.|

## <a name="report-server-blocks"></a>Blocos do servidor de relatório

Para definir um servidor de relatórios, crie uma **ReportServerWeb** bloco.
A função de servidor de relatório não é compatível com o serviço de solicitação SMB com base.
**ReportServerWeb** define as propriedades seguintes.

|Propriedade|Tipo|Descrição|
|---|---|---|
|AllowUnsecureConnection|Bool|Defina como **$TRUE** para permitir ligações a partir do nó para o servidor sem autenticação. Defina como **$FALSE** para exigir autenticação.|
|CertificateID|string|O thumbprint de um certificado utilizado para autenticar para o servidor.|
|RegistrationKey|string|Um GUID que identifica o nó para o serviço de solicitação.|
|ServerURL|string|O URL do servidor de configuração.|
|ProxyURL*|string|O URL de proxy http para utilizar ao comunicar com o serviço de configuração.|
|ProxyCredential*|pscredential|Credencial que deve utilizar para o proxy de http.|

>! Tenha em atenção \* suportado no Windows versões 1809 e posteriores.

Veja um script de exemplo para simplificar a configurar o valor de ReportServerWeb para nós no local está disponível - [metaconfigurations geração DSC](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Configurações parciais

Para definir uma configuração parcial, crie uma **PartialConfiguration** bloco.
Para obter mais informações sobre configurações parciais, consulte [configurações de DSC parcial](../pull-server/partialConfigs.md).
**PartialConfiguration** define as propriedades seguintes.

|Propriedade|Tipo|Descrição|
|---|---|---|
|ConfigurationSource|string[]|Uma matriz de nomes dos servidores de configuração, definidos anteriormente no **ConfigurationRepositoryWeb** e **ConfigurationRepositoryShare** blocos, onde a configuração parcial é extraída de um.|
|DependsOn|Cadeia de caracteres{}|Uma lista de nomes de outras configurações que devem ser concluídas antes desta configuração parcial é aplicada.|
|Descrição|string|Texto utilizado para descrever a configuração parcial.|
|ExclusiveResources|string[]|Um conjunto de recursos exclusivos para esta configuração parcial.|
|RefreshMode|string|Especifica como o LCM chega esta configuração parcial. Os valores possíveis são __"Desativado"__, __"Push"__, e __"Puxar"__. <ul><li>__Desativado__: Esta configuração parcial está desativada.</li><li> __Push__: A configuração parcial é emitida para o nó ao chamar o [Publish-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet. Depois de todas as configurações de parciais para o nó são emitidos via push ou obtidas a partir de um serviço, a configuração pode ser iniciada ao chamar `Start-DscConfiguration –UseExisting`. Este é o valor predefinido.</li><li>__Extrair:__ O nó está configurado para verificar regularmente para configuração parcial de um serviço de solicitação. Se esta propriedade estiver definida como __Pull__, tem de especificar um serviço pull de num __ConfigurationSource__ propriedade. Para obter mais informações sobre o serviço pull de automatização do Azure, consulte [descrição geral do Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|string[]|Uma matriz dos nomes dos servidores de recursos para transferir os recursos necessários para esta configuração parcial. Esses nomes têm de fazer referência a pontos finais de serviço definidos anteriormente no **ResourceRepositoryWeb** e **ResourceRepositoryShare** blocos.|

__Nota:__ configurações parciais são suportadas com DSC de automatização do Azure, mas apenas uma configuração pode ser obtida a partir de cada conta de automatização por nó.

## <a name="see-also"></a>Veja Também

### <a name="concepts"></a>Conceitos
[Desired State Configuration descrição-geral](../overview/overview.md)

[Introdução ao DSC de automatização do Azure](https://docs.microsoft.com/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Outros Recursos

[Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)

[Como configurar um cliente de solicitação com nomes de configuração](../pull-server/pullClientConfigNames.md)
