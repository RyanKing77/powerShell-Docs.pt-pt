---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5b31fe833fb0f9d0f3f2733e777e4608a697d583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057932"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Suporte de controlo de versões do módulo lado a lado para recursos de DSC

Módulos que contêm recursos de DSC podem ser instalada lado a lado e configurações de DSC podem utilizar uma versão específica do recurso que está instalado no sistema.

Para obter mais informações, consulte [utilizar recursos com várias versões](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Problemas conhecidos

Nesta versão, os seguintes são problemas conhecidos da instalação lado a lado:

-   Não é suportado para o utilizar duas versões diferentes do recurso de DSC na configuração do mesmo.
