---
ms.date: 2017-10-12
author: eslesar;mgreenegit
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Windows PowerShell 4.0 pretendido estado configuração Local do Configuration Manager (MMC)"
ms.openlocfilehash: d46862f9ea0f8e3206c596af7232160fc4a97939
ms.sourcegitcommit: 9a5da3f739b1eebb81ede58bd4fc8037bad87224
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2017
---
# <a name="windows-powershell-40-desired-state-configuration-local-configuration-manager-lcm"></a>Windows PowerShell 4.0 pretendido estado configuração Local do Configuration Manager (MMC)

>Aplica-se a: O Windows PowerShell 4.0

Gestor de configuração locais é o motor de configuração de estado pretendido do Windows PowerShell (DSC).
Este é executado em todos os nós de destino e é responsável pela chamar os recursos de configuração que estão incluídos num script de configuração de DSC.
Este tópico lista as propriedades do Local do Configuration Manager e descreve como pode modificar as definições do Gestor de configuração locais num nó de destino.

## <a name="local-configuration-manager-properties"></a>Propriedades do Gestor de configuração local

Segue-se as propriedades do Gestor de configuração locais que pode definir ou obter.

- **AllowModuleOverwrite**: controla se as novas configurações transferidas a partir do serviço de configuração estão autorizados a substituir as antigas no nó de destino. Os valores possíveis são True e False.
- **CertificateID**: O thumbprint de um certificado utilizado para proteger as credenciais transmitidas numa configuração. Para obter mais informações consulte [pretende proteger credenciais na configuração de estado pretendido do Windows PowerShell?](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx).
- **ConfigurationID**: indica um GUID que é utilizado para obter um ficheiro de configuração específica de um serviço de extração. O GUID assegura que o ficheiro de configuração correto é acedido.
- **ConfigurationMode**: Especifica a forma como o Gestor de configuração Local, na verdade, aplica-se a configuração para os nós de destino. Pode demorar até os seguintes valores:
  - **ApplyOnly**: com esta opção, DSC aplica-se a configuração e faz nada adicional a menos que seja detetada uma nova configuração, por que o envio de uma nova configuração diretamente para o nó de destino ou se estiver a ligar a um serviço de solicitação e DSC Deteta uma configuração de novo quando verifica com o serviço de extração. Se a configuração do nó de destino drifts, não é necessária nenhuma ação.
  - **ApplyAndMonitor**: com esta opção (que é a predefinição), DSC se aplica a todas as novas configurações, se enviado por si diretamente para o nó de destino ou detetados num serviço de extração. Depois disso, se a configuração do nó de destino drifts no ficheiro de configuração, DSC relatórios discrepância nos registos. Para obter mais informações sobre o registo DSC, consulte [utilizar registos de eventos para diagnosticar erros na configuração de estado pretendido](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
  - **ApplyAndAutoCorrect**: com esta opção, DSC aplica-se todas as novas configurações, quer enviado por si diretamente para o nó de destino ou detetados num serviço de extração. Depois disso, se a configuração do nó de destino drifts no ficheiro de configuração, DSC relatórios discrepância nos registos e, em seguida, tenta ajustar a configuração do nó de destino para colocar em conformidade com o ficheiro de configuração.
- **ConfigurationModeFrequencyMins**: representa a frequência (em minutos) na qual a aplicação de segundo plano do DSC tenta implementar a configuração atual no nó de destino. O valor predefinido é 15. Este valor pode ser definido em conjunto com RefreshMode. Quando RefreshMode está definida como SOLICITAÇÃO, o nó de destino contacta o serviço de configuração de um intervalo definido pelo RefreshFrequencyMins e transfere a configuração atual. Independentemente do valor de RefreshMode no intervalo definido pelo ConfigurationModeFrequencyMins, o motor de consistência aplica-se a configuração mais recente que foi transferida para o nó de destino. RefreshFrequencyMins deve ser definido como um número inteiro múltiplo de ConfigurationModeFrequencyMins.
- **Credencial**: indica as credenciais (tal como acontece com Get-Credential) necessárias para aceder a recursos remotos, tais como contactar o serviço de configuração.
- **DownloadManagerCustomData**: representa uma matriz que contenha dados personalizado específicos para o Gestor de transferências.
- **DownloadManagerName**: indica o nome da configuração e o Gestor de transferências do módulo.
- **RebootNodeIfNeeded**: determinadas alterações de configuração num nó de destino podem requerer que ser reiniciado para que as alterações sejam aplicadas. Com o valor **verdadeiro**, esta propriedade irá reiniciar o nó assim que a configuração foi completamente aplica-se, sem aviso adicional. Se **falso** (o valor predefinido), será possível concluir a configuração, mas o nó tem de ser reiniciado manualmente para que as alterações entrem em vigor.
- **RefreshFrequencyMins**: utilizado quando configurou um serviço de extração. Representa a frequência (em minutos) em que o Gestor de configuração Local entra em contacto com um serviço de solicitação para transferir a configuração atual. Este valor pode ser definido em conjunto com ConfigurationModeFrequencyMins. Quando RefreshMode está definida como SOLICITAÇÃO, o nó de destino contacta o serviço de extração com um intervalo definido pelo RefreshFrequencyMins e transfere a configuração atual. No intervalo definido pelo ConfigurationModeFrequencyMins, o motor de consistência, em seguida, aplica a configuração mais recente que foi transferida para o nó de destino. Se RefreshFrequencyMins não está definido para um número inteiro múltiplo de ConfigurationModeFrequencyMins, o sistema o irá arredondar por excesso. O valor predefinido é 30.
- **RefreshMode**: os valores possíveis são **Push** (predefinição) e **solicitar**. A configuração de "push", tem de colocar um ficheiro de configuração em cada nó de destino, utilizando qualquer computador cliente. No modo de "solicitação", tem de configurar um serviço de solicitação para o Local do Configuration Manager para contactar e aceder aos ficheiros de configuração.

### <a name="example-of-updating-local-configuration-manager-settings"></a>Exemplo de atualizar as definições do Gestor de configuração locais

Pode atualizar as definições do Gestor de configuração de locais de um nó de destino, incluindo um **LocalConfigurationManager** bloquear dentro do bloco de nó no script de configuração, conforme mostrado no exemplo seguinte.

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
Para aplicar as definições, pode utilizar o **conjunto DscLocalConfigurationManager** cmdlet, conforme mostrado no exemplo seguinte.

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> **Tenha em atenção**: para o **caminho** parâmetro, tem de especificar o mesmo caminho que especificou para o **OutputPath** parâmetro quando invocado a configuração no exemplo anterior.

Para ver as definições atuais do Gestor de configuração locais, pode utilizar o **Get-DscLocalConfigurationManager** cmdlet.
Se invocar este cmdlet sem parâmetros, por predefinição, irá obter as definições do Gestor de configuração locais para o nó em que executa.
Para especificar outro nó, utilize o **CimSession** parâmetro com este cmdlet.
