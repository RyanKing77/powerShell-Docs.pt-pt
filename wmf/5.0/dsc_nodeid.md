---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685761"
---
# <a name="separation-of-node-and-configuration-ids"></a>Separação dos IDs de Nó e de Configuração

## <a name="overview"></a>Descrição geral

Para fornecer uma experiência mais flexível e simplificada ao utilizar o DSC no modo de solicitação, adicionámos várias funcionalidades nesta versão. Estas funcionalidades destinam-se para permitir que tem a flexibilidade de facilmente configurar e implementar configurações em vários nós, enquanto ainda controlar o estado e informações para cada nó de relatórios individualmente.
Esses recursos são os seguintes:

* Um nome de configuração que identifica a configuração de um computador. Este nome pode ser partilhado por vários nós de destino
* Um ID de agente que identifica exclusivamente um único nó
* Um passo de registo que ocorre apenas na primeira vez que um nó de destino se liga a um servidor de solicitação

**Nota:** Esses recursos e funcionalidades foram adicionadas e não substituir o existente de solicitação de funcionalidades e conceitos. Pode usar esses novos recursos ou antigos com o novo servidor de solicitação de envio nesta versão.

Para obter mais informações, consulte [como configurar um cliente de solicitação através de nomes de configuração](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)
