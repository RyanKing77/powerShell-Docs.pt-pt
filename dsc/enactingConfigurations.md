---
ms.date: 10/16/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Aplicar configurações
ms.openlocfilehash: 28ca852eb00298c229be8104ecdfeabc47a10abc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="enacting-configurations"></a>Aplicar configurações

>Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

Existem duas formas de enact configurações do PowerShell pretendido Estado Configuration (DSC): push modo e o modo de extração.

## <a name="push-mode"></a>Modo de push

![Modo de push](images/pushModel.png "como push funciona do modo")

Modo de push refere-se a um utilizador ativamente aplicar uma configuração para um nó de destino ao chamar o [início DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.

Depois de criar e compilar uma configuração, pode enact-lo no modo de push chamando a [início DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, definir o parâmetro - Path do cmdlet para o caminho onde está localizada a configuração MOF.
Por exemplo, se a configuração MOF está localizada em `C:\DSC\Configurations\localhost.mof`, seria aplicá-la para o computador local com o seguinte comando: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Tenha em atenção__: por predefinição, o DSC é executada uma configuração como uma tarefa em segundo plano. Para executar a configuração de forma interativa, chame o [início DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) com o __-aguarde__ parâmetro.

## <a name="pull-mode"></a>Modo de extração

![Modo de extração](images/pullModel.png "como funciona do modo de extração")

No modo de extração, os clientes de extração estão configurados para obter as respetivas configurações de estado pretendido de um serviço de solicitação remoto.
Da mesma forma, o serviço de solicitação tiver sido configurado para o serviço anfitrião de DSC e tiver sido aprovisionado com as configurações e os recursos que são necessários para os clientes de extração.
Cada um dos clientes de solicitação tem um evento agendado que efetua uma verificação de compatibilidade periódica na configuração do nó.
Quando o evento é acionado pela primeira vez, o Gestor de configuração Local (MMC) no cliente solicitação faz um pedido para o serviço de extração para obter a configuração especificada no MMC.
Se essa configuração existe no serviço de solicitação e transmite-as verificações de validação inicial, a configuração é transferida para o cliente de solicitação, onde, em seguida, é executada através do MMC.

O MMC verifica se o cliente está em conformidade com a configuração em intervalos regulares especificado pelo **ConfigurationModeFrequencyMins** propriedade a MMC.
O MMC verifica a existência de configurações atualizadas no serviço de solicitação em intervalos regulares especificados pelo **RefreshModeFrequency** propriedade a MMC.
Para obter informações sobre como configurar o MMC, consulte [configurar o Gestor de configuração Local](metaConfig.md).

A solução recomendada para alojar um serviço de extração é o serviço de nuvem de DSC [da automatização do Azure](https://azure.microsoft.com/services/automation/).
Isto está alojado fornece a solução de gestão gráficas, relatórios e administração centralizada.

Para obter mais informações sobre como configurar um serviço de solicitação no Windows Server, consulte [configurar um servidor de solicitação do DSC web](pullServer.md).
No entanto, de compreender que esta implementação limitou as funcionalidades e exigir algumas integração "fazê-lo a próprio".

Os tópicos seguintes explicam o serviço de extração e os clientes:

- [Descrição geral do DSC da automatização do Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [Configurar um servidor de solicitação do SMB](pullServerSMB.md)
- [Configurar um cliente de solicitação](pullClientConfigID.md)