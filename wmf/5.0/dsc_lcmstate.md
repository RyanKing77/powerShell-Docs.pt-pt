---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219866"
---
# <a name="detailed-information-about-lcm-state"></a>Informações detalhadas sobre o estado de MMC

Efetuamos melhorias no expor os detalhes sobre o estado do MMC. LCMState que é devolvido pelo Get-DscLocalConfigurationManager agora pode conter os seguintes valores:

* **Inativo**
* **Ocupado**
* **PendingReboot**
* **PendingConfiguration**

Adicionámos tem também uma propriedade de LCMStateDetail contém mais informações sobre o estado.
