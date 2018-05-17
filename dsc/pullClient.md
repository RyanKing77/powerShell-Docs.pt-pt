---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Configurar um cliente de solicitação do DSC
ms.openlocfilehash: 7f8758bd7145518e30e9c28b74d0db5d74dfaab3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-dsc-pull-client"></a>Configurar um cliente de solicitação do DSC

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> O servidor de solicitação (funcionalidade do Windows *DSC serviço*) é um componente suportado do Windows Server no entanto, são não planos para oferecer novas funcionalidades ou capacidades. É recomendado para começar a transição geridos os clientes [Automation DSC do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação no Windows Server) ou uma das soluções de Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).

Cada nó de destino tem de ser disse para utilizar o modo de extração e determinados a localização do ficheiro ou URL em que podem contactar o servidor de solicitação para obter recursos e configurações e, em que deve enviar dados de relatório.

Os tópicos seguintes explicam como configurar clientes de extração:

* [Configurar um cliente de solicitação através de nomes de configuração](pullClientConfigNames.md)
* [Configurar um cliente de solicitação através de IDs de configuração](pullClientConfigID.md)

> **Tenha em atenção**: estes tópicos que se aplicam ao PowerShell 5.0. Para configurar um cliente de solicitação no PowerShell 4.0, consulte [configurar um cliente de extração com o ID de configuração no PowerShell 4.0](pullClientConfigID4.md).