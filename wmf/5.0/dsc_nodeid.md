---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 5b9eea1c90bfd5a8cee3897d832bf7775a750308
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="separation-of-node-and-configuration-ids"></a>Separação do nó e IDs de configuração

## <a name="overview"></a>Descrição geral

Para fornecer uma experiência mais flexível e simplificada quando o DSC no modo de extração, foi adicionado um número de funcionalidades nesta versão. Estas funcionalidades são concebidas para permitir que tem a flexibilidade para configurar e implementar configurações em vários nós, enquanto ainda estado e comunicar informações para cada nó individualmente facilmente. Estas funcionalidades são os seguintes:

* Um nome de configuração que identifica a configuração de um computador. Este nome pode ser partilhado por vários nós de destino 
* Um ID de agente que identifica exclusivamente um único nó
* Um passo de registo que só ocorre pela primeira vez um nó de destino estabelece ligação a um servidor de solicitação

**Nota:** estas funções e funcionalidades foram adicionadas e não substituem os conceitos e funcionalidades existentes de extração. Pode utilizar estas novas funcionalidades ou antigos com o novo servidor de solicitação envio nesta versão.

Para obter mais informações, consulte [configurar um cliente de solicitação utilizando nomes de configuração](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)

