---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Configurar o Gestor de configuração de Local em versões anteriores do Windows PowerShell
ms.openlocfilehash: cea32c9aa8144bc52f3d44f2ad852f577f6a5e6d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055313"
---
# <a name="configuring-the-local-configuration-manager-in-previous-versions-of-windows-powershell"></a>Configurar o Gestor de configuração de Local em versões anteriores do Windows PowerShell

>Aplica-se a: Windows PowerShell 4.0

**Para informações relacionadas ao Windows PowerShell 5.0 ou posterior, consulte [configurar o Gestor de configuração Local](metaConfig.md).**

Gestor de configuração local é o mecanismo do Windows PowerShell Desired State Configuration (DSC).
Ele é executado em todos os nós de destino e, é responsável por chamar os recursos de configuração que estão incluídos num script de configuração de DSC.
Este tópico lista as propriedades do Gestor de configuração do Local e descreve como modificar as definições do Gestor de configuração Local num nó de destino.

## <a name="local-configuration-manager-properties"></a>Propriedades do Gestor de configuração local

A seguinte lista as propriedades do Gestor de configuração Local que pode definir ou obter.

- **AllowModuleOverwrite**: Controla se as novas configurações transferidas do serviço de configuração podem substituir os antigos no nó de destino. Os valores possíveis são True e False.
- **CertificateID**: O thumbprint de um certificado utilizado para proteger as credenciais transmitidas numa configuração. Para obter mais informações, consulte [pretendem proteger as credenciais no Windows PowerShell Desired State Configuration?](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/).
- **ConfigurationID**: Indica um GUID que é utilizado para obter um arquivo de configuração específica de um serviço de solicitação. O GUID garante que o ficheiro de configuração correto é acessado.
- **ConfigurationMode**: Especifica como o Gestor de configuração de Local, na verdade, aplica-se a configuração para os nós de destino. Ele pode ter os seguintes valores:
  - **ApplyOnly**: Com esta opção, DSC aplica-se a configuração e não faz nada além disso, a menos que seja detetada uma nova configuração, ou por enviar uma nova configuração diretamente para o destino de nó ou se estiver a ligar a um serviço de solicitação e DSC Deteta uma nova configuração quando ele verifica-se com o serviço de solicitação. Se a configuração do nó de destino drifts, foi efetuada nenhuma ação.
  - **ApplyAndMonitor**: Com esta opção (que é o padrão), DSC se aplica a qualquer novas configurações, seja enviado por diretamente para o nó de destino ou detetados num serviço pull. Por esse motivo, se a configuração do nó de destino drifts do arquivo de configuração, o DSC relatórios discrepância nos registos. Para obter mais informações sobre o registo DSC, veja [utilizar registos de eventos para diagnosticar erros em Desired State Configuration do](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
  - **ApplyAndAutoCorrect**: Com esta opção, DSC aplica-se quaisquer novas configurações, seja enviado por diretamente para o nó de destino ou detetados num serviço pull. Por esse motivo, se a configuração do nó de destino drifts do arquivo de configuração, DSC relatórios discrepância nos registos e, em seguida, tenta ajustar a configuração do nó de destino para colocar em conformidade com o ficheiro de configuração.
- **ConfigurationModeFrequencyMins**: Representa a frequência (em minutos) em que o aplicativo em segundo plano do DSC tenta implementar a configuração atual no nó de destino. O valor predefinido é 15. Este valor pode ser definido em conjunto com RefreshMode. Quando RefreshMode está definida como PULL, o nó de destino contacta o serviço de configuração num intervalo definido por RefreshFrequencyMins e transfere a configuração atual. Independentemente do valor de RefreshMode no intervalo definido por ConfigurationModeFrequencyMins, o mecanismo de consistência aplica-se a configuração mais recente que foi transferida para o nó de destino. RefreshFrequencyMins deve ser definido como um número inteiro múltiplo de ConfigurationModeFrequencyMins.
- **Credencial**: Indica as credenciais (tal como acontece com Get-Credential) necessárias para aceder a recursos remotos, tais como contactar o serviço de configuração.
- **DownloadManagerCustomData**: Representa uma matriz que contém dados personalizados específicos para o Gestor de transferências.
- **DownloadManagerName**: Indica o nome da configuração e o Gestor de transferências do módulo.
- **RebootNodeIfNeeded**: Defina esta opção como `$true` para permitir que os recursos para reiniciar o nó utilizando o `$global:DSCMachineStatus` sinalizador. Caso contrário, terá de reiniciar manualmente o nó para qualquer configuração que requer ele. O valor predefinido é `$false`. Para utilizar esta definição quando uma condição de reinicialização é elaborada por algo que não seja o DSC (por exemplo, o programa de instalação do Windows), combinar esta definição com o [xPendingReboot](https://github.com/powershell/xpendingreboot) módulo.
- **RefreshFrequencyMins**: Utilizado quando tiver definido um serviço pull. Representa a frequência (em minutos) em que o Gestor de configuração Local entra em contacto com um serviço pull para transferir a configuração atual. Este valor pode ser definido em conjunto com ConfigurationModeFrequencyMins. Quando RefreshMode está definida como PULL, o nó de destino contacta o serviço de solicitação num intervalo definido por RefreshFrequencyMins e transfere a configuração atual. No intervalo definido por ConfigurationModeFrequencyMins, o mecanismo de consistência, em seguida, aplica a configuração mais recente que foi transferida para o nó de destino. Se RefreshFrequencyMins não estiver definido como um número inteiro múltiplo de ConfigurationModeFrequencyMins, o sistema será Arredonda-lo. O valor predefinido é 30.
- **RefreshMode**: Os valores possíveis são **Push** (predefinição) e **extrair**. A configuração de "push", tem de colocar um ficheiro de configuração em cada nó de destino, utilizando qualquer computador cliente. No modo de "pull", tem de configurar um serviço pull para o Gestor de configuração Local contactar e acessar os arquivos de configuração.

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

### <a name="example-of-updating-local-configuration-manager-settings"></a>Exemplo de a atualizar as definições do Gestor de configuração Local

Pode atualizar as definições do Gestor de configuração Local de um nó de destino, incluindo uma **LocalConfigurationManager** bloquear dentro do bloco de nó num script de configuração, conforme mostrado no exemplo a seguir.

```powershell
Configuration ExampleConfig
{
    Node “Server001”
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullService/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"
```

Executar o script no exemplo anterior, gera um ficheiro MOF que especifica e armazena as definições pretendidas.
Para aplicar as definições, pode utilizar o **Set-dsclocalconfigurationmanager para** cmdlet, conforme mostrado no exemplo a seguir.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> [!NOTE]
> Para o **caminho** parâmetro, tem de especificar o mesmo caminho que especificou para o **OutputPath** parâmetro quando a configuração no exemplo anterior é invocado.

Para ver as definições do Gestor de configuração Local atual, pode utilizar o **Get-dsclocalconfigurationmanager para** cmdlet.
Se invocar este cmdlet sem parâmetros, por padrão ele irá obter as definições do Gestor de configuração Local para o nó no qual executá-lo.
Para especificar outro nó, utilize o **CimSession** parâmetro com este cmdlet.
