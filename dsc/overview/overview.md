---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Windows PowerShell Desired State Configuration descrição-geral
ms.openlocfilehash: 3e4f0afa17ab60bfa98f1b86b9830462a7c8e1cf
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405268"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Windows PowerShell Desired State Configuration descrição-geral

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC é uma plataforma de gestão do PowerShell que permite-lhe gerir o departamento de TI e a infraestrutura de desenvolvimento com a configuração como código.

- Para obter uma descrição geral dos benefícios comerciais do uso de DSC, veja [Desired State Configuration descrição geral para os tomadores de decisão](decisionMaker.md).
- Para uma descrição geral dos benefícios da utilização do DSC engenharia, consulte [Desired State Configuration descrição geral para engenheiros de](DscForEngineers.md).
- Para começar a utilizar rapidamente o DSC, veja [guia de introdução do DSC](../quickstarts/website-quickstart.md).

## <a name="key-concepts"></a>Conceitos-chave

DSC é uma plataforma declarativa usada para configuração, implantação e gerenciamento de sistemas. Esta é composta por três componentes principais:

- [Configurações](../configurations/configurations.md) são scripts do PowerShell declarativas que definem e configure as instâncias de recursos.
    Após executar a configuração, DSC (e os recursos a ser chamados pela configuração) será simplesmente "que isso", garantindo que o sistema existe no Estado disposto pela configuração.
    As configurações de DSC também são idempotentes: o Gestor de configuração Local (LCM) irá continuar a garantir que as máquinas estão configuradas em tudo o que a configuração de estado declara.
- [Recursos](../resources/resources.md) são a parte "tornam isso" do DSC. Eles contêm o código que coloca e manter o destino de uma configuração no estado especificado.
    Recursos residem em módulos do PowerShell e podem ser escritos para modelar algo tão genérico, um arquivo ou um processo do Windows ou o mais específico que um servidor IIS ou uma VM em execução no Azure.
- O [Gestor de configuração Local (LCM)](../managing-nodes/metaConfig.md) é o mecanismo pelo qual o DSC facilita a interação entre os recursos e configurações.
    O LCM consulta regularmente o sistema usando o fluxo de controlo implementado pelos recursos para garantir que o estado definido por uma configuração é mantido.
    Se o sistema está sem estado, o LCM faz chamadas para o código em recursos para "tornam isso", de acordo com a configuração.

## <a name="see-also"></a>Consulte Também

- [Configurações de DSC](../configurations/configurations.md)
- [Recursos de DSC](../resources/resources.md)
- [Configurar o Gestor de configuração Local](../managing-nodes/metaConfig.md)
