---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: a565f2befddc32f5088fa3e158f58d2dd78d41b4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Suporte de controlo de versões de módulo de lado a lado dos recursos de DSC

Os módulos que contêm recursos de DSC podem ser instalados lado a lado e configurações de DSC podem utilizar uma versão específica do recurso que está instalado no sistema.

Para obter mais informações, consulte [através de recursos com várias versões](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Problemas conhecidos

Nesta versão, os seguintes são problemas conhecidos da instalação lado a lado:

-   Não é suportada a utilizar duas versões diferentes do recurso dentro da mesma configuração de DSC.