---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: e1faf71436c8ba0ae02a166ce06d03de9f66f094
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>Frequências para RefreshMode e ConfigurationMode não precisam de ser em múltiplos de si

Na versão anterior do DSC, deverá tratar o MMC `RefreshFrequencyMins` e `ConfigurationModeFrequencyMins` como múltiplos de si. WMF 5.0 RTM, estas propriedades são processadas independentes entre si.

Para obter mais informações, consulte [configurar o Gestor de configuração Local](https://msdn.microsoft.com/powershell/dsc/metaconfig).