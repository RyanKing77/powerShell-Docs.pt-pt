---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a3ac215396206fba62bce303733429d60722ee6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218387"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="1b5fc-102">Frequências para RefreshMode e ConfigurationMode não precisam de ser em múltiplos de si</span><span class="sxs-lookup"><span data-stu-id="1b5fc-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="1b5fc-103">Na versão anterior do DSC, deverá tratar o MMC `RefreshFrequencyMins` e `ConfigurationModeFrequencyMins` como múltiplos de si.</span><span class="sxs-lookup"><span data-stu-id="1b5fc-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="1b5fc-104">WMF 5.0 RTM, estas propriedades são processadas independentes entre si.</span><span class="sxs-lookup"><span data-stu-id="1b5fc-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="1b5fc-105">Para obter mais informações, consulte [configurar o Gestor de configuração Local](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="1b5fc-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
