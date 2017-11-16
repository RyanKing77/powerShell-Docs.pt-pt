---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 3261e5a07b8181190a04de3f210da50f23bb2953
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Suporte de controlo de versões de módulo de lado a lado dos recursos de DSC

Os módulos que contêm recursos de DSC podem ser instalados lado a lado e configurações de DSC podem utilizar uma versão específica do recurso que está instalado no sistema.

Para obter mais informações, consulte [através de recursos com várias versões](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Problemas conhecidos

Nesta versão, os seguintes são problemas conhecidos da instalação lado a lado:

-   Não é suportada a utilizar duas versões diferentes do recurso dentro da mesma configuração de DSC.

