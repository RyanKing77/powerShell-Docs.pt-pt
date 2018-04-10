---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Descrição geral da configuração do estado pretendido do Windows PowerShell
ms.openlocfilehash: 3f357ea11a388a05b73539a63e52e639ee906f68
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Descrição geral da configuração do estado pretendido do Windows PowerShell

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

DSC é uma plataforma de gestão do PowerShell que permite-lhe gerir o seu departamento de TI e a infraestrutura de desenvolvimento com a configuração como código.

- Para obter uma descrição geral das vantagens empresariais do DSC a utilizar, consulte [Desired Configuration descrição geral do Estado para os decisores](decisionMaker.md).
- Para obter uma descrição geral das vantagens de utilizar o DSC engenharia, consulte [Desired Configuration descrição geral do Estado para engenheiros](DscForEngineers.md).
- Para começar a utilizar o DSC rapidamente, consulte o artigo [início rápido do DSC](quickStart.md).

## <a name="key-concepts"></a>Conceitos chave

DSC é uma plataforma declarativa utilizada para gestão de sistemas, implementação e configuração. É composto por três componentes principais:

- [Configurações](configurations.md) são scripts do PowerShell declarativas que definirem e configurar as instâncias de recursos.
    Após executar a configuração, DSC (e os recursos a ser chamados na configuração da) irá simplesmente "torná-lo,", garantindo que o sistema existe no Estado disposto na configuração.
    Configurações de DSC são também idempotent: o Gestor de configuração Local (MMC) irá continuar a garantir que as máquinas estão configuradas em que a configuração de estado declara.
- [Recursos](resources.md) fazem parte "torná-la para" do DSC. Contêm o código que colocar e manter o destino de uma configuração no estado especificado.
    Recursos residem em módulos do PowerShell e podem ser escritos para modelar algo como genérica como um ficheiro ou de um processo do Windows ou tão específico como um servidor IIS ou uma VM em execução no Azure.
- O [Gestor de configuração Local (MMC)](metaConfig.md) é o motor através do qual o DSC facilita a interação entre os recursos e configurações.
    O MMC consulta regularmente o sistema utilizando o fluxo de controlo implementado por recursos para se certificar de que o estado definido por uma configuração é mantido.
    Se o sistema está fora do Estado, o MMC faz com que chamadas para o código de recursos para "torná-lo,", de acordo com a configuração.

## <a name="see-also"></a>Consulte Também

- [Configurações de DSC](configurations.md)
- [Recursos de DSC](resources.md)
- [Configurar o Gestor de configuração Local](metaConfig.md)