---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a>Informações detalhadas sobre o estado de MMC

Efetuamos melhorias no expor os detalhes sobre o estado do MMC. LCMState que é devolvido pelo Get-DscLocalConfigurationManager agora pode conter os seguintes valores:

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Adicionámos tem também uma propriedade de LCMStateDetail contém mais informações sobre o estado.