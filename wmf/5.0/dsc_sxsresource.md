---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0543afbc72148b1ba713e59655126c069b16ef33
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Suporte de controlo de versões de módulo de lado a lado dos recursos de DSC

Os módulos que contêm recursos de DSC podem ser instalados lado a lado e configurações de DSC podem utilizar uma versão específica do recurso que está instalado no sistema.

Para obter mais informações, consulte [através de recursos com várias versões](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Problemas conhecidos

Nesta versão, os seguintes são problemas conhecidos da instalação lado a lado:

-   Não é suportada a utilizar duas versões diferentes do recurso dentro da mesma configuração de DSC.
