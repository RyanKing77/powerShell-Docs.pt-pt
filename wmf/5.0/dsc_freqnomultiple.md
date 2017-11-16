---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 30055cff87159df98029e25409782e0fe2f0bae4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>Frequências para RefreshMode e ConfigurationMode não precisam de ser em múltiplos de si

Na versão anterior do DSC, deverá tratar o MMC `RefreshFrequencyMins` e `ConfigurationModeFrequencyMins` como múltiplos de si. WMF 5.0 RTM, estas propriedades são processadas independentes entre si. 

Para obter mais informações, consulte [configurar o Gestor de configuração Local](https://msdn.microsoft.com/powershell/dsc/metaconfig).

