---
ms.date: 10/16/2017
keywords: DSC, powershell, configuração, a configuração
title: Aplicar configurações
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079953"
---
# <a name="enacting-configurations"></a>Aplicar configurações

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Existem duas formas adotar configurações de PowerShell Desired State Configuration (DSC): o modo de solicitação e de push.

## <a name="push-mode"></a>Modo de push

![Modo push](../images/pushModel.png "como push funciona de modo")

Modo push refere-se a um utilizador ativamente aplicar uma configuração para um nó de destino ao chamar o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.

Depois de criar e compilar uma configuração, pode aplicá-lo no modo push ao chamar o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet, definindo o parâmetro - Path do cmdlet para o caminho onde está localizada a MOF de configuração.
Por exemplo, se a MOF de configuração está localizada em `C:\DSC\Configurations\localhost.mof`, poderia aplicá-lo na máquina local com o seguinte comando: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Tenha em atenção__: Por predefinição, o DSC é executada uma configuração como uma tarefa em segundo plano. Para executar a configuração de forma interativa, chame o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) com o __-aguardar__ parâmetro.

## <a name="pull-mode"></a>Modo de solicitação

![Modo de solicitação](../images/pullModel.png "funciona de modo por solicitação")

No modo de solicitação, os clientes de pull são configurados para obter as respetivas configurações de estado pretendido de um serviço pull de remoto.
Da mesma forma, o serviço de pull foi configurado para o serviço de anfitrião do DSC e tiver sido aprovisionado com as configurações e os recursos que são necessários para os clientes de pull.
Cada um dos clientes pull tem um evento agendado que realiza uma verificação de conformidade periódica na configuração do nó.
Quando o evento é acionado pela primeira vez, o Gestor de configuração Local (LCM) no cliente de solicitação faz um pedido para o serviço de extração para obter a configuração especificada no LCM.
Se essa configuração existe no serviço de solicitação e passa as verificações de validação inicial, a configuração é transferida para o cliente de solicitação, onde, em seguida, é executada pelo LCM.

O LCM verifica que o cliente está em conformidade com a configuração em intervalos regulares, especificado pelos **ConfigurationModeFrequencyMins** propriedade do LCM.
O LCM verifica a existência de configurações atualizadas no serviço pull em intervalos regulares, especificados pelos **RefreshModeFrequency** propriedade do LCM.
Para obter informações sobre como configurar o LCM, consulte [configurar o Gestor de configuração Local](../managing-nodes/metaConfig.md).

A solução recomendada para hospedar um serviço de solicitação, é o serviço de nuvem de DSC [automatização do Azure](https://azure.microsoft.com/services/automation/).
Isso está alojado a solução fornece gestão gráficas, relatórios e administração centralizada.

Para obter mais informações sobre como configurar um serviço Pull no Windows Server, consulte [como configurar um servidor de solicitação do DSC web](pullServer.md).
No entanto, a compreender que essa implementação tiver recursos limitados e exige alguns integração "faça mesmo".

Os tópicos seguintes explicam o serviço de solicitação e clientes:

- [Descrição geral de DSC de automatização do Azure](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Como configurar um servidor de solicitação SMB](pullServerSMB.md)
- [Configurar um cliente de solicitação](pullClientConfigID.md)
