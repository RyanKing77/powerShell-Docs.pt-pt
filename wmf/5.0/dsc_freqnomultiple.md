---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 23a5c8832f7c2888880a1ee846d75feaa95ebe47
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058408"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>As frequências para RefreshMode e ConfigurationMode não precisam de ser múltiplos entre si

Na versão anterior do DSC, trataria o LCM `RefreshFrequencyMins` e `ConfigurationModeFrequencyMins` em múltiplos entre si. No WMF 5.0 RTM, essas propriedades são processadas independentes umas das outras.

Para obter mais informações, consulte [configurar o Gestor de configuração Local](https://msdn.microsoft.com/powershell/dsc/metaconfig).
