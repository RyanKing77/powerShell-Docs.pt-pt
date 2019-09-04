---
ms.date: 12/12/2018
keywords: DSC, PowerShell, configuração, instalação
title: Configurando o Configuration Manager local
ms.openlocfilehash: 42544036d87fcea3189fd6d2e55579fe87f137e1
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215381"
---
# <a name="configuring-the-local-configuration-manager"></a>Configurando o Configuration Manager local

> Aplica-se a: Windows PowerShell 5,0

O Configuration Manager local (LCM) é o mecanismo da DSC (configuração de estado desejado).
O LCM é executado em cada nó de destino e é responsável pela análise e pela ação de configurações que são enviadas para o nó.
Ele também é responsável por vários outros aspectos do DSC, incluindo o seguinte.

- Determinando o modo de atualização (Push ou pull).
- Especificar a frequência com que um nó efetua pull e reage às configurações.
- Associando o nó ao serviço de pull.
- Especificando configurações parciais.

Você usa um tipo especial de configuração para configurar o LCM para especificar cada um desses comportamentos.
As seções a seguir descrevem como configurar o LCM.

O Windows PowerShell 5,0 introduziu novas configurações para o gerenciamento de Configuration Manager locais.
Para obter informações sobre como configurar o LCM no Windows PowerShell 4,0, consulte Configurando [o Configuration Manager local em versões anteriores do Windows PowerShell](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Gravando e agindo uma configuração do LCM

Para configurar o LCM, você cria e executa um tipo especial de configuração que aplica as configurações do LCM.
Para especificar uma configuração do LCM, use o atributo DscLocalConfigurationManager.
O seguinte mostra uma configuração simples que define o LCM para o modo de push.

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

O processo de aplicação de configurações ao LCM é semelhante à aplicação de uma configuração DSC.
Você criará uma configuração do LCM, a compilará em um arquivo MOF e a aplicará ao nó.
Ao contrário das configurações de DSC, você não aplicar uma configuração do LCM chamando o cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .
Em vez disso, chame [set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager), fornecendo o caminho para o MOF de configuração do LCM como um parâmetro.
Depois de aplicar a configuração do LCM, você pode ver as propriedades do LCM chamando o cmdlet [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) .

Uma configuração do LCM pode conter blocos somente para um conjunto limitado de recursos.
No exemplo anterior, o único recurso chamado é **configurações**.
Os outros recursos disponíveis são:

* **ConfigurationRepositoryWeb**: especifica um serviço de pull de http para configurações.
* **ConfigurationRepositoryShare**: especifica um compartilhamento SMB para configurações.
* **ResourceRepositoryWeb**: especifica um serviço de pull de http para módulos.
* **ResourceRepositoryShare**: especifica um compartilhamento SMB para módulos.
* **ReportServerWeb**: especifica um serviço de pull de http para o qual os relatórios são enviados.
* **PartialConfiguration**: fornece dados para habilitar configurações parciais.

## <a name="basic-settings"></a>Definições básicas

Além de especificar pontos de extremidade de serviço de pull/caminhos e configurações parciais, todas as propriedades do LCM são configuradas em um bloco de **configurações** .
As propriedades a seguir estão disponíveis em um bloco de **configurações** .

|  Propriedade  |  Tipo  |  Descrição   |
|----------- |------- |--------------- |
| ActionAfterReboot| string| Especifica o que acontece após uma reinicialização durante a aplicação de uma configuração. Os valores possíveis são __"ContinueConfiguration"__ e __"StopConfiguration"__ . <ul><li> __ContinueConfiguration__: Continue aplicando a configuração atual após a reinicialização do computador. Esse é o valor padrão</li><li>__StopConfiguration__: Pare a configuração atual após a reinicialização do computador.</li></ul>|
| AllowModuleOverwrite| bool| __$True__ se novas configurações baixadas do serviço de pull tiverem permissão para substituir as antigas no nó de destino. Caso contrário, $FALSE.|
| CertificateID| string| A impressão digital de um certificado usado para proteger as credenciais passadas em uma configuração. Para obter mais informações, consulte [quer proteger credenciais na configuração de estado desejado do Windows PowerShell](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)?. <br> __Observação:__ isso é gerenciado automaticamente se estiver usando o serviço de pull DSC de automação do Azure.|
| ConfigurationDownloadManagers| CimInstance[]| Obsoleto. Use os blocos __ConfigurationRepositoryWeb__ e __ConfigurationRepositoryShare__ para definir pontos de extremidade de serviço de pull de configuração.|
| ConfigurationID| string| Para compatibilidade com versões anteriores de serviço de pull. Um GUID que identifica o arquivo de configuração a ser obtido de um serviço de pull. O nó efetuará pull das configurações no serviço de pull se o nome do MOF de configuração for chamado ConfigurationId. mof.<br> __Nota:__ Se você definir essa propriedade, o registro do nó com um serviço de pull usando __RegistrationKey__ não funcionará. Para obter mais informações, consulte Configurando [um cliente de pull com nomes de configuração](../pull-server/pullClientConfigNames.md).|
| ConfigurationMode| string | Especifica como o LCM realmente aplica a configuração aos nós de destino. Os valores possíveis são __"ApplyOnly"__ , __"ApplyAndMonitor"__ e __"ApplyAndAutoCorrect"__ . <ul><li>__ApplyOnly__: A DSC aplica a configuração e não faz nada além disso, a menos que uma nova configuração seja enviada por push para o nó de destino ou quando uma nova configuração for retirada de um serviço. Após a aplicação inicial de uma nova configuração, a DSC não verifica se há descompasso de um Estado previamente configurado. Observe que o DSC tentará aplicar a configuração até que ela seja bem-sucedida antes de __ApplyOnly__ entrar em vigor. </li><li> __ApplyAndMonitor__: Este é o valor predefinido. O LCM aplica quaisquer novas configurações. Após a aplicação inicial de uma nova configuração, se o nó de destino se desconectar do estado desejado, a DSC relatará a discrepância nos logs. Observe que o DSC tentará aplicar a configuração até que ela seja bem-sucedida antes de __ApplyAndMonitor__ entrar em vigor.</li><li>__ApplyAndAutoCorrect__: A DSC aplica quaisquer novas configurações. Após a aplicação inicial de uma nova configuração, se o nó de destino se desconectar do estado desejado, o DSC relatará a discrepância nos logs e reaplicará a configuração atual.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| Com que frequência, em minutos, a configuração atual é verificada e aplicada. Essa propriedade será ignorada se a propriedade ConfigurationMode estiver definida como ApplyOnly. O valor padrão é 15.|
| DebugMode| string| Os valores possíveis são __None__, __ForceModuleImport__e __All__. <ul><li>Defina como __nenhum__ para usar os recursos armazenados em cache. Esse é o padrão e deve ser usado em cenários de produção.</li><li>A configuração de __ForceModuleImport__faz com que o LCM Recarregue todos os módulos de recursos de DSC, mesmo que eles tenham sido carregados e armazenados em cache anteriormente. Isso afeta o desempenho das operações de DSC à medida que cada módulo é recarregado em uso. Normalmente, você usaria esse valor durante a depuração de um recurso</li><li>Nesta versão, __tudo__ é o mesmo que __ForceModuleImport__</li></ul> |
| RebootNodeIfNeeded| bool| Defina como `$true` para permitir que os recursos reiniciem o nó `$global:DSCMachineStatus` usando o sinalizador. Caso contrário, você precisará reinicializar manualmente o nó para qualquer configuração que o exija. O valor predefinido é `$false`. Para usar essa configuração quando uma condição de reinicialização for imposta por algo diferente de DSC (como Windows Installer), combine essa configuração com o módulo [xPendingReboot](https://github.com/powershell/xpendingreboot) .|
| RefreshMode| string| Especifica como o LCM Obtém as configurações. Os valores possíveis são __"Disabled"__ , __"Push"__ e __"pull"__ . <ul><li>__Desabilitado__: As configurações DSC estão desabilitadas para este nó.</li><li> __Enviar por push__: As configurações são iniciadas chamando o cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) . A configuração é aplicada imediatamente ao nó. Este é o valor predefinido.</li><li>__Recebimento__ O nó é configurado para verificar regularmente as configurações de um serviço de pull ou caminho SMB. Se essa propriedade for definida como __pull__, você deverá especificar um caminho http (serviço) ou SMB (compartilhamento) em um bloco __ConfigurationRepositoryWeb__ ou __ConfigurationRepositoryShare__ .</li></ul>|
| RefreshFrequencyMins| Uint32| O intervalo de tempo, em minutos, no qual o LCM verifica um serviço de pull para obter configurações atualizadas. Esse valor será ignorado se o LCM não estiver configurado no modo de pull. O valor predefinido é 30.|
| ReportManagers| CimInstance[]| Obsoleto. Use blocos __ReportServerWeb__ para definir um ponto de extremidade para enviar dados de relatório para um serviço de pull.|
| ResourceModuleManagers| CimInstance[]| Obsoleto. Use blocos __ResourceRepositoryWeb__ e __ResourceRepositoryShare__ para definir pontos de extremidade http do serviço de pull ou caminhos SMB, respectivamente.|
| PartialConfigurations| CimInstance| Não implementado. Não utilizar.|
| StatusRetentionTimeInDays | UInt32| O número de dias que o LCM mantém o status da configuração atual.|

> [!NOTE]
> O LCM inicia o ciclo de **ConfigurationModeFrequencyMins** com base em:
>
> - Uma nova metaconfig é aplicada usando`Set-DscLocalConfigurationManager`
> - Uma reinicialização do computador
>
> Para qualquer condição em que o processo de timer passa por uma falha, ela será detectada em 30 segundos e o ciclo será reiniciado.
> Uma operação simultânea pode atrasar o ciclo de ser iniciado, se a duração dessa operação exceder a frequência de ciclo configurada, o próximo temporizador não será iniciado.
>
> Por exemplo, a metaconfig é configurada com uma frequência de pull de 15 minutos e um pull ocorre em T1.  O nó não termina o trabalho por 16 minutos.  O primeiro ciclo de 15 minutos é ignorado e o próximo pull ocorrerá em T1 + 15 + 15.

## <a name="pull-service"></a>Serviço de pull

A configuração do LCM dá suporte à definição dos seguintes tipos de pontos de extremidade de serviço de pull:

- **Servidor de configuração**: Um repositório para configurações DSC. Defina os servidores de configuração usando o **ConfigurationRepositoryWeb** (para servidores baseados na Web) e os blocos **ConfigurationRepositoryShare** (para servidores baseados em SMB).
- **Servidor de recursos**: Um repositório para recursos de DSC, empacotados como módulos do PowerShell. Defina os servidores de recursos usando o **ResourceRepositoryWeb** (para servidores baseados na Web) e os blocos **ResourceRepositoryShare** (para servidores baseados em SMB).
- **Servidor de relatório**: Um serviço para o qual a DSC envia dados de relatório. Defina servidores de relatório usando blocos de **ReportServerWeb** . Um servidor de relatório deve ser um serviço Web.

Para obter mais detalhes sobre o serviço de pull, consulte [serviço de pull de configuração de estado desejado](../pull-server/pullServer.md).

## <a name="configuration-server-blocks"></a>Blocos do servidor de configuração

Para definir um servidor de configuração baseado na Web, você cria um bloco **ConfigurationRepositoryWeb** .
Um **ConfigurationRepositoryWeb** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---|
|AllowUnsecureConnection|bool|Defina como **$true** para permitir conexões do nó para o servidor sem autenticação. Defina como **$false** para exigir autenticação.|
|CertificateID|string|A impressão digital de um certificado usado para autenticar no servidor.|
|ConfigurationNames|Cadeia de caracteres []|Uma matriz de nomes de configurações a serem extraídas pelo nó de destino. Eles serão usados somente se o nó estiver registrado com o serviço de pull usando um **RegistrationKey**. Para obter mais informações, consulte Configurando [um cliente de pull com nomes de configuração](../pull-server/pullClientConfigNames.md).|
|RegistrationKey|string|Um GUID que registra o nó com o serviço de pull. Para obter mais informações, consulte Configurando [um cliente de pull com nomes de configuração](../pull-server/pullClientConfigNames.md).|
|ServerURL|string|A URL do serviço de configuração.|
|ProxyURL|string|A URL do proxy http a ser usada ao se comunicar com o serviço de configuração.|
|ProxyCredential|PSCredential|Credencial a ser usada para o proxy http.|

> [!NOTE]
> * Com suporte no Windows versões 1809 e posteriores.

Um script de exemplo para simplificar a configuração do valor de ConfigurationRepositoryWeb para nós locais está disponível-consulte gerando metaconfigurações de [DSC](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Para definir um servidor de configuração baseado em SMB, você cria um bloco **ConfigurationRepositoryShare** .
Um **ConfigurationRepositoryShare** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---|
|Provedores|MSFT_Credential|A credencial usada para autenticar o compartilhamento SMB.|
|SourcePath|string|O caminho do compartilhamento SMB.|

## <a name="resource-server-blocks"></a>Blocos do servidor de recursos

Para definir um servidor de recursos baseado na Web, você cria um bloco **ResourceRepositoryWeb** .
Um **ResourceRepositoryWeb** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---|
|AllowUnsecureConnection|bool|Defina como **$true** para permitir conexões do nó para o servidor sem autenticação. Defina como **$false** para exigir autenticação.|
|CertificateID|string|A impressão digital de um certificado usado para autenticar no servidor.|
|RegistrationKey|string|Um GUID que identifica o nó para o serviço de pull.|
|ServerURL|string|A URL do servidor de configuração.|
|ProxyURL|string|A URL do proxy http a ser usada ao se comunicar com o serviço de configuração.|
|ProxyCredential|PSCredential|Credencial a ser usada para o proxy http.|

> [!NOTE]
> * Com suporte no Windows versões 1809 e posteriores.

Um script de exemplo para simplificar a configuração do valor de ResourceRepositoryWeb para nós locais está disponível-consulte gerando metaconfigurações de [DSC](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Para definir um servidor de recursos baseado em SMB, você cria um bloco **ResourceRepositoryShare** .
**ResourceRepositoryShare** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---|
|Provedores|MSFT_Credential|A credencial usada para autenticar o compartilhamento SMB. Para obter um exemplo de como transmitir credenciais, consulte Configurando [um servidor de pull de SMB de DSC](../pull-server/pullServerSMB.md)|
|SourcePath|string|O caminho do compartilhamento SMB.|

## <a name="report-server-blocks"></a>Blocos do servidor de relatório

Para definir um servidor de relatório, você cria um bloco **ReportServerWeb** .
A função do servidor de relatório não é compatível com o serviço de pull baseado em SMB.
**ReportServerWeb** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---|
|AllowUnsecureConnection|bool|Defina como **$true** para permitir conexões do nó para o servidor sem autenticação. Defina como **$false** para exigir autenticação.|
|CertificateID|string|A impressão digital de um certificado usado para autenticar no servidor.|
|RegistrationKey|string|Um GUID que identifica o nó para o serviço de pull.|
|ServerURL|string|A URL do servidor de configuração.|
|ProxyURL|string|A URL do proxy http a ser usada ao se comunicar com o serviço de configuração.|
|ProxyCredential|PSCredential|Credencial a ser usada para o proxy http.|

> [!NOTE]
> * Com suporte no Windows versões 1809 e posteriores.

Um script de exemplo para simplificar a configuração do valor de ReportServerWeb para nós locais está disponível-consulte gerando metaconfigurações de [DSC](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Configurações parciais

Para definir uma configuração parcial, você cria um bloco **PartialConfiguration** .
Para obter mais informações sobre configurações parciais, consulte [configurações parciais de DSC](../pull-server/partialConfigs.md).
**PartialConfiguration** define as propriedades a seguir.

|Propriedade|Tipo|Descrição|
|---|---|---|
|ConfigurationSource|string[]|Uma matriz de nomes de servidores de configuração, definida anteriormente nos blocos **ConfigurationRepositoryWeb** e **ConfigurationRepositoryShare** , onde a configuração parcial é extraída.|
|DependsOn|Strings{}|Uma lista de nomes de outras configurações que devem ser concluídas antes que essa configuração parcial seja aplicada.|
|Descrição|string|Texto usado para descrever a configuração parcial.|
|ExclusiveResources|string[]|Uma matriz de recursos exclusivos para essa configuração parcial.|
|RefreshMode|string|Especifica como o LCM obtém essa configuração parcial. Os valores possíveis são __"Disabled"__ , __"Push"__ e __"pull"__ . <ul><li>__Desabilitado__: Esta configuração parcial está desabilitada.</li><li> __Enviar por push__: A configuração parcial é enviada por push para o nó chamando o cmdlet [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) . Depois que todas as configurações parciais para o nó são enviadas por Push ou extraídas de um serviço, a configuração `Start-DscConfiguration –UseExisting`pode ser iniciada chamando. Este é o valor predefinido.</li><li>__Recebimento__ O nó é configurado para verificar regularmente a configuração parcial de um serviço de pull. Se essa propriedade for definida como __pull__, você deverá especificar um serviço de pull em uma propriedade ConfigurationName. Para obter mais informações sobre o serviço de pull da automação do Azure, consulte [visão geral do azure DSC de automação](https://docs.microsoft.com/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|string[]|Uma matriz dos nomes dos servidores de recursos dos quais baixar os recursos necessários para essa configuração parcial. Esses nomes devem se referir aos pontos de extremidade de serviço definidos anteriormente nos blocos **ResourceRepositoryWeb** e **ResourceRepositoryShare** .|

__Observação:__ há suporte para configurações parciais com o Azure DSC de automação, mas apenas uma configuração pode ser retirada de cada conta de automação por nó.

## <a name="see-also"></a>Veja Também

### <a name="concepts"></a>Conceitos
[Visão geral da configuração de estado desejado](../overview/overview.md)

[Introdução ao DSC de Automação do Azure](https://docs.microsoft.com/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Outros Recursos

[Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)

[Configurando um cliente de pull com nomes de configuração](../pull-server/pullClientConfigNames.md)
