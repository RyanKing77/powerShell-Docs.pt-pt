---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085801"
---
# <a name="detailed-information-about-lcm-state"></a>Informações detalhadas sobre o estado LCM

Fizemos melhorias em expor detalhes sobre o estado do LCM. O que é devolvido pelo Get-dsclocalconfigurationmanager para LCMState agora pode conter os seguintes valores:

* **Idle**
* **Ocupado**
* **PendingReboot**
* **PendingConfiguration**

Também adicionámos uma propriedade de LCMStateDetail que contém mais informações sobre o estado.
