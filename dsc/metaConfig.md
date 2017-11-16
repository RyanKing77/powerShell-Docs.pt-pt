---
ms.date: 2017-10-11
author: eslesar;mgreenegit
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Configurar o Gestor de configuração Local"
ms.openlocfilehash: 98470f45ca7c11ea63d68da7dec9fcd844f06192
ms.sourcegitcommit: 9a5da3f739b1eebb81ede58bd4fc8037bad87224
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2017
---
# <a name="configuring-the-local-configuration-manager"></a>Configurar o Gestor de configuração Local

> Aplica-se a: O Windows PowerShell 5.0

O Gestor de configuração Local (MMC) é o motor de configuração de estado pretendido (DSC).
O MMC é executada em cada nó de destino e é responsável pela análise e enacting configurações que são enviadas para o nó.
Também é responsável por um número de outros aspetos do DSC, incluindo o seguinte.

- Determinar o modo de atualização (push ou pull).
- Especificar com que frequência um nó obtém e enacts configurações.
- Associar o nó com o serviço de extração.
- Especificar configurações parciais.

Utilize um tipo especial de configuração para configurar o MMC para especificar cada um dos seguintes comportamentos.
As secções seguintes descrevem como configurar o MMC.

> **Tenha em atenção**: Este tópico aplica-se para MMC introduzido no Windows PowerShell 5.0.
Para obter informações sobre como configurar o MMC no Windows PowerShell 4.0, consulte [Windows PowerShell 4.0 pretendido estado de configuração Local do Configuration Manager](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Escrever e enacting uma configuração de MMC

Para configurar o MMC, pode criar e executar um tipo especial de configuração aplica-se as definições do MMC.
Para especificar uma configuração de MMC, pode utilizar o atributo DscLocalConfigurationManager.
O seguinte mostra uma configuração simple que define o MMC para o modo de push.

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

O processo de aplicar as definições para o MMC é semelhante ao aplicar uma configuração de DSC.
Irá criar uma configuração de MMC, compilá-la para um ficheiro MOF e aplicá-la para o nó.
Ao contrário das configurações de DSC não enact uma configuração de MMC ao chamar o [início DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.
Em vez disso, chame [conjunto DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx), fornecendo o caminho para a configuração de MMC MOF como parâmetro.
Depois de enact a configuração de MMC, pode ver as propriedades do MMC ao chamar o [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet.

Uma configuração de MMC pode conter blocos apenas para um conjunto limitado de recursos.
No exemplo anterior, é o recurso apenas chamado **definições**.
Os outros recursos disponíveis são:

* **ConfigurationRepositoryWeb**: Especifica um serviço de solicitação HTTP para as configurações.
* **ConfigurationRepositoryShare**: Especifica uma partilha SMB para configurações.
* **ResourceRepositoryWeb**: Especifica um serviço de solicitação HTTP de módulos.
* **ResourceRepositoryShare**: Especifica uma partilha SMB para módulos.
* **ReportServerWeb**: Especifica um serviço de solicitação HTTP para que os relatórios são enviados.
* **PartialConfiguration**: fornece dados para ativar a configurações parciais.

## <a name="basic-settings"></a>Definições básicas

Além de especificar pontos finais de serviço de solicitação/caminhos e configurações parciais, todas as propriedades do MMC são configuradas num **definições** bloco.
As seguintes propriedades estão disponíveis num **definições** bloco.

|  Propriedade  |  Tipo  |  Descrição   |
|----------- |------- |--------------- |
| ActionAfterReboot| cadeia| Especifica o que acontece após um reinício durante a aplicação de uma configuração. Os valores possíveis são __"ContinueConfiguration"__ e __"StopConfiguration"__. <ul><li> __ContinueConfiguration__: continuar a aplicar a configuração atual após o reinício do computador. Este é o falue predefinido</li><li>__StopConfiguration__: parar a configuração atual após o reinício do computador.</li></ul>|
| AllowModuleOverwrite| bool| __$TRUE__ se as novas configurações transferidas a partir do serviço de extração estão autorizadas a substituir as antigas no nó de destino. Caso contrário, $FALSE.|
| CertificateID| cadeia| O thumbprint de um certificado utilizado para proteger as credenciais transmitidas numa configuração. Para obter mais informações consulte [pretende proteger credenciais na configuração de estado pretendido do Windows PowerShell](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)?. <br> __Nota:__ é gerida automaticamente se utilizar o serviço de solicitação do Automation DSC do Azure.|
| ConfigurationDownloadManagers| CimInstance []| Obsoleto. Utilize __ConfigurationRepositoryWeb__ e __ConfigurationRepositoryShare__ pontos finais de serviço de blocos para definir a solicitação de configuração.|
| ConfigurationID| cadeia| Para efeitos de compatibilidade com mais antiga solicitação serviço versões. Um GUID que identifica o ficheiro de configuração a obter a partir de um serviço de extração. O nó irá solicitar configurações do serviço de solicitação, se o nome da configuração MOF denominado ConfigurationID.mof.<br> __Nota:__ se definir esta propriedade, registar o nó de um serviço de solicitação utilizando __RegistrationKey__ não funciona. Para obter mais informações, consulte [configurar um cliente de extração com nomes de configuração](pullClientConfigNames.md).|
| ConfigurationMode| cadeia | Especifica a forma como o MMC, na verdade, aplica-se a configuração para os nós de destino. Os valores possíveis são __"ApplyOnly"__,__"ApplyandMonitior"__, e __"ApplyandAutoCorrect"__. <ul><li>__ApplyOnly__: aplica-se a configuração de DSC e faz nada adicional a menos que é feito o Push de uma nova configuração para o nó de destino ou quando uma nova configuração é retirada de um serviço. Após a aplicação inicial de uma nova configuração, DSC não verificar que se desviam de um estado anteriormente configurado. Tenha em atenção que o DSC tentará aplicar a configuração até ter êxito antes de __ApplyOnly__ entra em vigor. </li><li> __ApplyAndMonitor__: Este é o valor predefinido. O MMC aplica-se as configurações de novo. Após a aplicação inicial de uma nova configuração, se o nó de destino drifts do estado pretendido, DSC relatórios discrepância nos registos. Tenha em atenção que o DSC tentará aplicar a configuração até ter êxito antes de __ApplyAndMonitor__ entra em vigor.</li><li>__ApplyAndAutoCorrect__: DSC aplica-se as configurações de novo. Após a aplicação inicial de uma nova configuração, se o nó de destino drifts do estado pretendido, DSC relatórios discrepância nos registos e, em seguida, volte aplica-se a configuração atual.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| Frequência, em minutos, a configuração atual é marcada e aplicada. Esta propriedade é ignorada se a propriedade ConfigurationMode estiver definida como ApplyOnly. O valor predefinido é 15.|
| DebugMode| cadeia| Os valores possíveis são __nenhum__, __ForceModuleImport__, e __todos os__. <ul><li>Definido como __nenhum__ a utilização de recursos em cache. Esta é a predefinição e deve ser utilizada em cenários de produção.</li><li>A definição para __ForceModuleImport__, faz com que o MMC para recarregar quaisquer módulos de recursos de DSC, mesmo que tenham sido previamente carregadas e colocadas em cache. Este problema afeta o desempenho das operações de DSC como cada módulo é recarregado em utilização. Normalmente, utilizaria este valor durante a depuração de um recurso</li><li>Nesta versão, __todos os__ é a mesma __ForceModuleImport__</li></ul> |
| RebootNodeIfNeeded| bool| Defina esta opção para __$true__ para reiniciar automaticamente o nó após a uma configuração que necessita de reiniciar o computador é aplicado. Caso contrário, terá de reiniciar o nó para qualquer configuração que obriga manualmente. O valor predefinido é __$false__. Para utilizar esta definição quando uma condição de reinício é enacted por algo diferente de DSC (por exemplo, o Windows Installer), combinar esta definição com a [xPendingReboot](https://github.com/powershell/xpendingreboot) módulo.|
| RefreshMode| cadeia| Especifica a forma como o MMC obtém configurações. Os valores possíveis são __"Desativado"__, __"Push"__, e __"Solicitar"__. <ul><li>__Desativado__: configurações de DSC estão desativadas para este nó.</li><li> __Push__: configurações são iniciadas ao chamar o [início DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet. A configuração é imediatamente aplicada ao nó. Este é o valor predefinido.</li><li>__Solicitação:__ o nó estiver configurado para verificar regularmente para configurações de um serviço de extração ou caminho SMB. Se esta propriedade estiver definida como __solicitar__, tem de especificar um HTTP (serviço) ou o caminho SMB (partilha) num __ConfigurationRepositoryWeb__ ou __ConfigurationRepositoryShare__ bloco.</li></ul>|
| RefreshFrequencyMins| UInt32| O intervalo de tempo, em minutos, no qual o MMC verifica um serviço de extração para obter configurações atualizadas. Este valor é ignorado se a MMC não está configurado no modo de extração. O valor predefinido é 30.|
| ReportManagers| CimInstance []| Obsoleto. Utilize __ReportServerWeb__ blocos para definir um ponto final para enviar dados de relatórios para um serviço de extração.|
| ResourceModuleManagers| CimInstance []| Obsoleto. Utilize __ResourceRepositoryWeb__ e __ResourceRepositoryShare__ blocos para definir a solicitação de serviço pontos finais de HTTP ou caminhos SMB, respetivamente.|
| PartialConfigurations| CimInstance| Não implementado. Não utilizar.|
| StatusRetentionTimeInDays | UInt32| O número de dias que o MMC mantém o estado da configuração atual.|

## <a name="pull-service"></a>Serviço de solicitação

Definições de DSC permite que um nó para serem geridos pelo extrair módulos e configurações e dados de relatórios, de publicação para uma localização remota.
As opções de atuais para o serviço de solicitação incluem:

- Serviço de configuração de estado de Desired de automatização do Azure
- Uma instância de serviço de solicitação em execução no Windows Server
- Uma partilha SMB (não suporta a publicação de dados de relatórios)

Configuração de MMC suporta definir os seguintes tipos de pontos finais do serviço de extração:

- **Servidor de configuração**: um repositório para configurações de DSC. Definir os servidores de configuração utilizando **ConfigurationRepositoryWeb** (para servidores baseada na web) e **ConfigurationRepositoryShare** (para servidores com base em SMB) blocos.
- **Servidor de recurso**: um repositório para recursos de DSC, empacotadas como módulos do PowerShell. Definir os servidores de recursos utilizando **ResourceRepositoryWeb** (para servidores baseada na web) e **ResourceRepositoryShare** (para servidores com base em SMB) blocos.
- **Servidor de relatórios**: um serviço que DSC envia dados de relatório. Definir os servidores de relatório utilizando **ReportServerWeb** blocos. Um servidor de relatórios tem de ser um serviço web.

**A solução recomendada**, e a opção com mais funcionalidades disponíveis, é [Automation DSC do Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).

O serviço do Azure pode gerir nós no local em centros de dados privados ou em nuvens públicas, tais como o Azure e AWS.
Para ambientes privados em que os servidores não é possível ligar diretamente à Internet, considere limitar o tráfego de saída para apenas o intervalo de IP de Azure publicado (consulte [intervalos de IP do Datacenter do Azure](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).

As funcionalidades do serviço online que não estão atualmente disponíveis no serviço de solicitação no Windows Server incluem:
- Todos os dados são encriptados em trânsito e o restante
- Certificados de cliente são criados e geridos automaticamente
- Armazenam segredos para gerir centralmente [palavras-passe/credenciais](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), ou [variáveis](https://docs.microsoft.com/en-us/azure/automation/automation-variables) tais como nomes de servidor ou cadeias de ligação
- Gerir centralmente o nó [configuração MMC](metaConfig.md#basic-settings)
- Atribuir centralmente configurações para nós de cliente
- Configuração de versão é alterada para "grupos canary" para fins de teste antes de atingir a produção
- Gráfico de relatórios
  - Detalhes de estado ao nível de recursos do DSC de granularidade
  - Mensagens de erro verbosas provenientes de máquinas de cliente para resolução de problemas
- [Integração com o Log Analytics do Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) para alertar, tarefas automatizadas, a aplicação Android/iOS para relatórios e alertas

Em alternativa, para obter informações sobre como configurar e utilizar o serviço de solicitação HTTP no Windows Server, consulte [configurar um servidor de solicitação do DSC](pullServer.md).
Volte a ser aconselhado que é uma implementação limitada com as capacidades de apenas básicas de armazenar configurações/módulos e capturar os dados de relatório numa base de dados.

## <a name="configuration-server-blocks"></a>Blocos de servidor de configuração

Para definir um servidor de configuração baseada na web, cria um **ConfigurationRepositoryWeb** bloco.
A **ConfigurationRepositoryWeb** define as propriedades seguintes.

|Propriedade|Tipo|Descrição|
|---|---|---| 
|AllowUnsecureConnection|bool|Definido como **$TRUE** para permitir ligações a partir do nó para o servidor sem autenticação. Definido como **$FALSE** para exigir a autenticação.|
|CertificateID|cadeia|O thumbprint de um certificado utilizado para autenticar para o servidor.|
|ConfigurationNames|String]|Uma matriz de nomes de configurações para ser solicitados pelo nó de destino. Estas são utilizadas apenas se o nó está registado com o serviço de solicitação utilizando um **RegistrationKey**. Para obter mais informações, consulte [configurar um cliente de extração com nomes de configuração](pullClientConfigNames.md).|
|RegistrationKey|cadeia|Um GUID que regista o nó com o serviço de extração. Para obter mais informações, consulte [configurar um cliente de extração com nomes de configuração](pullClientConfigNames.md).|
|ServerURL|cadeia|O URL do serviço de configuração.|

Um script de exemplo para simplificar a configurar o valor de ConfigurationRepositoryWeb para nós no local está disponível - consulte [metaconfigurations gerar DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Para definir um servidor de configuração com base em SMB, crie um **ConfigurationRepositoryShare** bloco.
A **ConfigurationRepositoryShare** define as propriedades seguintes.

|Propriedade|Tipo|Descrição|
|---|---|---|
|credencial|MSFT_Credential|A credencial utilizada para autenticar para a partilha SMB.|
|SourcePath|cadeia|O caminho da partilha do SMB.|

## <a name="resource-server-blocks"></a>Blocos de recursos de servidor

Para definir um servidor de recursos baseados na web, cria um **ResourceRepositoryWeb** bloco.
A **ResourceRepositoryWeb** define as propriedades seguintes.

|Propriedade|Tipo|Descrição|
|---|---|---|
|AllowUnsecureConnection|bool|Definido como **$TRUE** para permitir ligações a partir do nó para o servidor sem autenticação. Definido como **$FALSE** para exigir a autenticação.|
|CertificateID|cadeia|O thumbprint de um certificado utilizado para autenticar para o servidor.|
|RegistrationKey|cadeia|Um GUID que identifica o nó para o serviço de extração.|
|ServerURL|cadeia|O URL do servidor de configuração.|

Um script de exemplo para simplificar a configurar o valor de ResourceRepositoryWeb para nós no local está disponível - consulte [metaconfigurations gerar DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Para definir um servidor de recursos com base em SMB, crie um **ResourceRepositoryShare** bloco.
**ResourceRepositoryShare** define as propriedades seguintes.

|Propriedade|Tipo|Descrição|
|---|---|---|
|credencial|MSFT_Credential|A credencial utilizada para autenticar para a partilha SMB. Para obter um exemplo de transmissão credenciais, consulte [configurar um servidor de solicitação do DSC SMB](pullServerSMB.md)|
|SourcePath|cadeia|O caminho da partilha do SMB.|

## <a name="report-server-blocks"></a>Blocos de servidor de relatórios

Para definir um servidor de relatórios, criar um **ReportServerWeb** bloco.
A função de servidor de relatório não é compatível com o serviço de solicitação do SMB com base.
**ReportServerWeb** define as propriedades seguintes.

|Propriedade|Tipo|Descrição|
|---|---|---|
|AllowUnsecureConnection|bool|Definido como **$TRUE** para permitir ligações a partir do nó para o servidor sem autenticação. Definido como **$FALSE** para exigir a autenticação.|
|CertificateID|cadeia|O thumbprint de um certificado utilizado para autenticar para o servidor.|
|RegistrationKey|cadeia|Um GUID que identifica o nó para o serviço de extração.|
|ServerURL|cadeia|O URL do servidor de configuração.|

Um script de exemplo para simplificar a configurar o valor de ReportServerWeb para nós no local está disponível - consulte [metaconfigurations gerar DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Configurações parciais

Para definir uma configuração parcial, crie um **PartialConfiguration** bloco.
Para obter mais informações sobre as configurações parciais, consulte [configurações de DSC parcial](partialConfigs.md).
**PartialConfiguration** define as propriedades seguintes.

|Propriedade|Tipo|Descrição|
|---|---|---| 
|ConfigurationSource|String]|Uma matriz de nomes de servidores de configuração, anteriormente definidas na **ConfigurationRepositoryWeb** e **ConfigurationRepositoryShare** blocos, onde a configuração parcial é retirada da.|
|dependsOn|cadeia {}|Uma lista de nomes de outras configurações que têm de ser concluídas antes desta configuração parcial é aplicada.|
|Descrição|cadeia|Texto utilizado para descrever a configuração parcial.|
|ExclusiveResources|String]|Uma matriz de recursos exclusivas para esta configuração parcial.|
|RefreshMode|cadeia|Especifica a forma como o MMC obtém esta configuração parcial. Os valores possíveis são __"Desativado"__, __"Push"__, e __"Solicitar"__. <ul><li>__Desativado__: esta configuração parcial está desativada.</li><li> __Push__: A configuração parcial é enviada para o nó ao chamar o [publicar DscConfiguration](https://technet.microsoft.com/en-us/library/mt517875.aspx) cmdlet. Depois de todas as configurações parciais para o nó são enviadas por push ou solicitadas a partir de um serviço, a configuração pode ser iniciada ao chamar `Start-DscConfiguration –UseExisting`. Este é o valor predefinido.</li><li>__Solicitação:__ o nó está configurado para verificar regularmente parcial configuração a partir de um serviço de extração. Se esta propriedade estiver definida como __solicitação__, tem de especificar um serviço de solicitação num __ConfigurationSource__ propriedade. Para obter mais informações sobre o serviço de solicitação de automatização do Azure, consulte [descrição geral do Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|String]|Uma matriz dos nomes dos servidores de recursos a partir das quais transferir os recursos necessários para esta configuração parcial. Estes nomes tem de referenciar pontos finais de serviço definidos anteriormente no **ResourceRepositoryWeb** e **ResourceRepositoryShare** blocos.|

__Nota:__ parciais configurações são suportadas com o Automation DSC do Azure, mas pode ser solicitada apenas uma configuração de cada conta de automatização por nó.

## <a name="see-also"></a>Consulte Também 

### <a name="concepts"></a>Conceitos
[Descrição geral da configuração do Estado de pretendida](overview.md)
 
[Introdução ao Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Outros Recursos

[Conjunto DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx)

[Configurar um cliente de extração com nomes de configuração](pullClientConfigNames.md)
