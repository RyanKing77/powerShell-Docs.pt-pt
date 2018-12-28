---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Como configurar um cliente de solicitação de DSC
ms.openlocfilehash: b7cd6dc0087eb8368c5467df4c3c7266ed704451
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404692"
---
# <a name="setting-up-a-dsc-pull-client"></a>Como configurar um cliente de solicitação de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> O servidor de solicitação (recurso do Windows *DSC-serviço*) é um componente suportado do Windows Server no entanto, não existem planos para oferecer novas funcionalidades ou capacidades. É recomendado para começar a fazer a transição geridos os clientes [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação de mensagens em fila no Windows Server) ou uma das soluções da Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).

Cada nó de destino deve ser informado para utilizar o modo de solicitação e tendo em conta a localização do ficheiro ou URL onde ele pode contactar o servidor de solicitação para obter recursos e configurações, e onde ele deve enviar dados de relatório.

Os tópicos seguintes explicam como configurar clientes de extração:

* [Configurar um cliente de solicitação através de nomes de configuração](pullClientConfigNames.md)
* [Configurar um cliente de solicitação através de IDs de configuração](pullClientConfigID.md)

> **Tenha em atenção**: Estes tópicos que se aplicam ao PowerShell 5.0. Para configurar um cliente de solicitação no PowerShell 4.0, consulte [como configurar um cliente de solicitação com o ID de configuração no PowerShell 4.0](pullClientConfigID4.md).