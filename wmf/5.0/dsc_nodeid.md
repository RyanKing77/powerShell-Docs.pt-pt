---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 6d94de2d3f2c551219d8fbe5badb6e5bb913d796
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="separation-of-node-and-configuration-ids"></a>Separação dos IDs de Nó e de Configuração

## <a name="overview"></a>Descrição geral

Para fornecer uma experiência mais flexível e simplificada quando o DSC no modo de extração, foi adicionado um número de funcionalidades nesta versão. Estas funcionalidades são concebidas para permitir que tem a flexibilidade para configurar e implementar configurações em vários nós, enquanto ainda estado e comunicar informações para cada nó individualmente facilmente.
Estas funcionalidades são os seguintes:

* Um nome de configuração que identifica a configuração de um computador. Este nome pode ser partilhado por vários nós de destino
* Um ID de agente que identifica exclusivamente um único nó
* Um passo de registo que só ocorre pela primeira vez um nó de destino estabelece ligação a um servidor de solicitação

**Nota:** estas funções e funcionalidades foram adicionadas e não substituem os conceitos e funcionalidades existentes de extração. Pode utilizar estas novas funcionalidades ou antigos com o novo servidor de solicitação envio nesta versão.

Para obter mais informações, consulte [configurar um cliente de solicitação utilizando nomes de configuração](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)