---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="detailed-information-about-lcm-state"></a>Informações detalhadas sobre o estado de MMC

Efetuamos melhorias no expor os detalhes sobre o estado do MMC. LCMState que é devolvido pelo Get-DscLocalConfigurationManager agora pode conter os seguintes valores:

* **Inativo**
* **Ocupado**
* **PendingReboot**
* **PendingConfiguration**

Adicionámos tem também uma propriedade de LCMStateDetail contém mais informações sobre o estado.

