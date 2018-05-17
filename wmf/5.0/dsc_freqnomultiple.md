---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a3ac215396206fba62bce303733429d60722ee6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>Frequências para RefreshMode e ConfigurationMode não precisam de ser em múltiplos de si

Na versão anterior do DSC, deverá tratar o MMC `RefreshFrequencyMins` e `ConfigurationModeFrequencyMins` como múltiplos de si. WMF 5.0 RTM, estas propriedades são processadas independentes entre si.

Para obter mais informações, consulte [configurar o Gestor de configuração Local](https://msdn.microsoft.com/powershell/dsc/metaconfig).
