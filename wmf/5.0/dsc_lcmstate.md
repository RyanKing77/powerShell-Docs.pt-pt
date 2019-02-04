---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685747"
---
# <a name="detailed-information-about-lcm-state"></a>Informações detalhadas sobre o estado LCM

Fizemos melhorias em expor detalhes sobre o estado do LCM. O que é devolvido pelo Get-dsclocalconfigurationmanager para LCMState agora pode conter os seguintes valores:

* **Idle**
* **Ocupado**
* **PendingReboot**
* **PendingConfiguration**

Também adicionámos uma propriedade de LCMStateDetail que contém mais informações sobre o estado.
